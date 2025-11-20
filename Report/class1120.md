따로만들어본 Arraysum 실행코드
```
INCLUDE Irvine32.inc

.data 
array DWORD 10000h,20000h,30000h,40000h,50000h
theSum DWORD ?
msgDec BYTE "Decimal Sum: ",0 
msgHex BYTE "Hex Sum: ",0 

.code 
ArraySum PROC 
    push  esi
    push  ecx
    mov   eax,0

L1: add   eax,[esi]
    add   esi,TYPE DWORD
    loop  L1

    pop   ecx
    pop   esi
    ret
ArraySum ENDP

main PROC
    ; 1. 합계 계산
    mov   esi,OFFSET array
    mov   ecx,LENGTHOF array
    call  ArraySum              ; EAX에 합계 (F0000h) 반환
    mov   theSum,eax            ; theSum 변수에 저장

    ; 2. 16진수 출력
    mov   edx,OFFSET msgHex     ; "Hex Sum: " 출력
    call  WriteString
    mov   eax,theSum            ; 합계 값을 EAX에 로드
    call  WriteHex              ; 16진수 출력 (예: F0000)
    call  Crlf                  ; 줄 바꿈

    ; 3. 10진수 출력 (선택 사항)
    mov   edx,OFFSET msgDec     ; "Decimal Sum: " 출력
    call  WriteString
    mov   eax,theSum            ; 합계 값을 EAX에 로드
    call  WriteDec              ; 10진수 출력 (예: 983040)
    call  Crlf                  ; 줄 바꿈
    
    ; 4. 프로그램 종료
    INVOKE ExitProcess,0
main ENDP
END main
```
수업과제 (틀림)
<img width="1311" height="805" alt="image" src="https://github.com/user-attachments/assets/cd570e5c-026c-4664-a084-a5ec598a8b27" />

과제 안에 있는 코드들(정답)

<img width="1802" height="787" alt="image" src="https://github.com/user-attachments/assets/6b13df39-eb7c-4b7f-9f29-7eb66f6cd99a" />

## DisplaySum.asm
```
; DisplaySum Procedure (_display.asm)
INCLUDE Irvine32.inc
.code
;-----------------------------------------------------
DisplaySum PROC
; Displays the sum on the console.
; Receives:
; ptrPrompt ; offset of prompt string
; theSum ; the array sum (DWORD)
; Returns: nothing
;-----------------------------------------------------
theSum EQU [ebp+12]
ptrPrompt EQU [ebp+8]
enter 0,0
push eax
push edx
mov edx,ptrPrompt ; pointer to prompt
call WriteString
mov eax,theSum
call WriteInt ; display EAX
call Crlf
pop edx
pop eax
leave
ret 8 ; restore the stack
DisplaySum ENDP
END
```

## ArraySum.asm
```
; ArraySum Procedure (_arrysum.asm)
INCLUDE Irvine32.inc
.code
;-----------------------------------------------------
ArraySum PROC
;
; Calculates the sum of an array of 32-bit integers.
; Receives:
; ptrArray ; pointer to array
; arraySize ; size of array (DWORD)
; Returns: EAX = sum
;-----------------------------------------------------
ptrArray EQU [ebp+8]
arraySize EQU [ebp+12]
enter 0,0
push ecx ; don't push EAX
push esi
mov eax,0 ; set the sum to zero
mov esi,ptrArray
mov ecx,arraySize
cmp ecx,0 ; array size 

jle L2 ; yes: quit
L1: add eax,[esi] ; add each integer to sum
add esi,4 ; point to next integer
loop L1 ; repeat for array size
L2: pop esi
pop ecx ; return sum in EAX
leave
ret 8 ; restore the stack
ArraySum ENDP
END
```

## PromptForIntegers.asm
```

INCLUDE Irvine32.inc
.code
;----------------------------------------------------
PromptForIntegers PROC
; Prompts the user for an array of integers and fills
; the array with the user's input.
; Receives:
; ptrPrompt:PTR BYTE ; prompt string
; ptrArray:PTR DWORD ; pointer to array
; arraySize:DWORD ; size of the array
; Returns: nothing
;-----------------------------------------------------
arraySize EQU [ebp+16]
ptrArray EQU [ebp+12]
ptrPrompt EQU [ebp+8]
enter 0,0
pushad ; save all registers
mov ecx,arraySize
cmp ecx,0 ; array size 

jle L2 ; yes: quit
mov edx,ptrPrompt ; address of the prompt
mov esi,ptrArray
L1: call WriteString ; display string
call ReadInt ; read integer into EAX
call Crlf ; go to next output line
mov [esi],eax ; store in array
add esi,4 ; next integer
loop L1
L2: popad ; restore all registers
leave
ret 12 ; restore the stack
PromptForIntegers ENDP
END
```

## Sum_main.asm
```
; Integer Summation Program (Sum_main.asm)
; Multimodule example:
; This program inputs multiple integers from the user,
; stores them in an array, calculates the sum of the
; array, and displays the sum.
INCLUDE Irvine32.inc
EXTERN PromptForIntegers@0:PROC
EXTERN ArraySum@0:PROC, DisplaySum@0:PROC
; Redefine external symbols for convenience
ArraySum EQU ArraySum@0
PromptForIntegers EQU PromptForIntegers@0
DisplaySum EQU DisplaySum@0
; modify Count to change the size of the array:
Count = 3
.data
prompt1 BYTE "Enter a signed integer: ",0
prompt2 BYTE "The sum of the integers is: ",0
array DWORD Count DUP(?)
sum DWORD ?
.code
main PROC
call Clrscr
; PromptForIntegers( addr prompt1, addr array, Count )
push Count
push OFFSET array
push OFFSET prompt1
call PromptForIntegers
; sum = ArraySum( addr array, Count )
push Count
push OFFSET array
call ArraySum
mov sum,eax
; DisplaySum( addr prompt2, sum )
push sum
push OFFSET prompt2
call DisplaySum
call Crlf
exit
main ENDP
END main
```
