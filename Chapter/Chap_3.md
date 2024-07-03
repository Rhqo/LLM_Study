# Chap. 3 프롬프트 엔지니어링의 첫번째 단계

### 프롬프트 엔지니어링

언어 모델에서 ‘정렬’

- 직접 요청하기
    
    ```arduino
    영어를 한국어로 번역해주세요
    
    영어: How do I call a cab from the airport?
    한국어: 
    
    => <번역된 내용>
    ```
    
- 퓨샷 학습
    
    ```arduino
    리뷰: 이 영화는 거지같아
    주관적: 예
    ###
    리뷰: 이 tv 드라마는 바다에 대해 말한다
    주관적: 아니오
    ...
    리뷰: 이 책은 2차 세계대전에 대한 것이었다
    주관적:
    
    => 아니오
    ```
    
- 출력 구조화
    
    ```arduino
    영어를 한국어로 번역해주세요.
    최종 결과는 다음과 같은 유효한 JSON 형식으로 만들어 주세요
    
    English: How do I call a cab from the airport?
    JSON:
    
    => {"english": "How do I call a cab from the airport?", "korean": "<번역된 내용>"}
    ```
    
- 페르소나 지정
    
    ```arduino
    건방진 가게 점원이라 생각하고 질문에 답을 하세요
    
    질문: 당근이 어디 있나요?
    점원:
    
    => 저기
    ```
    

### 여러 모델과 프롬프트 작업하기

**ChatGPT**

**Cohere**

```arduino
Translate to Korean.

Where is the nearest restaurant?

=> Nearby restaurant is here
```

```arduino
Translate to Korean

English: Where is the nearest restaurant?
Korean:

=> 가장 가까운 레스토랑은 어디인가요?
```

Cohere 모델은 GPT보다 조금 더 구조화된 지시사항이 필요하다.

이는 GPT보다 나쁘다는 것을 의미하는 것은 아니다.

**오픈소스 프롬프트 엔지니어링**

### ChatGPT와 Q/A 챗봇 만들기

---

## 정리

언어 모델의 성능을 향상시키기 위해 `프롬프트` 를 디자인하고 최적화하는 과정인 `프롬프트 엔지니어링` 을 공부했다.

먼저 언어 모델에서의 정렬이 어떤 의미를 가지는지에 대해 알아보았고,

`직접 요청하기`

`퓨샷 학습`

`출력 구조화`

`페르소나 지정하기`

`다른 모델과 함께 프롬프트 작업하기` 등의 방법을 통해 프롬프트 엔지니어링을 할 수 있다.

잘 만들어진 프롬프트는 모델에 명확한 지시를 제공하여 원하는 답변과 밀접하게 일치하는 출력을 생성한다.

프롬프트 엔지니어링은 데이터 주석 지침을 만들거나 숙련된 글쓰기에 가깝다.