---
title: "[코드카타] Query II"
description: SQL 코드카타 1문제 풀이
date: 2026-03-21 00:00:00 +0900
categories: [Code Kata, SQL]
tags: [hackerrank]
math: true
mermaid: true
---

<!-- 파일명: _posts/2026-10-31-sql-codekata-주제-영문.md -->

## 1. [Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5/problem?isFullScreen=true)

- 테이블

![alt text](assets/img/kata_weather 5.jpg)


- 문제 
```plaintext
1. STATION 테이블의 가장 긴 이름과 짧은 이름을 가진 `CITY` 이름을 쿼리하시오.
2. 가장 짧고 긴 도시 이름의 길이를 각각 쿼리하시오. (ex: 도시, 길이)
```

- 풀이

1. 각 테이블에서 `char_length` 문법을 사용하고 `order by`절에서 
해당 도시와 컬럼의 길이를 가진 도시 한곳을 쿼리합니다.

2. 각 컬럼 두개를 `Union`으로 수직결합합니다.

```sql
(SELECT city, char_length(city)
from station
order by char_length(city) asc,
city asc
limit 1)

union all 

(SELECT city, char_length(city)
from station 
order by char_length(city) desc,
city asc
limit 1)
;
```