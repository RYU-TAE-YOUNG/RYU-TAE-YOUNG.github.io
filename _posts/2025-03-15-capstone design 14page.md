```
layout: single
titel: 캡스톤 디자인 14page
```
과제1.1
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
