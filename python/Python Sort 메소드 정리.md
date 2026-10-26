# [Python] Sort 메소드 정리

> 작성일: 2025-06-14 · 태그: Language/Python/Method, 기초

### 1. sorted() 함수
sorted()함수는 원본을 유지시키며 새로운 리스트를 반환한다.
```python
nums = [3, 1, 4, 2]
sorted_nums = sorted(num)
```

#### 주요옵션
```python
sorted(iterable, key=None, reverse=False)
```

| 옵션       | 설명                                      |
| -------- | --------------------------------------- |
| iterable | 정렬할 리스트, 튜플, 문자열 등                      |
| key      | 정렬 기준 함수 (예: `key=len` `key=str.lower`) |
| reverse  | True면 내림차순, 기본은 False                   |
```python
words = ['apple', 'banana', 'grape']
print(sorted(words, key=len)) # ['apple', 'grape', 'banana']
print(sorted(words, reverse=True)) # ['grape', 'banana', 'apple']
```

### 2. .sort() 함수
.sort() 함수는 원본 리스트를 직접 정렬시킨다.
```python
nums = [3, 1, 4, 2]
nums.sort()
print(nums) # [1, 2, 3, 4]
```

사용법은 sorted()와 같지만:
- 반환값은 None(리스트가 제자리에서 변경됨)
- 리스트 객체에만 사용 가능(문자열, 튜플 등에는 불가)
```python
nums.sort(reverse=True)
```

#### key 함수 예시
| 정렬 기준       | 코드 예시                             |
| ----------- | --------------------------------- |
| 길이 기준       | sorted(words, key=len)            |
| 대소문자 무시     | sorted(words, key=str.lower)      |
| 튜플의 두 번째 요소 | sorted(pairs, key=lambda x: x[1]) |
| 절댓값 기준      | sorted(nums, key=abs)             |
#### 오름차순 / 내림차순
```python
sorted([5, 2, 9], reverse=False)   # [2, 5, 9] (기본)
sorted([5, 2, 9], reverse=True)    # [9, 5, 2]
```

#### 문자열 정렬
```python
sorted("hello")     # ['e', 'h', 'l', 'l', 'o']
''.join(sorted("hello"))  # 'ehllo'
```

#### 정렬 방식 요약
| 방법       | 반환값   | 원본 변경 | 모든 iterable 사용 가능 | 특징          |
| -------- | ----- | ----- | ----------------- | ----------- |
| sorted() | 새 리스트 | ❌     | ✅                 | 가장 범용적, 안전함 |
| .sort()  | None  | ✅     | ❌ (리스트만)          | 빠름, 제자리 정렬  |
