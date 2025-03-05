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

# 연속되는 문자 추출

해당줄의 문자열에서 문자가 연속적이지않고 떨어져서 똑같은 문자가 나오면 count 안함
ex) 3, happy, new, year -> 3 전부다 해당조건을 만족
ex) 1, aba, abab, abcabc, aaaba -> 0  전부다 해당조건을 불만족
![image](https://github.com/user-attachments/assets/848b8b24-8774-43ef-a96d-7779c116a675)

unordered_set으로 해당 문자열을 저장하고 prev에 전 문자를 저장하여 if(c != prev) -> if(seen.find(c) == seen.end()) find = false 으로 char_set에서 해당문자를 찾지못한것이다. -> else find = true; break; 으로 해당문자가 그전에 이미 나왔던 문자라면 조건 불만족.
