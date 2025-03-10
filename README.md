# 숫자의 합

첫째 줄에 숫자의 개수 N이 주이지고, 둘째줄에 숫자 N개가 공백없이 주어진다.
![image](https://github.com/user-attachments/assets/0713c4d0-9e20-4556-adc6-da880172ce6d)

두번째 숫자열을 string타입으로 받고 숫자 - '0' 으로 다시 한자리 정수형으로 변환.

# 설탕배달 - DP

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

# 피보나치 0 과 1 몇번나오는지 계산 - DP

입력값을 넣으면 몇번의 0 과 1 을 도달하게되는지 다른 DP를 사용해서 풀어야한다. 
![image](https://github.com/user-attachments/assets/4cc1b274-53fc-4b9f-ac1a-2f7b5df85687)

int dp[41][2] = {0}; 2차원의 배열을 선언해줘서 초기값 0 과 1 을 선언해주고 40까지의 숫자들을 피보나치 DP 처럼 그대로 적용하여 계산해주면된다. 

    dp[0][0] = 1;  // fibonacci(0) 호출 시 0이 1번 출력
    dp[0][1] = 0;  // fibonacci(0) 호출 시 1이 0번 출력
    dp[1][0] = 0;  // fibonacci(1) 호출 시 0이 0번 출력
    dp[1][1] = 1;  // fibonacci(1) 호출 시 1이 1번 출력

    for (int i = 2; i <= 40; i++) {
        dp[i][0] = dp[i - 1][0] + dp[i - 2][0];
        dp[i][1] = dp[i - 1][1] + dp[i - 2][1];
    }


# LIS(가장 긴 증가하는 부분 수열 구하기) - DP

![image](https://github.com/user-attachments/assets/db2ec14e-98ae-48b0-9fdf-9dab8f6493e1)

O(n^2)으로 만들어 for i -> n 까지 for j -> i 까지 계속해서 앞과뒤의 숫자를 비교하며 dp[i] = max(dp[i],dp[j]+1) 로 갱신시켜준다.

    for(int i = 1; i < n; i++){
        for(int j = 0; j < i; j++){
            if(scores[i] > scores[j]) dp[i] = max(dp[i], dp[j]+1);
        }
        maxLength = max(maxLength, dp[i]);
    }

