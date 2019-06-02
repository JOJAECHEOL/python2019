# A형 간염

학과 | 학번 | 성명
---- | ---- | ---- 
분자생물학과 |201413551 |조재철


## 프로젝트 개요
A형 간염 발생자 수 데이터 분석을 통해 연령대에 따라 차이가 많이 남을 알 수 있고 그 원인을 파악해 본다. 

## 사용한 공공데이터 
[데이터보기](http://www.cdc.go.kr/npt/biz/npp/ist/bass/bassDissStatsMain.do)

## 소스
* [링크로 소스 내용 보기](https://github.com/JOJAECHEOL/python2019/blob/master/module1.py) 

* 코드 삽입
~~~python
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib import font_manager, rc
font_name = font_manager.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()
rc('font', family=font_name)

df1=pd.read_csv('yearmonth.csv')

year=int(input("연도를 입력해 주세요.(2011~2019)"))

dfx=df1.loc[df1['연도']==year]
print(dfx)

df2=pd.read_csv('old.csv')

old=int(input("연령대를 입력해주세요 (70은 70대 이상)"))

dfy=df2.loc[df2['연령대']==old]
print(dfy)

#올해 A형 작년과 비교
x=["2018","2019(5월 17일 까지)"]
y=[2437,5460]
plt.bar(x,y,color='r')
plt.xlabel("연도")
plt.ylabel("발생수")
plt.title("작년과 올해 A형간염 발생자 수 비교")
plt.show()

#올해 급증하게 된 원인은 지역별로 보면 경기권에 몰려있음에 의심
#인구수 차이를 생각해 인구 10만명당 발생률 통계 사용

x=['전국','서울','부산','대구','인천','광주','대전','울산','경기','강원','충북','충남','전북','전남','경북','경남','제주','세종']
y=[10.54, 9.86, 3.33, 1.94, 11.15, 2.81, 57.82, 1.64, 12.8, 5.82, 23.3, 21.02, 7.15, 2.96, 3.2, 2.34, 2.87, 45.44]

plt.bar(x,y,color='r')
plt.xlabel("지역")
plt.ylabel("10만명당 발생률")
plt.title("올해 지역별 A형 간염 10만명당 발생률")
plt.show()


#연령별 A형 간염 발생자 그래프를 보여줄것임 (연도별에 따른 상관관계 찾기 어려워서 주제 바꿈)

x=[1,10,20,30,40,50,60,70]
y=[151,1065,5805,11137,6884,1571,441,455]

plt.plot(x,y,color='r')
plt.xlabel("연령대")
plt.ylabel("발생자 수")
plt.title("연령대별 A형 간염 발생자 수")
plt.show()

#왜 이럴까 연령대별 a형 간염 항체 보유율을 알아보았다
#참고자료 http://news.chosun.com/site/data/html_dir/2017/12/14/2017121400324.html (서울대병원 임주원, 박상민 교수팀)
x=['10~14', '15~19', '20~29', '30~44', '45~']
y=[59.7, 24.0, 11.9, 46.6, 97.8]
plt.plot(x,y,color='r')
plt.xlabel("연령대")
plt.ylabel("항체 보유율")
plt.title("연령대별 A형 간염 항체 보유율")
plt.show()

#연령대별 발생자수 그래프와 연령대별 항체보유율 그래프를 겹쳐서 보여줌으로 둘간의 상관과계를 보여줌 (x축 값 기준이 달라도 그래프 변화를 보고 시각적으로 판단 가능)




#항체 보유율 차이는 아래를 통해 보여주면 된다





'''
A형 간염 예방접종은 1997년 신생아 대상으로 선택 접종 백신으로 쓰였고 2015년부터 영유야 대상 무려 접종.
현재 22세 이하에서 A형 간염 발생률이 낮은 이유(20대와 30대 큰차이 안나는 이유도 22세 이하부터 이므로)
50대 이상은 과거 위생 상태가 나쁜 어린시절을 보냈기에 A형 간염을 가볍게 앓고 지나가면서 항체가 생성된 이유

30, 40대는 어린시절 위생상태가 많이 괜찮아 졌고 예방접종 선택 및 무료 백신 대상자인 경우가 아니기 때문에 이 같이
많이 발생 했음을 예측 가능
'''
~~~
