```
layout: single
titel: 캡스톤 디자인 14page
```
# 과제1.1
# 세 자리 숫자 게임: 최적 전략 분석

주사위 두 개를 굴려 나온 눈의 수를 사용하여 두 자리 숫자를 만드는 게임에서,  
숫자가 클수록 이기는 게임입니다. 게임의 규칙은 다음과 같습니다:

1. **첫 번째 주사위**를 굴린 후,  
   이 눈을 **10의 자리**로 사용할지 **1의 자리**로 사용할지를 먼저 결정합니다.
2. 이후, **두 번째 주사위**를 굴린 눈은 자동으로 남은 자리(10의 자리 또는 1의 자리)에 배치됩니다.

어떤 전략을 사용해야 게임에 이길 가능성이 가장 클까?

```r
df <- read.csv("two_dice.csv")

# 전략 1: 첫 번째 주사위 값이 4 이상이면 10의 자리로 사용, 그렇지 않으면 1의 자리로 사용
df$score_4 <- ifelse(df$dice1 >= 4,
                     10 * df$dice1 + df$dice2,
                     10 * df$dice2 + df$dice1)

# 전략 2: 첫 번째 주사위 값이 5 이상이면 10의 자리로 사용, 그렇지 않으면 1의 자리로 사용
df$score_5 <- ifelse(df$dice1 >= 5,
                     10 * df$dice1 + df$dice2,
                     10 * df$dice2 + df$dice1)

# 전략 3: 첫 번째 주사위 값이 6 이상이면 10의 자리로 사용, 그렇지 않으면 1의 자리로 사용
df$score_6 <- ifelse(df$dice1 >= 6,
                     10 * df$dice1 + df$dice2,
                     10 * df$dice2 + df$dice1)

# 각 전략별 총점 및 평균 점수 계산
total_score_4 <- sum(df$score_4)
average_score_4 <- mean(df$score_4)
total_score_4
average_score_4

total_score_5 <- sum(df$score_5)
average_score_5 <- mean(df$score_5)
total_score_5
average_score_5

total_score_6 <- sum(df$score_6)
average_score_6 <- mean(df$score_6)
total_score_6
average_score_6

# 전략 1 (4 이상)
score_counts_4 <- table(df$score_4)
barplot(score_counts_4,
        main = "전략: 첫 번째 주사위 4 이상",
        xlab = "점수",
        ylab = "빈도",
        col = "skyblue",
        border = "blue")

# 전략 2 (5 이상)
score_counts_5 <- table(df$score_5)
barplot(score_counts_5,
        main = "전략: 첫 번째 주사위 5 이상",
        xlab = "점수",
        ylab = "빈도",
        col = "lightgreen",
        border = "green")

# 전략 3 (6 이상)
score_counts_6 <- table(df$score_6)
barplot(score_counts_6,
        main = "전략: 첫 번째 주사위 6 이상",
        xlab = "점수",
        ylab = "빈도",
        col = "salmon",
        border = "red")
```
![image](https://private-user-images.githubusercontent.com/126757930/423794518-ffad8b23-9b58-4155-a629-45e7ec72b9af.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzMxNzksIm5iZiI6MTc0MjI3Mjg3OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NTE4LWZmYWQ4YjIzLTliNTgtNDE1NS1hNjI5LTQ1ZTdlYzcyYjlhZi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDQxMTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kMWUwZjI4M2JkZTVkZjdiMmFiNjI2YTRlNzcxZDU5ZjU0NDdmYzgxN2Q0OTI1YzcxZGI1MTQxNWQ5MGFlMDQ5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.wtHz6wNOQv6slFflF2eIJg8U6oVHaBLNxtX3VvyxMgg)

![image](https://private-user-images.githubusercontent.com/126757930/423808014-7a870ae0-4329-4eab-8bb4-f3ebf65a2740.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzUzNDksIm5iZiI6MTc0MjI3NTA0OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzODA4MDE0LTdhODcwYWUwLTQzMjktNGVhYi04YmI0LWYzZWJmNjVhMjc0MC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNTE3MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iYWFiODZiM2QyZTI4ODI0NTBlMjEwNjk4NTA3YzdjM2ZkNDFhYTcwMWIyMDYyZDJjNjhhMDg3MTc1YWRjNTdhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.VZCTXLeeloomWygj4YxV6yC3tbd0cX0aMzNe1Evp-RI)

![image](https://private-user-images.githubusercontent.com/126757930/423808013-059ce642-e4ae-48b1-9d7f-26983463097f.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzUzNDksIm5iZiI6MTc0MjI3NTA0OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzODA4MDEzLTA1OWNlNjQyLWU0YWUtNDhiMS05ZDdmLTI2OTgzNDYzMDk3Zi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNTE3MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01ODI3NDhjN2IzNzg1ZWU1ZDRkNjg4MGE2ZmYzYTRiMjRiZDBhMzE2MjQwMmI2YWE1ZTA2MDE4YzkzM2JhZDI5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.rhuNu7RSOY5Tcv0wrw7IiUJGxL2rd_oTU5PSWAMiJ6w)


![image](https://private-user-images.githubusercontent.com/126757930/423794476-c6d4d7d8-5b7e-4067-9415-d67e36c956cc.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzI4ODIsIm5iZiI6MTc0MjI3MjU4MiwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NDc2LWM2ZDRkN2Q4LTViN2UtNDA2Ny05NDE1LWQ2N2UzNmM5NTZjYy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDM2MjJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jZGU4NGI3ZmQ4NzFlNjBlYmU0MjM0NDc4ODZkMjI1MDQwMmI2NmIyYmEzNDE5MTY3ODI5MDgyYjhjNzZjMmQxJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.1fFeUqIMRtjEoa3phlg2xygsc1fNCG8x-V8TJ2MQf34)

![image](https://private-user-images.githubusercontent.com/126757930/423794493-2c8b6686-b379-4317-b36b-2e36cbab0049.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzMxNzksIm5iZiI6MTc0MjI3Mjg3OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NDkzLTJjOGI2Njg2LWIzNzktNDMxNy1iMzZiLTJlMzZjYmFiMDA0OS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDQxMTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hZmU1OWYxMTA3YjJiODc1YjczYzVjY2Q5NzI2ZDY5YjQwN2Y1ODg5MDE4ZjQzMjJmOGJkYWUwZGQ2ZjJmMTc3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.eoGaUeejSdKDptlOER2WD-9zrhNlqcpeIz9yi1U_9aQ)

![image](https://private-user-images.githubusercontent.com/126757930/423794504-0e9f20c9-9002-4c05-817b-4ba98cde6a24.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzMxNzksIm5iZiI6MTc0MjI3Mjg3OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NTA0LTBlOWYyMGM5LTkwMDItNGMwNS04MTdiLTRiYTk4Y2RlNmEyNC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDQxMTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zNzFkZDU3NmU2MGQyYzMzNGI4NWZhNDQzMzRhYzRlYjIwYTdkZjYzODJiNjM1NjlkNDY4MWIyOTEzMDJmZDMzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Wk_ZsDCVQAheKNlD_x-RqVJmxqkz1Vz8JundLA5brOY)

# 이론적인 기대 점수 계산

이 문서에서는 주사위 두 개를 사용하여 다음과 같은 전략 하에서 최종 두 자리 수의 평균(기댓값)을 계산하는 과정을 설명합니다.

## 전략 1

**전략 1:**  
- **조건:**  
  - if (dice1 ≥ 4): 최종 점수 = 10 × dice1 + dice2  
  - else: 최종 점수 = 10 × dice2 + dice1  

### (A) dice1 = 1, 2, 3 (조건 미충족 → else 적용)

1. **dice1 = 1인 경우**  
   - dice2 = 1 → 10 × 1 + 1 = 11  
   - dice2 = 2 → 10 × 2 + 1 = 21  
   - dice2 = 3 → 10 × 3 + 1 = 31  
   - dice2 = 4 → 10 × 4 + 1 = 41  
   - dice2 = 5 → 10 × 5 + 1 = 51  
   - dice2 = 6 → 10 × 6 + 1 = 61  
   - **합계:** 11 + 21 + 31 + 41 + 51 + 61 = 216

2. **dice1 = 2일 경우**  
   - 점수: 12, 22, 32, 42, 52, 62  
   - **합계:** 222

3. **dice1 = 3일 경우**  
   - 점수: 13, 23, 33, 43, 53, 63  
   - **합계:** 228

### (B) dice1 = 4, 5, 6 (조건 충족 → if 적용)

1. **dice1 = 4인 경우**  
   - dice2 = 1 → 10 × 4 + 1 = 41  
   - dice2 = 2 → 10 × 4 + 2 = 42  
   - dice2 = 3 → 10 × 4 + 3 = 43  
   - dice2 = 4 → 10 × 4 + 4 = 44  
   - dice2 = 5 → 10 × 4 + 5 = 45  
   - dice2 = 6 → 10 × 4 + 6 = 46  
   - **합계:** 41 + 42 + 43 + 44 + 45 + 46 = 261

2. **dice1 = 5인 경우**  
   - 점수: 51, 52, 53, 54, 55, 56  
   - **합계:** 321

3. **dice1 = 6인 경우**  
   - 점수: 61, 62, 63, 64, 65, 66  
   - **합계:** 381

### 전체 경우의 계산

전체 36가지 경우(각 dice1에 대해 6가지 dice2 값)가 주어질 때,  
전체 36가지 경우의 총합은:

\[
216 + 222 + 228 + 261 + 321 + 381 = 1629
\]

따라서, 전략 1의 **평균 기대 점수**는

\[
\frac{1629}{36} \approx 45.25
\]

## 전략 2 및 전략 3

나머지 전략을 비슷한 방식으로 계산하면,  
- **전략 2**의 평균 기대 점수는 약 **44.50**,  
- **전략 3**의 평균 기대 점수는 약 **42.25**가 됩니다.

따라서,  
**전략 1이 가장 나은 방법임을 알 수 있습니다.**

---


# 과제1.2
# 세 자리 숫자 게임: 최적 전략 분석

주사위 3개를 굴려 나온 눈의 수를 사용하여 세 자리 숫자를 만드는 게임에서, 최종 숫자가 클수록 이기는 게임입니다.  
게임의 진행 방식은 다음과 같습니다:

1. **첫 번째 주사위**를 굴린 후, 그 눈을 세 자리 숫자 중 **어느 자리에 사용할지 결정**합니다.
2. 이후, **두 번째 주사위**의 결과는 남은 두 자리 중 하나에 자동으로 배정되고,
3. **세 번째 주사위**의 결과는 남은 한 자리에 배정됩니다.

어떤 전략이 최선의 전략인가?

```r
simulate_game_fixed <- function(d1, d2, d3) {
  # d1의 고정 배치: 1-2 → 1의자리, 3-4 → 10의자리, 5-6 → 100의자리
  if (d1 <= 2) {
    pos_d1 <- 3  # 일의 자리
  } else if (d1 <= 4) {
    pos_d1 <- 2  # 십의 자리
  } else {
    pos_d1 <- 1  # 백의 자리
  }
  
  # 빈 자리 설정 및 d1 배치
  slots <- rep(NA, 3)        # 길이 3의 벡터를 생성. 초기값은 NA로, 각 자리(백, 십, 일)를 나타냄
  slots[pos_d1] <- d1        # d1을 고정 전략에 따라 pos_d1 위치에 배치
  remaining <- setdiff(1:3, pos_d1)  # 1, 2, 3 중에서 d1이 배치된 자리를 제외한 나머지 자리의 인덱스를 구함
  
  # 남은 자리 중 d2 배치 결정:
  # d3 값(1:6)이 들어갔을 때 최종 수의 평균(기댓값)이 가장 높은 자리를 선택함
  best_exp <- -Inf          # best_exp 변수에 현재까지의 최고 기대값을 저장할 용도로, 아주 작은 값(-무한대)로 초기화함
  best_d2_pos <- NA         # d2를 배치할 최적의 자리 위치를 저장할 변수
  for (pos in remaining) {  # 남은 각 자리(pos)에 대해 반복
    temp <- slots          # 현재 슬롯 상태를 복사
    temp[pos] <- d2        # 후보로 현재 자리(pos)에 d2를 배치
    other <- setdiff(remaining, pos)  # d2를 배치한 후 남은 유일한 자리(나머지 하나)를 구함
    # sapply를 이용하여 d3가 1부터 6까지 들어갈 때의 최종 수를 계산하고, 그 평균을 exp_val에 저장
    exp_val <- mean(sapply(1:6, function(x) {
      temp[other] <- x      # 남은 자리(other)에 d3 후보값 x를 넣음
      make_number(temp[1], temp[2], temp[3])  # 최종 세 자리 수를 계산
    }))
    if (exp_val > best_exp) {  # 만약 현재 자리에서의 기대값이 이전보다 크면,
      best_exp <- exp_val      # best_exp를 갱신
      best_d2_pos <- pos       # 최적의 d2 배치 위치를 저장
    }
  }
  slots[best_d2_pos] <- d2  # 최적의 자리(best_d2_pos)에 d2를 배치
  
  # 남은 한 자리에 d3 배치
  last_pos <- setdiff(1:3, c(pos_d1, best_d2_pos))  # d1과 d2가 배치된 자리 외의 나머지 한 자리를 구함
  slots[last_pos] <- d3   # 남은 자리(last_pos)에 d3를 배치
  
  # 최종 세 자리 수를 계산하여 반환
  make_number(slots[1], slots[2], slots[3])
}


games <- read.csv("three_dice.csv")

# 각 게임의 최종 점수 
games$score <- mapply(simulate_game_fixed, games$dice1, games$dice2, games$dice3)

sum(games$score)
mean(games$score)


# 그래프
score_table <- table(games$score)
barplot(score_table, main = "최적 전략 사용 시 세 자리 수 분포",
        xlab = "점수", ylab = "빈도",
        col = "skyblue", border = "blue")

# 모든 216가지 경우에 대한 이론적 기댓값 
outcomes <- expand.grid(dice1 = 1:6, dice2 = 1:6, dice3 = 1:6) # expand.grid() 함수를 사용하여 d1, d2, d3 각각 1부터 6까지 가능한 모든 조합(총 216가지)을 생성하여 outcomes 데이터프레임에 저장
all_scores <- mapply(simulate_game_fixed, outcomes$dice1, outcomes$dice2, outcomes$dice3) # mapply() 함수를 사용해 216가지 조합 각각에 대해 simulate_game_fixed() 함수를 실행하고, 결과(최종 세 자리 수)를 all_scores 벡터에 저장
theoretical_expectation <- mean(all_scores)
theoretical_expectation
```

![image](https://private-user-images.githubusercontent.com/126757930/423800802-9a1779ef-cfed-40ca-a8fb-9016b51f5973.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzM5NzMsIm5iZiI6MTc0MjI3MzY3MywicGF0aCI6Ii8xMjY3NTc5MzAvNDIzODAwODAyLTlhMTc3OWVmLWNmZWQtNDBjYS1hOGZiLTkwMTZiNTFmNTk3My5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDU0MzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02YzUwOWM1YTMwOTk4YWI2Nzg0MTE2ZGUxZjQyMjEzNzQyNGE4ZjRkNjQ0MTllZWY2YjEzYjZjZWJjNzA5Zjg3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.iuEHPFVN4xUsAm7TTjdmUrstwZD3kj6_9kdDhBEkHA8)

![image](https://private-user-images.githubusercontent.com/126757930/423811083-1382fef4-a9d7-43f7-a5fc-391c43c64e11.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzYwMzIsIm5iZiI6MTc0MjI3NTczMiwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzODExMDgzLTEzODJmZWY0LWE5ZDctNDNmNy1hNWZjLTM5MWM0M2M2NGUxMS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNTI4NTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05Yzc4MmQ1MzEwYTRhYzU5YjZiZWM4NWYxYTdlNjNhYzExZGMyZDVlNmNlMmQ3NTE4ZTI3MDliMTk0MDk0MjMzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.H-SlDawTNoC2h9mJSggIZorblEPWciFgCu5a_VTzbXE)

![image](https://private-user-images.githubusercontent.com/126757930/423800822-12802d4d-753e-4187-9c8d-20f45127577d.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzM5NzMsIm5iZiI6MTc0MjI3MzY3MywicGF0aCI6Ii8xMjY3NTc5MzAvNDIzODAwODIyLTEyODAyZDRkLTc1M2UtNDE4Ny05YzhkLTIwZjQ1MTI3NTc3ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDU0MzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00MDkzNDg2YzNjMzA0YWRkYzIyOTdjZTI1MDk2ZjBiNzMwZGIxOTVkYzUwYTg5ZjZiMWJlZjQ0NGJmMWQxYWU3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.lVU5JdXq_iB4yrYd0NhpTsBfEf3MzGKDsxmCqcg25-M)



