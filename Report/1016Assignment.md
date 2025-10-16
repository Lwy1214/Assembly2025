
4장 어셈블리 문제풀이
# 4.9 Review Questions and Exercises 풀이

## 4.9.1 Short Answer (단답형 질문)

**1. 다음 코드 실행 후 EDX의 값은?**
```assembly
.data
one WORD 8002h
two WORD 4321h
.code
mov edx,21348041h
movsx edx,one ; (a)
movsx edx,two ; (b)
```

1.  **(a) `movsx edx,one`:** `one` ($8002h$)는 16비트 값이며 최상위 비트가 1이므로 음수입니다. `MOVSX` (부호 확장) 명령어는 상위 16비트를 1로 채웁니다.
    $$ EDX = FFFF8002h $$
2.  **(b) `movsx edx,two`:** `two` ($4321h$)는 최상위 비트가 0이므로 양수입니다. `MOVSX`는 상위 16비트를 0으로 채웁니다.
    $$ EDX = 00004321h $$

**2. 다음 코드 실행 후 EAX의 값은?**
```assembly
mov eax,1002FFFFh
inc ax
```
`inc ax`는 `AX`($FFFFh$)를 1 증가시키며, 결과는 $0000h$가 되고 상위 워드($1002h$)로 캐리가 전파됩니다.
$$ EAX = 10030000h $$

**3. 다음 코드 실행 후 EAX의 값은?**
```assembly
mov eax,30020000h
dec ax
```
`dec ax`는 `AX`($0000h$)를 1 감소시키며, 결과는 $FFFFh$가 되고 상위 워드($3002h$)에서 빌림(borrow)이 발생하여 $3001h$가 됩니다.
$$ EAX = 3001FFFFh $$

**4. 다음 코드 실행 후 EAX의 값은?**
```assembly
mov eax,1002FFFFh
neg ax
```
`neg ax`는 `AX`($FFFFh$)의 2의 보수(2's complement)를 계산합니다. $FFFFh$의 2의 보수는 $0001h$입니다.
$$ EAX = 10020001h $$

**5. 다음 코드 실행 후 패리티 플래그(Parity flag)의 값은?**
```assembly
mov al,1
add al,3
```
`ADD` 실행 후 `AL`의 값은 4 ($00000100b$)입니다. 패리티 플래그(PF)는 결과의 하위 바이트에 1의 개수가 짝수일 때 설정됩니다. `AL`은 1의 개수가 1개(홀수)이므로 PF는 **클리어(0)**됩니다.

**6. 다음 코드 실행 후 EAX와 부호 플래그(Sign flag)의 값은?**
```assembly
mov eax,5
sub eax,6
```
`SUB` 실행 후 `EAX`는 $-1$ ($FFFFFFFFh$)이 됩니다. 부호 플래그(SF)는 결과가 음수($FFFFFFFFh$의 MSB=1)일 때 **설정(1)**됩니다.
$$ EAX = FFFFFFFFh, SF = 1 $$

**7. 다음 코드에서 AL의 값이 부호 있는 바이트의 유효 범위 내에 있는지 판단하는 데 오버플로우 플래그(Overflow flag)가 어떻게 도움이 되는지 설명하시오.**
```assembly
mov al,-1
add al,130
```
8비트 부호 있는 정수 범위는 $-128$에서 $+127$입니다. 계산 결과는 $-1 + 130 = 129$입니다. $129$는 $+127$을 초과하므로 유효 범위를 벗어납니다. 오버플로우 플래그(OF)는 부호 있는 연산의 결과가 대상 레지스터의 부호 있는 범위를 초과할 때 **설정(1)**됩니다. 따라서 OF는 결과가 유효 범위를 벗어났음을 알려주므로 도움이 됩니다.

**8. 다음 명령어 실행 후 RAX의 값은?**
```assembly
mov rax,44445555h
```
32비트 상수를 64비트 레지스터(`RAX`)로 이동할 때, 상위 32비트는 **0으로 확장(Zero-Extended)**됩니다.
$$ RAX = 0000000044445555h $$

**9. 다음 명령어 실행 후 RAX의 값은?**
```assembly
.data
dwordVal DWORD 84326732h
.code
mov rax,0FFFFFFFF00000000h
mov rax,dwordVal
```
`DWORD` 변수($84326732h$)를 64비트 레지스터(`RAX`)로 이동할 때, 해당 값은 **0으로 확장**됩니다.
$$ RAX = 0000000084326732h $$

**10. 다음 명령어 실행 후 EAX의 값은?**
```assembly
.data
dVal DWORD 12345678h
.code
mov ax,3
mov WORD PTR dVal+2,ax
mov eax,dVal
```
`dVal` ($12345678h$)는 리틀 엔디안으로 메모리에 $78h, 56h, 34h, 12h$ 순서로 저장됩니다.
1.  `mov ax,3`: $\text{AX} = 0003h$.
2.  `mov WORD PTR dVal+2,ax`: 오프셋 +2에 $0003h$를 저장합니다. 메모리($34h, 12h$)는 $03h, 00h$로 바뀝니다 (LE 순서).
3.  `mov eax,dVal`: 메모리 내용 ($78h, 56h, 03h, 00h$)을 읽으면 $00035678h$가 됩니다.
    $$ EAX = 00035678h $$

**11. 다음 명령어 실행 후 EAX의 값은?**
```assembly
.data
.dVal DWORD ?
.code
mov dVal,12345678h
mov ax,WORD PTR dVal+2
add ax,3
mov WORD PTR dVal,ax
mov eax,dVal
```
1.  `mov dVal,12345678h`: 메모리($78h, 56h, 34h, 12h$).
2.  `mov ax,WORD PTR dVal+2`: 오프셋 +2의 워드(상위 워드 $1234h$)를 `AX`로 로드. $\text{AX} = 1234h$.
3.  `add ax,3`: $\text{AX} = 1237h$.
4.  `mov WORD PTR dVal,ax`: 오프셋 0에 $1237h$를 저장. 메모리($37h, 12h, 34h, 12h$).
5.  `mov eax,dVal`: 최종 메모리 내용을 읽으면 $12341237h$.
    $$ EAX = 12341237h $$

**12. 양의 정수와 음의 정수를 더하여 오버플로우 플래그를 설정하는 것이 가능한가?**
*   **아니요**. 오버플로우는 두 피연산자의 부호가 같을 때만 발생하며, 부호가 다르면 오버플로우는 발생하지 않습니다.

**13. 음의 정수와 음의 정수를 더하여 양의 결과가 나오는 경우 오버플로우 플래그가 설정되는가?**
*   **네**. 두 음수를 더했는데 결과가 양수가 나왔다면 (즉, 결과의 부호가 바뀌었다면) 오버플로우가 발생한 것입니다.

**14. NEG 명령어로 오버플로우 플래그를 설정하는 것이 가능한가?**
*   **네**. 목적지 피연산자가 올바르게 저장될 수 없는 경우 `NEG` 명령은 유효하지 않은 결과를 생성할 수 있으며, 이때 OF가 설정됩니다. 예를 들어, 가장 큰 음수 값(예: 8비트에서 $-128$, $80h$)을 `NEG`할 때 OF가 설정됩니다.

**15. 부호 플래그와 제로 플래그가 동시에 설정되는 것이 가능한가?**
*   **아니요**. 제로 플래그(ZF=1)는 결과가 0임을 의미하며, 0은 양수(SF=0)로 간주됩니다.

**16. 다음 명령어 중 유효한지(valid) 여부를 판단하시오.**
(데이터 정의: `var1 SBYTE -4,-2,3,1`, `var2 WORD 1000h,2000h,3000h,4000h`, `var3 SWORD -16,-42`, `var4 DWORD 1,2,3,4,5`)

| 명령어 | 유효성 | 설명 (Source 기반) |
| :--- | :--- | :--- |
| a. `mov ax,var1` | **유효하지 않음** | 크기가 다른 메모리 피연산자 간의 이동에는 확장 명령어(`MOVSX`/`MOVZX`) 또는 `PTR`이 필요합니다. |
| b. `mov ax,var2` | **유효함** | 16비트 메모리를 16비트 레지스터로 이동합니다. |
| c. `mov eax,var3` | **유효함 (MASM 허용)** | 16비트(`SWORD`)를 32비트(`EAX`)로 이동합니다. MASM은 메모리 크기에 따라 레지스터를 허용하지만, 명확하게는 `MOVSX`나 `MOVZX`를 사용해야 합니다. |
| d. `mov var2,var3` | **유효하지 않음** | 메모리 대 메모리 이동은 허용되지 않습니다. |
| e. `movzx ax,var2` | **유효하지 않음** | `MOVZX`는 작은 크기의 소스를 큰 크기의 대상으로 0 확장하는 데 사용되므로, 16비트 소스를 16비트 대상으로 이동하는 데는 적합하지 않습니다. |
| f. `movzx var2,al` | **유효하지 않음** | `MOVZX`의 목적지는 레지스터여야 합니다 (메모리 불가). |
| g. `mov ds,ax` | **유효함** | `DS`는 세그먼트 레지스터이며 `MOV` 명령의 목적지가 될 수 있습니다. |
| h. `mov ds,1000h` | **유효하지 않음** | 즉시 값(immediate value)은 세그먼트 레지스터로 직접 이동할 수 없습니다. |

**17. 다음 명령어 순서 실행 후 목적지 피연산자의 16진수 값은?**
(`var1 SBYTE -4,-2,3,1` $\rightarrow$ $FCh, FEh, 03h, 01h$)
```assembly
mov al,var1 ; a.
mov ah,[var1+3] ; b.
```
1.  a. `mov al,var1`: $\text{AL} = FCh$.
2.  b. `mov ah,[var1+3]`: `var1`의 4번째 바이트($01h$). $\text{AH} = 01h$.
    $$ \text{AX} = 01FCh $$

**18. 다음 명령어 순서 실행 후 목적지 피연산자의 값은?**
(`var2` $\rightarrow$ $1000h, 2000h, 3000h, 4000h$. `var3` $\rightarrow$ $FFF0h, FFD6h$)
```assembly
mov ax,var2 ; a.
mov ax,[var2+4] ; b.
mov ax,var3 ; c.
mov ax,[var3-2] ; d.
```
1.  a. `mov ax,var2`: `var2`의 첫 번째 워드($1000h$). $\text{AX} = 1000h$.
2.  b. `mov ax,[var2+4]`: `var2`는 16비트 배열이므로, 오프셋 +4는 세 번째 요소($3000h$)입니다. $\text{AX} = 3000h$.
3.  c. `mov ax,var3`: `var3`의 첫 번째 워드($FFF0h$). $\text{AX} = FFF0h$.
4.  d. `mov ax,[var3-2]`: `var3` 직전 2바이트는 `var2`의 마지막 워드($4000h$)입니다. $\text{AX} = 4000h$.

**19. 다음 명령어 순서 실행 후 EDX의 값은?**
(`var1` $\rightarrow$ $FCh$. `var2` $\rightarrow$ $1000h$. `var4` $\rightarrow$ $1, 2, 3, 4, 5$)
```assembly
mov edx,var4 ; a.
movzx edx,var2 ; b.
mov edx,[var4+4] ; c.
movsx edx,var1 ; d.
```
1.  a. `mov edx,var4`: `var4`의 첫 번째 `DWORD`($1$). $\text{EDX} = 1$.
2.  b. `movzx edx,var2`: `var2`의 첫 번째 `WORD`($1000h$)를 32비트로 **0 확장**. $\text{EDX} = 00001000h$.
3.  c. `mov edx,[var4+4]`: 오프셋 +4는 두 번째 `DWORD`($2$). $\text{EDX} = 2$.
4.  d. `movsx edx,var1`: `var1`의 첫 번째 `SBYTE`($FCh$)를 32비트로 **부호 확장**. $\text{EDX} = FFFFFFFFh$.

---

## 4.9.2 Algorithm Workbench (알고리즘 작업대)

**1. DWORD 변수 `three`의 상위 워드와 하위 워드를 교환하는 `MOV` 명령어 시퀀스를 작성하시오.**
```assembly
; three가 DWORD 변수라고 가정
mov ax, WORD PTR three+2  ; 상위 워드 (Offset +2)를 AX에 로드
xchg ax, WORD PTR three    ; AX (상위)와 하위 워드 (Offset 0)를 교환
mov WORD PTR three+2, ax   ; AX (원래 하위 워드)를 상위 워드 위치에 저장
```

**2. XCHG 명령을 세 번 이하로 사용하여 네 개의 8비트 레지스터(A, B, C, D)의 값을 B, C, D, A 순서로 재배열하시오.**
(AL=A, BL=B, CL=C, DL=D로 시작하여 AL=B, BL=C, CL=D, DL=A로 변경)
```assembly
xchg al, bl ; 결과: (B, A, C, D)
xchg bl, cl ; 결과: (B, C, A, D)
xchg cl, dl ; 결과: (B, C, D, A)
```

**3. AL 레지스터의 메시지 바이트($01110101$)가 짝수 패리티인지 홀수 패리티인지 판단하기 위해 패리티 플래그(PF)와 산술 명령어를 사용하는 방법을 보이시오.**
$01110101b$는 1이 5개(홀수)입니다. PF는 1의 개수가 짝수일 때 설정됩니다.
```assembly
mov al, 01110101b 
cmp al, 0             ; AL을 0과 비교하여 플래그 설정 (AL 값은 변경되지 않음)
                      ; CMP는 산술 연산(뺄셈)의 일종이므로 플래그를 수정합니다.
jp  EvenParityHandler ; PF=1이면 짝수 패리티. PF=0이므로 홀수 패리티입니다.
; PF=0일 경우, 이 위치에서 홀수 패리티 처리
```

**4. 8비트 피연산자를 사용하여 두 개의 음의 정수를 더하고 오버플로우 플래그(OF)가 설정되도록 하는 코드를 작성하시오.**
(8비트 최대 음수 범위는 $-128$에서 $+127$입니다. 두 음수를 더해 양수가 나와야 합니다.)
```assembly
mov al, -100 ; AL = 9Ch
add al, -100 ; 9Ch + 9Ch = 138h. AL = 38h (양수 56).
             ; 음수 + 음수 = 양수이므로 OF=1이 설정됩니다.
```

**5. 덧셈을 사용하여 제로 플래그(ZF)와 캐리 플래그(CF)를 동시에 설정하는 두 명령어 시퀀스를 작성하시오.**
(ZF=1은 결과 0, CF=1은 캐리 발생을 의미하며, 16비트에서 $FFFFh + 1$로 달성 가능)
```assembly
mov ax, 0FFFFh
add ax, 1    ; AX=0000h. ZF=1, CF=1.
```

**6. 뺄셈을 사용하여 캐리 플래그(CF)를 설정하는 두 명령어 시퀀스를 작성하시오.**
(뺄셈 시 CF는 부호 없는 $Destination < Source$일 때 빌림(borrow)이 필요하여 설정됩니다.)
```assembly
mov al, 5
sub al, 6 ; AL=FFh. 부호 없는 5 < 6이므로 CF=1.
```

**7. 어셈블리 언어로 다음 산술식을 구현하시오: $\text{EAX} = -\text{val2} + 7 - \text{val3} + \text{val1}$. (`val1`, `val2`, `val3`는 32비트 정수 변수라고 가정)**
```assembly
mov eax, val2     ; EAX = val2
neg eax           ; EAX = -val2
add eax, 7        ; EAX = -val2 + 7
sub eax, val3     ; EAX = -val2 + 7 - val3
add eax, val1     ; EAX = -val2 + 7 - val3 + val1
```

**8. 스케일 팩터와 인덱스 어드레싱을 사용하여 더블워드 배열을 반복하고 요소의 합을 계산하는 루프를 작성하시오.**
```assembly
.data
dArray DWORD 1, 2, 3, 4, 5
.code
mov eax, 0            ; EAX: 합계 저장
mov esi, 0            ; ESI: 인덱스 (0, 1, 2...)
mov ecx, LENGTHOF dArray ; ECX: 루프 카운터 (5)

L1:
    add eax, dArray[esi*4] ; 인덱스 어드레싱: ESI*4 (DWORD는 4바이트)
    inc esi                ; 인덱스 증가
loop L1
```

**9. 어셈블리 언어로 다음 식을 구현하시오: $\text{AX} = (\text{val2} + \text{BX}) - \text{val4}$. (`val2`와 `val4`는 16비트 정수 변수라고 가정)**
```assembly
mov ax, val2
add ax, bx
sub ax, val4
```

**10. 캐리 플래그(CF)와 오버플로우 플래그(OF)를 동시에 설정하는 두 명령어 시퀀스를 작성하시오.**
(`NEG` 명령을 사용하여 최대 음수 값의 2의 보수를 취하면 두 플래그가 모두 설정됩니다.)
```assembly
mov ax, 8000h ; 16비트에서 최대 음수 (-32768)
neg ax        ; AX=8000h. CF=1, OF=1.
```

**11. INC 및 DEC 명령어 실행 후 부호 없는 오버플로우를 나타내는 데 제로 플래그를 사용하는 명령어 시퀀스를 보이시오.**
(부호 없는 오버플로우는 `FFFFh + 1` 또는 `0000h - 1` 연산을 통해 ZF와 CF가 함께 설정되는 경우를 통해 확인합니다.)
```assembly
mov ax, 0FFFFh
inc ax             ; AX=0000h. ZF=1, CF=1
jz UnsignedOverflow ; ZF=1 이므로 점프
```

**다음 데이터 정의를 사용하여 12번부터 18번까지의 질문에 답하시오:**
`.data myBytes BYTE 10h,20h,30h,40h myWords WORD 3 DUP(?),2000h myString BYTE "ABCDE"`

**12. `myBytes`를 짝수 주소에 정렬하도록 지시어(directive)를 삽입하시오.**
```assembly
ALIGN 2 ; 2바이트 경계에 정렬
myBytes BYTE 10h,20h,30h,40h
```

**13. 다음 명령어 실행 후 EAX의 값은?**

| 명령어 | 계산 | EAX 값 | 근거 |
| :--- | :--- | :--- | :--- |
| a. `mov eax,TYPE myBytes` | `BYTE`의 크기 | $1$ | `TYPE`은 단일 요소의 크기를 반환. |
| b. `mov eax,LENGTHOF myBytes` | `myBytes`의 요소 개수 | $4$ | `LENGTHOF`는 배열의 요소 개수를 반환. |
| c. `mov eax,SIZEOF myBytes` | $4 \times 1$ (byte) | $4$ | `SIZEOF`는 `LENGTHOF` $\times$ `TYPE`과 동일. |
| d. `mov eax,TYPE myWords` | `WORD`의 크기 | $2$ | `WORD`는 2바이트. |
| e. `mov eax,LENGTHOF myWords` | `3 + 1` (4개 요소) | $4$ | `DUP` 연산자 사용. |
| f. `mov eax,SIZEOF myWords` | $4 \times 2$ (bytes) | $8$ | `SIZEOF`. |
| g. `mov eax,SIZEOF myString` | "ABCDE" (5개 문자) | $5$ | `SIZEOF`. |

**14. `myBytes`의 첫 두 바이트를 DX 레지스터로 이동하여 결과 값이 $2010h$가 되도록 하는 단일 명령어를 작성하시오.**
(리틀 엔디안이므로 $10h$가 $\text{DL}$에, $20h$가 $\text{DH}$에 저장되어 $\text{DX} = 2010h$가 되어야 합니다.)
```assembly
mov dx, WORD PTR myBytes
```

**15. `myWords`의 두 번째 바이트를 AL 레지스터로 이동하는 명령어를 작성하시오.**
(`myWords`는 16비트 배열이므로 두 번째 바이트는 오프셋 1에 있습니다.)
```assembly
mov al, [myWords+1]
```

**16. `myBytes`의 네 바이트 전체를 EAX 레지스터로 이동하는 명령어를 작성하시오.**
```assembly
mov eax, DWORD PTR myBytes
```

**17. `myWords`를 32비트 레지스터로 직접 이동할 수 있도록 `LABEL` 지시어를 삽입하시오.**
(`LABEL`을 사용하여 크기 속성만 변경합니다.)
```assembly
.data
myDWords LABEL DWORD ; myWords와 동일한 주소를 갖지만 크기는 DWORD
myWords WORD 3 DUP(?),2000h
```

**18. `myBytes`를 16비트 레지스터로 직접 이동할 수 있도록 `LABEL` 지시어를 삽입하시오.**
```assembly
.data
myWBytes LABEL WORD ; myBytes와 동일한 주소를 갖지만 크기는 WORD
myBytes BYTE 10h,20h,30h,40h
```

-------------------------------------------------------------------------------

# 4.10 Programming Exercises (프로그래밍 연습 문제)

**1. Converting from Big Endian to Little Endian (빅 엔디안을 리틀 엔디안으로 변환)**

**문제:** 아래 변수를 사용하여 `MOV` 명령어를 이용해 `bigEndian`의 값을 `littleEndian`으로 복사하고, 바이트 순서를 역순으로 만드십시오. 32비트 값은 16진수로 12345678*h*입니다.

```
.data
bigEndian BYTE 12h,34h,56h,78h
littleEndian DWORD ?

```

**풀이:** 리틀 엔디안(Little Endian) 시스템에서 DWORD 12345678*h*는 메모리에 78*h*,56*h*,34*h*,12*h* 순서로 저장됩니다. `bigEndian` 배열은 이미 12*h*,34*h*,56*h*,78*h* 순서로 바이트가 저장되어 있으므로, 이를 역순으로 `littleEndian`의 각 바이트 위치에 옮겨야 합니다.

```
mov al, bigEndian+3       ; 78h (Offset 3)를 AL에 로드
mov BYTE PTR littleEndian+0, al ; 78h를 littleEndian의 최하위 바이트에 저장

mov al, bigEndian+2       ; 56h (Offset 2)를 AL에 로드
mov BYTE PTR littleEndian+1, al ; 56h를 littleEndian의 다음 바이트에 저장

mov al, bigEndian+1       ; 34h (Offset 1)를 AL에 로드
mov BYTE PTR littleEndian+2, al ; 34h를 littleEndian의 다음 바이트에 저장

mov al, bigEndian+0       ; 12h (Offset 0)를 AL에 로드
mov BYTE PTR littleEndian+3, al ; 12h를 littleEndian의 최상위 바이트에 저장

```

**2. Exchanging Pairs of Array Values (배열 값 쌍 교환)**

**문제:** 짝수 개의 요소로 구성된 배열에서 모든 값의 쌍을 교환하는 루프와 인덱스 주소 지정을 사용하는 프로그램을 작성하십시오. 요소 *i*는 *i*+1과, *i*+2는 *i*+3과 교환되어야 합니다.

**풀이:** `DWORD` 배열이라 가정하고, 배열 길이의 절반만큼 반복하며 인접한 두 요소를 `XCHG` 명령어와 인덱스 주소 지정([esi], [esi+4])을 사용하여 교환합니다.

```
.data
dArray DWORD 10, 20, 30, 40 ; 예시 배열

.code
mov esi, OFFSET dArray
mov ecx, (LENGTHOF dArray) / 2 ; 루프는 길이의 절반만큼 실행

L1:
    mov eax, [esi]       ; dArray[i]를 EAX에 로드
    xchg eax, [esi+4]    ; EAX와 dArray[i+1]의 값을 교환 [7]
    mov [esi], eax       ; dArray[i]에 dArray[i+1]의 원래 값을 저장
    add esi, 8           ; 다음 쌍으로 이동 (4바이트 * 2 = 8바이트)
loop L1

```

**3. Summing the Gaps between Array Values (배열 값 사이의 간격 합산)**

**문제:** 반복문과 인덱스 주소 지정을 사용하여 연속적인 배열 요소 사이의 모든 간격의 합을 계산하는 프로그램을 작성하십시오. 배열 요소는 non-decreasing 순서로 배열된 doubleword입니다. (예: {0,2,5,9,10}의 간격 2,3,4,1, 합은 10).

**풀이:** 배열의 길이 *N*에 대해 *N*−1번 반복하며 arr[*i*+1]−arr[*i*]를 계산하고 합계 레지스터에 누적합니다.

```
.data
dArray DWORD 0, 2, 5, 9, 10
SumOfGaps DWORD 0

.code
mov esi, OFFSET dArray
mov ecx, (LENGTHOF dArray) - 1  ; N-1회 반복
mov ebx, 0                      ; EBX는 합계 누적 레지스터

L1:
    mov eax, [esi+4]          ; EAX = arr[i+1]
    sub eax, [esi]            ; EAX = arr[i+1] - arr[i] (간격 계산) [9]
    add ebx, eax              ; EBX에 간격 합산 [6]
    add esi, 4                ; ESI를 다음 요소(arr[i+1])의 시작으로 이동
loop L1

mov SumOfGaps, ebx

```

**4. Copying a Word Array to a DoubleWord array (워드 배열을 더블워드 배열로 복사)**

**문제:** 루프를 사용하여 부호 없는 Word(16비트) 배열의 모든 요소를 부호 없는 Doubleword(32비트) 배열로 복사하는 프로그램을 작성하십시오.

**풀이:** 16비트 소스 값을 32비트 대상으로 옮길 때, 부호 없는 정수이므로 `MOVZX` 명령어를 사용하여 상위 16비트를 0으로 확장해야 합니다.

```
.data
wArray WORD 1000h, 2000h, 3000h
dArray DWORD (LENGTHOF wArray) DUP(?)

.code
mov esi, OFFSET wArray
mov edi, OFFSET dArray
mov ecx, LENGTHOF wArray

L1:
    movzx eax, WORD PTR [esi] ; 16비트 값을 32비트로 0 확장 [10, 11]
    mov [edi], eax            ; 32비트 대상에 저장
    add esi, TYPE WORD        ; ESI 2바이트 증가 [12]
    add edi, TYPE DWORD       ; EDI 4바이트 증가
loop L1

```

**5. Fibonacci Numbers (피보나치 수열)**

**문제:** 루프를 사용하여 피보나치 수열의 첫 일곱 개 값을 계산하는 프로그램을 작성하십시오. 공식: Fib(1)=1,Fib(2)=1,Fib(*n*)=Fib(*n*–1)+Fib(*n*–2).

**풀이:** *F*(1)과 *F*(2)를 초기화하고, 두 개의 레지스터를 사용하여 이전 두 값을 저장하면서 반복적으로 덧셈을 수행합니다.

```
.data
fibArray DWORD 7 DUP(?) ; 7개 요소 저장

.code
; F(1) = 1, F(2) = 1 초기화
mov DWORD PTR fibArray+0, 1
mov DWORD PTR fibArray+4, 1

mov ecx, 5              ; 남은 5개 요소 (F(3)부터 F(7)까지)
mov esi, OFFSET fibArray + 8 ; F(3)이 저장될 위치
mov ebx, 1              ; EBX = F(n-2)
mov edx, 1              ; EDX = F(n-1)

L1:
    mov eax, ebx        ; EAX = F(n-2)
    add eax, edx        ; EAX = F(n) = F(n-2) + F(n-1)
    mov [esi], eax      ; F(n) 저장

    mov ebx, edx        ; 다음 루프를 위해 F(n-2) 업데이트
    mov edx, eax        ; 다음 루프를 위해 F(n-1) 업데이트

    add esi, 4          ; 다음 DWORD 위치로 이동
loop L1

```

**6. Reverse an Array (배열 제자리 역순 배치)**

**문제:** 간접 또는 인덱스 주소 지정을 사용하는 루프를 사용하여 정수 배열의 요소를 **제자리에서** 역순으로 만드십시오. 다른 배열로 복사하지 마십시오. `SIZEOF`, `TYPE`, `LENGTHOF` 연산자를 사용하여 유연성을 확보하십시오.

**풀이:** 배열의 시작(`ESI`)과 끝(`EDI`)을 가리키는 두 개의 포인터를 사용하고, 배열 길이의 절반만큼 `XCHG` 명령어를 사용하여 교환합니다.

```
.data
dArray DWORD 10, 20, 30, 40, 50, 60 ; 예시 배열 (길이 6)

.code
mov esi, OFFSET dArray                              ; 시작 포인터 (dArray)
mov edi, OFFSET dArray + SIZEOF dArray - TYPE dArray ; 끝 포인터 (dArray[N-1]) [12, 13]
mov ecx, LENGTHOF dArray / 2                        ; 길이의 절반만큼 루프

L1:
    mov eax, [esi]          ; EAX에 앞쪽 요소 로드
    xchg eax, [edi]         ; EAX와 뒤쪽 요소를 교환 [7]
    mov [esi], eax          ; 앞쪽 위치에 뒤쪽 요소 저장

    add esi, TYPE dArray    ; 앞쪽 포인터 전진 (4바이트)
    sub edi, TYPE dArray    ; 뒤쪽 포인터 후진 (4바이트)
loop L1

```

**7. Copy a String in Reverse Order (문자열 역순 복사)**

**문제:** 루프와 간접 주소 지정을 사용하여 `source` 문자열을 `target`으로 복사하되, 문자 순서를 역순으로 만드십시오.

```
source BYTE "This is the source string",0
target BYTE SIZEOF source DUP('#')

```

**풀이:** 먼저 `source` 문자열의 길이 *N*을 찾은 다음, *N*−1 위치(마지막 문자)부터 0 위치(첫 문자)까지 역순으로 `target` 배열의 0 위치부터 *N*−1 위치까지 복사합니다.

```
.data
source BYTE "This is the source string",0
target BYTE (SIZEOF source) DUP('#')
N EQU (SIZEOF source) - 1 ; 문자열 길이 (널 문자 제외)

.code
mov ecx, N               ; 루프 카운터 (문자 수)
mov esi, OFFSET source + N - 1 ; ESI: 소스 배열의 마지막 문자 위치
mov edi, OFFSET target   ; EDI: 대상 배열의 시작 위치

L1:
    mov al, [esi]   ; 소스에서 문자를 뒤에서부터 로드
    mov [edi], al   ; 대상에 앞에서부터 저장
    dec esi
    inc edi
loop L1

mov BYTE PTR [edi], 0 ; 마지막에 널 문자 추가

```

**8. Shifting the Elements in an Array (배열 요소 순환 이동)**

**문제:** 루프와 인덱스 주소 지정을 사용하여 32비트 정수 배열의 멤버를 앞으로 한 위치 순환 이동(rotation)시키는 코드를 작성하십시오. 배열의 끝에 있는 값이 첫 번째 위치로 되돌아와야 합니다. (예: →).

**풀이:**

1. 마지막 요소를 저장합니다.

2. 마지막에서 두 번째 요소부터 첫 번째 요소까지, 각 요소를 한 칸씩 뒤로 이동시킵니다.

3. 저장해 둔 마지막 요소를 배열의 첫 번째 위치에 삽입합니다.
