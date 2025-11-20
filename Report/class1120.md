실행코드
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
수업과제
<img width="1311" height="805" alt="image" src="https://github.com/user-attachments/assets/cd570e5c-026c-4664-a084-a5ec598a8b27" />
