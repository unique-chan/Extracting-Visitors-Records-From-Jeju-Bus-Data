# Extracting Visitors Records From Jeju Bus Smart Card Data
암호화된 대중교통 교통카드 빅데이터에서의 관광객 O-D 통행패턴 추출 알고리즘: 관광도시, 제주에의 적용 (김예찬)

## Prerequisites
- Python 3.7.4
- Pandas 0.25.1

## Cautions
- 이 알고리즘은 제주 빅데이터 센터에서 제공하는 제주 대중교통 버스 이용 (교통카드) 데이터에 최적화되어 있습니다.
- 만약 제주 빅데이터 센터에서 제공하는 데이터의 스키마가 변경될 경우, # 컬럼 상수 하단의 코드를 수정하면 됩니다.
- 예로, 'user_id'라는 필드가 'bus_user_id'로 변경된 경우, 
~~~
user_id = 'bus_user_id'
~~~

## How to use
- 임의로 디렉토리를 생성한 뒤, 다음과 같이 제주 대중교통 버스 이용 (교통카드) 데이터를 배치합니다. 파일 이름은 임의로 두어도 됩니다. 다만, 하단과 같이 파일에 이름을 부여하면 더 직관적일 것입니다.
~~~
tb_bus_user_usage_190601.csv
tb_bus_user_usage_190602.csv
tb_bus_user_usage_190603.csv
... 중략 ...
~~~
- path 변수에 디렉토리의 주소를 삽입합니다.
~~~
# 예로, d 드라이브 밑 tb_bus_user_usage 디렉토리에 분석할 데이터 파일을 저장한 경우,
### (1) 이하 전처리
path = 'd:/tb_bus_user_usage'
~~~
- 알고리즘의 세부적인 사항을 필요하면 수정합니다.
~~~
# 예로, 연속으로 15일 미만이 아니라, 10일 미만인 버스 이용자를 필터링하고자 할 경우,
### (2) 이하 추출 ①
... 중략 ...
U = list(date_cnt[date_cnt[base_date] 10][user_id].unique())
... 중략 ...
### (3) 이하 추출 ②
... 중략 ...
U2 = list(M2_2[M2_2['diff'] '11 days'][user_id].unique()) 
... 중략 ...
~~~
- 알고리즘을 실행합니다. 관광객으로 추정된 버스 이용자의 USER_ID를 추출합니다.

## Acknowledgement
- 데이터 제공 및 알고리즘 배포를 허용한 제주 테크노 파크-제주특별자치도 빅데이터 센터(약칭 'JTP-제주 빅데이터 센터')에 감사의 말씀을 전합니다.
