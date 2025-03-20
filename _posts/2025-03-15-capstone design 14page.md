 ```
layout: single
titel: 캡스톤 디자인 14page
```
# PPDAC: 데이터 분석 과정 이해하기

PPDAC는 **Problem, Plan, Data, Analysis, Conclusion**의 약자로,  
데이터 분석 프로젝트를 체계적으로 수행하기 위한  
기본적인 다섯 단계 모델입니다. 이 모델은 데이터 분석의 모든 과정을  
논리적이고 일관되게 진행하는 데 도움을 줍니다.

---

## 1. Problem (문제 정의)

- **문제 정의:**  
  분석할 문제나 질문을 명확하게 정의합니다.  
  예를 들어, "어떤 요인이 판매에 영향을 미치는가?"와 같이,  
  해결해야 할 구체적인 문제를 설정합니다.

- **목표 설정:**  
  분석의 목표를 설정하고, 어떤 결과를 도출할 것인지 결정합니다.

---

## 2. Plan (계획)

- **분석 계획 수립:**  
  문제를 해결하기 위한 방법론과 접근 방식을 결정합니다.  
  예를 들어, 어떤 통계적 기법을 사용할지, 모델링 방법은 무엇인지 등을  
  계획합니다.

- **분석 도구 및 기법:**  
  사용할 데이터 분석 도구(R, Python 등)와 기법(회귀분석, 군집분석 등)을  
  정합니다.

---

## 3. Data (데이터)

- **데이터 수집:**  
  문제 해결에 필요한 데이터를 수집합니다.  
  데이터는 내부 데이터베이스, 공개 데이터셋, 웹 크롤링 등 여러 경로로  
  얻을 수 있습니다.

- **데이터 전처리:**  
  수집한 데이터를 정리하고, 결측치 처리, 이상치 제거, 데이터 정규화 등  
  필요한 전처리 과정을 수행합니다.

---

## 4. Analysis (분석)

- **탐색적 데이터 분석 (EDA):**  
  데이터의 특성을 이해하기 위해 시각화 및 기초 통계 분석을 진행합니다.

- **모델링 및 추론:**  
  문제 해결에 필요한 통계 모델이나 기계 학습 모델을 구축하고,  
  모델의 성능을 평가하며, 인사이트를 도출합니다.

---

## 5. Conclusion (결론)

- **결과 요약:**  
  분석 결과를 요약하고, 문제 해결에 얼마나 기여했는지 평가합니다.

- **의사결정 및 실행:**  
  분석 결과를 바탕으로 의사결정을 내리고, 실제 행동에 옮길 수 있는  
  실행 계획을 수립합니다.

---

## 결론

PPDAC 모델은 데이터 분석의 시작부터 끝까지  
체계적이고 일관된 접근을 가능하게 하며,  
문제 정의, 계획 수립, 데이터 처리, 분석, 결론 도출의 각 단계에서  
중요한 포인트를 놓치지 않도록 도와줍니다.

이 모델을 활용하면,  
복잡한 데이터 분석 프로젝트에서도 명확한 목표와 체계적인 진행 방식을 유지할 수 있으며,  
분석 결과를 보다 효과적으로 의사결정에 반영할 수 있습니다.

---

# 과제1.1
# 두 자리 숫자 게임: 최적 전략 분석

주사위 두 개를 굴려 나온 눈의 수를 사용하여 두 자리 숫자를 만드는 게임에서,  
숫자가 클수록 이기는 게임입니다. 게임의 규칙은 다음과 같습니다:

1. **첫 번째 주사위**를 굴린 후,  
   이 눈을 **10의 자리**로 사용할지 **1의 자리**로 사용할지를 먼저 결정합니다.
2. 이후, **두 번째 주사위**를 굴린 눈은 자동으로 남은 자리(10의 자리 또는 1의 자리)에 배치됩니다.

어떤 전략을 사용해야 게임에 이길 가능성이 가장 클까?

---

```r
df <- read.csv("two_dice.csv")
df
```
![2025 캡스톤 디자인 14page(과제1 1결과0)](https://github.com/user-attachments/assets/cca21882-bd65-4154-b4f5-9307600082fb)

---

```r
# 전략 1: 첫 번째 주사위 값이 4 이상이면 10의 자리로 사용, 그렇지 않으면 1의 자리로 사용
df$score_4 <- ifelse(df$dice1 >= 4,
                     10 * df$dice1 + df$dice2,
                     10 * df$dice2 + df$dice1)

# 전략 1: 총점 및 평균 점수 계산
total_score_4 <- sum(df$score_4)
average_score_4 <- mean(df$score_4)
total_score_4
average_score_4
```
![2025 캡스톤 디자인 14page(과제1 1결과)](https://github.com/user-attachments/assets/8de4f0da-70f7-472e-8dc6-0c6823ca8a3e)


```r
# 전략 2: 첫 번째 주사위 값이 5 이상이면 10의 자리로 사용, 그렇지 않으면 1의 자리로 사용
df$score_5 <- ifelse(df$dice1 >= 5,
                     10 * df$dice1 + df$dice2,
                     10 * df$dice2 + df$dice1)
# 전략 2: 총점 및 평균 점수 계산
total_score_5 <- sum(df$score_5)
average_score_5 <- mean(df$score_5)
total_score_5
average_score_5
```
![2025 캡스톤 디자인 14page(과제1 1결과2)](https://github.com/user-attachments/assets/e8262c6d-ad3b-426b-88bf-6ffa6abe846e)


```r
# 전략 3: 첫 번째 주사위 값이 6 이상이면 10의 자리로 사용, 그렇지 않으면 1의 자리로 사용
df$score_6 <- ifelse(df$dice1 >= 6,
                     10 * df$dice1 + df$dice2,
                     10 * df$dice2 + df$dice1)

# 전략 3: 총점 및 평균 점수 계산
total_score_6 <- sum(df$score_6)
average_score_6 <- mean(df$score_6)
total_score_6
average_score_6
```
![2025 캡스톤 디자인 14page(과제1 1결과3)](https://github.com/user-attachments/assets/3ef91ea2-7e3e-400b-a8ac-e4f739c5f899)

---

```r
# 이론적인 기대값과 확률분포 구하기
# 모든 경우의 수 구하기
all_combinations <- expand.grid(dice1 = 1:6, dice2 = 1:6)
all_combinations
```
![2025 캡스톤 디자인 14page(과제1 1결과4)](https://github.com/user-attachments/assets/e0736b65-609f-4e5e-a2fc-335c8545e9e1)

---

```r
# 전략 1 : 첫 번째 주사위가 4 이상이면 10의 자리로, 그렇지 않으면 1의 자리로 사용
score_strategy1 <- ifelse(all_combinations$dice1 >= 4,
                       10 * all_combinations$dice1 + all_combinations$dice2,
                       10 * all_combinations$dice2 + all_combinations$dice1)

score_strategy1
```
![2025 캡스톤 디자인 14page(과제1 1결과5)](https://github.com/user-attachments/assets/2b88154c-2c54-4b39-815a-5140ecfd01f5)

```r
# 전략 2 : 첫 번째 주사위가 5 이상이면 10의 자리로, 그렇지 않으면 1의 자리로 사용
score_strategy2 <- ifelse(all_combinations$dice1 >= 5,
                       10 * all_combinations$dice1 + all_combinations$dice2,
                       10 * all_combinations$dice2 + all_combinations$dice1)
score_strategy2
```
![2025 캡스톤 디자인 14page(과제1 1결과6)](https://github.com/user-attachments/assets/fb465fc1-cd3f-4d90-9515-de663baa9032)

```r 
# 전략 3 : 첫 번째 주사위가 6 이상이면 10의 자리로, 그렇지 않으면 1의 자리로 사용
score_strategy3 <- ifelse(all_combinations$dice1 >= 6,
                       10 * all_combinations$dice1 + all_combinations$dice2,
                       10 * all_combinations$dice2 + all_combinations$dice1)
score_strategy3
```
![2025 캡스톤 디자인 14page(과제1 1결과7)](https://github.com/user-attachments/assets/464b1dcb-662a-4054-84c0-26313576a3fc)

---

```r
# 전략 1의 기댓값
expectation_strategy1 <- mean(score_strategy1)
expectation_strategy1
```
![2025 캡스톤 디자인 14page(과제1 1결과8)](https://github.com/user-attachments/assets/4a36cb64-83b2-4b2c-abf9-db327a7aee0d)

```r
# 전략 2의 기댓값
expectation_strategy2 <- mean(score_strategy2)
expectation_strategy2
```
![2025 캡스톤 디자인 14page(과제1 1결과9)](https://github.com/user-attachments/assets/9885dc49-9d33-424e-a2fb-e48e37e5671c)

```r
# 전략 3의 기댓값
expectation_strategy3 <- mean(score_strategy3)
expectation_strategy3
```
![2025 캡스톤 디자인 14page(과제1 1결과10)](https://github.com/user-attachments/assets/d47fc5ec-4121-4376-ba30-57fec6078606)

---

```r
# 전략 1 확률 분포
dist_strategy1 <- prop.table(table(score_strategy1))
barplot(dist_strategy1, main = "Strategy 1 Score Distribution",
        xlab = "Score", ylab = "Probability", col = "skyblue", border = "blue")
```
![2025 캡스톤 디자인 14page(과제1 1, 그래프1)](https://github.com/user-attachments/assets/99eb0cd7-fa2c-4047-943a-22ead651246c)

```r
# 전략 2 확률 분포
dist_strategy2 <- prop.table(table(score_strategy2))
barplot(dist_strategy2, main = "Strategy 2 Score Distribution",
        xlab = "Score", ylab = "Probability", col = "lightgreen", border = "darkgreen")
```
![2025 캡스톤 디자인 14page(과제1 1, 그래프2)](https://github.com/user-attachments/assets/f9cc8e1c-72f3-44e5-a9d4-1ce6935c3006)

```r
# 전략 3 확률 분포
dist_strategy3 <- prop.table(table(score_strategy3))
barplot(dist_strategy3, main = "Strategy 3 Score Distribution",
        xlab = "Score", ylab = "Probability", col = "salmon", border = "red")
```
![2025 캡스톤 디자인 14page(과제1 1, 그래프3)](https://github.com/user-attachments/assets/3e0c8dca-76ac-430f-af47-d84ea396dbd8)

---

# 이론적인 기대 점수 계산(수식)

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
1629/36=45.25
\]

## 전략 2 및 전략 3

나머지 전략을 비슷한 방식으로 계산하면,  
- **전략 2**의 평균 기대 점수는 약 **44.50**,  
- **전략 3**의 평균 기대 점수는 약 **42.25**가 됩니다.

따라서,  
**전략 1이 가장 나은 방법임을 알 수 있습니다.**

-------------------------------------------------------------------------


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
```

---

```r
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



- **첫 번째 후회:**  
  만약 첫 번째 주사위가 3이나 4와 같이 애매한 숫자가 나왔는데,  
  너무 소극적으로 이 숫자를 100의 자리에 배치해버린다면,  
  이후 두 번째와 세 번째 주사위에서 5나 6이 나와야 할 기회를 잃어  
  "100% 후회"하게 될 것임

- **두 번째 후회:**  
  또 다른 예로,  
  첫 번째와 두 번째 주사위가 모두 3이나 4가 나왔는데,  
  마지막 주사위에서 높은 숫자를 기대하고 과감하게 100의 자리를 남겨두었다가  
  실제로 1이나 2가 나오면 역시 "100% 후회"하게 될 것임

## 인생과 사업에 대한 교훈

- **인생에서의 첫 번째 후회:**  
  만약 인생에서 도전할 기회가 여러 번 주어졌는데,  
  한 번 실패했다고 두 번째, 세 번째 기회를 포기한다면,  
  평생 후회할 수 있다는 교훈을 얻을 수 있음

- **사업에서의 두 번째 후회:**  
  예를 들어, 내가 사업을 시작해 회사를 세우고 직원들을 두고 있다가,  
  두 번의 실패 후 마지막 도전에서 파산에 이르게 된다면,  
  나뿐만 아니라 직원들까지 큰 위험에 빠져 후회할 수 있음

## 결론

이 사례들을 통해,  
**어떤 결정도 성급하게 내리지 말고, 충분한 고민과 계획 후에 신중하게 선택해야 한다**는 중요한 교훈을 얻을 수 있음.  
한 번의 실패에 좌절하여 추가 도전을 포기하면 평생 후회할 수 있으며,  
또한 과감한 결정이 오히려 위험으로 이어질 수도 있으므로,  
늘 모든 기회를 꼼꼼히 따져보고 진행해야함
