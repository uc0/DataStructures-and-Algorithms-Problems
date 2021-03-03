## 시간 복잡도

#### 알고리즘 문제를 해결할 때 효율성

- **수행 시간** > 사용한 메모리
- 코드가 짧다고 해서 시간이 짧게 걸리는게 아님
- 알아보기 쉽게 작성
- **우선적으로 문제의 크기를 파악**하여 알맞은 방법 선택하여 해결



#### 시간 복잡도(Big-O)

- **최악의 경우**에 얼마나 걸릴지 예상할 수 있음
- 1억 대략 1초
- 상수는 신경쓰지 않음
  - O(5N^3) = O(N^3)
  - O(12) = O(1)
- 두 가지 항이 있을 때, 변수가 같으면 큰 것만 빼고 나머지를 제외
  - O(N^2 + NlgN) = O(N^2)
- 두가지 항이 있을 때, 변수가 다르면 놔둠



- **O(1) > O(lgN) > O(N) > O(NlgN) > O(N^2) > O(N^3) > O(2^N) > O(N!)**





## 유의할 점

- 입력 속도 비교 자료
  - 10,000이하의 자연수 10,000,000개가 적힌 파일을 입력받는데 걸리는 시간
  - https://www.acmicpc.net/blog/view/56
- 출력 속도 비교 자료 
  - 1부터 10 ,000 ,000까지 자연수를 한 줄에 하나씩 출력하는 시간
  - https://www.acmicpc.net/blog/view/57
  - 

#### C++

- scanf/printf, cin/cout

  - cin/cout의 경우 아래 세 줄을 추가하면 scanf/printf 만큼 빨라짐

    ```c++
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);
    ```

  - 이 경우에는 cin/cout만 사용! scanf/printf 금지..

- endl 대신에 '\n'을 사용

- 문자열 주의할 점!

  ```c++
  #include <iostream>
  #include <string>
  using namespace std;
  
  int main() {
      string s;
      string t;
      int n = 1000000;
      
      for (int i=0;i<n;i++) {
          s += "A";	// O(n) +=연산을 n번 수행
          t = t + "A";	// O(n^2) 매번 새로운 문자열을 생성
      }
      
      return0;
  }
  ```

  - C++에서 string 의 += 연산은 O(K)
  - C++에서 string 의 + 연산은 O(N+K)



#### Java

- 입력은 Scanner, 출력은 System.out을 사용

  ```java
  Scanner sc = new Scanner(System.in);
  ```

  - 자료형에 따라 알아서 입력을 받아줌
  - 편리한 대신 속도가 느림

- 입력이 많은 경우에는 속도가 느리기 때문에, BufferedReader를 사용

  ```java
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
  ```

- 출력이 많은 경우에는 StringBuilder를 사용해서 한 문자열로 만들어서 출력을 한 번만 사용하거나 BufferedWriter를 사용

- 문자열 주의할 점

  ```java
  import java.util.*;
  
  public class Main{
      public static void main(String args[]) {
          String s = "";
          int n = 1000000;
          
          for(inti=0;i<n;i++) {
              s += "A";	// O(n^2) Java는 +=연산도 새로운 문자열 생성
          }
      }
  }
  ```

  - Java에서 String 의 += 연산은 O(N+K)
  - Java 의 경우 StringBuilder를 이용



#### Python

- Python은 입력은 input, 출력은 print를 사용
- 입력이 많은 경우에는 속도가 느리기 때문에,`sys.stdin.readline()`를 사용
- 출력이 많은 경우에는 한 문자열로 만들어서 출력을 한 번만 사용

- Python 각 연산의 시간 복잡도

  ```python
  a = list(range(1, 10000001))
  
  a = a + [1000001] # 리스트를 합칠 때 O(N)
  
  a.append(1000001) # append 사용 O(1)
  
  a = a + [1,2,3] # O(N+K) K는 더하는 배열의 수
  a.extend([1, 2, 3]) # O(K)
  a += [4, 5, 6] #O(K) 리스트인 경우 자동으로 append 함수처럼 수행
  
  if 10 in a: # O(N)
      print(1)
      
  print(len(a)) # O(1)
  ```

  



#### 문자열

- strlen(s)의 시간 복잡도는 O(s의 길이)

  `for (int i=0; i<strlen(s); i++)` 반복 조건문 안에 함수 사용 유의!

- C++ string의 .length() 와 Java String의 .length(), Python의 len은 **O(1)**

- `=+`의 실행 시간은 추가하려고 하는 문자열의 크기

