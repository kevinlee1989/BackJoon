# 숫자의 합

첫째 줄에 숫자의 개수 N이 주이지고, 둘째줄에 숫자 N개가 공백없이 주어진다.
![image](https://github.com/user-attachments/assets/0713c4d0-9e20-4556-adc6-da880172ce6d)

두번째 숫자열을 string타입으로 받고 숫자 - '0' 으로 다시 한자리 정수형으로 변환.

# 설탕배달

주어진 숫자가 5킬로그램 과 3킬로그램 가방으로 들고 갈수있는지,
들고갈수있다면 더 적은 개수의 봉지를 사용
들고갈수없다면 -1 반환.

![image](https://github.com/user-attachments/assets/3c96a559-af40-4d57-957e-ca8bbda7ccc1)

1. 5로 나누어 떨어지면 count += 숫자 / 5 를 해주고
2. 5로 나누어 떨어지지않는다면 숫자 -= 3 으로 계속 감소 시키고 다시 1번부터 반복.
