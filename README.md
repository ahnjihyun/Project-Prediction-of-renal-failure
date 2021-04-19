# Project-Prediction-of-renal-failure-(신부전증 예측)
<br><br>

- 데이터 선정 배경
> 신장질환 환자 증가율이 세계4위 (현재 국내 만성신부전증 환자수는 약 10만명)
> 
> 신부전증은 초기 발견이 어려울뿐만 아니라 증상이 심할 경우 지속적인 투석 혹은 장기 이식을 해야함.
> 
> 이것은 환자의 건강에도 치명적이고, 치료할 시 의료비용이 상당히 많이 들어 부담이 됨
> 
> 만성 신장질환의 조기발견 및 관리의 중요성이 점점 더 커지고 있음
<br><br>

- 데이터 분석 목표
> 많은 기관들이 혈청 크레아티닌 (Scr)을 신기능 저하의 선별검사로 사용하고 있음
> 
> 이를 신장기능의 지표중 하나인 "혈청 크레아티닌" 수치로 신부전증을 예측하고자 함
> 
> 가설 : "시력/혈압/혈당/간기능/흡연유무가 신장기능에 Negative한 영향을 미칠것이다"
<br><br>

- 설명 <br>
[데이터 수집 - EDA - 전처리 - 모델 파이프라인 구축 - 최적 파라미터 찾기 - 학습 - 테스트] 과정으로 진행되었습니다 <br>
> ['성별', '나이', '키', '체중', '허리둘레', '시력L', '시력R', '청력L', '청력R', '수축기혈압',
>
> '이완기혈압', '공복혈당', '혈색소', '요단백', 'AST', 'ALT', '감마GTP', '흡연상태', '음주여부',
>
> 'cr'] 
<br>
randomforest classifier 모델에 위의 21가지 특징을 학습시켜 신장기능에 이상이 있는지/없는지를 예측하고, <br>
어떤 요소가 신장 기능에 가장 큰 영향을 주는지 상관분석을 시행했습니다. <br>
그 결과 다음의 7가지 요소가 차례대로 신장기능에 영향을 미친것으로 확인했습니다. <br>

> 공복혈당, 요단백, 이완기혈압, 감마GTP, AST, 혈색소, 음주여부

<br><br><br>


### * 아이디어를 확장하여 <br>
1. MDRD공식을 사용해 mdrd()함수에 입력으로 [나이, 체중, 혈청크레아티닌, 성별] 4가지 파라미터를 넣으면 사구체 여과율을 계산해줍니다 <br>
2. 사구체 여과율에 따라서 만성신부전증 1~5단계로 나뉘는데, recc()함수가 이를 계산하여 위험 수준을 알려줍니다 <br>
(2단계부터는 조기 검사와 관리가 필요한 수준) <br>
