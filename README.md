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

# 시간초과 문제를 해결하기위해

    ios::sync_with_stdio(false); 
    cin.tie(NULL); 

// cin와 cout은 내부적으로 C의 scanf() 와 printf()와 버퍼를 공유하기때문에 stdin과 stdout의 버퍼를 동기화하는과정에서 시간이 많이걸림 그 동기화 과정을 끄게함.

// 기본적으로 cin과 cout의 연결을 끊음. 즉 cin을 실행하기 전에 cout의 출력 버퍼를 비움하도록 동작.

# 최소 묶음으로 값더해주기 - 자료구조(priority queue, min heap)

ex) 10장, 20장, 40장이 있으면 -> (10+20) + (30+40) = 100 이되는것. 가장 최소의 합이 나오게 결과값을 구해야한다.
![image](https://github.com/user-attachments/assets/5aedfbe7-e4bf-4871-8587-5d3879e14672)

구하기위해서 min heap을 사용하여 가장 최소의 두개의 묶음을 선별하고 result에 더하고나서 다시 그 합을 pq.push(합) 으로 넣어주면 min heap의 성질때문에 계속해서 최솟값이 top()으로 가게 되어서 가장 작은 두개의 묶음을 계속해서 업데이트 가능하다. 

    while (pq.size() > 1) {
        int first = pq.top(); pq.pop();
        int second = pq.top(); pq.pop();
        
        int sum = first + second; // 두 묶음을 합친 비교 횟수
        total_comparisons += sum;
        
        pq.push(sum); // 합친 묶음을 다시 힙에 삽입
    }

# 송신탑 왼쪽에 더큰 높이가 있으면 그 index에서 수신하는것을 출력 - 자료구조, stack

ex) 6 9 5 7 4 -> 0 0 2 2 4 , 5랑 7의 높이를 가진 송신탑은 왼쪽으로 레이저를 보내며 9라는 더 큰 송신탑에게 송신 가능.

계속해서 스택으로 높이가 큰 송신탑을 업데이트하며 높이가 더작으면 pop()을 하고 높이가 크면 그 인덱스를 저장하는 방식으로 해결가능.
예를들어 9에서 스택에 저장하고 5에서도 스택을 저장하면 그다음 7에서 5보다 더큰 송신탑을 가지고있기떄문에 pop()으로 5를 제거하고 9 송신탑이 top()이 되게된다.

    for (int i = 0; i < N; i++) {
        while (!s.empty() && s.top().first < heights[i]) {
            s.pop(); // 현재 탑보다 낮은 탑들은 수신할 수 없으므로 제거
        }

        if (!s.empty()) {
            results[i] = s.top().second + 1; // 탑의 인덱스는 1-based index로 저장
        }

        s.push({heights[i], i});
    }
