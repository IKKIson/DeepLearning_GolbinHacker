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
    - 랭크는 차원단위를 표현하므로 랭크값이 0이면 스칼라, 1이면 벡터, 2이면 행렬, 3이면 n-Tensor 또는 n차원 텐서라고한다.
    - 예를 들어, 아래 tensor(Python 리스트로 정의)의 rank는 2다.
    ```markdown
    t = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    ```
    - rank 2인 tensor는 행렬, rank 1인 tensor는 벡터로 생각할 수 있다. rank 2인 tensor는 t[i, j] 형식으로 원소에 접근할 수 있다. rank 3인 tensor는 t[i, j, k] 형식으로 원소를 지정할 수 있다.
    
|Rank|Math entity                     |Python example                                               |
|----|--------------------------------|-------------------------------------------------------------|
|0   |Scalar(magnitude only)          |s = 483                                                      |
|1   |Vector(magnitude and direction) |v = [1.1, 2.2, 3.3]                                          |
|2   |Matrix(table of numbers)        |m = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]                        |
|3   |3-Tensor(cube of numbers)       |t = [[[2], [4], [6]], [[8], [10], [12]], [[14], [16], [18]]] |
|n   |n-Tensor(you get the idea)      |....
    
    
    
- **셰이프(_Shape_)**
    - TensorFlow 문서는 tensor 차원을 표현할 때 세 가지 기호를 사용한다. rank, shape, 차원수. 아래 표는 그 세 가지의 관계를 보여준다
    - Shape는 Python 리스트 / 정수형 튜플 또는 TensorShape class로 표현 할 수 있다.
    - 셰이프는 각 차원의 요소개수로, 텐서의 구조를 설명해준다.
|Rank |Shape              |Dimension number|Example                                 |
|-----|-------------------|----------------|----------------------------------------|
|0    |[]                 |0-D             |A 0-D tensor. A scalar.                 |
|1    |[D0]               |1-D             |A 1-D tensor with shape [5].            |
|2    |[D0, D1]           |2-D             |A 2-D tensor with shape [3, 4].         |
|3    |[D0, D1, D2]       |3-D             |A 3-D tensor with shape [1, 4, 3].      |
|n    |[D0, D1, ... Dn-1] |n-D             |A tensor with shape [D0, D1, ... Dn-1]. |


2. 자료형(_Data Types_)
- Tensor는 차원 말고도 데이터 타입도 갖는다. 아래의 데이터 타입을 tensor에 지정할 수 있다.

|Data type     |Python type   |Description                                |
|--------------|--------------|-------------------------------------------|
|DT_FLOAT      |tf.float32    |32 비트 부동 소수.                             |
|DT_DOUBLE     |tf.float64    |64 비트 부동 소수.                             |
|DT_INT8       |tf.int8       |8 비트 부호 있는 정수.                          |
|DT_INT16      |tf.int16      |16 비트 부호 있는 정수.                         |
|DT_INT32      |tf.int32      |32 비트 부호 있는 정수.                         |
|DT_INT64      |tf.int64      |64 비트 부호 있는 정수.                         |
|DT_UINT8      |tf.uint8      |8 비트 부호 없는 정수.                          |
|DT_STRING     |tf.string     |가변 길이 바이트 배열. Tensor의 각 원소는 바이트 배열. |
|DT_BOOL       |tf.bool       |불리언.                                      |
|DT_COMPLEX64  |tf.complex64  |2개의 32 비트 부동 소수로 만든 복소수 : 실수부 + 허수부 |
|DT_COMPLEX128 |tf.complex128 |2개의 64 비트 부동 소수로 만든 복소수 : 실수부 + 허수부 |
|DT_QINT8      |tf.qint8      |8 비트 부호 있는 정수로 quantized Ops에서 사용.     |
|DT_QINT32     |tf.qint32     |32 비트 부호 있는 정수로 quantized Ops에서 사용.    |
|DT_QUINT8     |tf.quint8     |8 비트 부호 없는 정수로 quantized Ops에서 사용.     |


3. 변수

4. 연산

5. 그래프
- 그래프 생성
- 그래프 실행
- 지연 실행

6. 플레이스홀더

## 텐서와 그래프 실행

1. 텐서플로우를 사용하기 위해 텐서플로우 라이브러리 import
```markdown
import tensorflow as tf
```

2. tf의 클래스 사용
- tf.constant: 말 그대로 상수이다.
- hello 변수에 tf.constant로 상수를 저장.(문자열)
```markdown
hello = tf.constant('Hello, TensorFlow!')
print(hello)
```

- 위까지 코드의 실행결과
    - hello 변수의 출력 결과로 텐서자료형을 보여준다. 상수constant와 shape가 값이 없는 real number(scalar)로 구성되어 있고 string type을 나타낸다.
```markdown
Tensor("Const:0", shape=(), dtype=string)
```


3. 텐서를 이용한 연산(함수)
- 변수 c는 a,b를 이용하여 덧셈 연산을 하는 텐서이다.
```markdown
a = tf.constant(10)
b = tf.constant(32)
c = tf.add(a, b)
print(c)
```

- 위 코드의 실행결과
    - c텐서를 출력한 결과로 Add연산과 스칼라, 정수형(int32)
```markdown
Tensor("Add:0", shape=(), dtype=int32)
```

4. 그래프 생성 및 실행
- 텐서들의 연산 모음을 그래프라 할 수 있다.
- 텐서들을 정의한 후 그래프를 만든 후 필요한 코드를 넣고 원하는 시점에 실제 연산을 수행하도록 한다.(=지연 연산)
- 그래프의 실행은 세션(_Session_)에서 이루어져야한다.
- Session 객체와 run 메서드를 이용
```markdown
sess = tf.Session()

print(sess.run(hello))
print(sess.run([a, b, c]))

sess.close()
```

- 위 코드의 실행결과
    - print(sess.run(hello)) : hello를 세션에서 실행하여 저장된 문자열을 출력한다.
    - print(sess.run([a, b, c])) : a, b, c로 구성된 그래프를 세션에서 실행하여 정수값들을 출력한다.
```markdown
b'Hello, TensorFlow!'
[10, 32, 42]
```

5. 전체코드
```markdown
# 텐서플로우의 기본적인 구성을 익힙니다.
import tensorflow as tf

# tf.constant: 말 그대로 상수입니다.
hello = tf.constant('Hello, TensorFlow!')
print(hello)

a = tf.constant(10)
b = tf.constant(32)
c = tf.add(a, b)  # a + b 로도 쓸 수 있음
print(c)

# 위에서 변수와 수식들을 정의했지만, 실행이 정의한 시점에서 실행되는 것은 아닙니다.
# 다음처럼 Session 객제와 run 메소드를 사용할 때 계산이 됩니다.
# 따라서 모델을 구성하는 것과, 실행하는 것을 분리하여 프로그램을 깔끔하게 작성할 수 있습니다.
# 그래프를 실행할 세션을 구성합니다.
sess = tf.Session()
# sess.run: 설정한 텐서 그래프(변수나 수식 등등)를 실행합니다.
print(sess.run(hello))
print(sess.run([a, b, c]))

# 세션을 닫습니다.
sess.close()
```
