```
layout: single
title: 캡스톤 디자인 14page 과제
```

과제 1.1
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


total_score_6 <- sum(df$score_6)
average_score_6 <- mean(df$score_6)


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
---
img_path:/_posts/2025 캡스톤 디자인 14page(과제1.1, 그래프1).png
---















과제1.2
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
