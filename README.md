# wanted_pre_onboarding
wanted Pro-onboarding 지원을 위한 사전과제 입니다.

내용
### **문제 1) Tokenizer 생성하기**

**1-1. `preprocessing()`** 완

텍스트 전처리를 하는 함수입니다.

- input: 여러 영어 문장이 포함된 list 입니다. ex) ['I go to school.', 'I LIKE pizza!']
- output: 각 문장을 토큰화한 결과로, nested list 형태입니다. ex) [['i', 'go', 'to', 'school'], ['i', 'like', 'pizza']]
- 조건 1: 입력된 문장에 대해서 소문자로의 변환과 특수문자 제거를 수행합니다.
- 조건 2: 토큰화는 white space 단위로 수행합니다.
    
    

**1-2. `fit()`**

어휘 사전을 구축하는 함수입니다.

- input: 여러 영어 문장이 포함된 list 입니다. ex) ['I go to school.', 'I LIKE pizza!']
- 조건 1: 위에서 만든 `preprocessing` 함수를 이용하여 각 문장에 대해 토큰화를 수행합니다.
- 조건 2: 각각의 토큰을 정수 인덱싱 하기 위한 어휘 사전(`self.word_dict`)을 생성합니다.
    - 주어진 코드에 있는 `self.word_dict`를 활용합니다.
    

**1-3. `transform()`**

어휘 사전을 활용하여 입력 문장을 정수 인덱싱하는 함수입니다.

- input: 여러 영어 문장이 포함된 list입니다. ex) ['I go to school.', 'I LIKE pizza!']
- output: 각 문장의 정수 인덱싱으로, nested list 형태입니다. ex) [[1, 2, 3, 4], [1, 5, 6]]
- 조건 1: 어휘 사전(`self.word_dict`)에 없는 단어는 'oov'의 index로 변환합니다.

### **문제 2) TfidfVectorizer 생성하기**

**2-1. `fit()`**

입력 문장들을 이용해 IDF 행렬을 만드는 함수입니다.

- input: 여러 영어 문장이 포함된 list 입니다. ex) ['I go to school.', 'I LIKE pizza!']
- 조건 1: IDF 행렬은 list 형태입니다.
    - ex) [토큰1에 대한 IDF 값, 토큰2에 대한 IDF 값, .... ]
- 조건 2: IDF 값은 아래 식을 이용해 구합니다.
    
    $$
    idf(d,t)=log_e(\frac{n}{1+df(d,t)})
    $$
    
    - $df(d,t)$ : 단어 t가 포함된 문장 d의 개수
    - $n$ : 입력된 전체 문장 개수
- 조건 3: 입력된 문장의 토큰화에는 문제 1에서 만든 Tokenizer를 사용합니다.
    
    

**2-2. `transform()`**

입력 문장들을 이용해 TF-IDF 행렬을 만드는 함수입니다.

- input: 여러 영어 문장이 포함된 list입니다. ex) ['I go to school.', 'I LIKE pizza!']
- output : nested list 형태입니다.
    
    ex) [[tf-idf(1, 1), tf-idf(1, 2), tf-idf(1, 3)], [tf-idf(2, 1), tf-idf(2, 2), tf-idf(2, 3)]]
    
    |  | 토큰1 | 토큰2 | 토큰3 |
    | --- | --- | --- | --- |
    | 문장1 | tf-idf(1,1) | tf-idf(1,2) | tf-idf(1,3) |
    | 문장2 | tf-idf(2,1) | tf-idf(2,2) | tf-idf(2,3) |
- 조건1 : 입력 문장을 이용해 TF 행렬을 만드세요.
    - $tf(d, t)$ : 문장 d에 단어 t가 나타난 횟수
- 조건2 : 문제 2-1( `fit()`)에서 만든 IDF 행렬과 아래 식을 이용해 TF-IDF 행렬을 만드세요
    
    $$
    tf-idf(d,t) = tf(d,t) \times idf(d,t)
    $$
