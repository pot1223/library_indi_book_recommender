# 2024 도서관데이터활용공모전 제출용 코드 
## 사용한 데이터셋은 본 레포지토리에서 다운가능합니다. 

|데이터명|설명| 
|-----|---|
|popular_loan_book|도서관 정보나루 7월 인기대출도서 상위 5권(장르 및 null 값 전처리 적용)|
|indi_book|인디펍 플랫폼 독립서적 2085건|

## 프로젝트 목표 
### 독립 서적 추천을 활용한 콘텐츠 제공으로 독립 서적의 정보 접근성을 높이고, 독립 서적 시장 활성화에 기여

![이미지](https://github.com/user-attachments/assets/1b68b08e-ae35-4863-9ec7-a793cab001aa) 


> 추천코드 구현Step
>> * Step 1. 전처리 과정 
>>> *가져온 데이터셋에서 빈 feature 값이 존재하는 데이터 삭제 및 독립 서적 장르 전처리 후 만화 및 동화, 그림 장르 제외

>
>>Step 2. 명사로만 이루어진 문자열 생성
>>> Okt의 형태소 분석기를 사용해서 명사를 추출한 뒤, 한 글자로 구성된 단어를 불용어로 판단하여 제거

>>Step 3. subword 사전 구축
>>> 독립 서적 문자열 대상으로 sentencepice 모델을 통해 subword 사전을 구축

>>Step 4. document 생성
>>> subword 사전을 통해 토큰화를 수행하여 document 생성

>>Step 5. 유사도 계산
>>> Weighted Jaccard similarity를 통해 키워드가 포함된 독립 서적 집합 구축 
>>> Padding이 적용된 cosine similarity를 통해 인기대출도서와 연관있는 독립 서적 추천
