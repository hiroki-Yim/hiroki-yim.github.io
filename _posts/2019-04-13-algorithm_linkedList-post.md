---
title: "LinkedList의 특성과 ArrayList와의 차이"
date: "2019-04-13 20:10:00"
categories: study algorithm dataStructure
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "Index" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

# Linked list

![image](https://user-images.githubusercontent.com/33077726/56078921-65bb7e80-5e28-11e9-81f5-d71a472e890f.png)

Linked List - 연결된 리스트
Linked List는 pointer 또는 참조값(next)로 값을 가져오기 때문에 메모리가 허용하는 한 node를 무한대로 키울 수 있다.
즉, List의 크기가 확정적이지 않다. (기본적인 장점)

## ArrayList와의 차이(trade off 관계)

ArrayList의 경우에는 배열(array)라고 하는 융통성 없는 data structure 사용하고 있기 때문에

데이터를 추가하게 됬을 시, array가 갖고 있는 크기를 넘어서면 error가 발생한다.

![image](https://user-images.githubusercontent.com/33077726/56077358-284df580-5e16-11e9-9790-5b4bbdd3851c.png)

ArrayList - element(node)들이 같은 곳에 모여있음 (엑세스 속도가 빠름)

LinekdList - element(node)들이 흩어져 있고 **서로 연결(link)되어 있음** (맨 끝 노드를 찾기 위해 처음 노드부터 탐색하기 때문에 전자보다 느림)

- Linked List
  ![image](https://user-images.githubusercontent.com/33077726/56077360-36037b00-5e16-11e9-883e-f2f1a1f5f337.png)

### ArrayList와 LinkedList의 핵심적인 차이

1. Array의 경우 element를 중간에 add/delete 할 경우 해당 element 뒤에 있는 **모든 element의 자리 이동이 필요함.**
   그래서 Array는 add/delete가 느림

2. LinkedList의 경우 add/delete 될 element의 이전, 이후 노드의 **참조값(next)만 변경하면 됨.**
   때문에 속도가 빠름

3. 그림으로 이해하는 차이
   ![image](https://user-images.githubusercontent.com/33077726/56078486-87fecd80-5e23-11e9-8a1e-b4820be97fcd.png)

**간략하게**

- ArrayList 는 Random Access Memory(Ram)을 사용한 조회로 index조회가 빠름
- head의 next의 next의 next를 찾아야 해서 느림

## 구조

![image](https://user-images.githubusercontent.com/33077726/56077366-47e51e00-5e16-11e9-8f88-150f3cc6c09c.png)

- 하나의 노드에 두 개의 필드(변수)가 있다.

1. 첫 번째 변수는 저장되는 **값(data)**
2. 두 번째 변수(Link Field)는 **다음 노드의 정보**

첫번 째 **노드가 무엇인가를 HEAD필드가 가지고 있다.**

객체 지향에서는 **객체에 데이터 필드(value)와 링크 필드(next)를 만들어서 구현**한다.

## Head

### 데이터의 추가

### 시작(head) 부분에 추가 (add)

```java

Vertex temp = new Vertex(input) // 1.새로운 노드 생성

temp.next = head    // 2.새로운 노드의 다음 노드로 첫번째 노드를 가르킴.

head = temp         // 3.새로 만들어진 노드가 첫번째 노드가 되도록 head의 값을 변경함.

```

- 그림으로 보는 1~3번 까지의 과정

1. ![image](https://user-images.githubusercontent.com/33077726/56077503-02c1eb80-5e18-11e9-96af-67fdca9331d3.png)
2. ![image](https://user-images.githubusercontent.com/33077726/56077509-05244580-5e18-11e9-91ba-42aaeb78bb0d.png)
3. ![image](https://user-images.githubusercontent.com/33077726/56077511-08b7cc80-5e18-11e9-923f-d8b32618bf3c.png)

### 특정한 위치(k)에 있는 Element 추가하기(add)

```java

Vartex temp1 = head
// 1. head를 참조해서 첫번째 노드를 찾는다.

// 23의 자리에 새로운 노드를 위치시키기 위해서 6이 어디있는지 알고 있어야 한다.
// (6의 next를 이용해서 새로운 노드를 지정해야하기 때문)
while (--k!==0)
// 2. k가 0이 될 때 까지 다음 노드의 next값을 temp1에 저장한다.
    temp1 = temp1.next

Vertex temp2 = temp1.next
//3. next를 이용하여 temp2에 다음 노드값을 저장
Vertex newVertex = new Vertex(input)
//4. 값이 n인 새로운 node를 생성한다.
temp1.next = newVertex
//5. 前node의 next가 추가되는 node를 가르키게 한다.
newVertex.next = temp2
//6 추가된 node의 next가 後node를 가르키게 한다.

```

이렇게 前과 後노드 사이에 새로운 노드를 위치 시킬 수 있다.

- 그림으로 보는 1~6번 사이의 과정(3번째 자리(indexnum2)에 90을 추가하는 예제)

![image](https://user-images.githubusercontent.com/33077726/56077617-4e28c980-5e19-11e9-8710-4f129983db48.png)
![image](https://user-images.githubusercontent.com/33077726/56077618-508b2380-5e19-11e9-9064-dc4292f4f38b.png)
![image](https://user-images.githubusercontent.com/33077726/56077795-49fdab80-5e1b-11e9-81eb-92b58b5efc8f.png)
![image](https://user-images.githubusercontent.com/33077726/56077796-4b2ed880-5e1b-11e9-96f6-f06a149e4790.png)
![image](https://user-images.githubusercontent.com/33077726/56077799-4cf89c00-5e1b-11e9-8956-7445534fa530.png)
![image](https://user-images.githubusercontent.com/33077726/56077801-508c2300-5e1b-11e9-9b68-9316e9c47757.png)
![image](https://user-images.githubusercontent.com/33077726/56077802-51bd5000-5e1b-11e9-980f-d6c932900856.png)
![image](https://user-images.githubusercontent.com/33077726/56077803-53871380-5e1b-11e9-9b75-48f07bbcedde.png)

#### 이렇게 해서 90을 3번째 인덱스에 위치시킬 수 있다.

### 특정한 위치(k)에 있는 Element 삭제하기(delete)

```java
Vertex current = head
//1. head를 이용해 시작점(첫번째 노드)를 찾는다.

while (--k!==0)//k가 0이 아니면
    current = current.next
    //2. 두번 째 노드로 이동

Vertex toBeDeleted = current.next
//3. 이동이 끝나면, 이동한 노드 다음 노드를 삭제하기 전 변수에 담는다. 삭제해버리면 다음 노드의 정보(next)를 알 수 없기 때문.

current.next = current.next.next
//4. 삭제할 node의 next를 현재 노드의 next에다가 넣어준다.

delete toBeDeleted
//5. 삭제할 node의前 node의 next가 삭제할 node의 後node의 next로 바뀌었다면 삭제한다.

```

### 인덱스를 이용한 데이터 조회

k번째 노드를 가져오고 싶다면(k번째 노드를 찾고 싶다면?)

1. head를 통하여 (첫번째) 노드의 값이 4인지 확인한다.
2. 아니면 next를 이용하여 다음 노드의 값을 확인한다. (k번째 값이 나올때까지 반복!)
3. 해당 값이 k번째 노드의 값이 맞다면 그 값(value)를 return 해준다.

```java

Vertex temp1 = head     //1. 해당 node의 첫번째 node를 가르킨다.

while (--k!==0)         //2. 찾고자 하는 node의 index만큼 이동한 뒤
    temp1 = temp1.next  //3. 참조값(next)를 변수에 저장한다.

return temp1.value      //4. 해당 node의 값을 return 해준다.

```

- 그림으로 이해하는 1~4번 까지의 과정
  ![image](https://user-images.githubusercontent.com/33077726/56078721-66531580-5e26-11e9-98ff-61735e30adff.png)
  ![image](https://user-images.githubusercontent.com/33077726/56078724-68b56f80-5e26-11e9-8259-6656c6b7bf96.png)

  1. 인덱스를 이용해서 데이터를 조회할 때 linked list는 head가 가리키는 노드부터 시작해서 순차적으로 노드를 찾아가는 과정을 거쳐야 한다.
     만약 찾고자 하는 엘리먼트가 가장 끝에 있다면 모든 노드를 탐색해야 한다.
  2. 반면에 array를 이용해서 리스트를 구현하면 인덱스를 이용해서 해당 엘리먼트에 바로 접근 할 수 있기 때문에 매우 빠르다.
     그 이유는 컴퓨터의 내부적인 메커니즘 때문이다.

### 용어 설명

#### Trade Off

트래이드 오프는 어떤 특성이 좋아지면 다른 특성이 나뻐지는 상황을 의미한다.

**array list와 linked list는 트레이드 오프의 좋은 사례**라고 할 수 있다.

데이터 스트럭쳐를 배우는 이유 중의 하나는 이러한 트레이드 오프를 이해하기 위해서다.

장점과 단점의 미묘한 균형을 이해할 수 있어야 올바른 선택을 할 수 있기 때문.

### 참고한 사이트

[자료구조의 이해를 돕는 사이트](https://visualgo.net/en/list?slide=1)

[openTutorials dateStructure](https://opentutorials.org/module/1335)
