## Lab 01 - Dataset Exploration

* 데이터 합치기

  ```python
  pd.concat([left, right],  # Series, DataFrame, Panel object
            axis=0,  # 0: 위+아래로 합치기, 1: 왼쪽+오른쪽으로 합치기
            join='outer', # 'outer': 합집합(union), 'inner': 교집합(intersection)
            ignore_index=False,  # False: 기존 index 유지, True: 기존 index 무시
            keys=None, # 계층적 index 사용하려면 keys 튜플 입력
            levels=None,
            names=None, # index의 이름 부여하려면 names 튜플 입력
            verify_integrity=False, # True: index 중복 확인
            sort=Flase, # 정렬
            copy=True) # 복사
  ```

* Window

  ```
  DataFrame.resample(rule,
                     axis=0,
                     closed=None,
                     label=None,
                     convention='start',
                     kind=None,
                     loffset=None,
                     base=None,
                     on=None,
                     level=None,
                     origin='start_day',
                     offset=None)
  ```

  

