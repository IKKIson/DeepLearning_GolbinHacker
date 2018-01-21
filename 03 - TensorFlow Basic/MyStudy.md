# 텐서플로우 프로그래밍

## 텐서플로우 기초

텐서플로우TensorFlow의 기본 데이터 구조인 텐서Tensor는 보통 다차원 배열이라고 말합니다. 텐서플로우에는 세 가지의 핵심 데이터 구조인 상수Constant, 변수Variable, 플레이스홀더Placeholder가 있다.

### 기본구조와 문법

1. 텐서(_Tensor_)
- 텐서플로우의 기본 데이터 구조인 텐서는 보통 다차원 배열로 설명하지만 맞기도하고 틀리기도하다. 
    - C++ API에서 말하는 텐서는 다차원 배열에 가깝다. 메모리를 할당하고 데이터 구조를 직접 챙긴다.
    - 파이썬 API 입장에서 텐서는 메모리를 할당하거나 어떤 값을 가지고 있지 않으며 계산 그래프의 연산(_Operation_) 노드(_Node_)를 가리키는 객체에 가깝다. 우리가 주로 다루는 파이썬 API의 텐서는 넘파이(_NumPy_)의 다차원 배열 보다는 어떤 함수를 의미하는 수학 분야의 텐서(_Tensor_)에 더 비슷합니다.
- **랭크(_Rank_)**
    - TensorFlow 시스템에서, tensor는 rank라는 차원 단위로 표현된다. Tensor rank는 행렬의 rank와 다르다. Tensor rank(order, degree, -n_dimension 으로도 언급됨)는 tensor의 차원수다. 
    - 예를 들어, 아래 tensor(Python 리스트로 정의)의 rank는 2다.
    ```markdown
    t = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    ```
    - rank 2인 tensor는 행렬, rank 1인 tensor는 벡터로 생각할 수 있다. rank 2인 tensor는 t[i, j] 형식으로 원소에 접근할 수 있다. rank 3인 tensor는 t[i, j, k] 형식으로 원소를 지정할 수 있다.
    
    Rank	Math entity	Python example
0	Scalar (magnitude only)	s = 483
1	Vector (magnitude and direction)	v = [1.1, 2.2, 3.3]
2	Matrix (table of numbers)	m = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
3	3-Tensor (cube of numbers)	t = [[[2], [4], [6]], [[8], [10], [12]], [[14], [16], [18]]]
n	n-Tensor (you get the idea)	....
    
    
    
- **셰이프(_Shape_)**

2. 플레이스홀더

3. 변수

4. 연산

5. 그래프
- 그래프 생성
- 그래프 실행
- 지연 실행

