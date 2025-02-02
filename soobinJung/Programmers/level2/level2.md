
## 🏷 전화번호 목록
```java
import java.util.HashMap;
import java.util.Map;

class Solution { 
    public boolean solution(String[] phoneBook) { 
        boolean answer = true; 
        HashMap<String, Integer> map = new HashMap<>(); 
        for(int i = 0; i < phoneBook.length; i++) 
            map.put(phoneBook[i], i); 
        for(int i = 0; i < phoneBook.length; i++) { 
            for(int j = 1; j < phoneBook[i].length(); j++) { 
                if(map.containsKey(phoneBook[i].substring(0,j))) { 
                    answer = false; return answer; 
                } 
            } 
        } 
        return answer; 
    } 
}
// 위의 코드 성공함.

import java.util.*;

class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        for (String phoneIndex : phone_book) {
            for (String phoneCompare : phone_book) { // 자기자신 비교 제거
                if (phoneIndex.length() < phoneCompare.length()) {
                    // 문자열 비교할 때, == 랑 equals비교해서 잘 쓰기
                    if (phoneIndex.equals(phoneCompare.substring(0, phoneIndex.length()))) {
                        answer = false;
                        return answer;
                    }
                }
            }
        }
        return answer;
    }
}
// 위의 코드 실행 시간 에러 뜸.

class Solution {
    public boolean solution(String[] phoneBook) {
        for (int i = 0; i < phoneBook.length - 1; i++) {
            for (int j = i + 1; j < phoneBook.length; j++) {
                if (phoneBook[i].startsWith(phoneBook[j])) {
                    return false;
                }
                if (phoneBook[j].startsWith(phoneBook[i])) {
                    return false;
                }
            }
        }
        return true;
    }
}
// 효율성 씨발 뭔데
```

## 🏷 위장

```java
import java.util.HashMap;

class Solution {
    public int solution(String[][] clothes) { // 2차원 배열 vs 1차원배열
        int answer = 1;
        HashMap<String, Integer> hm = new HashMap();
        for (int i = 0; i < clothes.length; i++)
            hm.put(clothes[i][1], hm.getOrDefault(clothes[i][1], 1) + 1);
        for (String kinds : hm.keySet())
            answer *= hm.get(kinds);
        return answer - 1;
    }
}

// import java.util.*;
// import java.util.HashMap;

// // 문제는 풀었는데, 속도가 느림
// class Solution {
// public int solution(String[][] clothes) { // 2차원 배열 vs 1차원배열
// int answer = 0;
// Map<String, Integer> hm = new HashMap();

// for (int i = 0; i < clothes.length; i++) {
// hm.put(clothes[i][1], 1);
// }
// for (int i = 0; i < clothes.length; i++) {
// hm.put(clothes[i][1], hm.get(clothes[i][1]) + 1);
// }

// int xCal = 1;
// for (String kinds : hm.keySet()) {
// xCal = xCal * hm.get(kinds);
// }
// answer = answer + xCal;
// answer += xCal;
// answer = answer - 1;

// return answer;
// }
// }

// import java.util.HashMap;

// class Solution {
// public int solution(String[][] clothes) { // 2차원 배열 vs 1차원배열
// int answer = 1;
// HashMap<String, Integer> hm = new HashMap();
// for (int i = 0; i < clothes.length; i++) {
// hm.put(clothes[i][1], 1);
// }
// for (int i = 0; i < clothes.length; i++) {
// hm.put(clothes[i][1], hm.get(clothes[i][1]) + 1);
// }
// for (String kinds : hm.keySet()) {
// answer *= hm.get(kinds);
// }
// return answer - 1;
// }
// }

// 코드 똑같은데, 길이 줄인거

// import java.util.HashMap;
// import java.util.Iterator;
// class Solution {
// public int solution(String[][] clothes) {
// int answer = 1;
// HashMap<String, Integer> map = new HashMap<>();
// for(int i=0; i<clothes.length; i++){
// String key = clothes[i][1];
// if(!map.containsKey(key)) {
// map.put(key, 1);
// } else {
// map.put(key, map.get(key) + 1);
// }
// }
// Iterator<Integer> it = map.values().iterator();
// while(it.hasNext()) {
// answer *= it.next().intValue()+1;
// }
// return answer-1;
// }
// }

// 풀이는 똑같은데 다르게 표현

// import java.util.*;
// import static java.util.stream.Collectors.*;

// class Solution {
// public int solution(String[][] clothes) {
// return Arrays.stream(clothes)
// .collect(groupingBy(p -> p[1], mapping(p -> p[0], counting())))
// .values()
// .stream()
// .collect(reducing(1L, (x, y) -> x * (y + 1))).intValue() - 1;
// }
// }

// new
```

## 🏷 고양이와 개는 몇 마리 있을까

```sql
-- 코드를 입력하세요
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) as count
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE
```

## 🏷 동명 동물 수 찾기

```sql
-- 코드를 입력하세요
SELECT NAME, COUNT(NAME) as COUNT
FROM ANIMAL_INS
GROUP BY NAME
HAVING COUNT(NAME) > 1
ORDER BY NAME
```

## 🏷 입양 시각 구하기

```sql
-- 코드를 입력하세요
SELECT HOUR(DATETIME), COUNT(HOUR(DATETIME)) as COUNT
FROM ANIMAL_OUTS
WHERE HOUR(DATETIME) > 8 AND HOUR(DATETIME) < 20
GROUP BY HOUR(DATETIME)
# HAVING HOUR(DATETIME) > 8 AND HOUR(DATETIME) < 20
ORDER BY HOUR(DATETIME)
```

## 🏷 NULL 처리하기

```sql
-- 코드를 입력하세요
SELECT ANIMAL_TYPE, IFNULL(NAME, 'No name') AS NAME, SEX_UPON_INTAKE
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```

## 🏷 중복 제거하기

```sql
SELECT COUNT(DISTINCT NAME)
FROM ANIMAL_INS
WHERE NAME IS NOT NULL
```

## 🏷 동물 수 구하기

```sql
-- 코드를 입력하세요
SELECT COUNT(*) as 'count'
FROM ANIMAL_INS
```

## 🏷 최솟값
```sql
-- 코드를 입력하세요
SELECT min(DATETIME) as '시간' FROM ANIMAL_INS;
```

## 🏷 루시와 엘라 찾기
```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE
FROM ANIMAL_INS
WHERE NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
ORDER BY ANIMAL_ID
```

## 🏷 이름에 el 들어가는 동물 찾기 
```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE LOWER(NAME) LIKE LOWER('%el%') AND ANIMAL_TYPE='Dog'
ORDER BY NAME
```

## 🏷 DATETIME에서 DATE로 형변환
```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, '%Y-%m-%d') as 날짜
FROM ANIMAL_INS
```