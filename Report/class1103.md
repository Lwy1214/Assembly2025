# SHL,SHR : 로지컬shift 좌우 
- 빠른 2곱하기나누기 연산, 항상 새공간은 0으로 채워짐,캐리생김

# SAL,SAR : 산술 shift 좌우 
- SAL은 SHL과같지만 SAR의 경우는 최상위 부호비트유지,정수 나눗셈과 유사 
  
---------------------------
🔧 SHL (Shift Left)
- 기능: 지정된 수만큼 비트를 왼쪽으로 이동.
- 결과: 값이 2의 제곱 배로 증가.
- MSB(최상위 비트) → **CF(Carry Flag)**로 복사됨.
- LSB(최하위 비트) → 0으로 채워짐.
- 사용 예: SHL AX, 1 → AX 레지스터의 값을 2배로 만듦.

🔧 SHR (Shift Right)
- 기능: 지정된 수만큼 비트를 오른쪽으로 이동.
- 결과: 값이 2의 제곱 배로 감소.
- MSB → 0으로 채워짐.
- LSB → CF로 복사됨.
- 사용 예: SHR BX, 2 → BX 값을 4로 나눈 효과.

🔧 SAL (Shift Arithmetic Left)
- 기능: SHL과 동일하게 왼쪽으로 이동.
- 차이점: 산술적 의미를 강조하지만 실제로는 SHL과 동일하게 동작.
- 사용 예: SAL CX, 1 → CX 값을 2배로 증가.

🔧 SAR (Shift Arithmetic Right)
- 기능: 지정된 수만큼 비트를 오른쪽으로 이동하면서 부호 비트(MSB)를 유지.
- 결과: 음수일 경우에도 부호가 유지되며, 정수 나눗셈과 유사한 효과.
- MSB → 원래의 부호 비트로 채워짐.
- 사용 예: SAR DX, 1 → DX 값을 2로 나눈 결과, 음수일 경우에도 음수 유지.

⚠️ 주요 차이점 요약
<img width="702" height="247" alt="image" src="https://github.com/user-attachments/assets/dd1e63cd-a45e-4826-bcda-2ab9bc7babf5" />

🔄 ROL (Rotate Left)
- 기능: 비트를 왼쪽으로 회전.
- 동작 방식:
- 최상위 비트(MSB)가 밀려나면 → 최하위 비트(LSB)로 이동.
- 나머지 비트는 왼쪽으로 한 칸씩 이동.
- CF(Carry Flag): 회전으로 밀려난 MSB 값이 CF에 저장됨.
- 예시:
- AL = 1101 0011 (0xD3)
- ROL AL, 1 실행 후 → 1010 0111 (0xA7), CF = 1

🔄 ROR (Rotate Right)
- 기능: 비트를 오른쪽으로 회전.
- 동작 방식:
- 최하위 비트(LSB)가 밀려나면 → 최상위 비트(MSB)로 이동.
- 나머지 비트는 오른쪽으로 한 칸씩 이동.
- CF(Carry Flag): 회전으로 밀려난 LSB 값이 CF에 저장됨.
- 예시:
- AL = 1101 0011 (0xD3)
- ROR AL, 1 실행 후 → 1110 1001 (0xE9), CF = 1

🧠 요약 비교
<img width="683" height="148" alt="image" src="https://github.com/user-attachments/assets/aa2ba161-d445-43e4-ae7c-8ca6ef62f766" />


이 명령어들은 암호화, 비트 마스킹, 순환 버퍼 처리 등에서 유용하게 사용됩니다.
필요하다면 RCL/RCR(회전 + CF 포함)도 함께 설명해드릴 수 있어요!
🔄 RCL (Rotate through Carry Left)
- 기능: 비트를 왼쪽으로 회전하면서 CF도 함께 회전.
- 동작 방식:
- MSB → CF로 이동
- CF → LSB로 이동
- 나머지 비트는 왼쪽으로 한 칸씩 이동
- 비트 수: 총 비트 수 + CF = 9비트(8비트 레지스터 기준)
- 예시:
- AL = 1011 0110, CF = 1
- RCL AL, 1 실행 후 → AL = 0110 1101, CF = 1

🔄 RCR (Rotate through Carry Right)
- 기능: 비트를 오른쪽으로 회전하면서 CF도 함께 회전.
- 동작 방식:
- LSB → CF로 이동
- CF → MSB로 이동
- 나머지 비트는 오른쪽으로 한 칸씩 이동
- 비트 수: 총 비트 수 + CF = 9비트
- 예시:
- AL = 1011 0110, CF = 1
- RCR AL, 1 실행 후 → AL = 1101 1011, CF = 0
<img width="701" height="153" alt="image" src="https://github.com/user-attachments/assets/ba9ae278-e277-4665-9226-a6e7fcbf3598" />




