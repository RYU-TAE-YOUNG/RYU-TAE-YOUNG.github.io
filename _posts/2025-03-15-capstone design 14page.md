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
![image](https://private-user-images.githubusercontent.com/126757930/423794518-ffad8b23-9b58-4155-a629-45e7ec72b9af.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzMxNzksIm5iZiI6MTc0MjI3Mjg3OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NTE4LWZmYWQ4YjIzLTliNTgtNDE1NS1hNjI5LTQ1ZTdlYzcyYjlhZi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDQxMTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kMWUwZjI4M2JkZTVkZjdiMmFiNjI2YTRlNzcxZDU5ZjU0NDdmYzgxN2Q0OTI1YzcxZGI1MTQxNWQ5MGFlMDQ5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.wtHz6wNOQv6slFflF2eIJg8U6oVHaBLNxtX3VvyxMgg)

![image](https://private-user-images.githubusercontent.com/126757930/423794476-c6d4d7d8-5b7e-4067-9415-d67e36c956cc.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzI4ODIsIm5iZiI6MTc0MjI3MjU4MiwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NDc2LWM2ZDRkN2Q4LTViN2UtNDA2Ny05NDE1LWQ2N2UzNmM5NTZjYy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDM2MjJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jZGU4NGI3ZmQ4NzFlNjBlYmU0MjM0NDc4ODZkMjI1MDQwMmI2NmIyYmEzNDE5MTY3ODI5MDgyYjhjNzZjMmQxJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.1fFeUqIMRtjEoa3phlg2xygsc1fNCG8x-V8TJ2MQf34)

![image](https://private-user-images.githubusercontent.com/126757930/423794493-2c8b6686-b379-4317-b36b-2e36cbab0049.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzMxNzksIm5iZiI6MTc0MjI3Mjg3OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NDkzLTJjOGI2Njg2LWIzNzktNDMxNy1iMzZiLTJlMzZjYmFiMDA0OS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDQxMTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hZmU1OWYxMTA3YjJiODc1YjczYzVjY2Q5NzI2ZDY5YjQwN2Y1ODg5MDE4ZjQzMjJmOGJkYWUwZGQ2ZjJmMTc3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.eoGaUeejSdKDptlOER2WD-9zrhNlqcpeIz9yi1U_9aQ)

![image](https://private-user-images.githubusercontent.com/126757930/423794504-0e9f20c9-9002-4c05-817b-4ba98cde6a24.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIyNzMxNzksIm5iZiI6MTc0MjI3Mjg3OSwicGF0aCI6Ii8xMjY3NTc5MzAvNDIzNzk0NTA0LTBlOWYyMGM5LTkwMDItNGMwNS04MTdiLTRiYTk4Y2RlNmEyNC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOFQwNDQxMTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zNzFkZDU3NmU2MGQyYzMzNGI4NWZhNDQzMzRhYzRlYjIwYTdkZjYzODJiNjM1NjlkNDY4MWIyOTEzMDJmZDMzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Wk_ZsDCVQAheKNlD_x-RqVJmxqkz1Vz8JundLA5brOY)


