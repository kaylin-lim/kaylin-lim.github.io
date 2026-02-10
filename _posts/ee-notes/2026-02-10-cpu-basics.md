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
- transistor라는 반도체로 만들어짐(transistor - pnp/npn에서 특정 전압을 가해서 스위치 역할을 해주는 반도체, 이를 이용해 logic gate 만들 수 있)

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
- ALU
- Control Unit
- Registers

## Execution Flow
Fetch → Decode → Execute

## What I Learned
- CPU is not just “compute”
- Control logic dominates complexity

## Next
→ Hardware interfaces & memory hierarchy
