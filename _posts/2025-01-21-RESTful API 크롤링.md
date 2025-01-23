---
layout : post
title : "RESTful API 크롤링 기초 "

categories:
  - Blog
tags:
  - [AI, Machine_Learning, Pandas, Python, API, RESTful API]

toc: true
toc_sticky: true
 
date: 2025-01-21 22:52:00 +0900
---

# RESTful API 크롤링
- RESTful API 크롤링을 하는 이유?  
아마... 실시간으로 계속 업데이트 되는 데이터는 html로 긁어올 수 없기 때문에... 좀 더 자세한 이유가 있을 거 같은데, 그건 차차 알아보기로 하자(지금은 복습 시간도 부족함)

## 코스피, 코스닥, USD 
```python
import requests
import pandas as pd
```
#### 코스피
```python
# 개발자 도구 network에서 찾아온 코스피 링크
kospi_url = "https://api.stock.naver.com/chart/domestic/index/KOSPI?periodType=dayCandle"

res = requests.get(kospi_url)
res
```
res를 입력했을 때, `<Response [200]>` 가 나오면 정상 연결, 숫자가 400번대 나오면 나의문제^^(문법, 오타 등등,,,)

```python
# 응답받은 json형식의 원하는 정보를 datas에 저장
datas = res.json()["priceInfos"]

# 데이터 프레임 구성
kospi_df = pd.DataFrame(datas)
kospi_df.head()
```
#### 코스닥
```python
cosdak_url = "https://api.stock.naver.com/chart/domestic/index/KOSDAQ?periodType=dayCandle"
res_cos = requests.get(cosdak_url)
datas_cos = res_cos.json()["priceInfos"]
cosdak_df = pd.DataFrame(data_cos)
cosdak_df.head()
```


