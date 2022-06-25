# 유통회사 매출감소고객 개인 맞춤형 솔루션

<img src = "https://user-images.githubusercontent.com/96767467/168734801-7cb69337-6700-450d-99d1-32fe266854e9.png" align = 'center' width = "95%" >

### 들어가기 전에
- 발표영상: https://www.youtube.com/watch?v=WBpVgxsxNrA
- 유통회사 L사의 구매 데이터를 분석하여 유의미한 솔루션을 도출하는 프로젝트입니다.
- 원본 데이터는 보얀 규약상 보여드릴 수 없고, 이에 따라 데이터 가공 과정 역시 구두설명만 드리게 되었습니다. 이 점 양해 부탁드립니다.
- 자세한 내용은 소스코드 혹은 ppt를 참고해 주시기 바랍니다.
   
---

## 1. 기획

### 주제 선정 배경
<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/175243201-38864733-2e23-47eb-b69a-e87f39194fe1.png" align = 'left' width = "48%" height = "300">
<img src = "https://user-images.githubusercontent.com/96767467/175243564-9310d463-af06-4ea5-8289-ba92f6fdf674.png" align = 'right' width = "48%" height = "300">
</p>
</br>
</br>
</br>


<p> 
최근 유통회사들은 경쟁에서 도태되지 않기 위해 고객 맞춤형 서비스의 필요성이 대두되고 있습니다.
특히, L사는 4분기 매출이 다른 분기에 더 취약한 부분이 있었습니다.
<p>
   
### 유의고객 정의

<img src = "https://user-images.githubusercontent.com/96767467/175244717-bf7f050c-a63d-4439-9f4b-3b0f06d48c6f.png" align = 'left' width = "450" height = "300">   <img src = "https://user-images.githubusercontent.com/96767467/175245222-fb261ddb-088a-4ac0-bfcd-631616ff25c8.png" align = 'right' width = "450" height = "300">

<div>
2년간 구매 이력이 있는 지속고객들 중에서 솔루션 대상을 정의합니다.  
전년도 대비 4분기 매출이 감소한 고객을 유의고객이라고 정의합니다.  
이 고객들은 다른 분기에서도 많은 구매 감소를 보이고 있었고, 이 감소금액은 회사에 타격을 줄 만큼 큰 금액입니다.
</div>


    
## 2. 모델링

### 시스템 요약도

<img src = "https://user-images.githubusercontent.com/96767467/175251069-166e03e6-91cf-4766-82ee-c5c8e105e20d.png" align = 'center' width = "95%" height = "600">

### 변수 개발

<img src = "https://user-images.githubusercontent.com/96767467/175251614-564230f4-f2c4-4a24-a3c0-f4984e43cc26.png" width = "450" height = "300">   <img src = "https://user-images.githubusercontent.com/96767467/175251678-1b1fa22d-4beb-4025-9a4e-37f3b83ba8e9.png" width = "450" height = "300">

제휴사별 카테고리를 통합 카테고리로 재분류하고, 변수를 개발합니다.  
변수는 다중공선성 문제가 없도록 상관도를 고려하여 재선정하고, 오른쪽 사진과 같이 구성되었습니다.

### 모델 선정

<img src = "https://user-images.githubusercontent.com/96767467/175253738-61d12605-e7f5-491e-a692-d41f083f91cf.png" width = "450" height = "300">   <img src = "https://user-images.githubusercontent.com/96767467/175253773-0c1557e9-b174-4f74-b0a7-a2c51eed4a1e.png" width = "450" height = "300">

유의 고객을 예측하는 분류 모델을 선정하기 위해 평가지표들을 확인합니다.  
2년 중 7분기분을 train 데이터와 validation 데이터로 나누어 모델을 구성하였고, 8분기를 test 데이터로 활용하였습니다.
오른쪽 사진 내용과 같이 XGBoost를 선택하였습니다.

## 3. 결과 해석 및 인사이트 도출

![image](https://user-images.githubusercontent.com/96767467/175255644-5c000aba-0193-40a1-a7b1-246cebc00fb3.png)

# 추가 수정 예정입니다! 6/23

- 해당 고객들을 군집화하여 군집별 특성 파악
- 군집별 솔루션에 개인 맞춤형 솔루션을 더해 유의미한 솔루션 도출
