# 유통회사 매출감소고객 개인 맞춤형 솔루션

<img src = "https://user-images.githubusercontent.com/96767467/197762710-edc55929-e046-4a71-a063-92043890846f.png" align = 'center' width = "95%" >

### 들어가기 전에
- 발표영상: https://www.youtube.com/watch?v=WBpVgxsxNrA
- 유통회사 L사의 구매 데이터를 분석하여 유의미한 솔루션을 도출하는 프로젝트입니다.  
- 원본 데이터는 보얀 규약상 보여드릴 수 없고, 이에 따라 데이터 가공 과정 역시 구두설명만 드리게 되었습니다. 이 점 양해 부탁드립니다.  
- 자세한 내용은 소스코드 혹은 ppt를 참고해 주시기 바라며 모바일은 최적화가 되어 있지 않습니다.  
</br>

### 목차

[1. 기획 및 타겟 정의](#1-기획)</br>
[2. 모델링](#2-모델링)</br>
[3. 군집화 및 인사이트 도출](#3-군집화-및-인사이트-도출)</br>
[4. 팀원소개](#팀원-소개)</br>
</br>

---

## 1. 기획

### 1-1 주제 선정 배경
<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/197762716-16793737-9039-437e-9649-a8f2a73a5c8e.PNG" width = "48%" height = "27%">
<img src = "https://user-images.githubusercontent.com/96767467/197762719-ca196a56-7973-4546-bd9d-577b6146546b.PNG" width = "48%" height = "27%">
</p>
<p> 
최근 유통회사들은 경쟁에서 도태되지 않기 위해 고객 맞춤형 서비스의 필요성이 대두되고 있습니다.  
특히, L사는 4분기 매출이 다른 분기에 더 취약한 부분이 있었습니다.  
<p>
</br>

### 1-2 유의고객 정의

<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/197762720-a77bcef3-8858-474b-99c1-6a315c5dc3ca.PNG" width = "48%" height = "27%">
<img src = "https://user-images.githubusercontent.com/96767467/197762721-2290ded8-9d75-4701-a15c-cacadd49a1e1.PNG" width = "48%" height = "27%">
</p>
<p>
2년간 구매 이력이 있는 지속고객들 중에서 솔루션 대상을 정의합니다.  
전년도 대비 4분기 매출이 감소한 약 2만명의 고객을 유의고객이라고 정의합니다.  
이 고객들은 다른 분기에서도 많은 구매 감소를 보이고 있었고, 이 감소금액은 회사에 타격을 줄 만큼 큰 금액입니다.
</p>
</br>
</br>
    
## 2. 모델링

### 2-1 시스템 요약도

<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/197762723-d3b056bb-65c4-4991-9166-1f8eee74ae2d.PNG" align = 'center' width = "95%" height = "53%">
</p>
</br>

### 2-2 변수 개발

<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/197762725-cbf658af-b1fe-404d-8c42-795ed9cb2863.PNG" width = "48%" height = "27%">
<img src = "https://user-images.githubusercontent.com/96767467/197762728-cc0e9612-80b4-4413-ac87-00e5ef190e7f.PNG" width = "48%" height = "27%">
</p>
<p>
제휴사별 카테고리를 통합 카테고리로 재분류하고, 변수를 개발합니다.  
변수는 다중공선성 문제가 없도록 상관도를 고려하여 재선정하고, 오른쪽 사진과 같이 구성되었습니다.  
</p>
</br>
   
### 2-3 모델 선정

<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/197762730-5b2f97d9-9243-492b-9730-586b55e8340d.PNG" width = "48%" height = "27%">
<img src = "https://user-images.githubusercontent.com/96767467/197762733-cc750988-9572-4bd1-8372-1d7c444ddb32.PNG" width = "48%" height = "27%">
</p>
<p>
유의 고객을 예측하는 분류 모델을 선정하기 위해 평가지표들을 확인합니다.</br>
2년 중 7분기분을 train 데이터와 validation 데이터로 나누어 모델을 구성하였고, 8분기를 test 데이터로 활용하였습니다.</br>
오른쪽 사진 내용과 같이 XGBoost를 선택하였습니다.</br>
</p>

</br>
</br>
   
## 3. 군집화 및 인사이트 도출

### 3-1 군집 개수 선정

<img src = "https://user-images.githubusercontent.com/96767467/197762734-2d9f0dc3-d97c-471f-b6c0-de7aa2571fa5.PNG" align = 'center' width = "95%" height = "53%">
</br>

<p>
이제 유의고객이 될 고객을 예측하고, 해당 고객들을 군집분석하여 군집별 솔루션을 제시합니다.</br>
군집화 알고리즘은 K-평균 알고리즘을 사용하였으며, 실루엣 계수를 확인하고 군집 수는 3개로 결정합니다.</br>
</p>
</br>

### 3-2 군집별 솔루션

<p align = 'left'>
<img src = "https://user-images.githubusercontent.com/96767467/197762736-4b339bd2-7a78-4e1b-b4c4-01c28bb14c9b.PNG" width = "70%" height = '39%'>
</p>

"잠재적 충성 고객층"</br>  
- 단계별 마케팅</br>
- 평소 선호 제품군 추천</br> 
- 소속감을 부여하는 서비스</br>
</br>

<p align = 'left'>
<img src = "https://user-images.githubusercontent.com/96767467/197762739-cf2ecc0e-6d3d-40c9-a384-6ba9aacca946.PNG" width = '70%' height = '39%'>
</p>

"이탈 예상 고객층"</br>  
- 이벤트 등의 추가 서비스</br>
- 자주 구매하는 상품 위주</br>
- 온라인 채널 홍보</br>
</br>

<p align = 'left'>
<img src = "https://user-images.githubusercontent.com/96767467/197762743-daf30b73-b51c-4923-8fa8-a44d7615b026.PNG" width = '68%' height = '39%'>
</p>

"구매력 높은 고객층"</br>  
- 구매 금액에 따른 혜택</br>  
- 고품질의 고가 상품군</br>
- 계절 상품 개발</br>
</br>

### 3-3 개인맞춤형 추천시스템

<p>
<img src = "https://user-images.githubusercontent.com/96767467/197762745-3deec220-f169-432a-9ded-933876359a43.PNG" align = 'center' width = 95% height = "53%">
</p>
<p>
최근에는 큰 틀에서의 추천 시스템은 효과를 별로 보지 못합니다.</br>
따라서 군집솔루션과 고객들의 개인 선호도를 결합하여 Base 추천 시스템을 구성할 필요가 있습니다.</br>
여기에 계절 인기상품과 개인 선호 상품군, 가격대 등이 결합되어 더 유의미한 추천이 이루어집니다.
</p>

<p align = 'center'>
<img src = "https://user-images.githubusercontent.com/96767467/197762745-3deec220-f169-432a-9ded-933876359a43.PNG" width = "48%" height = "27%">
<img src = "https://user-images.githubusercontent.com/96767467/197762748-6e449b02-f978-4e2f-867b-5b516faee16b.PNG" width = "48%" height = "27%">
</p>
<p>
Surprise api를 통해 구성하였으며, Baseline은 SVD알고리즘과 Knn 알고리즘 중 rmse가 낮은 것이 선택되어 적용되도록 하였습니다.</br>
전년 동월의 상품군별 인기 상품과 개인 추천 리스트와 곂치는 것이 있다면, 가중치를 주어 상단으로 올라오게 됩니다.</br>
이를 통해 개인 맞춤형 추천에 군집 솔루션을 자연스럽게 녹일 수 있으며, 가중치 등은 전문가와 함께 보완할 여지가 있습니다.
</p>

</br>
</br>

## 팀원 소개

<img align="left" width="180" height="180"  src="https://user-images.githubusercontent.com/96767467/175776031-f03f973a-ad72-490f-af43-80ebac94bde0.png"/>

  [팀장] 어정호 <br><br><br><br><br>

MAIL : fishup97@gmail.com <br>

Github : https://github.com/fish-ho <br>

---

<img align="left" width="180" height="180" src="https://user-images.githubusercontent.com/96767467/175776083-7b96dcca-0357-4c22-a39e-366cfc84dd24.png"/>

  [수석개발자] 조남현 <br><br><br><br><br>

MAIL : chonh0531@gmail.com <br>

Github : https://github.com/MiddleJo <br>

---

<img align="left" width="180" height="180" src="https://user-images.githubusercontent.com/96767467/175776239-e4f7823a-4493-4673-8146-42b1845c3000.png" />

  [수석디자인] 최지원 <br><br><br><br><br>

MAIL : plasticmelody@gmail.com <br>

Github : https://github.com/JadeWednesday <br>

---

<img align="left" width="180" height="180" src="https://user-images.githubusercontent.com/96767467/175776334-d2e0b212-9fea-4164-8ddc-944608e7b3f5.png"/>

  [데이터마이너] 김민성 <br><br><br><br><br>

MAIL : nycticebus0915@gmail.com <br>

Github : https://github.com/nycticebus0915 <br>

---

<img align="left" width="180" height="180" src="https://user-images.githubusercontent.com/96767467/175776612-5502a307-31b3-4ded-a09e-5a11b2ad3c67.png" />

  조경윤 <br><br><br><br><br>

MAIL : kkyxxn@gmail.com <br>

Github : https://github.com/kkyxxn <br>

---
