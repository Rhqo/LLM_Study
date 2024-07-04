# Chap. 6 임베딩과 모델 아키텍쳐 맞춤화

## 추천 시스템 만들기

문제와 데이터 설정하기

추천의 문제 정의하기

추천 문제 정의

- 패턴 활용: 사용자의 과거 선호도를 바탕으로 **사용자가 좋아할 것이라고 확신하는 아이템**, **혹은 이전에 상호작용한 아이템과 유사한 아이템**을 추천하는 것.
- 탐색: 사용자가 **이전에 고려하지 않았을 수 있는 아이템**을 제안, 특히 추천이 과거에 좋아했던 것과 정확히 유사하지 않을 때 사용

추천 엔진의 접근 방식

- 콘텐츠 기반 추천: 추천되는 **아이템의 특성**에 초점. 사용자의 과거 상호작용을 기반으로 비슷한 콘텐츠 추천
- 협업 필터링: **사용자의 선호도와 행동**에 초점. 유사한 관심사나 취향을 가진 사용자 간의 패턴을 식별하여 추천
    - 사용자 기반 접근: 유사한 선호도를 가진 사용자 → 그 사용자들이 좋아하거나 상호작용한 아이템 추천
    - 아이템 기반 접근: 다른 사용자의 상호작용 기반 → 사용자가 이전에 좋아했던 아이템과 유사한 아이템을 찾는 데 중점.

자카드 점수 (자카드 유사도): 공통으로 가지고 있는 요수의 수를 두 그룹의 총 고유 요소의 수로 나누어 계산

추천 시스템의 전체 개요

항목 비교를 위한 맞춤형 설명 필드 생성

데이터셋에서 여러 관련 정보를 통합하여, 맞춤 생성된 설명 필드를 만들 것.

| MAL_ID | Name | Score | Genres | English name | Type | Episodes | Premiered | Producers | Studios | Source | Duration | Rating | Ranked | Members | Favorites | Completed | On-Hold | synopsis |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | Cowboy Bebop | 8.78 | Action, Adventure, Comedy, Drama, Sci-Fi, Space | Cowboy Bebop | TV | 26 | Spring 1998 | Bandai Visual | Sunrise | Original | 24 min. per ep. | R - 17+ (violence & profanity) | 28.0 | 1251960 | 61971 | 718161 | 71513 |

```arduino
Cowboy Bebop is a TV Show.
Synopsis: In the year 2071, humanity has colonized several of the planets and moons of the solar system leaving the now uninhabitable surface of planet Earth behind. The Inter Solar System Police attempts to keep peace in the galaxy, aided in part by outlaw bounty hunters, referred to as "Cowboys." The ragtag team aboard the spaceship Bebop are two such individuals. Mellow and carefree Spike Spiegel is balanced by his boisterous, pragmatic partner Jet Black as the pair makes a living chasing bounties and collecting rewards. Thrown off course by the addition of new members that they meet in their travelsEin, a genetically engineered, highly intelligent Welsh Corgi; femme fatale Faye Valentine, an enigmatic trickster with memory loss; and the strange computer whiz kid Edward Wongthe crew embarks on thrilling adventures that unravel each member's dark and mysterious past little by little. Well-balanced with high density action and light-hearted comedy, Cowboy Bebop is a space Western classic and an homage to the smooth and improvised music it is named after.
It was produced by Bandai Visual and it is from Sunrise Studio.
Its source is Original.
It premiered in Spring 1998.
Its genres are Action, Adventure, Comedy, Drama, Sci-Fi, Space
```

다차원적 표현, 제목을 비교하고 유사성을 식별할 때 더 광범위한 정보를 고려할 수 있게 정확하고 의미있는 추천 가능해진다.

파운데이션 임베더로 기준선 설정

파인튜닝 데이터 준비

SBERT 임베더 사용

max_seq_length 고려

문장 트랜스포머 라이브러리로 오픈소스 임베더 파인튜닝하기

RoBERTa (paraphrase-distilroberta-base-v1)

mpnet (all-mpnet-basev2)

결과

mpnet → 512의 max_token_length를 가진 mpnet의 성능이 가장 좋았다.

RoBERTa의 token length를 384로 바꾼 모델은 오히려 성능이 떨어졌다.

- 어텐션 계층에 충분한 파라미터가 없어 추천 문제를 잘 파악하지 못했을 것. → 파인튜닝되지 않은 모델은 단순히 **의미론적으로 유사한 제목**을 추천하는 데 의존했을 수 있음
- 384보다 더 많은 토큰이 필요할 수 있음

---

## 정리

`임베딩 모델`을 파인튜닝하는 과정을 알아보았다.

오픈소스 모델을 파인튜닝하여 사용자의 과거 선호도를 기반으로 **애니메이션 추천 시스템**을 만들어 보았다.

`레이블`이 `지정된 데이터`와 `테스트를 위한 자원`에 접근가능할 때, 임베딩 모델과 그들의 아키텍처를 특수한 작업에 맞추는 것으로 성능 향상을 이끌어내고, 이것이 OpenAI와 같은 클로즈드 모델의 대안이 될 수 있음을 배웠다.