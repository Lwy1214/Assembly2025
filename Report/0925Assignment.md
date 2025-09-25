## 📘 3.9.1 단답형 (문제 & 정답)

# 📘 Assembly Language 단답형 문제 (1~29) 정리

---

### **1. Provide examples of three different instruction mnemonics.**

**한글:** 세 가지 다른 명령어 니모닉의 예를 제시하시오.

✅ 정답: `MOV`, `ADD`, `SUB`

---

### **2. What is a calling convention, and how is it used in assembly language declarations?**

**한글:** 호출 규약이란 무엇이며, 어셈블리 언어 선언에서 어떻게 사용되는가?

✅ 정답: 함수 호출 시 인자 전달, 반환값, 스택 정리 규칙을 정한 것. 어셈블리에서는 `PROTO` 등을 통해 호출 규약을 정의.

---

### **3. How do you reserve space for the stack in a program?**

**한글:** 프로그램에서 스택을 위한 공간을 어떻게 예약하는가?

✅ 정답: `.STACK 100h` 와 같이 스택 세그먼트를 선언.

---

### **4. Explain why the term assembler language is not quite correct.**

**한글:** “assembler language”라는 용어가 정확하지 않은 이유를 설명하시오.

✅ 정답: Assembler는 프로그램 이름이고, 언어의 올바른 이름은 **assembly language**.

---

### **5. Explain the difference between big endian and little endian. Also, look up the origins of this term on the Web.**

**한글:** 빅 엔디언과 리틀 엔디언의 차이를 설명하고, 이 용어의 기원을 찾아보시오.

✅ 정답:

- Big endian: 가장 중요한 바이트(MSB)를 낮은 주소에 저장.
- Little endian: 가장 덜 중요한 바이트(LSB)를 낮은 주소에 저장.
- 기원: *걸리버 여행기*에서 달걀을 깨는 방식(Big end vs Little end).

---

### **6. Why might you use a symbolic constant rather than an integer literal in your code?**

**한글:** 정수 리터럴 대신 기호 상수를 사용하는 이유는?

✅ 정답: 가독성 증가, 유지보수 용이, 한 곳만 수정해도 전체 반영.

---

### **7. How is a source file different from a listing file?**

**한글:** 소스 파일과 리스팅 파일의 차이는?

✅ 정답: 소스 파일(.asm)은 사람이 작성, 리스팅 파일(.lst)은 어셈블러가 생성(주소, 기계어, 오류 포함).

---

### **8. How are data labels and code labels different?**

**한글:** 데이터 레이블과 코드 레이블의 차이는?

✅ 정답: 데이터 레이블 → 변수/데이터 이름, 코드 레이블 → 분기/점프 위치 이름.

---

### **9. (True/False): An identifier cannot begin with a numeric digit.**

**한글:** 식별자는 숫자로 시작할 수 없다.

✅ 정답: True

---

### **10. (True/False): A hexadecimal literal may be written as 0x3A.**

**한글:** 16진수 리터럴은 0x3A와 같이 쓸 수 있다.

✅ 정답: True (MASM에서는 `3Ah`도 가능)

---

### **11. (True/False): Assembly language directives execute at runtime.**

**한글:** 어셈블리 지시문은 실행 시간에 실행된다.

✅ 정답: False (어셈블 시점에만 작동)

---

### **12. (True/False): Assembly language directives can be written in any combination of uppercase and lowercase letters.**

**한글:** 지시문은 대소문자를 혼합해 쓸 수 있다.

✅ 정답: True

---

### **13. Name the four basic parts of an assembly language instruction.**

**한글:** 어셈블리 명령어의 네 가지 기본 부분은?

✅ 정답: Label, Mnemonic, Operand(s), Comment

---

### **14. (True/False): MOV is an example of an instruction mnemonic.**

**한글:** MOV는 명령어 니모닉의 예이다.

✅ 정답: True

---

### **15. (True/False): A code label is followed by a colon (:), but a data label does not end with a colon.**

**한글:** 코드 레이블은 콜론(:)으로 끝나지만, 데이터 레이블은 콜론으로 끝나지 않는다.

✅ 정답: True

---

### **16. Show an example of a block comment.**

**한글:** 블록 주석의 예를 제시하시오.

✅ 정답:

```nasm
COMMENT !
이것은 블록 주석입니다.
여러 줄 작성 가능.
!

```

---

### **17. Why is it not a good idea to use numeric addresses when writing instructions that access variables?**

**한글:** 변수를 접근할 때 숫자 주소를 쓰면 안 좋은 이유는?

✅ 정답: 가독성 저하, 유지보수 어려움, 메모리 주소 변경 시 코드 전체 수정 필요.

---

### **18. What type of argument must be passed to the ExitProcess procedure?**

**한글:** ExitProcess에 어떤 인자를 전달해야 하는가?

✅ 정답: 32비트 정수(DWORD, 종료 코드).

---

### **19. Which directive ends a procedure?**

**한글:** 어떤 지시어가 프로시저를 끝내는가?

✅ 정답: `ENDP`

---

### **20. In 32-bit mode, what is the purpose of the identifier in the END directive?**

**한글:** 32비트 모드에서 END 지시문의 식별자는 무엇을 의미하는가?

✅ 정답: 프로그램의 시작 지점(entry point)을 지정.

---

### **21. What is the purpose of the PROTO directive?**

**한글:** PROTO 지시문의 목적은?

✅ 정답: 외부 또는 미리 정의되지 않은 프로시저를 선언하여 호출 규약을 알려줌.

---

### **22. (True/False): An Object file is produced by the Linker.**

**한글:** 오브젝트 파일은 링커가 만든다.

✅ 정답: False (어셈블러가 생성)

---

### **23. (True/False): A Listing file is produced by the Assembler.**

**한글:** 리스팅 파일은 어셈블러가 만든다.

✅ 정답: True

---

### **24. (True/False): A link library is added to a program just before producing an Executable file.**

**한글:** 실행 파일 생성 직전에 링크 라이브러리가 추가된다.

✅ 정답: True

---

### **25. Which data directive creates a 32-bit signed integer variable?**

**한글:** 32비트 부호 있는 정수 변수를 만드는 지시어는?

✅ 정답: `SDWORD`

---

### **26. Which data directive creates a 16-bit signed integer variable?**

**한글:** 16비트 부호 있는 정수 변수를 만드는 지시어는?

✅ 정답: `SWORD`

---

### **27. Which data directive creates a 64-bit unsigned integer variable?**

**한글:** 64비트 부호 없는 정수 변수를 만드는 지시어는?

✅ 정답: `QWORD`

---

### **28. Which data directive creates an 8-bit signed integer variable?**

**한글:** 8비트 부호 있는 정수 변수를 만드는 지시어는?

✅ 정답: `SBYTE`

---

### **29. Which data directive creates a 10-byte packed BCD variable?**

**한글:** 10바이트 패킹된 BCD 변수를 만드는 지시어는?

✅ 정답: `TBYTE`

# 📘 3.9.2 Algorithm Workbench

---

### **1. Define four symbolic constants that represent integer 25 in decimal, binary, octal, and hexadecimal formats.**

**한글:** 정수 25를 10진수, 2진수, 8진수, 16진수 형식으로 나타내는 네 가지 기호 상수를 정의하시오.

✅ 정답:

```nasm
DEC25 = 25
BIN25 = 11001b
OCT25 = 31o
HEX25 = 19h

```

---

### **2. Find out, by trial and error, if a program can have multiple code and data segments.**

**한글:** 시행착오를 통해 프로그램이 여러 개의 코드 세그먼트와 데이터 세그먼트를 가질 수 있는지 확인하시오.

✅ 정답: 대부분의 어셈블러에서 **여러 데이터/코드 세그먼트를 선언할 수 있으나, 실제로는 링커에서 하나의 실행 가능한 세그먼트로 병합됨**.

---

### **3. Create a data definition for a doubleword that stored it in memory in big endian format.**

**한글:** 메모리에 빅 엔디언 형식으로 저장되는 더블워드 데이터 정의를 작성하시오.

✅ 정답:

```nasm
myVal BYTE 12h, 34h, 56h, 78h   ; 빅 엔디언 (12345678h)

```

---

### **4. Find out if you can declare a variable of type DWORD and assign it a negative value. What does this tell you about the assembler’s type checking?**

**한글:** DWORD 변수에 음수를 할당할 수 있는지 확인하시오. 이것이 어셈블러의 타입 검사에 대해 무엇을 의미하는가?

✅ 정답:

가능하다. (예: `myVar DWORD -5`)

👉 어셈블러는 부호 여부를 엄격히 검사하지 않고, 단순히 값을 2의 보수 형태로 저장함.

---

### **5. Write a program that contains two instructions: (1) add the number 5 to the EAX register, and (2) add 5 to the EDX register. Generate a listing file and examine the machine code generated by the assembler. What differences, if any, did you find between the two instructions?**

**한글:** EAX 레지스터에 5를 더하는 명령과 EDX 레지스터에 5를 더하는 명령을 작성하고, 리스팅 파일의 기계어 코드를 비교하시오.

✅ 정답:

- `ADD EAX, 5` → 짧은 인코딩(특수 오피코드).
- `ADD EDX, 5` → 일반 인코딩(오피코드 + ModR/M 바이트).
    
    👉 같은 동작이라도 레지스터에 따라 기계어 코드 길이가 다름.
    

---

### **6. Given the number 456789ABh, list out its byte values in little-endian order.**

**한글:** 456789ABh 값을 리틀 엔디언 순서로 나열하시오.

✅ 정답: `ABh, 89h, 67h, 45h`

---

### **7. Declare an array of 120 uninitialized unsigned doubleword values.**

**한글:** 초기화되지 않은 부호 없는 더블워드 120개 배열을 선언하시오.

✅ 정답:

```nasm
arr DWORD 120 DUP(?)

```

---

### **8. Declare an array of byte and initialize it to the first 5 letters of the alphabet.**

**한글:** 바이트 배열을 선언하고 알파벳 처음 5글자로 초기화하시오.

✅ 정답:

```nasm
letters BYTE "ABCDE"

```

---

### **9. Declare a 32-bit signed integer variable and initialize it with the smallest possible negative decimal value.**

**한글:** 32비트 부호 있는 정수 변수를 선언하고 가장 작은 음수 값으로 초기화하시오.

✅ 정답:

```nasm
minVal SDWORD -2147483648

```

---

### **10. Declare an unsigned 16-bit integer variable named wArray that uses three initializers.**

**한글:** 16비트 부호 없는 정수형 변수 `wArray`를 선언하고 세 개의 초기값을 주시오.

✅ 정답:

```nasm
wArray WORD 1000, 2000, 3000

```

---

### **11. Declare a string variable containing the name of your favorite color. Initialize it as a null-terminated string.**

**한글:** 가장 좋아하는 색깔 이름을 담은 문자열 변수를 선언하고 널 종료 문자열로 초기화하시오.

✅ 정답 (예: BLUE):

```nasm
colorName BYTE "Blue", 0

```

---

### **12. Declare an uninitialized array of 50 signed doublewords named dArray.**

**한글:** 초기화되지 않은 부호 있는 더블워드 50개 배열 `dArray`를 선언하시오.

✅ 정답:

```nasm
dArray SDWORD 50 DUP(?)

```

---

### **13. Declare a string variable containing the word “TEST” repeated 500 times.**

**한글:** "TEST" 단어를 500번 반복한 문자열 변수를 선언하시오.

✅ 정답:

```nasm
bigStr BYTE 500 DUP("TEST")

```

---

### **14. Declare an array of 20 unsigned bytes named bArray and initialize all elements to zero.**

**한글:** 20개의 부호 없는 바이트 배열 `bArray`를 선언하고, 모든 요소를 0으로 초기화하시오.

✅ 정답:

```nasm
bArray BYTE 20 DUP(0)

```

---

### **15. Show the order of individual bytes in memory (lowest to highest) for the following doubleword variable: val1 DWORD 87654321h**

**한글:** 다음 더블워드 변수의 메모리 내 바이트 순서를 (낮은 주소 → 높은 주소) 나열하시오:

```nasm
val1 DWORD 87654321h

```

✅ 정답 (리틀 엔디언 기준): `21h, 43h, 65h, 87h`

## 📘 3.1.0 Programming Exercises

# **문제 1. Integer Expression Calculation**

> **AddTwo 프로그램(3.2절 예제)**를 참고하여, 레지스터를 사용해 다음 수식을 계산하는 프로그램을 작성하시오.
> 

A=(A+B)−(C+D)A = (A + B) - (C + D)

A=(A+B)−(C+D)

- **EAX → A**
- **EBX → B**
- **ECX → C**
- **EDX → D**

---

### ✅ 풀이 방법

1. `EAX`에 A 값을 저장한다.
2. `EBX` 값을 더해 `(A+B)`를 만든다.
3. `ECX`와 `EDX`를 더해 `(C+D)`를 만든다.
4. `EAX`에서 `(C+D)` 값을 빼 최종 결과 `(A+B) - (C+D)`를 얻는다.
5. 결과는 `EAX` 레지스터에 저장된다.

---

### 💻 코드 예시 (MASM)

```nasm
; CalcExpr.asm - calculates A = (A + B) - (C + D)
; Reference: AddTwo.asm (Chapter 3 example)

.386
.model flat,stdcall
.stack 4096
ExitProcess proto, dwExitCode:dword

.code
main proc
    ; 예시 값 할당
    mov eax, 10      ; A = 10
    mov ebx, 5       ; B = 5
    mov ecx, 3       ; C = 3
    mov edx, 2       ; D = 2

    ; (A + B)
    add eax, ebx     ; EAX = A + B

    ; (C + D)
    add ecx, edx     ; ECX = C + D

    ; (A + B) - (C + D)
    sub eax, ecx     ; EAX = (A + B) - (C + D)

    ; 결과는 EAX에 저장됨
    invoke ExitProcess, 0
main endp
end main

```

---

### 📊 실행 예시

- A=10, B=5, C=3, D=2일 때:
    
    ```
    (10 + 5) - (3 + 2) = 15 - 5 = 10
    
    ```
    
- 최종 결과: **EAX = 10**

# **문제 2. Symbolic Integer Constants**

> 일주일의 7일을 모두 기호 상수(symbolic constants)로 정의하시오.
> 
> 
> 그리고 이 상수들을 초기값으로 사용하는 배열 변수를 작성하시오.
> 

---

### ✅ 풀이 방법

1. `EQU` 지시문을 사용하여 월~일을 **기호 상수**로 정의한다.
    - 예: `MONDAY EQU 1`
2. `.data` 영역에 배열을 선언하고, 각 요일 기호 상수를 초기값으로 넣는다.
    - 예: `weekDays DWORD MONDAY, TUESDAY, ...`

---

### 💻 코드 예시 (MASM)

```nasm
; WeekDays.asm - defines symbolic constants for days of the week
; and creates an array using them

.386
.model flat,stdcall
.stack 4096
ExitProcess proto, dwExitCode:dword

; 기호 상수 정의
MONDAY    EQU 1
TUESDAY   EQU 2
WEDNESDAY EQU 3
THURSDAY  EQU 4
FRIDAY    EQU 5
SATURDAY  EQU 6
SUNDAY    EQU 7

.data
; 요일 배열 (DWORD = 32비트 정수)
weekDays DWORD MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY

.code
main proc
    ; 배열 선언 예제 프로그램이므로 계산은 생략
    invoke ExitProcess, 0
main endp
end main

```

---

### 📊 메모리 초기값 예시

`weekDays` 배열에는 아래 값들이 저장됨:

```
1, 2, 3, 4, 5, 6, 7

```

# **문제 3. Data Definitions**

> Table 3-2의 모든 데이터 타입을 정의하고, 각 타입에 맞는 값으로 초기화하시오.
> 

---

### 💻 MASM 코드 예시

```nasm
; DataTypes.asm - Definitions of all intrinsic data types (Table 3-2)

.386
.model flat,stdcall
.stack 4096
ExitProcess proto, dwExitCode:dword

.data
; 8-bit
uByteVar   BYTE   255        ; 8-bit unsigned (0 ~ 255)
sByteVar   SBYTE  -128       ; 8-bit signed (-128 ~ 127)

; 16-bit
uWordVar   WORD   65535      ; 16-bit unsigned (0 ~ 65535)
sWordVar   SWORD  -32768     ; 16-bit signed (-32768 ~ 32767)

; 32-bit
uDwordVar  DWORD  4294967295 ; 32-bit unsigned (0 ~ 4,294,967,295)
sDwordVar  SDWORD -2147483648 ; 32-bit signed (-2,147,483,648 ~ 2,147,483,647)

; 48-bit (Far pointer 용도)
fWordVar   FWORD  123456789ABC h ; 48-bit integer example (hexadecimal)

; 64-bit
qWordVar   QWORD  1234567890ABCDEFh ; 64-bit integer

; 80-bit (Ten-byte)
tByteVar   TBYTE  112233445566778899AABh ; 80-bit integer

; Floating-point
real4Var   REAL4  3.14       ; 32-bit short real
real8Var   REAL8  2.718281828 ; 64-bit long real
real10Var  REAL10 1.6180339887 ; 80-bit extended real

.code
main proc
    invoke ExitProcess, 0
main endp
end main

```

---

### 📊 정리

| 타입 | 예제 변수명 | 초기값 |
| --- | --- | --- |
| BYTE | uByteVar | 255 |
| SBYTE | sByteVar | -128 |
| WORD | uWordVar | 65535 |
| SWORD | sWordVar | -32768 |
| DWORD | uDwordVar | 4294967295 |
| SDWORD | sDwordVar | -2147483648 |
| FWORD | fWordVar | 123456789ABCh |
| QWORD | qWordVar | 1234567890ABCDEFh |
| TBYTE | tByteVar | 112233445566778899AABh |
| REAL4 | real4Var | 3.14 |
| REAL8 | real8Var | 2.718281828 |
| REAL10 | real10Var | 1.6180339887 |

---

4. Symbolic Text Constants
Write a program that defines symbolic names for several string literals (characters between
quotes). Use each symbolic name in a variable definition

# **문제4. 상징적 문자열 상수**

여러 문자열 리터럴(큰따옴표로 묶인 문자)에 대해 상징적 이름(symbolic name)을 정의하고, 각 상징적 이름을 변수 정의에 사용하시오.

---

### **예제 답안 (NASM, x86 32-bit)**

```nasm
section .data
    GREETING db "안녕하세요", 0      ; 문자열 끝에 NULL(0) 추가
    FAREWELL db "안녕히 가세요", 0
    QUESTION db "오늘 기분은 어떠세요?", 0
    THANKS   db "감사합니다", 0

section .text
    global _start

_start:
    ; 예시: GREETING 문자열 출력
    mov edx, 15          ; 문자열 길이 (한글 5글자 * 3바이트 UTF-8) <- 정확히 계산 필요
    mov ecx, GREETING    ; 출력할 문자열 주소
    mov ebx, 1           ; stdout
    mov eax, 4           ; sys_write
    int 0x80

    ; 프로그램 종료
    mov eax, 1           ; sys_exit
    xor ebx, ebx
    int 0x80

```

---

### **설명**

1. `db "문자열", 0`
    - 문자열을 정의하고, 끝에 `0`을 붙여서 NULL 종료.
    - 이 방식으로 상징적 이름(GREETING, FAREWELL 등)을 만들어서 변수처럼 사용 가능.
2. `mov ecx, GREETING`
    - `GREETING`은 문자열 시작 주소를 의미하므로 바로 사용할 수 있음.
3. `mov eax, 4 / int 0x80`
    - 리눅스에서 `sys_write` 시스템 콜을 이용해 문자열을 출력.




5. Listing File for AddTwoSum
Generate a listing file for the AddTwoSum program and write a description of the machine code
bytes generated for each instruction. You might have to guess at some of the meanings of the
byte values
# **문제5. AddTwoSum 프로그램의 리스팅 파일 생성**
AddTwoSum 프로그램의 리스팅 파일을 생성하고, 각 명령어에 대해 생성된 기계어 바이트에 대한 설명을 작성하십시오. 일부 바이트 값의 의미를 추측해야 할 수도 있습니다.

## **1.AddTwoSum.asm 프로그램 (참고)**

```nasm
; AddTwoSum.asm - Chapter 3 example.

.386
.model flat,stdcall
.stack 4096
ExitProcess proto,dwExitCode:dword

.data
sum dword 0

.code
main proc
    mov eax,5
    add eax,6
    mov sum,eax

    invoke ExitProcess,0
main endp
end main

```

---

## **2. Listing File 예시 (각 명령어와 머신 코드 바이트)**

| 어셈블리 명령어 | 머신 코드 바이트 (예시) | 설명 |
| --- | --- | --- |
| `mov eax,5` | `B8 05 00 00 00` | `B8` → `MOV EAX, imm32`, `05 00 00 00` → 32비트 즉시값 5 |
| `add eax,6` | `83 C0 06` | `83` → ALU 명령 + 8bit 즉시값, `C0` → EAX 레지스터 지정, `06` → 즉시값 6 |
| `mov sum,eax` | `A3 ?? ?? ?? ??` | `A3` → MOV moffs32,EAX, `?? ?? ?? ??` → sum의 메모리 주소 (링커에서 결정) |
| `invoke ExitProcess,0` | `B8 00 00 00 00FF 15 ?? ?? ?? ??` | `B8 00 00 00 00` → 인자 0을 EAX로 로드, `FF 15 ?? ?? ?? ??` → CALL DWORD PTR [ExitProcess] (주소는 링커가 결정) |

> 참고: ?? ?? ?? ??는 링커가 최종 주소를 할당하기 전에는 알 수 없는 값입니다.
> 

---

## **3. 바이트별 설명**

1. **`mov eax,5` → `B8 05 00 00 00`**
    - `B8` : opcode, EAX에 즉시값 이동
    - `05 00 00 00` : little-endian 방식으로 32비트 숫자 5
2. **`add eax,6` → `83 C0 06`**
    - `83` : 8-bit 즉시값을 사용한 ADD 명령
    - `C0` : ModR/M byte, 대상 = EAX
    - `06` : 더할 값 6
3. **`mov sum,eax` → `A3 ?? ?? ?? ??`**
    - `A3` : 메모리 직접 주소(moffs32)로 EAX 이동
    - `?? ?? ?? ??` : sum 변수의 메모리 주소 (링커에서 결정)
4. **`invoke ExitProcess,0` → `B8 00 00 00 00 / FF 15 ?? ?? ?? ??`**
    - `B8 00 00 00 00` : EAX 레지스터에 0 로드 (Exit code)
    - `FF 15 ?? ?? ?? ??` : 메모리 주소에 있는 ExitProcess 함수 호출

# **문제 6**
6. AddVariables Program
 Modify the AddVariables program so it uses 64-bit variables. Describe the syntax errors gener
ated by the assembler and what steps you took to resolve the errors
6. AddVariables 프로그램
AddVariables 프로그램을 수정하여 64비트 변수를 사용하도록 하십시오. 어셈블러에서 생성된 구문 오류와 해당 오류를 해결하기 위해 취한 조치를 설명하십시오.

## **1. 원래 프로그램 (참고)**

```nasm
; AddVariables.asm - Chapter 3 example.

.386
.model flat,stdcall
.stack 4096
ExitProcess proto,dwExitCode:dword

.data
firstval  dword 20002000h
secondval dword 11111111h
thirdval  dword 22222222h
sum dword 0

.code
main proc
    mov eax,firstval
    add eax,secondval
    add eax,thirdval
    mov sum,eax

    invoke ExitProcess,0
main endp
end main

```

---

## **2. 64-bit 변수로 수정**

1. 32-bit `dword` → 64-bit `qword`
2. 32-bit 레지스터(`eax`) → 64-bit 레지스터(`rax`)

```nasm
; AddVariables64.asm - 64-bit variables version

.model flat,stdcall
.stack 4096
ExitProcess proto,dwExitCode:QWORD

.data
firstval  qword 20002000h
secondval qword 11111111h
thirdval  qword 22222222h
sum       qword 0

.code
main proc
    mov rax,firstval      ; 64-bit 레지스터 사용
    add rax,secondval
    add rax,thirdval
    mov sum,rax

    invoke ExitProcess,0
main endp
end main

```

---

## **3. 발생할 수 있는 문법 오류(Syntax Error)와 해결 방법**

| 오류 메시지 (예시) | 원인 | 해결 방법 |
| --- | --- | --- |
| `error A2070: invalid combination of opcode and operand` | `mov eax, firstval`에서 32-bit 레지스터와 64-bit 변수 사용 | 32-bit 레지스터(`eax`) → 64-bit 레지스터(`rax`)로 변경 |
| `error A2003: unknown data type` | `ExitProcess proto,dwExitCode:dword` 그대로 사용 | `dword` → 64-bit 환경에 맞게 `QWORD`로 변경 |
| `operand size mismatch` | `add eax, secondval`에서 레지스터 크기와 변수 크기 불일치 | `eax` → `rax`로 변경 |
| 기타 주소 관련 오류 | 32-bit 코드(`.386`) + 64-bit 변수 사용 | `.386` 제거, 64-bit 환경에서 어셈블리 수행 |

---

### **4. 수정 후 요약**

1. 데이터 섹션: `dword` → `qword`
2. 레지스터: `eax` → `rax`
3. 함수 프로토타입: `dword` → `qword`
4. `.386` 지시문 제거 또는 `.x64` 사용 (MASM 64-bit 환경에서는 `.386` 불필요)
5. 레지스터 크기와 변수 크기가 항상 일치하도록 주의
