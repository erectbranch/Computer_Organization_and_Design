# 1 Computer Abstractions and Technology

## 1.1 컴퓨터의 응용 분야와 특성

컴퓨터는 크게 세 가지 응용 분야에서 사용된다.

- PC(Personal Computer)

- Server

    보통 network를 통해서만 접근되고, 대형 작업을 수행하기 위해 사용한다. 주로 특정한 기능을 수행할 수 있도록 customized되는 경우가 많다.

    > 고장이 나면 PC와는 비교할 수 없이 큰 손해가 발생하므로, 일반적으로 dependability(신용도)를 중요시한다.

    > 수만 개의 processor와 굉장히 큰 memory를 가진 슈퍼컴퓨터도 server에서는 작은 부분에 해당된다.

- embedded system

    오늘날 가장 많이 사용되고 있으며, 보통은 한 가지 application을 수행하거나 연관된 일련의 application을 수행하도록 설계된다.

    > embedded system에서 구현되는 software를 firmware라고 한다. 하지만 PC의 software와 다르게, firmware는 hardware의 논리적인 부분을 보강 및 대신할 수 있게 구현한다.(OS의 기능을 대신하므로 일종의 OS로도 볼 수도 있다.)

    > 요즘은 firmware를 수정이 가능한 PROM이나 flash에 저장하므로, 기능의 update가 필요하면 firmware를 수정해서 update를 한다.

    > 최근의 Embedded System은 processor를 대부분 가지고 있으며, processor의 OS를 사용해서 이더넷에 접속할 수 있다.

---

## 1.2 performance에 영향을 끼치는 요소

컴퓨터의 performance에 영향을 끼치는 몇 가지 hardware 혹은 software 구성 요소는 다음과 같은 것들이 있다.

- algorithm: I/O 작업 수, source program 문장 수, complexity 등을 결정한다.

    > 다양한 sorting altorithm을 떠올리면 알 수 있다.

- programming language: C, Java, Python 등. machine code 수를 결정한다.

- processor, memory system: instruction의 실행 속도를 결정한다.

- I/O system: I/O 작업의 속도를 결정한다.

이외 여러 parallelism과 memory hierarchy 최적화(cache blocking 등)와 같은 기법으로 performance를 더 향상시킬 수 있다.

---

## 1.3 compiler

**compiler**는 C, C++, Java 등 high level language를 machine code로 변환하는 역할을 수행한다.

- High-level language(C) -> Assembly language -> Machine language

처음 컴퓨터는 binary digit, 즉 **bit**를 사용해서, bit들의 집합인 **instruction**을 만들어 지시를 내렸다. 하지만 이런 과정은 너무나 복잡했기 때문에 사람이 생각하는 것과 비슷한 표시 방법을 고안했고, 이 작업을 수행하도록 만든 program이 바로 **assembler**(어셈블러)였다.

예를 들어 `add A, B`를 assembler에게 주면, assembler는 이를 `100101010010110`과 같은 machine language로 변환한다.

> 다른 machine language를 사용하는 processor도 opcode의 실제 bit pattern은 다르겠지만, assembly language에서 `add`와 같이 common한 opcode의 이름 자체는 같을 수 있다.

가장 중요한 **abstraction**(추상화) 중 하나가 바로 hardware와 최하위 software 간의 interfae로, 이를 **ISA**(Instruction Set Architecture) 또는 단순히 **architecture**라고 지칭한다.

---

## 1.4 register, buffer

**register**와 **buffer**는 모두 data를 임시로 저장하는 데 사용하지만 차이점이 있다.

- register: <U>processor 내부의 작은 memory space</U>로, processor에서 바로 access할 수 있다. 

    - 작은 양의 data만 저장할 수 있으며 특히 intermediate value를 저장하기 위해 사용한다.

- buffer: <U>memory</U>에서 data를 임시로 저장하기 위해 사용한다.

    - 주로 data를 다른 곳으로 전송 / data를 처리 / network에서 data를 수신하는 등 여러 작업에서 사용된다.

    - 대표적으로 **cache**가 DRAM의 buffer 역할을 수행하는 작고 빠른 memory이다.

---

## 1.5 performance의 정의

- **response time**(응답 시간) = **execution time**(실행 시간)

    task(작업, operation)의 시작부터 끝까지 걸린 시간. formal하게 **latency**로도 부른다.

- **throughput**(처리량) = **bandwidth**(대역폭)

    일정 시간동안 처리한 일(operation)의 양. 단위로 **FLOPS**(floating point operations per second)를 사용한다.

    > 예를 들어 2GFLOPS 능력을 가진 core가 4개가 있다면, 1초에 8GFLOPS를 처리할 수 있다. 

    > integer operation 단위로는 **TOPS**(tera operations per second)을 주로 사용한다.(주로 Deep Learning에서 볼 수 있다.)

---

### 1.5.1 performance 측정: execution time

그런데 execution time은 여러 방법으로 측정할 수 있다. 

- **wall clock time**(벽시계 시간) = **elaspsed time**(경과 시간)

    한 task를 끝내는 데 필요한 전체 시간. disk/memory access, I/O, OS overhead 등을 모두 포함한다.

    > 주로 리눅스 시간을 사용해서 측정한다.

- **CPU time**(CPU 시간)

    program이 순수하게 해당 program을 시행하는 데 걸린 시간. 즉, I/O나 다른 program을 실행하는 데 걸린 시간은 포함되지 않는다.

또한 거의 모든 컴퓨터는 hardware event가 발생하는 시점을 **clock**을 이용해서 결정한다.

- **clock rate**(frequency)

    cycles/sec. 즉, cycle frequency. [Hz]

- **clock period**(clock cycle time)

    ![clock period](images/clock_period.jpg)

    clock cycle 한 번에 걸리는 시간. 즉, clock cycle의 period. [s] (= 1/clock rate) 

> 예를 들어 1GHz frequency(clock rate)를 갖는 CPU가 있다면, period(clock cycle time)은 1/10^9 = 1ns이다.

따라서 어떤 program이 몇 clock cycles를 사용해서 수행됐는지를 알면, clock cycle time을 곱해서 총 CPU execution time을 구할 수 있는 것이다.

```
CPU execution time = CPU clock cycles * clock cycle time
```

혹은 역수 관계인 frequency로 표시한다면 다음과 같다.

```
CPU execution time = CPU clock cycles / clock rate
```

이 공식으로 알 수 있는 것은, 'execution time'을 줄이기 위해서는(performance 향상을 위해서는) frequency를 늘리거나, clock cycle time을 줄이는 방법이 필요하다는 사실이다.

---

### <span style='background-color: #393E46; color: #F7F7F7'>&nbsp;&nbsp;&nbsp;📝 예제 1: 성능 개선&nbsp;&nbsp;&nbsp;</span>

두 개의 컴퓨터 A, B가 있다. 두 컴퓨터는 같은 프로그램을 실행할 것이다.

- A: 2GHz clock을 갖고, program 실행에 10s가 걸린다.

- B: ? clock을 갖는다.

현재 B clock cycle을 A의 1.2배로 고치면 6s의 시간으로 수행할 수 있다고 한다. 그렇다면 원래 B의 clock은 몇 GHz였을까?

### <span style='background-color: #C2B2B2; color: #F7F7F7'>&nbsp;&nbsp;&nbsp;🔍 풀이&nbsp;&nbsp;&nbsp;</span>

A를 바탕으로 program을 수행하는 데 필요한 clock cycle 수를 계산할 수 있다.

10s \* 2 \* 10^9 Hz = 20 \* 10^9 clock cycles

6s \* 1.2 \* (B clock rate) = 20 \* 10^9 이므로, B clock rate = 4GHz라는 결과를 얻을 수 있다.

---

### 1.5.2 performance 측정: CPI

execution time은 instruction 수와 크게 관련이 있다.

```
CPU clock cycles = instruction 수 * CPI
```

**CPI**(Clock cycles Per Instruction)은 instruction 하나에 필요한 clock cycle의 수를 의미한다. instruction마다 실행 시간이 다르기 때문에, 모든 instruction의 평균 값으로 산출한다.

---

### <span style='background-color: #393E46; color: #F7F7F7'>&nbsp;&nbsp;&nbsp;📝 예제 2: CPI를 이용한 성능 계산&nbsp;&nbsp;&nbsp;</span>

같은 ISA를 사용하는 두 컴퓨터 A, B가 있다.

- A: clock cycle time은 250ps, 어떤 program P에 대한 CPI는 2.0이다.

- B: clock cycle time은 500ps, 어떤 program P에 대한 CPI는 1.2이다.

program P를 실행하는 데 있어서 어떤 컴퓨터가 얼마나 더 빠른가?

### <span style='background-color: #C2B2B2; color: #F7F7F7'>&nbsp;&nbsp;&nbsp;🔍 풀이&nbsp;&nbsp;&nbsp;</span>

ISA가 같으므로 두 컴퓨터가 실행해야 하는 instruction의 총 개수는 같다. 따라서 다음과 같이 간단히 계산할 수 있다.

- A: instruction 수 \* 2.0 = 필요한 clock cycle 수

- B: instruction 수 \* 1.2 = 필요한 clock cycle 수 

execution time은 clock cycle 수 * clock cycle time이므로, 다음과 같이 계산할 수 있다.

- A: instruction 수 \* 2.0 \* 250ps 

- B: instruction 수 \* 1.2 \* 500ps

따라서 A가 B보다 1.2배 더 빠르다. 

---

### <span style='background-color: #393E46; color: #F7F7F7'>&nbsp;&nbsp;&nbsp;📝 예제 3: CPI 비교&nbsp;&nbsp;&nbsp;</span>

어떤 엔지니어는 compiler 설계를 위해 두 가지 방법(1, 2) 중 하나를 선택하려고 한다.

| | | 실행에 필요한 instruction 개수 | |
| :---: | :---: | :---: | :---: | 
| 코드 | A | B | C |
| 1 | 2 | 1 | 2 |
| 2 | 4 | 1 | 1 |

- A는 CPI가 1, B는 CPI가 2, C는 CPI가 3이다.

> CPI가 클수록 더 complex한 instruction이다.

두 코드의 차이를 비교하라. (1) 어떤 코드가 더 많은 instruction을 실행하는가 (2) 어떤 코드가 더 빠른가 (3) 각 코드의 CPI는 얼마인가

### <span style='background-color: #C2B2B2; color: #F7F7F7'>&nbsp;&nbsp;&nbsp;🔍 풀이&nbsp;&nbsp;&nbsp;</span>

(1) instruction 총 개수는 각 A, B, C instruction 개수를 더하면 된다.

- 코드 1: 2 + 1 + 2 = 5

- 코드 2: 4 + 1 + 1 = 6

따라서 절대적인 instruction 개수는 코드 1이 더 적다.

(2) 어떤 코드가 더 빠른가

먼저 instruction마다 필요한 cycle을 도출해 보자.

- 코드 1: 2 \* 1 + 1 \* 2 + 2 \* 3 = 10

- 코드 2: 4 \* 1 + 1 \* 2 + 1 \* 3 = 9

코드 1이 더 사이클이 많으므로 execution time도 더 소요될 것이다. 따라서 코드 2가 instruction 수는 더 많아도 execution time 자체는 더 짧다.

(3) 각 코드의 CPI는 얼마인가

각 코드에 instruction 개수를 나눠서 평균을 구하면 된다.

- 코드 1: 10 / 5 = 2.0

- 코드 2: 9 / 6 = 1.5

---
