<img width="1536" height="756" alt="image" src="https://github.com/user-attachments/assets/b945933b-8f87-4fe5-8ec4-631fde0974c7" />

BinarySearch.asm
```
INCLUDE Irvine32.inc

; 프로시저를 미리 선언해서 undefined symbol 오류 방지
BinarySearch PROTO pArray:PTR DWORD, Count:DWORD, searchVal:DWORD

.data
array DWORD 10,20,30,40,50,60,70,80
arrSize = LENGTHOF array
targetVal DWORD 40                ; ← 이름을 targetVal로 변경하여 충돌 해결
msgFound BYTE "Value found at index: ",0
msgNotFound BYTE "Value not found.",0

.code
main PROC
    ; BinarySearch 호출
    INVOKE BinarySearch, ADDR array, arrSize, targetVal

    ; 결과 확인
    cmp eax, -1
    je NotFound

    ; 값 찾았을 때
    mov edx, OFFSET msgFound
    call WriteString
    call WriteInt        ; EAX에 인덱스가 들어있음
    call Crlf
    jmp EndProgram

NotFound:
    mov edx, OFFSET msgNotFound
    call WriteString
    call Crlf

EndProgram:
    exit
main ENDP

;--------------------------------------------------------------
; BinarySearch 프로시저
;--------------------------------------------------------------
BinarySearch PROC USES ebx edx esi edi,
    pArray:PTR DWORD,
    Count:DWORD,
    searchVal:DWORD
LOCAL first:DWORD, last:DWORD, mid:DWORD

    mov first,0
    mov eax,Count
    dec eax
    mov last,eax
    mov edi,searchVal
    mov ebx,pArray

L1:
    mov eax,first
    cmp eax,last
    jg L5

    mov eax,last
    add eax,first
    shr eax,1
    mov mid,eax

    mov esi,mid
    shl esi,2
    mov edx,[ebx+esi]

    cmp edx,edi
    jge L2

    mov eax,mid
    inc eax
    mov first,eax
    jmp L4

L2: cmp edx,edi
    jle L3

    mov eax,mid
    dec eax
    mov last,eax
    jmp L4

L3: mov eax,mid
    jmp L9

L4: jmp L1

L5: mov eax,-1

L9: ret
BinarySearch ENDP

END main
```
