---
layout: page

title: 숙제
---

## Homework#6 - 재귀와 반복 : 검색 (마감: 10월 26일 오후 5시)

### 1. 중복 골라내기

문자열 인수를 받아서 2번 이상 나온 문자를 리스트로 모아서 내주는 함수 `collect_ dups`를 다음 틀에 맞추어 작성하자.

```
def collect_dups(s):
    singles = ""
    duplicates = []
    pass # Write your for-loop here.
    return duplicates

# Test code
print(collect_dups("sophisticated"))
# ['s', 'i', 't']
print(collect_dups("I'm no angel."))
# [' ', 'n']
print(collect_dups("Stay Hungry. Stay Foolish."))
# ['y', ' ', 'S', 't', 'a', 'o', '.']
print(collect_dups("Your time is limited, so don't waste it living someone else's life."))
# [' ', 'i', 'm', 't', 'e', 's', 'o', 'd', 'l', 'n', "'"]
```

### 2. 아나그램 확인

단어를 구성하고 있는 문자의 순서를 바꾸어 다른 단어가 되면, 이 두 단어를 아나그램(anagram)이라고 한다. 아나그램의 사례 몇 개만 들어보면 다음과 같다.

```
"silent" "listen" 
"elvis" "lives" 
"restful" "fluster" 
"문전박대" "대박전문"
```

두 문자열이 아나그램인지 확인하여 맞으면 `True`, 맞지 않으면 `False`를 리턴해 주는 함수를 아래 뼈대코드에 맞추어 작성하자(`find` 메소드는 허용, `sort()` 메소드는 불허).

```
def isanagram(word1,word2):
    while word1 != '':
        if word1[0] in word2:
            pass # write your code here.
        else:
            return False
    return word2 == ''

# Test code
print(isanagram('silent','listen'))     # True
print(isanagram('silent','listens'))    # False
print(isanagram('elvis','lives'))       # True
print(isanagram('restful','fluster'))   # True
print(isanagram('restfully','fluster')) # False
```

### 3. 정렬된 리스트에서 가장 넓은 간격 찾기

정렬된 정수 리스트를 인수로 받아서 인접한 수의 크기 차이가 가장 큰 두 수를 찾 아서 그 위치와 차이를 튜플로 내주는 함수 `search_widest_gap`을 작성하자. 예를 들어 정렬된 리스트 `[3,5,8,20,22]`의 인접한 수의 크기 차이가 가장 큰 두 수 는 `8`, `20`이다. 이 경우 위치는 앞 수의 인덱스인 `2`이며, 두 수의 차이는 `12`이다. `[3,5,8,20,22,34,37,40]`과 같이 동률이 있는 경우는 앞에 작은 인덱스를 선택한 다. 리스트는 항상 정렬되어 있다고 가정한다. 실행 사례는 몇 개만 살펴보면 다음과 같다.
```
# Test code
print(search_widest_gap([]))                     # (None, 0)
print(search_widest_gap([3]))                    # (0, 0)
print(search_widest_gap([3,5,8,20,22]))          # (2, 12)
print(search_widest_gap([3,5,8,20,22,34,37,40])) # (2, 12)
```
다음 테스트 함수를 호출하여 잘 작동하는지 확인해 보자.

```
import random
def testsearch_widest_gap():
    db = random.sample(range(500),100)
    print("Searching the widest gap...")
    db.sort()
    print(db)
    index, gap = search_widest_gap(db)
    print("The widest gap is:", gap)
    print("between", db[index], "and", db[index+1])
    print("at", index)
```

## Homework#5 - 재귀와 반복 : 정렬 (마감: 10월 22일 오후 5시)

### 1. 실습문제 #5.10, #5.11, #5.12

### 2. 부분리스트

시퀀스의 일부를 덩어리로 만들어 내주는 공통 연산인 `s[i:j]`를 사용하면, 
시퀀스 `s`의 인덱스 `i`부터 인덱스 `j`까지 
연결된 시퀀스 일부(`i` 원소 포함, `j` 원소 제외)를 복사하여 만들어준다. 
이 연산을 리스트에 한정지어 작동하도록 직접 함수로 구현하자. 
즉, 작성할 함수 `sublist`는 리스트와 인덱스 범위를 인수로 받아서, 
범위에 해당하는 리스트를 만들어 리턴해주면 된다. 
`sublist(s,low,high)`를 호출한 경우, 인수 `s`는 리스트, `low`는 범위의 시작 인덱스, 
`high`는 끝 인덱스를 나타낸다. 
인덱스가 음수로 주어지는 경우 모두 `0`으로 처리하기로 한다. 
이 함수는 다음 실행 사례와 같이 작동하면 된다.

```
# 테스트 코드
s = [1,2,3,4,5]
print("s = [1,2,3,4,5]") # 
print("sublist(s,0,0) => [] ?", sublist(s,0,0)) # []
print("sublist(s,0,1) => [1] ?", sublist(s,0,1)) # [1]
print("sublist(s,0,2) => [1, 2] ?", sublist(s,0,2)) # [1, 2]
print("sublist(s,0,3) => [1, 2, 3] ?", sublist(s,0,3)) # [1, 2, 3]
print("sublist(s,0,4) => [1, 2, 3, 4] ?", sublist(s,0,4)) # [1, 2, 3, 4]
print("sublist(s,0,5) => [1, 2, 3, 4, 5] ?", sublist(s,0,5)) # [1, 2, 3, 4, 5]
print("sublist(s,0,6) => [1, 2, 3, 4, 5] ?", sublist(s,0,6)) # [1, 2, 3, 4, 5]
print("sublist(s,1,1) => [] ?", sublist(s,1,1)) # []
print("sublist(s,1,2) => [2] ?", sublist(s,1,2)) # [2]
print("sublist(s,1,3) => [2, 3] ?", sublist(s,1,3)) # [2, 3]
print("sublist(s,1,4) => [2, 3, 4] ?", sublist(s,1,4)) # [2, 3, 4]
print("sublist(s,1,5) => [2, 3, 4, 5] ?", sublist(s,1,5)) # [2, 3, 4, 5]
print("sublist(s,1,6) => [2, 3, 4, 5] ?", sublist(s,1,6)) # [2, 3, 4, 5]
print("sublist(s,2,2) => [] ?", sublist(s,2,2)) # []
print("sublist(s,2,3) => [3] ?", sublist(s,2,3)) # [3]
print("sublist(s,2,4) => [3, 4] ?", sublist(s,2,4)) # [3, 4]
print("sublist(s,2,5) => [3, 4, 5] ?", sublist(s,2,5)) # [3, 4, 5]
print("sublist(s,2,6) => [3, 4, 5] ?", sublist(s,2,6)) # [3, 4, 5]
print("sublist(s,3,3) => [] ?", sublist(s,3,3)) # []
print("sublist(s,3,4) => [4] ?", sublist(s,3,4)) # [4]
print("sublist(s,3,5) => [4, 5] ?", sublist(s,3,5)) # [4, 5]
print("sublist(s,3,6) => [4, 5] ?", sublist(s,3,6)) # [4, 5]
print("sublist(s,5,2) => [] ?", sublist(s,5,2)) # []
print("sublist(s,-3,-2) => [] ?", sublist(s,-3,-2)) # []
```
이 작업을 완수하기 위해서 앞부분 떼어내는 작업과 
뒷부분 떼어내는 작업을 분리하여 따로 함수를 만든 다음, 
`sublist` 함수는 이 두 함수를 잇달아 호출하여 작업을 수행할 수 있도록 하자.

#### 가. `drop_before` 함수

앞부분을 떼어내는 함수를 먼저 만들자. 
리스트 `s`와 인덱스 `index`를 인수로 받아서 `index` 앞에 있는 원소들 제거한 
나머지 리스트를 내주는 함수 `drop_before`는 다음과 같이 작성할 수 있다. 
이 함수는 저절로 꼬리재귀 형태가 되었다. 
이 함수를 이해한 다음, `while` 루프 버전으로 변환하여 완성하자.

```
def drop_before(s,index):
    if s != [] and index > 0:
        return drop_before(s[1:],index-1) 
    else:
        return s

# 테스트 코드
s = [1,2,3,4,5]
print("s = [1,2,3,4,5]")
print("drop_before(s,0) =", drop_before(s,0)) # [1, 2, 3, 4, 5]
print("drop_before(s,1) =", drop_before(s,1)) # [2, 3, 4, 5]
print("drop_before(s,2) =", drop_before(s,2)) # [3, 4, 5]
print("drop_before(s,3) =", drop_before(s,3)) # [4, 5]
print("drop_before(s,4) =", drop_before(s,4)) # [5]
print("drop_before(s,5) =", drop_before(s,5)) # []
print("drop_before(s,6) =", drop_before(s,6)) # []
print("drop_before(s,-3) =", drop_before(s,-3)) # [1, 2, 3, 4, 5]
print("drop_before([],4) =", drop_before([],4)) # []
```

#### 나. `take_before` 함수

이번에는 뒷부분을 떼어내는 함수를 만들 차례이다. 
리스트 `s`와 인덱스 `index`를 인수로 받아서 `index` 뒤에 있는 원소를 제거한 
(`index` 원소도 제거 대상) 나머지 리스트를 내주는 함수 `take_before`를 
재귀 함수, 꼬리재귀 함수, `while` 문 함수 차례로 각각 작성하자. 
이 함수는 다음 실행 사례와 같이 작동하면 된다.

```
# 테스트 코드
s = [1,2,3,4,5]
print("take_before(s,0) =", take_before(s,0)) # []
print("take_before(s,1) =", take_before(s,1)) # [1]
print("take_before(s,2) =", take_before(s,2)) # [1, 2]
print("take_before(s,3) =", take_before(s,3)) # [1, 2, 3]
print("take_before(s,4) =", take_before(s,4)) # [1, 2, 3, 4]
print("take_before(s,5) =", take_before(s,5)) # [1, 2, 3, 4, 5]
print("take_before(s,6) =", take_before(s,6)) # [1, 2, 3, 4, 5]
print("take_before([],4) =", take_before([],4)) # []
print("take_before(s,-3) =", take_before(s,-3)) # []
```

####  다. sublist 함수

위에서 작성한 `drop_before`와 `take_before`를 사용하여 
다음 형식에 맞추어 `sublist` 함수를 완성하자.

```
def sublist(s,low,high): 
    if low < 0: low = 0 
    if high < 0: high = 0 
    if low <= high:
		return None # Write your expression here. 
	else:
		return []
```


## Homework#4 - 재귀와 반복 : 자연수 계산 (마감: 10월 12일 오후 5시)

### 가. 삼각수

삼각수(triangular number)는 1, 3, 6, 10, 15, 21, ... 로서 다음과 같은 방식으로 구한다.

![Tri](https://i.imgur.com/0vcij8E.png)


삼각수를 구하는 재귀 함수 `trinum`을 작성한 다음, 
꼬리재귀 함수와 `while` 루프 함수로 차례로 변환하자. 
`0` 이하의 인수에 대해서는 모두 `0`을 내주어야 한다.

```
def trinum(n):
	pass # Write your code here.

# Test code
print(trinum(1))  # 1
print(trinum(3))  # 6
print(trinum(6))  # 21
print(trinum(11)) # 66
print(trinum(0))  # 0
print(trinum(-3)) # 0
```

### 나. 덧셈만 가지고 제곱 계산하기

자연수 `n`의 제곱(square)은 첫 `n`개 홀수의 합으로 구할 수 있다. 즉,

![Square](https://i.imgur.com/Dd80eYy.png)

이 성질을 이용하여 덧셈만으로 정수 인수의 제곱을 계산하는 재귀 함수 `square`를 작성하고, 
이어서 꼬리재귀 함수와 `while` 루프 함수로 변환하자. 
그런데 음수 인수에 대해서도 제대로 작동해야 한다. 
먼저 양수 인수만 처리한다고 가정하고 코드를 완성한 다음, 
음수 처리에 대해서 고민하면 쉽다.  
`n`의 제곱은 `-n`의 제곱과 동일하기 때문이다.
정수 `n`의 절대 값은 라이브러리 내장 함수 `abs(n)`을 호출하여 구할 수 있다.

```
def square(n):
	pass # Write your code here.

# Test code
print(square(0))  # 0
print(square(1))  # 1
print(square(-2)) # 4
print(square(3))  # 9
print(square(-4)) # 16
print(square(5))  # 25
```

## Homework#3 - 논리식 + 제어구조 (마감: 10월 5일 오후 5시)

### 가. 윤년 확인 함수

2월은 평년인지 윤년인지에 따라 각각 28일 또는 29일이 있다. 
기본적으로 윤년은 4년마다 한 번씩 돌아오는데 오차를 줄이기 위해서 예외를 둔다. 
윤년을 결정하는 규칙은 다음과 같다.

> 4의 배수이면 윤년인데, 그 중에서 400의 배수를 제외한 100의 배수는 평년이다.

예를 살펴보면,
- 2008, 2012, 2016년은 4의 배수이고 100의 배수가 아니므로 윤년이고,
- 1600, 2000, 2400년은 100의 배수이지만 400의 배수이므로 윤년이고,
- 2013, 2014, 2015년은 4의 배수가 아니므로 평년이고,
- 2100, 2200, 2300년은 100의 배수이고 400의 배수가 아니므로 평년이다.

`0` 이상의 정수를 받아서 윤년이면 `True`, 평년이면 `False`를 리턴 하는 
함수 `isleapyear`를 작성하자. 
아래 뼈대코드의 `None` 부분을 논리식 하나만으로 대치하면 충분하다. 
(음수 인수의 경우에는 `None`을 리턴 해야 한다.)

```
def isleapyear(year):
    if year >= 0:
        return None # Replace None with Boolean expression.
    else:
        return None

# Test code
print(isleapyear(0))     # True
print(isleapyear(1))     # False
print(isleapyear(4))     # True
print(isleapyear(2010))  # False
print(isleapyear(2011))  # False
print(isleapyear(2012))  # True
print(isleapyear(2013))  # False
print(isleapyear(2016))  # True
print(isleapyear(1900))  # False
print(isleapyear(2000))  # True
print(isleapyear(2020))  # True
print(isleapyear(2100))  # False
print(isleapyear(2200))  # False
print(isleapyear(2400))  # True
print(isleapyear(-2000)) # None
```

### 나. 유효 날짜 검증 함수

년, 월, 일을 정수 인수로 받아서 실제로 존재하는 날짜인지 검증하는 함수 `is_valid_date`를 만들자.

- 년 `year` : `0` 이상의 정수 (음수는 불허)
- 월 `month` : `1∼12` 범위의 정수
- 일 `day` : 1/3/5/7/8/10/12월은 `1∼31` 범위의 정수, 4/6/9/11월은 `1∼30` 범위의 정수, 2월은 평년의 경우 `1∼28` 범위의 정수, 윤년의 경우 `1∼29` 범위의 정수

예를 들어, 2019년 11월 31일은 존재하지 않는 날짜이고, 2020년 2월 29일은 존재하는 날짜이다. 따라서, 완성할 날짜 검증 함수는 `is_valid_date(2019,11,31)`을 호출하면 `False`를 리턴 하고, `is_valid_date(2020,2,29)`을 호출하면 `True`를 리턴 해야 한다. 다음 뼈대코드의 논 리식의 뒷부분을 채워 넣어 검증 함수를 완성해보자. (윤년 확인은 앞 문제에서 작성한 함수를 사용해도 좋다.)

```
def is_valid_date(year,month,day):
    return year >= 0 and 1 <= month <= 12 and \
           None
```

### 다. 수강과목 평균 점수 계산 서비스 (과락 제외)

실습 3.8에서 완성한 수강과목 평균 점수 계산 서비스 프로그램에서 점수가 60점미만이라 낙제 한 과목은 평균 계산에서 제외하고 대신 낙제한 과목의 수를 추가로 아래와 같이 프린트해달라 는 요구사항이 발생하였다. 출력 요구사항에 맞게 아래 사항을 고려하여 프로그램을 수정하자.

```
Score Average Calculator 
How many classes? 5 
Enter your score: 92 
Enter your score: 78 
Enter your score: 54 
Enter your score: 88 
Enter your score: 64 
Your average score =
1 class failed
```

실습 3.8에서 완성한 프로그램과 동일한 요령으로 평균을 계산하되, 1∼59점 사이의 점수는 낙 제이므로 평균 계산에 제외해야 한다. 위의 사례에서는 54점이 유일하게 낙제 점수이다. 따라서 마지막 줄에 1과목이 낙제임을 알려주었다.

평균을 계산할 점수가 없을 때에도, 다음과 같이 낙제한 과목의 개수를 알려주어야 함에 주의 하자.

```
Score Average Calculator 
How many classes? 2
Enter your score: 43
Enter your score: 59
Your average score = 0.0 점 
2 classes failed
```



## Homework#2 - 대출 원리금 균등분할 상환금 계산 (마감: 9월 21일 오후 5시)

### 가. 함수 구현

은행 대출금의 원리금 균등분할 상환 방식은 
원금과 이자 합계를 매월 균등하게 나누어 상환하는 방식이다. 
이자를 월복리로 계산하여, 원금이 `p`, 월이자율이 `r`, 상환 월수가 `m` 일때, 
매월 상환해야 하는 금액을 계산하는 공식은 다음과 같다.

![payback](https://i.imgur.com/TDspr0m.png)

이 공식을 구현하는 함수 `monthly_payment_plan`을 구현하자. 
원금, 연 이자율, 상환기간은 각각 인수로 주어지며, 
각 인수의 단위 및 타입은 다음 테이블과 같다.

![table](https://i.imgur.com/8rMF1wf.png)

계산한 월상환액의 소수점 이하는 잘라버리고 자연수로 제시해야 한다.

다음 코드 틀에 맞추어 함수를 완성하자.

```
def monthly_payment_plan(principal, interest, year): 
    pass # Write your code here.

# Test code
print(monthly_payment_plan(10000000, 2.8, 4)) # 220460
```

### 나. 서비스 구현

위 문제에서 작성한 함수를 활용하여 원리금 균등분할 상환 방식으로 
월 상환금 및 총 상환 금액을 계산해주는 서비스를 구현하자. 
원금(원), 연 이자율(백분율), 상환기간(년)을 차례로 키보드로 입력받아, 
월상환금과 상환금 총액을 계산하여 실행창에 프린트해야 한다. 
프로그램을 실행하여 계산 완료한 후에 
다음과 같은 형식으로 실행창에 나타나도록 프로그램을 작성한다.

```
자유은행 대출 상환금 계산 서비스에 오심을 환영합니다. 
대출원금이 얼마인가요? (백만원 이상) 5000000
연 이자율은 몇% 인가요? (0.0-9.9) 2.9
상환기간은 몇 년인가요? 4

대출 상환금 내역을 알려드리겠습니다.
대출원금: 5000000 원
연 이자율 2.9 %로 4 년 동안 매월 원리금 균등 상환 
매월 110450 원씩 지불하셔야 합니다.
상환 완료시까지 총 상환금액은 5301600 원 입니다.

저희 자유은행은 항상 여러분과 함께 합니다. 
또 들려주세요.
```

여기서 둘째, 셋째, 넷째 줄의 뒤쪽에 있는 
`5000000`, `2.9`, `4`는 모두 키보드 입력이고, 
나머지는 프로그램이 프린트 한 것이다. 
띄어쓰기와 줄넘기기도 똑같이 나타나도록 프린트해야 함에 주의하자.


## Homework#1 - 마라톤 세계 기록의 초속 계산 (마감: 9월 14일 오후 5시)

마라톤은 42.195km를 달리는 도로 경주인데, 2020년 1월 현재 마라톤 세계 기록은 케냐 국적 의 엘리우드 킵초게 선수가 2018년 9월 16일 베를린 마라톤에서 세운 2시간 1분 39초이다. 이 선수는 이 기록을 세우면서 평균하여 1초당 몇 미터를 뛰었는지 식을 세워서 계산하자. 소수점 아래는 버리고 정수로 결과를 얻도록 한다.

제출 : 블랙보드

