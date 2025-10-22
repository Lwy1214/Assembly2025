

<img width="1034" height="590" alt="스크린샷 2025-10-16 091528" src="https://github.com/user-attachments/assets/8d84e0da-a5fc-4154-9c8d-f2eb6b4ac642" />

# 중간고사문제 64비트 레지스터에 대해 기술하시오
```
EAX (32비트)
 └── AX (하위 16비트)
      ├── AH (상위 8비트)
      └── AL (하위 8비트)
```
      
  <img width="745" height="563" alt="image" src="https://github.com/user-attachments/assets/236ac897-571e-46e1-9065-40e9eaf21648" />


# 부호확장

## MOVZX
앞의 숫자를 무조건 0으로채움 

## MOVSX
최상위 비트에 따라서 앞의숫자가 채워짐 

🧭 주요 플래그 설명

| 플래그명 | 약어 | 의미 |
| --- | --- | --- |
| Carry Flag | CF | 덧셈에서 자리올림(overflow), 뺄셈에서 자리내림(borrow)이 발생했는지 표시 |
| Zero Flag | ZF | 연산 결과가 0이면 설정됨 |
| Sign Flag | SF | 결과의 최상위 비트(부호 비트)가 1이면 설정됨 → 음수 |
| Overflow Flag | OF | 부호 있는 연산에서 결과가 표현 범위를 벗어났을 때 설정됨 |
| Parity Flag | PF | 결과의 하위 8비트에서 1의 개수가 짝수면 설정됨 |
| Auxiliary Carry Flag | AF | BCD 연산에서 사용됨. 하위 4비트에서 자리올림이 발생하면 설정됨 |

🔍 예시로 이해하기

예: `add al, 1` → `al = 255` + `1` = `0` (256 → overflow)

- **CF = 1** (자리올림 발생)
- **ZF = 1** (결과가 0)
- **SF = 0** (0은 양수)
- **OF = 0** (부호 있는 overflow는 아님)
- **PF = 1** (0은 1의 개수가 0 → 짝수)
- **AF = ?** (BCD 연산이 아니면 무시)

✅ 요약
- CF: 자리올림/내림
- ZF: 결과가 0
- SF: 결과가 음수
- OF: 부호 있는 overflow
- PF: 짝수 패리티
- AF: BCD용 자리올림
