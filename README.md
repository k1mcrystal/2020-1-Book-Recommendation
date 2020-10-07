# 2020-1-Book-Recommendation
> YBIGTA 2020-1 conference project
> 각 도서의 내용을 대표하는 키워드를 기반으로 하는 도서 추천시스템 구현

members: 김수정, 김용우, 노시영, 박솔희, 박준민

**1. 프로젝트 목표**
- 인터파크, 알라딘, yes24등 기존의 도서 판매 사이트에서는 장르별 추천 혹은 유저 기반 추천이 대부분
- 책 내용에 기반한 추천시스템을 만들자!
- 선택한 책과 비슷한 내용의 책을 추천해주는 모델 구현 목표

**2. 프로젝트 진행 단계**
1) Crawling
- Request와 Beautiful Soup 활용
- yes24 도서 약 40,000권의 '책 제목', '책 소개', '작가' 정보 크롤링
2) Tokenize
- KoNLPy 활용
- 데이터 tokenize & 품사 tagging
- 문장에서 가장 많은 의미를 차지하고 있고 키워드로 활용하기 좋은 명사, 형용사만 사용하기로 결정
3) Modeling
- 구현하고자 하는 시스템: 책 이름을 검색 -> 해당 책의 대표 키워드 5개 확인 -> 마음에 드는 키워드 3개 선택 -> 선택한 키워드와 유사한 내용의 책 추천
- 구현 과정: Rake 모델로 핵심 키워드 뽑아내기 -> TF-IDF vectorizer를 이용하여 벡터화 -> Cosine Similarity로 키워드간 유사도 계산
- 추천 시스템 실행 과정: 모든 책마다 벡터화된 대표 키워드 5개를 가지고 있다. -> 각 도서의 5개의 키워드와 선택된 3개의 키워드 간 코사인 유사도의 평균 계산 -> 가장 낮은 값을 가지는 책 n개를 추천
