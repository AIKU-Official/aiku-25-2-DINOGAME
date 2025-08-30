# 세상에서가장잘뛰는공룡만들기

📢 2025년 여름학기 [AIKU](https://github.com/AIKU-Official) 활동으로 진행한 프로젝트입니다.
🎉 2025년 여름학기 AIKU Conference 열심히상 수상!

## 소개

<img width="671" height="235" alt="image" src="https://github.com/user-attachments/assets/8fe8d433-3c2f-4c2b-8ca1-98a02295d1d6" />

크롬 공룡게임(T-Rex Runner)을 자동으로 플레이하는 에이전트를  
**강화학습(Reinforcement Learning)** 알고리즘 중 하나인 **DQN (Deep Q-Network)** 으로 학습시킨 프로젝트입니다.  

프레임 단위의 게임 화면을 입력으로 받아, 공룡이 점프(↑)와 대기(–) 같은 액션을 선택하도록 학습합니다.
학습이 진행될수록 공룡은 더 빠르게 뛰고, 장애물(선인장, 새)을 피할 확률이 점점 높아집니다.

## 방법론

- **문제 정의**:  
  크롬 공룡게임은 사람이 키보드 입력을 통해 **점프**와 **엎드리기**로 장애물을 피하며 최대한 오래 생존하는 게임입니다.  
  이를 **강화학습 환경**으로 정의하여, 에이전트가 매 프레임마다 액션을 선택하고 보상을 받도록 설정했습니다.  

- **해결 방법**:  
  - CNN 기반의 Q-network를 설계하여 프레임 스택(최근 4장)을 입력으로 받음.
  - Replay Buffer와 Target Network를 적용하여 안정적인 학습 진행  
  - ε-greedy exploration 정책을 변형하여 **탐험 vs 활용** 균형 조절.
  - ε 값을, timestep에 따라 점차 감소시켜 학습 후반부의 안정적인 수렴성 보장 
  - Reward 설계:
    - 생존 시 + r   
    - 불필요한 행동(점프, 엎드리기) 시 소량 패널티
    - 장애물 충돌 시 큰 음수 보상
    - 일정한 milestone score 획득 시 추가 보상 (milestone score는 50점에서 시작하여, 25점 씩 증가)
  - "엎드리기" action이 불필요하다고 판단되어, 점프와 대기만 학습.
    
## 환경 설정

```
# Anaconda 환경 생성
conda create -n dino_rl python=3.9
conda activate dino_rl

# 첨부된 requirements.txt를 설치해주세요.
pip install -r requirements.txt
```

## 사용 방법

```
# 프로젝트 디렉토리로 이동
cd dino_rl

# 학습 시작
python main.py

# 학습 중지 후 이어서 학습
python main.py
```

학습 파라미터가 필요할 경우, 개인적으로 연락주세요!

## 예시 결과

<img width="1907" height="1008" alt="dino_game" src="https://github.com/user-attachments/assets/5e0f255d-2cb4-4a24-ada9-e0c079953850" />

## 팀원

- [지세현](https://github.com/sehyeonji321): 베이스라인 코드 작성, train, github 작성
- [유창우](https://github.com/changwoolab): 코드 작성 및 수정, train, 발표 자료 제작
- [최우석](https://github.com/woosukqw12): 코드 작성 및 수정, train, 노션 자료 제작
- [마현우](https://github.com/ruaqktk): 코드 작성 및 수정, train, 발표
