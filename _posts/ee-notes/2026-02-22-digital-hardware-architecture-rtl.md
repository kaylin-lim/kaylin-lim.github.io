1. HDL (Hardware Description Language)

HDL은 Hardware Description Language의 약자다.
예전에는 하드웨어 회로를 손으로 그리고 설계했지만, 집적도가 매우 높아지면서 컴퓨터 기반으로 설계하게 되었고, 이를 위해 사용하는 언어가 HDL이다.

대표적인 HDL: Verilog, VHDL, SystemVerilog (앞으로 스터디할 것)

SystemVerilog는 Verilog를 확장한 언어로, 설계뿐 아니라 검증(verification)까지 포함한다.
이러한 설계를 지원하는 회사들이 EDA 회사다.
EDA = Electronic Design Automation
반도체 설계 자동화 툴을 만드는 회사

대표적인 EDA 회사: Cadence, Synopsys, Siemens EDA (Mentor)


2. 트랜지스터 기본 구조

MOSFET(Metal-Oxide-Semiconductor Field-Effect Transistor):
전압으로 전류를 조절하는 스위치/증폭기 역할을 하는 반도체 소자
Gate에 전압을 주면 Source-Drain 사이에 전류가 흐를지 말지를 결정하는 전자 스위

MOSFET 트랜지스터 기본 구성:

VDD: 전원 (양전압) - 회로에 에너지 공급 - 주로 Drain에 연결
GND: 접지 (0V 기준) - 주로 Source에 연
Gate - 전압 입력하는 곳
Source - 전류가 들어오는 
Drain - 전류가 나가는 

(헷갈렸던 부분: VDD가 p형 반도체고 GND가 n형 반도체인 것은 아니다. 트랜지스터 자체가 p형, n형 반도체로 구성된다.
ex. NMOS: p형 기판 위에 n+ 영역 (source/drain), PMOS: n형 기판 위에 p+ 영역)

Gate에 전압을 주면, 채널이 형성되어 Source와 Drain 사이로 전류가 흐른다. - 이것이 “반도체”의 의미: 전류가 conditionally 흐름.


3. Oscillator
   
Oscillator는 클럭(clock)을 생성하는 회로다.

CPU나 디지털 회로는 클럭 신호(틱-틱-틱 하는 기준 신호)에 맞춰 동작
그래서 oscillator는 시스템 전체의 동작 타이밍을 정해주는 매우 중요한 회로


4. 웨이퍼 위에 그리는 것 = 공정

Gate, Source, Drain 등을 웨이퍼 위에 패터닝하는 과정이 반도체 공정이다.

공정 단계 예시: 산화, 포토리소그래피, 식각, 이온주입, 증착, CMP

이 과정을 반복해 수십억 개의 트랜지스터를 집적한다.


5. 반도체는 매우 많은 트랜지스터의 집합

현대 CPU는 수십억 개 이상의 트랜지스터로 구성된다.
이 트랜지스터들이 모여: 논리 게이트, 플립플롭, 레지스터, 캐시, ALU, 코어 등을 구성한다.

논리 게이트 - 전기 신호(0/1)를 입력받아 새로운 0/1 출력하는 가장 기본적인 회로
flip-flop - 1bit 저장하는 회로. 클럭 신호에 맞춰 값을 저장하는 memory 기능
register - 여러 개의 flipflop 묶은거. cpu안에서 가장 빠른 저장공간으로 연산시 데이터 잠시 보
cache - cpu와 ram 사이의 고속 메모리로 자주 쓰는 데이터를 임시 저장함. 
ALU(Arithmetic Logic Unit) - 덧셈, 뺄셈, AND, OR 같은 연산 수행 장치, CPU의 계산기
Core - 하나의 독립적인 연산 처리 유닛(alu, register, L1 cache, 제어장치, pipeline 등으로 구성)


6. YAPP Router

YAPP: 내가 배우는 RTL 설계 예제용 Router

Router의 역할:
입력 포트로 들어온 데이터를 적절한 출력 포트로 전달하는 것

즉, 내부적으로: 
패킷을 받고 - 목적지 정보를 읽고 - 해당 output port로 스위칭

CPU 전체에서 아주 큰 부분은 아니지만 SoC 내부 통신 구조에서는 매우 중요한 블록


7. CPU 동작 구조

CPU는 명령어(instruction)를 받아 실행한다.

기본 동작 흐름: Instruction Fetch - Decode - Execute - Memory Access - Write Back

IP = Intellectual Property

반도체 설계에서 IP란: 재사용 가능한 기능 블록

예: UART IP, Ethernet IP, Memory Controller IP, PCIe IP
(헷갈렸던 내용: IP는 단순 부품이 아닌 설계 블록)


8. Bus란?

Bus는 데이터가 이동하는 통로

종류: Address Bus, Data Bus, Control Bus

CPU가 DRAM에 접근, 주변장치(IP)와 통신, Ethernet 통해 외부와 통신할 때 사용하는 내부 통신 구조가 Bus


9. APB란?

APB = Advanced Peripheral Bus, ARM AMBA 규격 중 하나. 버스 프로토콜

AMBA 계열: AXI (고성능), AHB (중간), APB (저속, 단순한 주변장치용)

APB는 저속 주변장치 제어용 프로토콜


10. Layer 개념 정리

  1) OSI 네트워크 레이어
  - Physical Layer
  - Data Link Layer
  - Network Layer
  - Transport Layer
  - Application Layer

  2) 시스템 추상화 레이어

  하드웨어와 소프트웨어는 여러 레이어로 구성된다:

  Physical Layer → Transistor

  Logic Layer → Gate, Flip-flop

  Microarchitecture → Pipeline, ALU

  ISA Layer → Instruction Set

  Operating System

  Application

  API는 보통 상위 소프트웨어 레이어에서 제공된다.


Layer는 시스템을 계층적으로 나눈 개념이다.
