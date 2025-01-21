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

## 코스피, 코스닥, USD 
```python
import requests
import pandas as pd
```

```python
# 코스피 링크
kospi_url = "https://api.stock.naver.com/chart/domestic/index/KOSPI?periodType=dayCandle"

res = requests.get(kospi_url)
res
```
res를 입력했을 때, `<Response [200]>` 가 나오면 정상 연결, 숫자가 400번대 나오면 나의문제^^(문법, 오타 등등,,,)

```python
datas = res.json()["priceInfos"]

# 데이터 프레임 구성
kospi_df = pd.DataFrame(datas)
kospi_df.head()
```

