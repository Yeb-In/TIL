# Mar 2 Wed

# 데이터 프레임

1. 데이터 프레임의 구조

- auto-mpg.csv 데이터셋 사용

- mpg(연비), cylindes(실린더 수), displacement(배기량), horsepower(출력), weight(차중), acceleration(가속 능력), model_year(출시 년도), origin(제조국), model_name(모델 명) 순으로 나열

2. 데이터프레임 내용 확인

- 앞부분 미리보기 : DataFrame 객체.head(n)
- 뒷부분 미리보기 : DataFrame 객체.tail(n)

```python
import pandas as pd

# read_csv() 함수로 df 생성
# 열을 따로 지정해주지 않기 위해 header=None 옵션 사용
df = pd.read_csv('./auto-mpg.csv', header=None)

# print(df)

# 열이름 지정
df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight', 
              'acceleration', 'model year', 'origin', 'name']
```

```python
# 처음 5개 행 출력
print(df.head())
# 마지막 5개 행 출력
print(df.tail())
```

3. 데이터 요약 정보 확인하기

- 데이터 프레임 크기(행,열)
  - 데이터프레임의 shape 속성은 행과 열의 개수를 튜플 형태로 출력
  - 데이터프레임의 크기 확인 : DataFrame 객체.shape

```python
# df의 모양과 크기 확인: (행의 개수, 열의 개수)를 튜플로 반환
print(df.shape)
```

4. 데이터 프레임 기본 정보

- Info() 함수를 데이터 프레임에 적용하면 데이터 프레임에 관한 기본 정보를 화면에 출력

  - 클래스 유형, 행 인덱스 구성, 열 이름의 종류와 개수, 각 열의 자료형과 개수, 메모리 할당량 등 정보 포함

- 데이터 프레임 기본 정보 출력:` dataframe object.info()`

  ```python
  # 데이터프레임의 기본 정보 확인
  print(df.info())
  ```

- 판다스 자료형

  - Int64: 정수형 데이터
  - Float64: 실수형 데이터
  - Object: 문자열 데이터
  - datetime64, timedelta64: 시간 데이터

- dtypes 속성에는 각 열의 자료형 개수 포함

  ```python
  # 데이터프레임 df의 자료형 확인
  print(df.dtypes)
  # 데이터프레임의 특정 열(mpg)의 자료형 확인
  print(df.mpg.dtypes)
  ```

5. 데이터 프레임 기술 통계 정보 요약

- 데이터 프레임에 `describe()` 함수 적용시, 숫자 데이터를 갖는 열에 대한 주요 기술 통계 정보(평균, 표준편차, 최대값, 중간값 등) 요약해 출력

  ```python
  # 데이터프레임 df의 기술 통계 정보 확인
  print(df.describe())
  # 데이터프레임 df의 기술 통계 정보 확인
  print(df.describe(include='all'))
  ```

- 기본 describe() 함수 사용시 데이터 수(count), 평균(mean), 표준편차(std), 분위수(25%,50%,75%), 최대최소값(max, min) 출력

- include='all' 옵션 사용시 고유값 개수(unique), 최빈값(top), 빈도수(freq) 추가로 출력

6. 통계 함수 적용

- 평균값

  - 데이터프레임에 mean() 함수를 사용하면, 산술 데이터를 갖는 모든 열의 평균값을 계산하여 시리즈 객체로 반환

  - 전체 평균값을 확인 가능, 특정 열의 평균값도 확인 가능

    ```python
    #모든 열의 평균값
    dataframe 객체.mean()
    #특정 열의 평균값
    dataframe 객체["열 이름"].mean()
    -
    # 열 전체 평균값
    print(df.mean())
    # 특정 열 평균값
    print(df['mpg'].mean())
    # 특정 열 두 개 평균값
    print(df[['mpg', 'weight']].mean())
    ```

  

- 중간값

  - 데이터 프레임에 `median()` 함수를 사용하면 산술 데이터를 갖는 모든 열의 중간값을 계산해 시리즈로 반환

    ```python
    #모든 열의 중간값
    DataFrame 객체.median()
    #특정 열의 중간값
    DataFrame 객체["열 이름"].median()
    -
    #모든 열의 중간값
    print(df.median())
    #mpg 열의 중간값
    print(df['mpg'].median())
    ```

    ```python
    #짝수개 데이터 중간값
    import pandas as pd
    
    df = pd.DataFrame({'X' : [1, 2, 4, 7, 10, 13],
                       'Y' : [3, 5, 9, 11, 12, 15]})
    
    medians = df.median()
    print(medians)
    
    데이터의 개수가 짝수일 경우 중간값(2개) 사이의 값을 출력해줌
    ```

- 최대값

  - 데이터프레임에 max() 함수를 사용하면 산술 데이터를 갖는 모든 열의 최대값을 계산하여 시리즈로 반환

  - 데이터프레임의 모든 열의 최대값 계산 가능, 특정 열의 최대값 계산 가능

    ```python
    #모든 열의 최대값
    DataFrame 객체.max()
    #특정 열의 최대값
    DataFrame 객체["열 이름"].max()
    ```

```python
print(df.max())
print(df['mpg'].max())
```

- 최소값

  - 데이터프레임에 min() 함수를 사용하면 산술 데이터를 갖는 모든 열의 최소값을 계산하여 시리즈로 반환

  - 데이터프레임의 모든 열의 최소값 계산 가능, 특정 열의 최소값 계산 가능

    ```python
    #모든 열의 최소값
    DataFrame 객체.min()
    #특정 열의 최소값
    DataFrame 객체["열 이름"].min()
    -
    #df 데이터 프레임 모든 열의 최소값
    print(df.min())
    #mpg 열의 최소값
    print(df['mpg'].min())
    ```

- 표준편차

  - 데이터프레임에 std() 함수를 사용하면 산술 데이터가 있는 열의 표준 편차를 계산하여 시리즈로 반환

  - 편차 : 기본 데이터가 평균으로부터 얼마나 떨어져 있는지를 알 수 있는 척도

    ```python
    #모든 열의 표준편차
    DataFrame 객체.std()
    #특정 열의 표준편차
    DataFrame 객체["열 이름"].std()
    -
    #df 데이터 프레임 모든 열의 표준편차
    print(df.std())
    #mpg 열의 표준편자
    print(df['mpg'].std())
    ```

- 상관계수

  - 데이터프레임에 corr() 함수를 사용하면 두 열 간의 상관계수를 계산
  - 산술 데이터를 갖는 모든 열에 대해서 2개씩 서로 짝을 짓고, 각각의 경우에 대하여 상관계수를 계산
  - 상관계수 절대값의 크기는 직선관계와 가까운 정도를 표현, 부호는 직선관계의 방향을 나타냄
    - r > 0 : 양의 상관관계, 산점도에서 점들이 우상향방향으로 띠를 형성(기울기 양수)
    - r < 0 : 음의 상관관계, 산점도에서 점들이 우하향방향으로 띠를 형성(기울기 음수)
    - r = +1 : 모든 점이 정확히 기울기가 양수인 직선 위에 위치
    - r = -1 : 모든 점이 정확히 기울기가 음수인 직선 위에 위치

  ```python
  #모든 열의 상관계수
  DataFrame 객체.corr()
  #특정 열의 상관계수
  DataFrame 객체[열 이름 리스트].corr()
  -
  #df 데이터 프레임 모든 열의 상관계수
  print(df.corr())
  #mpg열과 weight 열의 상관계수
  print(df[['mpg', 'weight']].corr())
  ```



7. 판다스 내장 그래프 도구 활용

- 판다스 내장 그래프 도구 활용

  - 데이터를 그래프로 표현하는 것은 매우 효과적인 정보 전달 방식

  - 시리즈 또는 데이터프레임 객체에 plot() 함수를 적용하여 그래프를 생성

  - kind 옵션으로 그래프의 종류 선택

  - "line" : 선 그래프

    - 데이터프레임(또는 시리즈) 객체에 plot() 함수를 사용할 경우, 다른 옵션을 추가하지 않으면 가장 기본적인 선 그래프를 그림
      `선 그래프 : DataFrame 객체.plot()`

      ```python
      import pandas as pd
      
      df = pd.read_excel('./남북한발전전력량.xlsx', engine='openpyxl')
      
      # 남북한 발전량 합계 데이터를 추출
      df_ns = df.iloc[[0, 5], 2:]
      
      # 행 인덱스 변경
      df_ns.index = ['South', 'North']
      
      # 열 이름의 자료형을 정수형으로 변경
      df_ns.columns = df_ns.columns.map(int)
      
      # 추출 데이터 확인
      print(df_ns)
      
      # 선 그래프 그리기
      print(df_ns.plot())
      
      # 행, 열 전치하여 다시 그리기
      tdf_ns = df_ns.T
      print(tdf_ns.head())
      
      print(tdf_ns.plot())
      ```

      

  - "bar" : 수직 막대 그래프

    - lot() 함수로 선 그래프가 아닌 다른 종류의 그래프를 그리려면 kind 옵션에 그래프 종류를 지정
      kind="bar"
      `막대 그래프 : DataFrame 객체.plot(kind="bar")`

  - "bath" : 수평 막대 그래프

  - "hist" : 히스토그램

    - 빈도와 관련

    - plot() 함수에 kind="hist" 옵션 추가
      `히스토그램 : DataFrame 객체.plot(kind="hist")`

      ```python
      import pandas as pd
      
      df = pd.read_excel('./남북한발전전력량.xlsx', engine='openpyxl')
      
      # 남북한 발전량 합계 데이터를 추출
      df_ns = df.iloc[[0, 5], 2:]
      
      # 행 인덱스 변경
      df_ns.index = ['South', 'North']
      
      # 열 이름의 자료형을 정수형으로 변경
      df_ns.columns = df_ns.columns.map(int)
      
      # 행, 열 전치하여 다시 그리기
      tdf_ns = df_ns.T
      print(tdf_ns.head())
      -
      print(tdf_ns.plot(kind="hist"))
      ```

      

  - "box" : 박스 플롯

    - 특정 변수의 데이터 분포와 분산 정도에 대한 정보를 제공
      - 변수들의 데이터가 퍼져 있는 정도를 확인할 때 사용
    - plot() 함수에 kind="box" 옵션을 입력

    ```python
    #예제
    import pandas as pd
    
    # read_csv() 함수로 df 생성
    # 열을 따로 지정해주지 않기 위해 header=None 옵션 사용
    df = pd.read_csv('./auto-mpg.csv', header=None)
    
    # print(df)
    
    # 열이름 지정
    df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight', 
                  'acceleration', 'model year', 'origin', 'name']
    -
    # 열을 선택하여 박스 플롯 그리기
    print(df[['mpg', 'cylinders']].plot(kind='box'))

  - "kde" : 커널 밀도 그래프

  - "area" : 면적 그래프

  - "pie" : 파이 그래프

  - "scatter" : 산점도

    - 두 변수의 관계를 점으로 나타내는 그래프

      ```python
      #예제
      import pandas as pd
      
      # read_csv() 함수로 df 생성
      # 열을 따로 지정해주지 않기 위해 header=None 옵션 사용
      df = pd.read_csv('./auto-mpg.csv', header=None)
      
      # print(df)
      
      # 열이름 지정
      df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight', 
                    'acceleration', 'model year', 'origin', 'name']
      -
      # 2개의 열을 선택하여 산점도 그리기
      df.plot(x = 'weight', y = 'mpg', kind='scatter')
      ```

      

  - "hexbin" : 고밀도 산점도



# matplotlib(기본 그래프 도구)

- 시각화 도구를 사용하면 다양한 종류의 데이터 분석 가능
  - 데이터에는 수천, 수만 개를 넘기는 경우가 많음
- 그래프를 이용하면 데이터의 구조와 패턴을 파악하기가 용이
- 다양한 관점에서 데이터에 관한 통찰력 제공
- 판다스는 데이터 시각화를 지원하는 내장 기능이 존재하지만 풍부하진 않음
  - 다른 시각화 도구와 함게 사용하는 것을 추천

---

## matplotlib

- 2D 평면 그래프에 관한 다양한 포맷과 기능 지원
- 그래프 요소 꾸미기 가능

1. 선 그래프

- 선 그래프(line plot)는 연속하는 데이터 값들을 직선 또는 곡선으로 연결하여 데이터 값 사이의 관계를 표현
- 시계열 데이터와 같이 연속적인 값의 변화와 패턴을 파악하는데 적합

```python
1.
import pandas as pd

# 데이터 시각화에 사용할 matplotlib.pyplot 모듈을 import
import matplotlib.pyplot as plt

# Excel 데이터를 데이터프레임 변환
# 첫 열을 헤더로 사용
df = pd.read_excel("./시도별 전출입 인구수.xlsx", engine = "openpyxl", header = 0)
df.head()

''''
전출지별' 열에는 누락 데이터(NaN) 다수 존재
Excel 파일에서 병합된 셀을 데이터프레임으로 변환할 때 적절한 값을 찾지 못해 발생
method='ffill' 옵션을 사용하여 누락 데이터가 있는 행의 바로 앞에 위치한 데이터 값으로 채움
3행의 NaN 값을 2행의 데이터('전국')로 대체 가능

서울 -> 다른 지역 조건
method='ffill'
서울에서 다른 지역으로 이동한 데이터만 추출(A 열은 서울, B 열은 서울 X)
전출지별 열 제거
전입지별 -> 전입지
전입지를 행 인덱스로 지정'''

#데이터 추출 선 그래프 예제
import pandas as pd

# 데이터 시각화에 사용할 matplotlib.pyplot 모듈을 import
import matplotlib.pyplot as plt

# Excel 데이터를 데이터프레임 변환
# 첫 열을 헤더로 사용
df = pd.read_excel("./시도별 전출입 인구수.xlsx", engine = "openpyxl", header = 0)

# 누락값(NaN)을 앞 데이터로 채움(엑셀 양식 병합)
df = df.fillna(method='ffill')

# 서울에서 다른 지역으로 이동한 데이터만 추출
mask = (df['전출지별'] == '서울특별시') & (df['전입지별'] != '서울특별시')
df_seoul = df[mask]
df_seoul = df_seoul.drop(['전출지별'], axis=1)
df_seoul.rename({'전입지별':'전입지'}, axis=1, inplace=True)
df_seoul.set_index('전입지', inplace=True)

# 서울에서 경기도로 이동한 인구 데이터 값만 선택
dt_g = df_seoul.loc['경기도']

# x, y축 데이터를 plot() 함수에 직접 입력
print(plt.plot(dt_g.index, dt_g.values))

# 차트 제목 추가
plt.title('서울 -> 경기 인구 이동')

# 축이름 추가
plt.xlabel('기간')
plt.ylabel('이동 인구수')

# 차트를 시각화
plt.show()

or

# 판다스 객체를 plot() 함수에 입력
print(plt.plot(dt_g))
```

- 한글 폰트 지정 방법

  ```python
  import matplotlib 이후
  
  from matplotlib import rc
  rc('font', family='AppleGothic')
  ```

  

2. 그래프 꾸미기

   - x축 눈금 라벨의 글씨가 서로 겹쳐 잘 보이지 않는 문제를 해결
     - 눈금 라벨이 들어갈 만한 충분한 여유 공간이 없기 때문에 발생하는 문제

   - 해결방법:
     1. 공간을 만들기 위해 figure() 함수를 사용하여 그림틀의 가로 사이즈를 더 크게 설정
     2. xticks() 함수를 사용하여 x축 눈금 라벨을 반시계 방향으로 90도 회전하여 글씨가 겹치지 않게 하기

3. Matplotlib의 스타일 서식 지정

   - 색, 스타일 등 디자인적 요소를 사전에 지정된 스타일로 빠르게 변경 가능

     - 스타일 서식을 지정하는 것은 Matplotlib 실행 환경 설정을 변경하는 것이므로 다른 파일을 실행할 때도 계속 적용되는 점 유의

     - 예제에서는 'ggplot'이라는 스타일 서식 지정

     - x축 눈금 라벨을 지정하는 xticks() 함수에 size=10 옵션을 추가하여 폰트 크기를 10으로 설정

     - plot() 함수에 marker='o' 옵션을 추가하면 원 모양의 점을 마커로 표시

4. **Matplotlib 스타일 서식 종류**
   - default, classic, bmh, dark_background, fast, grayscale, seaborn 등