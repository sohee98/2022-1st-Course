## Lab 01 - Data Visualization

* `loc, iloc` - 행 데이터 가져오기

  * `loc` : 인덱스를 통해 행 데이터를 가져옴 (인덱스는 사용자가 지정하는거)

    ```python
    df.loc[0]
    df.loc[1,3,5]
    df.loc[:,['year','continent']]	# 모든 행에 대해 지정한 열 데이터만 가져옴
    df.loc[[1,4], ['year','pop']]	# 1,4행의 year,pop열만
    ```

  * `iloc` : 행 번호를 통해 행데이터를 가져옴 (0부터 순서대로 정해짐)

    ```python
    df.iloc[0]
    df.iloc[-1] # 마지막 행
    df.iloc[:,:3] # 모든 행에 대해 3번열 데이터 전까지
    df.iloc[[1,4],[2,4]]
    ```

    > 행과 열 인덱스에 정수 리스트를 넣어야함 (열 이름 넣으면 에러)

  * `:` - 모든 데이터를 가져옴



### Plotly

```python
import plotly.graph_objs as go

trace1 = go.Scatter(
                    x = df.world_rank,
                    y = df.citations,
                    mode = "lines",		# "lines+markers", "markers"
                    name = "citations",
                    marker = dict(color = 'rgba(16, 112, 2, 0.8)'), # RGB (red, green, blue) and opacity (alpha)
                    text= df.university_name) # hover text  

data = [trace1, trace2, trace3]

layout = dict(title = 'Citation, Teaching, Research vs World Rank of Top 100 Universities',
              xaxis= dict(title= 'World Rank',ticklen= 5,zeroline= False)
             )

fig = go.Figure(data = data, layout = layout)
fig.show() 
```

* `ticklen` : 눈금 길이 (Default=5)

* colorscale

  * ```
    ['aggrnyl', 'agsunset', 'algae', 'amp', 'armyrose', 'balance',
    'blackbody', 'bluered', 'blues', 'blugrn', 'bluyl', 'brbg',
    'brwnyl', 'bugn', 'bupu', 'burg', 'burgyl', 'cividis', 'curl',
    'darkmint', 'deep', 'delta', 'dense', 'earth', 'edge', 'electric',
    'emrld', 'fall', 'geyser', 'gnbu', 'gray', 'greens', 'greys',
    'haline', 'hot', 'hsv', 'ice', 'icefire', 'inferno', 'jet',
    'magenta', 'magma', 'matter', 'mint', 'mrybm', 'mygbm', 'oranges',
    'orrd', 'oryel', 'peach', 'phase', 'picnic', 'pinkyl', 'piyg',
    'plasma', 'plotly3', 'portland', 'prgn', 'pubu', 'pubugn', 'puor',
    'purd', 'purp', 'purples', 'purpor', 'rainbow', 'rdbu', 'rdgy',
    'rdpu', 'rdylbu', 'rdylgn', 'redor', 'reds', 'solar', 'spectral',
    'speed', 'sunset', 'sunsetdark', 'teal', 'tealgrn', 'tealrose',
    'tempo', 'temps', 'thermal', 'tropic', 'turbid', 'twilight',
    'viridis', 'ylgn', 'ylgnbu', 'ylorbr', 'ylorrd'].
    ```



#### 카테고리 자료형

```python
index_vals = df['class'].astype('category').cat.codes
```

* `astype('category')` : 컬럼을 카테고리형 시리즈로 제작

  * Categorical 인스턴스 : categories와 code 속성을 가짐 (cat 속성 이용)

    ```python
    cat_s.cat.categories  	# Index(['a','b'], dtype='object')
    cat_s.cat.codes			# 0 0 .. 표 형태로 나타남 dtype:int8
    ```

  * | **메서드**               | **설명**                                                     |
    | ------------------------ | ------------------------------------------------------------ |
    | add_categories           | 기존 카테고리 끝에 새로운 카테고리 추가                      |
    | as_ordered               | 카테고리가 순서를 가지도록 함                                |
    | as_unordered             | 카테고리가 순서를 가지지 않도록 함                           |
    | remove_categories        | 카테고리를 제거,  해당 카테고리에 속한 값들은 null로 설정됨  |
    | remove_unused_categories | 데이터에서 관측되지 않는 카테고리 삭제                       |
    | rename_categories        | 카테고리 이름을 지정한 이름으로 변경                         |
    | reorder_categories       | rename_categories와 유사하나,  새로운 카테고리가 순서를 가짐 |
    | set_categories           | 카테고리를 지정한 새로운 카테고리로 변경  카테고리 추가 혹은 삭제 가능 |



### Datetime

`pd.to_datetime()`

