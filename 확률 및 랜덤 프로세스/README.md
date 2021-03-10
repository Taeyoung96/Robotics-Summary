# 확률 및 랜덤 프로세스  

## Contents
- [Definitions of Probability](#Definitions-of-Probability)  


## Definitions of Probability  

확률의 기본적인 용어를 정리하고 확률의 정의에 대해서 알아보자.  
- 집합 : Set  
- 부분 집합 : Subset - 원소의 갯수가 N개일 때, 가질 수 있는 부분집합의 갯수 2^n개  
- 진부분집합 : Proper subset (부분집합 중 A = B가 아닌 다른 부분집합, 출처 : [위키백과](https://ko.wikipedia.org/wiki/%EB%B6%80%EB%B6%84%EC%A7%91%ED%95%A9))  
- 상호 베타적인 관계 : Disjoint or Mutually exclusive (두 집합의 관계에서 공통된 원소가 존재하지 않을 때)  
- 주어진 상황에서 가장 큰 집합 : Universal Set  

### 집합을 구분하는 방법  

**Countable vs Uncountable**  

- Countable : 원소들이 자연수와 일대일 대응이 가능한 집합  
- Uncountable : 원소들이 자연수와 일대응 대응이 되지 않는 집합  
- Empty : 원소가 없는 집합 (= null set), **주의, A = {0}은 empty set이 아니라 원소가 0인 집합**  


**Finite vs Infinite**  

- Finite : 집합이 비어있거나, 원소의 갯수가 유한할 때(셀 수 있을 때)  
- Infinite : 원소의 갯수가 무한할 때(셀 수 없을 때)  

Ex ) 정수의 집합을 Z라 할 때, 이 집합은 Countable, inifinite  
(자연수의 집합으로 정수의 집합과 일대응 대응이 가능하고, 원소의 갯수를 셀 수 없다.)  
유리수의 집합 Q라 할 때, 이 집합은 Countable, infinite  
실수의 집합 R이라 할 때, 이 집합은 Uncountable, infinite  

---  

### 집합 기호

- 합집합 : Union (= sum)  
- 교집합 : Intersection (= product) - mutually exclusive일 때 교집합은 공집합이다.  
- 여집합 : Complement  
- 집합의 연산 법칙 (벤 다이어그램으로 증명)  
    1. 교환 법칙 (The commutative law)  
    2. 분배 법칙 (The distributive law)  
    3. 결합 법칙 (The associatove law)  
    4. 드모르간 법칙 (De Morgan's law)  
    5. 쌍대성 원리 (Duality principle) - 참고 : [쌍대성](https://gazelle-and-cs.tistory.com/17)  

### 확률의 정의  

- 이론에 의한 정의
- 실험을 통한 상대적인 빈도수에 의한 정의  
- Sample space S : 실험을 통해 나올 수 있는 모든 경우의 수 (Discrete and continous sample spaces)  
- Event : sample space의 부분 집합  
- 확률 : **어떤 Sample sapce S에서 event가 발생할 수 있는 가능성 (확률은 함수로 정의)** - Relative frequency ([상대 도수](https://m.blog.naver.com/PostView.nhn?blogId=mathfiend&logNo=220507086937&proxyReferer=https:%2F%2Fwww.google.com%2F))를 이용하여 정의할 수 있다.  
- 만족해야 하는 3가지 법칙  

 <p align="center">
 <img width="400"  src="Image/image1.JPG">
 </p>
  
- 실험을 통한 수학적 모델  

 <p align="center">
 <img width="550"  src="Image/image2.JPG">
 </p>

- Joint probability : A의 event와 B event가 동시에 일어날 확률 = (A와 B 교집합이 일어날 확률)  
 
 <p align="center">
 <img width="550"  src="Image/image3.jpg">
 </p>
 
 A와 B가 Mutually exclusive 관계일 때 위 그림에서 등호가 성립한다.  

- **조건부 확률 (Conditional probability)** - Event B가 일어날 확률이 0보다 클 때, Event A가 일어날 확률을 Event B가 일어날 확률을 고려하여 구하는 확률  
 <p align="center">
 <img width="250"  src="Image/image4.jpg">
 </p> 
 
 - 만족하는 3가지 법칙
<p align="center">
<img width="350"  src="Image/image5.jpg">
</p> 
 
 - 대표적인 조건부 확률 문제 : [몬티홀 문제 설명 블로그](https://tali.tistory.com/1113)  

- 전체 확률의 법칙 (Total probability) : 조건부 확률로부터 조건이 붙지 않은 확률을 계산할 때 사용  
<p align="center">
<img width="550"  src="Image/image6.jpg">
</p> 

위와 같은 조건을 만족해야한다.  

<p align="center">
<img width="300"  src="Image/image7.jpg">
</p> 

- **베이지안 확률 (Bayes’ theorem)** : p(B_n) 과 𝑝(𝐴|𝐵) 을 알고 있다고 할 때, 다음과 같은 식이 성립한다.  

<p align="center">
<img width="400"  src="Image/image8.jpg">
</p> 

베이즈 정리는 근본적으로 사전확률과 사후확률 사이의 관계를 나타내는 정리이다.  

- 참고자료 : [베이즈 정리의 의미](https://angeloyeo.github.io/2020/01/09/Bayes_rule.html)  

- 독립 사건 (Independent Event) : 𝑝(𝐴) ≠ 0 𝑎𝑛𝑑 𝑝(𝐵) ≠ 0 일 때,  
𝑝(𝐴|𝐵) = 𝑝(𝐴), 𝑝(𝐵|𝐴) = 𝑝(𝐵), 𝑝(𝐴 ∩ 𝐵) = 𝑝(𝐴)𝑝(𝐵)를 만족한다.  

- Multiple events : N개의 events에서 Multiple events의 경우의 수는 2^n - N - 1이다.  
(N은 하나만 뽑는 갯수, 1은 아무것도 안 뽑는 갯수)


 [위로](#Contents) / [뒤로](https://github.com/Taeyoung96/Robotics-Summary)   
