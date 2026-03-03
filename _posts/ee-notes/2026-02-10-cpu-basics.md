---
title: CPU Basics
category: EE
subcategory: Architecture
tags: [CPU, Architecture]
---

## What is a CPU?

Central Processing Unit (CPU) 중앙처리장치 
- 컴퓨터 중앙에서 모든 data를 처리하도록 각 구성들에게 명령을 내리는 장치
- 입력받은 내용 해석>연산>결과 출력
- transistor(반도체)로 만들어짐(transistor - pnp/npn에서 특정 전압을 가해서 스위치 역할을 해주는 반도체, 이를 이용해 logic gate 만들 수 있)

- CPU 성능 파악의 척도
    - 높은 clock(동일 코어수, thread 수, 동일 캐시 메모리의 경우)
    - multicore - core 다다익선
    - cache memory - 용량이 클 수록 좋다
    - 보통 core가 적은 cpu일 때 clock 수가 높음(둘 다 높을 경우 발열 등의 issue로 관리가 힘듦)
  
- 용어 정리
    - clock: core 하나 당 일의 처리 속도(요리사의 속도)
    - core: cpu 안에서 물리적 연산을 담당하는 곳(요리사) - 코어 수 증가 -> 일 처리 속도 증가
    - thread: 운영체제(os)에서 인식하고 작동하는 작업 단위(화구 1개) - 코어 하나당 2개로 성능 향상
    - cache memory: 속도가 빠른 장치와 느린 장치 사이에서 속도 차이에 따른 병목 현상을 줄이기 위한 범용 메모리 (상대적으로 빠른 cpu가 상대적으로 느린 system memory로 넘어갈 때 수용하기 힘든 속도로 정보가 몰려 병목현상 발생. 도로로 예를 들면 4차선>3차선>2차선>1차선 하는 식으로 점차적으로 data 를 줄어들게 함)

## Core Components
- ALU(Arithmetic Logic Unit) 산술 논리연산 장치 - 계산 수행
  cpu 안에서 실제 계산 수행하는 핵심 부품(산술연산 + 논리연산)
  cpu의 계산엔진(프로그램 실행, 조건문 판단, 반복문 비ㅣ교, 주소 계산, 암호 연산 등)

  내부 구성:
  Adder(계산기), Logic gates(ANDm OR 등), Shifter, Comparator 같은 combinational logic circuit
  결국 transistor > logic gate > combinational logic circuits > alu > cpu
  
  
- Control Unit 제어장치 - 명령해석, 모든 부품에 제어 신호 보
  아래의 Execution Flow 과정 지휘함, control signal 만들어 다른 부품 움직임
  Hardwired control / Microprogrammed Control

- Registers - 임시 저장소 in CPU
  연산 데이터,ALU 결과, instruction, address, state 저장
  여러 종류...
  ( general purpose register - 계산용 데이터 저장
  program counter(PC) - 다음에 실행할 명령어 주소 저장
  instruction register(IR) - 현재 실행중인 명령어 저장
  memory address register(MAR) - 접근할 메모리 주소 저장
  memory data register(MDR) - 메모리에서 읽은 데이터 저장
  status register(flag register) - 연산 결과 상태 저장 ~~flag)

  * hw 관점 - 여러 개의 flip-flop으로 구성, clock에 맞춰 동작
    transistor > logic gate > flip-flop > register
  
  
## Execution Flow
Fetch → Decode → Execute
가져오기 > 해석 > 실행 지시

Fetch : 메모리에서 instruction read / pc 가 가리키는 주소에서 cmd 로드
Decode : 명령어가 뭔지 분석 / ADD? LOAD? JUMP?
Execute :  실행 지시 / ALU에 계산 시키거나 memory에 write 명령, registor 이동 지시, pc 변경 지시 

## Instruction Cycle
Fetch > Decode > Execute > Write-back > PC update
시각적 이해를 돕기 위한 영상: https://youtu.be/Z5JC9Ve1sfI?si=cFchKc0EHqrIhj7a

