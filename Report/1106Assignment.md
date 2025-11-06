# 6.10 Review Questions and Exercises

## 6.10.1 Short Answer

### **1. What will be the value of BX after the following instructions execute?**

**1. BX 레지스터의 값은 무엇인가?**

**풀이**

`AND` 연산은 두 비트가 모두 1일 때만 1이 됩니다.

```
BX = 0FFFFh
AND 6Bh → 0000 0000 0110 1011
결과: 006Bh

```

✅ **정답:** BX = **006Bh**

---

### **2. What will be the value of BX after the following instructions execute?**

**2. BX 레지스터의 값은 무엇인가?**

**풀이**

```
BX = 91BAh
AND 92h
1001 0001 1011 1010
0000 0000 1001 0010
결과: 0000 0000 1001 0010 = 0092h

```

✅ **정답:** BX = **0092h**

---

### **3. What will be the value of BX after the following instructions execute?**

**3. BX 레지스터의 값은 무엇인가?**

**풀이**

```
BX = 649Bh
OR 3Ah
0110 0100 1001 1011
0000 0000 0011 1010
결과: 0110 0100 1011 1011 = 64BBh

```

✅ **정답:** BX = **64BBh**

---

### **4. What will be the value of BX after the following instructions execute?**

**4. BX 레지스터의 값은 무엇인가?**

**풀이**

```
BX = 29D6h
XOR 8181h
0010 1001 1101 0110
1000 0001 1000 0001
결과: 1010 1000 0101 0111 = A857h

```

✅ **정답:** BX = **A857h**

---

### **5. What will be the value of EBX after the following instructions execute?**

**5. EBX 레지스터의 값은 무엇인가?**

**풀이**

```
EBX = 0AFAF649Bh
OR 3A219604h
결과: 0BFAFF69Fh

```

✅ **정답:** EBX = **0BFAFF69Fh**

---

### **6. What will be the value of RBX after the following instructions execute?**

**6. RBX 레지스터의 값은 무엇인가?**

**풀이**

`XOR 0FFFFFFFFh`는 하위 32비트 반전 연산임.

```
AFAF649Bh XOR FFFFFFFFh = 50509B64h

```

✅ **정답:** RBX = **0000000050509B64h**

---

### **7. Show the resulting value of AL (in binary):**

**7. 다음 연산 후 AL의 값을 2진수로 나타내시오.**

**풀이**

a.

```
01101111 AND 00101101 = 00101101

```

b.

```
6Dh = 01101101
AND 4Ah = 01001010
결과: 01001000

```

c.

```
00001111 OR 01100001 = 01101111

```

d.

```
94h = 10010100
37h = 00110111
XOR → 10100011

```

✅ **정답:**

a. 00101101

b. 01001000

c. 01101111

d. 10100011

---

### **8. Show the resulting value of AL (in hexadecimal):**

**8. 다음 연산 후 AL의 값을 16진수로 나타내시오.**

**풀이**

a. `NOT 7Ah → 85h`

b. `3Dh AND 74h = 34h`

c. `9Bh OR 35h = BFh`

d. `72h XOR DCh = AEh`

✅ **정답:**

a. 85h

b. 34h

c. BFh

d. AEh

---

### **9. Show the values of the Carry, Zero, and Sign flags:**

**9. 다음 명령 후 CF, ZF, SF의 값을 나타내시오.**

**풀이**

a.

```
AL=00001111b
TEST 00000010b → 결과: 00000010b (0이 아님)
CF=0 ZF=0 SF=0

```

b.

```
AL=00000110b
CMP 00000101b → 6-5=1
CF=0 ZF=0 SF=0

```

c.

```
AL=00000101b
CMP 00000111b → 5-7 음수
CF=1 ZF=0 SF=1

```

✅ **정답:**

a. CF=0, ZF=0, SF=0

b. CF=0, ZF=0, SF=0

c. CF=1, ZF=0, SF=1

---

### **10. Which conditional jump instruction executes a branch based on the contents of ECX?**

**10. ECX의 내용을 기준으로 분기하는 조건 분기 명령은?**

**풀이**

→ `LOOP`, `JCXZ`, `JECXZ` 명령이 ECX 값에 따라 분기함.

✅ **정답:** **JCXZ / JECXZ**

---

### **11. How are JA and JNBE affected by the Zero and Carry flags?**

**11. JA와 JNBE 명령은 ZF와 CF에 어떻게 영향을 받는가?**

**풀이**

`JA`(Jump if Above) = `CF=0` 그리고 `ZF=0`일 때 점프

✅ **정답:** CF=0, ZF=0 → 점프 실행

---

### **12. What will be the final value in EDX after this code executes?**

**12. 코드 실행 후 EDX의 최종 값은?**

```nasm
mov  edx,1
mov  eax,7FFFh
cmp  eax,8000h
jl   L1
mov  edx,0
L1:

```

**풀이**

7FFFh < 8000h → `JL` 조건 참 → L1로 점프 → `mov edx,0` 실행 안 됨

✅ **정답:** EDX = **1**

---

### **13. What will be the final value in EDX after this code executes?**

**13. 코드 실행 후 EDX의 최종 값은?**

```nasm
mov  edx,1
mov  eax,7FFFh
cmp  eax,8000h
jb   L1
mov  edx,0
L1:

```

**풀이**

Unsigned 비교에서 7FFFh < 8000h → 참 → `JB` 점프 발생

✅ **정답:** EDX = **1**

---

### **14. What will be the final value in EDX after this code executes?**

**14. 코드 실행 후 EDX의 최종 값은?**

```nasm
mov  edx,1
mov  eax,7FFFh
cmp  eax,0FFFF8000h
jl   L2
mov  edx,0
L2:

```

**풀이**

Signed 비교에서 7FFFh(32767) > 0FFFF8000h(-32768) → `JL` 조건 거짓 → 점프 안 함 → `mov edx,0` 실행

✅ **정답:** EDX = **0**

---

### **15. (True/False)**

**15. 다음 코드가 Target으로 점프할 것이다.**

```nasm
mov  eax,-30
cmp  eax,-50
jg   Target

```

**풀이**

-30 > -50 → 조건 참 → 점프 발생

✅ **정답:** **True**

---

### **16. (True/False)**

**16. 다음 코드가 Target으로 점프할 것이다.**

```nasm
mov  eax,-42
cmp  eax,26
ja   Target

```

**풀이**

`JA`는 부호 없는 비교임.

-42는 unsigned로 매우 큰 수로 간주되지 않음 (실제로 음수는 큰 unsigned 값이지만 부호 있는 비교가 아님)

→ `ja`는 CF=0, ZF=0일 때만 점프

이 경우 CF=1 → 점프 안 함

✅ **정답:** **False**

---

### **17. What will be the value of RBX after the following executes?**

**17. RBX의 값은 무엇인가?**

```nasm
mov  rbx,0FFFFFFFFFFFFFFFFh
and  rbx,80h

```

**풀이**

`AND 80h` → 하위 바이트만 남음

결과: 0000000000000080h

✅ **정답:** RBX = **0000000000000080h**

---

### **18. What will be the value of RBX after the following executes?**

**18. RBX의 값은 무엇인가?**

```nasm
mov  rbx,0FFFFFFFFFFFFFFFFh
and  rbx,808080h

```

**풀이**

`AND` 결과는 0000000000808080h

✅ **정답:** RBX = **0000000000808080h**

---

### **19. What will be the value of RBX after the following executes?**

**19. RBX의 값은 무엇인가?**

```nasm
mov  rbx,0FFFFFFFFFFFFFFFFh
and  rbx,80808080h

```

**풀이**

`AND` 결과는 0000000080808080h

✅ **정답:** RBX = **0000000080808080h**

## 🧩 **6.10.2 Algorithm Workbench (Irvine32 Version)**

```nasm
TITLE 6.10.2 Algorithm Workbench - Irvine32 Version
INCLUDE Irvine32.inc

.data
; 공통 변수
val1  DWORD  15
A     DWORD  5
B     DWORD  20
N     DWORD  10
X     DWORD  ?
SetX  DWORD  0F0F0F0Fh
SetY  DWORD  00FF00FFh
mem32 DWORD  12345678h

.code
main PROC

; ======================================================
; 1. Convert ASCII digit in AL to binary value
; ======================================================
mov  al, '7'      ; 예: ASCII '7' (0x37)
and  al, 0Fh      ; 결과: 07h (숫자 7)
; 결과 확인용
call DumpRegs

; ======================================================
; 2. Calculate parity of 32-bit memory operand
; ======================================================
mov  eax, mem32
mov  ebx, eax
shr  ebx, 16
xor  eax, ebx
shr  eax, 8
xor  al, ah
; AL = B0 XOR B1 XOR B2 XOR B3
call DumpRegs

; ======================================================
; 3. Set difference: SetX - SetY
; ======================================================
mov  eax, SetX
mov  ebx, SetY
not  ebx
and  eax, ebx     ; EAX = SetX AND (NOT SetY)
call DumpRegs

; ======================================================
; 4. Unsigned DX <= CX → Jump to L1
; ======================================================
mov  dx, 5
mov  cx, 10
cmp  dx, cx
jbe  L1
jmp  SkipL1
L1:
  call WriteString
  db "Jumped to L1 (DX <= CX)",0
  call Crlf
SkipL1:

; ======================================================
; 5. Signed AX > CX → Jump to L2
; ======================================================
mov  ax, -5
mov  cx, -10
cmp  ax, cx
jg   L2
jmp  SkipL2
L2:
  call WriteString
  db "Jumped to L2 (AX > CX)",0
  call Crlf
SkipL2:

; ======================================================
; 6. Clear bits 0,1 in AL, jump L3 if zero else L4
; ======================================================
mov  al, 3Ah
and  al, 0FCh
test al, al
jz   L3
jmp  L4
L3:
  call WriteString
  db "L3: AL is zero",0
  call Crlf
  jmp Next6
L4:
  call WriteString
  db "L4: AL is nonzero",0
  call Crlf
Next6:

; ======================================================
; 7. if( val1 > ecx ) AND ( ecx > edx ) X=1 else X=2
; ======================================================
mov  ecx, 10
mov  edx, 5
mov  eax, val1
cmp  eax, ecx
jle  SetX2_7
cmp  ecx, edx
jle  SetX2_7
mov  X, 1
jmp  Done7
SetX2_7:
mov  X, 2
Done7:
call DumpRegs

; ======================================================
; 8. if( ebx > ecx ) OR ( ebx > val1 ) X=1 else X=2
; ======================================================
mov  ebx, 5
mov  ecx, 3
cmp  ebx, ecx
jg   SetX1_8
cmp  ebx, val1
jg   SetX1_8
mov  X, 2
jmp  Done8
SetX1_8:
mov  X, 1
Done8:
call DumpRegs

; ======================================================
; 9. if( (ebx>ecx AND ebx>edx) OR (edx>eax) ) X=1 else X=2
; ======================================================
mov  ebx, 10
mov  ecx, 5
mov  edx, 2
mov  eax, 1
cmp  ebx, ecx
jle  CheckRight9
cmp  ebx, edx
jle  CheckRight9
mov  X, 1
jmp  Done9
CheckRight9:
cmp  edx, eax
jg   Set1_9
mov  X, 2
jmp  Done9
Set1_9:
mov  X, 1
Done9:
call DumpRegs

; ======================================================
; 10. while (N>0) { if (N!=3 AND (N<A OR N>B)) N-=2; else N-=1; }
; ======================================================
WhileLoop:
    mov  eax, N
    cmp  eax, 0
    jle  EndWhile

    cmp  eax, 3
    je   Sub1

    cmp  eax, A
    jl   Sub2
    cmp  eax, B
    jg   Sub2
Sub1:
    sub  N, 1
    jmp  WhileLoop

Sub2:
    sub  N, 2
    jmp  WhileLoop

EndWhile:
call DumpRegs

exit
main ENDP
END main

```

## 🧩 6.11.1 Suggestions for Testing Your Code

*(코드 테스트를 위한 제안)*

---

### 🔹 원문

> Always step through your program with a debugger the first time you test it. It’s so easy to forget a small detail, and the debugger lets you see exactly what’s going on.
> 

### 🔸 해설

프로그램을 처음 실행할 때는 **항상 디버거(Step Into / Step Over)** 로 한 줄씩 실행하세요.

작은 실수(예: PUSH/POP 순서, CALL/RET 짝 안 맞음 등)는 자주 발생하므로, **실행 흐름과 레지스터 변화**를 직접 보는 것이 중요합니다.

---

### 🔹 원문

> If the specifications call for a signed array, be sure to include some negative values.
> 

### 🔸 해설

**부호 있는 배열(signed array)** 을 테스트할 때는 반드시 **음수 값도 포함**해야 합니다.

예: `DWORD -5, 0, 10` 같은 테스트 데이터를 써야 올바른 결과를 확인할 수 있습니다.

---

### 🔹 원문

> When a range of input values is specified, include test data that falls before, on, and after these boundaries.
> 

### 🔸 해설

입력 값의 **경계 조건(boundary)** 도 꼭 확인하세요.

예를 들어 “입력값은 0~100”이라면, `-1`, `0`, `100`, `101` 을 모두 테스트해야 합니다.

---

### 🔹 원문

> Create multiple test cases, using arrays of different lengths.
> 

### 🔸 해설

배열 크기를 다양하게 바꾼 **여러 테스트 케이스**를 만들어야 합니다.

예: 배열 크기 3, 10, 100 등의 경우를 각각 돌려보세요.

---

### 🔹 원문

> When you’re writing a program that writes to an array, the Visual Studio debugger is the best tool for evaluating your program’s correctness. Use the debugger’s Memory window to display the array, choosing either hexadecimal or decimal representation.
> 

### 🔸 해설

배열에 값을 저장하는 프로그램이라면, **Visual Studio의 Memory 창**을 활용하세요.

배열의 실제 메모리 내용을 **16진수 또는 10진수**로 보며 결과를 검증할 수 있습니다.

---

### 🔹 원문

> Immediately after calling the procedure you’re testing, call it a second time to verify that the procedure has preserved all registers.
> 

### 🔸 해설

테스트할 함수를 호출한 직후, **같은 함수를 한 번 더 호출**해서

해당 함수가 **레지스터를 올바르게 보존했는지 확인**하세요.

예시:

```nasm
mov esi, OFFSET array
mov ecx, count
call CalcSum       ; 첫 번째 호출 (EAX에 합이 반환됨)
call CalcSum       ; 두 번째 호출 → 레지스터 보존 확인

```

※ 단, `EAX`는 일반적으로 반환값용이므로, 입력값으로 쓰지 않는 게 좋습니다.

---

### 🔹 원문

> If you’re planning to pass more than one array to a procedure, make sure you do not refer to the array by name inside the procedure. Instead, set ESI or EDI to the array’s offset before calling your procedure.
> 

### 🔸 해설

하나의 프로시저에 **여러 배열을 인자로 전달**할 때는,

프로시저 안에서 배열 이름을 직접 쓰면 안 됩니다.

대신:

```nasm
mov esi, OFFSET array1
mov edi, OFFSET array2
call CompareArrays

```

이렇게 레지스터(`ESI`, `EDI`)에 주소를 저장해 넘긴 뒤,

프로시저 내부에서는 `[esi]`, `[edi]` 형태의 **간접 주소 지정(indirect addressing)** 을 써야 합니다.

---

### 🔹 원문

> If you need to create a variable for use only inside the procedure, you can use the .data directive before the variable, and then follow it with the .code directive.
> 

### 🔸 해설

프로시저 내부에서만 사용할 변수를 만들고 싶다면

아래처럼 `.data` → `.code` 구조로 선언하세요:

```nasm
MyCoolProcedure PROC
    .data
        sum SDWORD ?
    .code
        mov sum,0
        ; (코드 계속)
MyCoolProcedure ENDP

```

이 변수는 **전역 변수처럼 접근 가능하지만**,

프로시저 내부에서만 쓸 의도를 명확히 보여줍니다.

---

### 🔹 원문

> Of course, you must use a runtime instruction to initialize variables used inside a procedure, because you will call this procedure more than once.
> 

### 🔸 해설

이런 내부 변수는 프로그램 실행 중(`runtime`)에 직접 초기화해야 합니다.

왜냐하면 **프로시저가 여러 번 호출되더라도 이전 값이 남을 수 있기 때문**입니다.

## 🌟 6.11.2 Exercise Descriptions (문제 설명 및 해설)

---

### ★ 1. Filling an Array

**📘 원문:**

Create a procedure that fills an array of doublewords with N random integers, making sure the values fall within the range j...k, inclusive. When calling the procedure, pass a pointer to the array that will hold the data, pass N, and pass the values of j and k. Preserve all register values between calls to the procedure. Write a test program that calls the procedure twice, using different values for j and k. Verify your results using a debugger.

**🇰🇷 해설:**

`DWORD` 배열에 **N개의 난수**를 채워 넣는 프로그램.

각 난수는 **j~k 범위(포함)** 안에 있어야 함.

- 인자: 배열 주소(ESI 등), N, j, k
- 레지스터 보존 필수 (`pushad`/`popad` 사용)
- 디버거로 배열 내용 확인

**💡 힌트:**

`RandomRange`로 (k - j + 1) 범위 생성 후 j 더하기 → `[esi + ecx*4]`에 저장

---

### ★★ 2. Summing Array Elements in a Range

**📘 원문:**

Create a procedure that returns the sum of all array elements falling within the range j...k (inclusive). Write a test program that calls the procedure twice, passing a pointer to a signed doubleword array, the size of the array, and the values of j and k. Return the sum in the EAX register, and preserve all other register values between calls.

**🇰🇷 해설:**

배열 중 **지정된 범위(j~k)** 내에 있는 값만 골라 합산하는 프로그램.

- 입력: 배열 포인터, 배열 크기, j, k
- 출력: EAX ← 합계
- 나머지 레지스터 보존

**💡 힌트:**

루프를 돌며 `[esi + ecx*4]`값이 범위 내인지 `cmp`로 비교 후,

해당되면 `add eax, [esi + ecx*4]`

---

### ★★ 3. Test Score Evaluation

**📘 원문:**

Create a procedure named `CalcGrade` that receives an integer value between 0 and 100, and returns a single capital letter in AL register. Preserve all other registers.

Grade mapping:

- 90–100 → A
- 80–89 → B
- 70–79 → C
- 60–69 → D
- 0–59 → F

Write a test program that generates 10 random integers between 50 and 100, inclusive, and pass each to `CalcGrade`. Optionally display both the integer and grade using Irvine32 library.

**🇰🇷 해설:**

`CalcGrade` 프로시저 작성 — 점수(0~100)에 따라 등급(A~F) 반환.

`AL`에 문자 저장 (‘A’ = 65h 등).

**테스트:** 난수 10개 생성 후 `CalcGrade` 호출 및 결과 출력.

**💡 힌트:**

```nasm
cmp eax, 90
jae gradeA
cmp eax, 80
jae gradeB
...

```

---

### ★★ 4. College Registration

**📘 원문:**

Recreate the “College Registration” example from Section 6.7.3, but use CMP and Jxx (conditional jump) instructions instead of .IF/.ELSEIF.

Check that credits are between 1 and 30. If invalid, show an error.

Prompt user for grade average and credits, and display message:

“The student can register” or “cannot register.”

**🇰🇷 해설:**

조건문 매크로 대신 **CMP / Jxx 명령**으로 논리 구현.

학점(1~30) 범위 검사 후 잘못된 입력 시 에러 메시지 출력.

평균 점수와 학점 입력받아 등록 가능 여부 출력.

**💡 Irvine32 함수 사용:**

`ReadInt`, `WriteString`, `CrLf` 등으로 입출력 처리.

---

### ★ 5. Boolean Calculator (1)

**📘 원문:**

Make a Boolean calculator that shows a menu:

1. x AND y
2. x OR y
3. NOT x
4. x XOR y
5. Exit program
    
    Use **Table-Driven Selection** (see Section 6.5.4).
    
    Each menu item calls a procedure that displays the name of the operation.
    

**🇰🇷 해설:**

사용자 메뉴 기반 불린 연산기 (AND, OR, NOT, XOR).

이번 단계에서는 **연산 수행 X**,

선택된 연산의 **이름만 출력하는 함수 호출**.

**💡 힌트:**

테이블 (주소 테이블) + 인덱스로 점프 → `jmp [table + ecx*4]`

---

### ★★ 6. Boolean Calculator (2)

**📘 원문:**

Extend Exercise 5 by implementing the actual operations:

- AND_op → 입력 2개, AND 후 출력
- OR_op → 입력 2개, OR 후 출력
- NOT_op → 입력 1개, NOT 후 출력
- XOR_op → 입력 2개, XOR 후 출력
    
    All in **hexadecimal** format.
    

**🇰🇷 해설:**

이전 문제의 메뉴를 완성 — 실제 논리연산 수행.

각 프로시저가 `Prompt`, `ReadHex`, `WriteHex` 사용.

**💡 예:**

```nasm
ReadHex
mov ebx, eax
ReadHex
and eax, ebx
WriteHex

```

---

### ★ 7. Probabilities and Colors

**📘 원문:**

Display 20 lines of text with random colors.

Probabilities:

- White = 30%
- Blue = 10%
- Green = 60%
    
    Hint: Generate random integer 0–9.
    
    0–2 = white, 3 = blue, 4–9 = green.
    

**🇰🇷 해설:**

난수(0~9)에 따라 **색상 확률 제어 출력**.

20회 반복하여 콘솔에 출력.

**테스트:** 여러 번 실행해 확률 확인.

**💡 힌트:**

`SetTextColor`, `WriteString`, `RandomRange` 사용.

---

### ★★ 8. Message Encryption

**📘 원문:**

Modify XOR encryption so the **key repeats** for the entire message.

Example key: “ABXmv#7”

Each message byte XOR key[i mod key_length].

**🇰🇷 해설:**

XOR 암호화 프로그램을 확장.

키 문자열이 반복적으로 메시지에 적용됨.

**💡 예:**

```nasm
mov al, [esi]         ; plain byte
xor al, [edi + ecx]   ; repeat key
mov [esi], al

```

`ecx MOD key_length` 로 순환.

---

### ★★★ 9. Validating a PIN

**📘 원문:**

Validate 5-digit PIN according to per-digit ranges:

| Digit | Range |
| --- | --- |
| 1 | 5–9 |
| 2 | 2–5 |
| 3 | 4–8 |
| 4 | 1–4 |
| 5 | 3–6 |

If any digit is invalid → return position (1–5) in `EAX`.

If all valid → return 0.

Preserve all registers. Test with valid/invalid PINs.

**🇰🇷 해설:**

각 자리별 허용 범위를 저장한 배열 2개(`min[]`, `max[]`)를 만들어

PIN 배열(5자리) 검증.

범위 벗어나면 그 자리 번호를 `EAX`에 반환.

**💡 예:**

```nasm
movzx eax, byte ptr [esi+ecx]
cmp  eax, [min+ecx]
jb   invalid
cmp  eax, [max+ecx]
ja   invalid

```

---

### ★★★★ 10. Parity Checking

**📘 원문:**

Create a procedure that checks if a byte array has **even or odd parity**.

Return True (1) if total bits = even, False (0) if odd.

Preserve all registers.

Test with two arrays: one even parity, one odd parity.

**🇰🇷 해설:**

배열의 모든 바이트 비트를 세어 총합의 짝/홀 판정.

EAX = 1 (짝수), 0 (홀수).

레지스터 보존 필요.

**💡 힌트:**

`TEST`, `SHR`, `JNC`, `ADC` 명령으로 비트 카운트.

마지막에 `test eax, 1`로 짝/홀 판별.

---

## ✅ 정리표

| 번호 | 주제 | 주요 기술 | 핵심 Irvine32 함수 |
| --- | --- | --- | --- |
| 1 | 배열 난수 채우기 | RandomRange, 루프 | RandomRange |
| 2 | 범위 내 합산 | CMP, 조건 합계 | 없음 |
| 3 | 성적 평가 | 조건 분기, 문자 반환 | RandomRange, WriteString |
| 4 | 학점 등록 조건 | CMP, Jxx, 입출력 | ReadInt, WriteString |
| 5 | 불린 계산기 (1) | Table-Driven 선택 | WriteString |
| 6 | 불린 계산기 (2) | 논리연산 AND/OR/XOR | ReadHex, WriteHex |
| 7 | 색상 확률 출력 | RandomRange, 색상제어 | SetTextColor |
| 8 | XOR 암호화 | 반복키, XOR | ReadString |
| 9 | PIN 검증 | 배열 비교, 조건 분기 | 없음 |
| 10 | 패리티 체크 | 비트 카운트, 루프 | 없음 |
