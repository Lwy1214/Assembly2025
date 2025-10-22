

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

✅ 요약
- CF: 자리올림/내림
- ZF: 결과가 0
- SF: 결과가 음수
- OF: 부호 있는 overflow
- PF: 짝수 패리티
- AF: BCD용 자리올림

