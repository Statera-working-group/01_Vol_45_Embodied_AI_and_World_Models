**Volume 45. Embodied AI and World Models**

# Chapter 01. Perception Action Loop

## 01.00. Overview

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

체화 지능(Embodied Intelligence)은 고립된 계산(Isolated Computation)이 아니라 에이전트(Agent)와 환경(Environment) 사이의 지속적인 상호작용(Continuous Interaction)에서 출현합니다. 지각-행동 루프(Perception-Action Loop)는 이러한 상호작용을 감각 관측(Sensory Observations)이 내부 표현(Internal Representations), 의사결정(Decisions), 물리적 행동(Physical Actions)으로 변환되고, 그 행동의 결과가 다시 다음 관측을 생성하는 반복 과정으로 설명합니다. 이러한 폐쇄적 관계(Closed Relationship)는 지각(Perception)과 행동(Action)을 지능적 행동(Intelligent Behavior)의 상호 의존적인 구성 요소로 만듭니다.

정적인 데이터셋(Static Datasets)을 처리하고 입력 자체를 변화시키지 않은 채 예측 결과를 반환하는 기존 인공지능(Conventional AI) 시스템과 달리, 체화 에이전트(Embodied Agents)는 자신의 행동에 반응하는 환경 내부에서 작동합니다. 이동 로봇(Mobile Robot)이 회전하고, 가속하고, 물체를 조작하거나 관측 시점(Viewpoint)을 변경하면 센서(Sensor)가 다음 순간 관측하게 될 정보도 달라집니다. 따라서 지능(Intelligence)은 감지(Sensing), 해석(Interpreting), 행동(Acting), 결과 관측(Observing Consequences), 행동 수정(Correcting Behavior)이 연속적으로 반복되는 동적 과정(Dynamic Process)이 됩니다.

이 루프는 지각(Perception)에서 시작하며, 카메라(Camera), 라이다(LiDAR), 지표투과레이더(Ground-Penetrating Radar), 관성 센서(Inertial Sensors), 마이크(Microphones), 촉각 센서(Tactile Sensors) 또는 기타 감각 모달리티(Sensing Modalities)의 원시 신호(Raw Signals)가 의미 있는 정보로 변환됩니다. 지각은 객체(Object)를 식별하고, 깊이(Depth)를 추정하며, 장애물(Obstacles)을 탐지하고, 지형(Terrain)을 인식하며, 움직임(Motion)을 측정하거나 개체(Entity) 사이의 관계를 추론할 수 있습니다. 다중모달 융합(Multimodal Fusion)은 상호 보완적인 관측을 결합하여 한 센싱 모달리티(Sensing Modality)의 약점을 다른 정보로 보완합니다.

원시 지각(Raw Perception)만으로는 충분하지 않습니다. 지능형 에이전트(Intelligent Agent)는 주변 세계와의 관계 속에서 자신의 현재 상태(Current Condition)를 파악해야 하기 때문입니다. 상태 추정(State Estimation)은 현재 센서 측정값(Current Sensor Measurements)을 이전 관측(Previous Observations) 및 운동 정보(Motion Information)와 통합하여 위치(Position), 자세(Orientation), 속도(Velocity), 환경 구조(Environmental Structure), 불확실성(Uncertainty) 등을 추정합니다. 위치추정(Localization)은 에이전트가 어디에 있는지를 결정하고, 매핑(Mapping)은 환경의 관련 특성을 표현하여 행동을 위한 지속적으로 갱신되는 운영 맥락(Operational Context)을 형성합니다.

추정된 상태(Estimated State)는 의사결정(Decision Making)과 계획(Planning)의 기반을 제공합니다. 에이전트는 적절한 행동을 선택하기 전에 목표(Goals), 현재 상황(Current Situation), 환경 제약(Environmental Constraints), 예상 위험(Predicted Risks), 가능한 행동(Possible Actions)을 평가합니다. 경로 계획(Path Planning)은 공간을 통과하는 실행 가능한 경로(Feasible Route)를 결정할 수 있으며, 상위 수준의 의사결정 메커니즘(Higher-Level Decision Mechanisms)은 어떤 목표(Objective)를 추구해야 하는지를 결정합니다. 이러한 과정은 지각적 이해(Perceptual Understanding)를 궁극적으로 물리적으로 실행될 수 있는 의도(Intentions)로 변환합니다.

행동 시스템(Action System)은 선택된 의도(Selected Intentions)를 모터(Motors), 액추에이터(Actuators), 조향 시스템(Steering Systems), 매니퓰레이터(Manipulators), 추진 장치(Propulsion Mechanisms) 또는 기타 물리적 인터페이스(Physical Interfaces)를 위한 명령으로 변환합니다. 운동 제어(Motion Control)는 실제 세계의 동역학(Real-World Dynamics) 아래에서 원하는 궤적(Trajectories)이나 상태(Configuration)를 어떻게 달성할 것인지를 결정합니다. 액추에이터에는 한계가 있고 환경에는 외란(Disturbances), 불확실성(Uncertainty), 마찰(Friction), 지연(Delay), 예상하지 못한 상호작용(Unexpected Interactions)이 존재하기 때문에 명령된 행동이 항상 예상한 결과를 정확하게 만들어내지는 않습니다. 따라서 행동은 이후의 지각과 지속적으로 연결되어야 합니다.

이러한 의존 관계는 폐루프 제어(Closed-Loop Control)를 형성합니다. 명령을 실행한 뒤 예상한 결과가 발생했다고 가정하는 대신, 에이전트는 행동의 결과를 관측하고 이를 원하는 상태(Desired State)와 비교합니다. 예상 결과(Expected Outcomes)와 실제 관측 결과(Observed Outcomes)의 차이는 피드백(Feedback)이 되어 이후의 제어 명령(Control Commands)을 수정합니다. 반복적인 피드백은 개루프 시스템(Open-Loop System)에서 위험하게 누적될 수 있는 외란, 모델링 오류(Modeling Errors), 노면 변화(Changing Surfaces), 외력(External Forces), 기타 편차(Deviations)를 시스템이 지속적으로 보상할 수 있도록 합니다.

지각-행동 루프(Perception-Action Loop)는 여러 공간적·시간적 규모(Spatial and Temporal Scales)에서 동시에 작동합니다. 빠른 제어 루프(Fast Control Loops)는 수 밀리초 단위로 바퀴 속도(Wheel Velocity), 관절 토크(Joint Torque), 균형(Balance), 자세(Attitude)를 조절할 수 있으며, 상대적으로 느린 루프는 객체 인식(Object Recognition), 위치추정(Localization), 경로 계획(Path Planning), 행동 의사결정(Behavioral Decisions)을 수행합니다. 더 높은 수준에서는 작업(Tasks), 목표(Goals), 장기적인 결과(Long-Term Consequences)를 추론할 수 있습니다. 효과적인 체화 시스템(Embodied Systems)은 빠른 반응과 숙고적 행동(Deliberative Behavior)이 동일하게 변화하는 환경 상태(Environmental State)와 일관성을 유지하도록 이러한 계층을 조정합니다.

시간(Time)은 특히 중요합니다. 감지(Sensing), 추론(Inference), 통신(Communication), 계획(Planning), 구동(Actuation)에는 지연시간(Latency)이 발생하기 때문입니다. 하나의 관측은 측정된 순간의 세계를 나타내지만, 그 관측을 기반으로 생성된 의사결정이 액추에이터에 도달할 때에는 물리적 시스템이 이미 이동했을 수 있습니다. 따라서 강건한 체화 시스템(Robust Embodied Systems)은 행동이 오래된 관측(Outdated Observation)이 아니라 실제 실행 순간의 세계와 대응하도록 시간 동기화(Synchronization), 시간적 상태 추정(Temporal State Estimation), 운동 예측(Motion Prediction), 지연시간 인지 제어(Latency-Aware Control)를 필요로 합니다.

불확실성(Uncertainty) 역시 루프의 근본적인 특성입니다. 센서에는 잡음(Noise)이 존재하고, 지각 모델(Perception Models)은 오류를 만들며, 객체는 가려질 수 있고, 지도(Map)는 오래된 상태가 될 수 있으며, 물리적 동역학(Physical Dynamics)을 항상 정확하게 모델링할 수도 없습니다. 따라서 체화 에이전트는 환경에 대해 무엇을 믿고 있는지만이 아니라 그 믿음에 대해 얼마나 확신하는지도 표현해야 합니다. 센서 융합(Sensor Fusion), 확률적 추정(Probabilistic Estimation), 예측 모델링(Predictive Modeling), 불확실성 인지 계획(Uncertainty-Aware Planning)을 활용하면 정보가 불완전하거나 서로 충돌할 때 더욱 보수적인 행동을 선택할 수 있습니다.

학습(Learning)은 이러한 루프를 즉각적인 피드백(Immediate Feedback)을 넘어 확장합니다. 각각의 상호작용은 환경이 행동에 어떻게 반응하는지에 대한 정보를 제공하며, 이를 통해 에이전트는 지각, 동역학 추정(Dynamics Estimation), 의사결정 정책(Decision Policies), 제어 전략(Control Strategies)을 개선할 수 있습니다. 강화학습(Reinforcement Learning)은 행동과 지연된 결과(Delayed Outcomes)를 연결할 수 있고, 모방학습(Imitation Learning)은 시연(Demonstrations)으로부터 성공적인 행동을 재현할 수 있으며, 자기지도학습(Self-Supervised Learning)은 방대한 수작업 라벨(Manual Labels) 없이도 센서 스트림(Sensor Streams)의 시간적 구조를 활용할 수 있습니다.

지각-행동 루프(Perception-Action Loop)는 또한 월드 모델(World Models)로 이어지는 자연스러운 연결 고리를 제공합니다. 순수 반응형 에이전트(Purely Reactive Agent)는 현재 관측을 직접 행동으로 변환하지만, 더욱 능력 있는 에이전트는 세계가 어떻게 변화하는지에 대한 내부 표현(Internal Representation)을 유지할 수 있습니다. 여러 대안 행동(Alternative Actions)에 따른 미래 상태(Future States)를 예측함으로써 시스템은 실제 행동을 수행하기 전에 그 결과를 평가할 수 있습니다. 지각은 내부 모델(Internal Model)을 갱신하고, 모델은 예측과 계획을 지원하며, 행동 이후의 실제 관측은 예측 오류(Prediction Errors)를 수정합니다.

이러한 아키텍처(Architecture)는 자율 로봇(Autonomous Robots), 드론(Drones), 차량(Vehicles)에 공통적으로 적용할 수 있으며, 이들은 해당 장의 구조에서도 주요 응용 영역(Application Areas)으로 명시되어 있습니다. 센서, 동역학, 운영 환경(Operating Environments), 안전 제약(Safety Constraints)은 서로 다르지만, 세계를 관측하고, 상태를 추정하고, 행동을 결정하고, 이를 실행하며, 결과를 측정하고, 다음 행동을 적응시키는 동일한 기본 순환 구조(Fundamental Cycle)를 공유합니다.

자율 로봇(Autonomous Robots)에서 이 루프는 사전에 완전히 정의할 수 없는 환경에서의 내비게이션(Navigation)과 조작(Manipulation)을 가능하게 합니다. 드론에서는 플랫폼이 3차원 공간(Three-Dimensional Space)을 지속적으로 이동하는 동안 지각 및 상태 추정이 빠른 자세 제어(Attitude Control)와 궤적 제어(Trajectory Control)에 결합됩니다. 자율주행 차량(Autonomous Vehicles) 역시 도로, 교통 참여자(Traffic Participants), 기반시설(Infrastructure), 날씨(Weather), 변화하는 운행 조건(Operational Conditions)에 대응하면서 환경 감지, 위치추정, 예측, 계획, 차량 제어(Vehicle Control)를 통합합니다.

체화 인공지능(Embodied AI)의 능력이 향상될수록 이 루프에는 학습된 지각(Learned Perception), 다중모달 표현(Multimodal Representations), 예측형 월드 모델(Predictive World Models), 파운데이션 모델(Foundation Models), 적응형 의사결정 시스템(Adaptive Decision Systems)이 점차 통합됩니다. 그러나 이러한 고급 구성 요소가 기본적인 피드백 구조(Fundamental Feedback Structure)를 제거하는 것은 아닙니다. 이들의 가치는 환경의 중요한 변화를 더 정확하게 지각하고, 상태를 유지하며, 결과를 예측하고, 적절한 행동을 선택하며, 예측과 현실이 불일치할 때 복구하는 에이전트의 능력을 얼마나 향상시키는지에 의해 결정됩니다.

따라서 지각-행동 루프(Perception-Action Loop)는 단순히 여러 소프트웨어 모듈(Software Modules)을 순차적으로 연결한 구조가 아니라 체화 지능(Embodied Intelligence)을 조직하는 기본 원리(Organizing Principle)로 이해해야 합니다. 지각(Perception)은 환경과의 상호작용에 의미를 부여하고, 상태 추정(State Estimation)은 시간적 연속성을 제공하며, 계획(Planning)은 현재 상태를 미래 목표와 연결합니다. 행동(Action)은 물리적 세계를 변화시키고, 피드백(Feedback)은 다시 전체 순환을 닫습니다. 이러한 과정의 지속적인 반복을 통해 체화 시스템은 실제 세계의 결과에 기반한 적응적이고 목표 지향적인 행동(Adaptive, Goal-Directed Behavior)을 수행할 수 있게 됩니다.

## 01.01. Perception System

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

지각 시스템(Perception System)은 체화 에이전트(Embodied Agent)와 물리적 세계(Physical World)를 연결하는 핵심 인터페이스입니다. 지각 시스템은 연속적으로 들어오는 감각 측정값(Sensory Measurements)을 상태 추정(State Estimation), 계획(Planning), 제어(Control), 학습(Learning)을 지원할 수 있는 구조화된 정보(Structured Information)로 변환합니다. 체화 인공지능(Embodied AI)에서 지각은 독립적인 인식 작업이 아니라 에이전트가 이동하고, 관측 시점을 변경하고, 객체와 상호작용하며, 자신의 행동을 통해 환경을 변화시키는 동안 지속적으로 수행되는 과정입니다.

지각 시스템(Perception System)의 설계는 서로 보완적인 물리적 특성을 가진 센서(Sensors)를 결합하는 방식에 따라 달라집니다. 카메라(Cameras)는 풍부한 외형(Appearance), 질감(Texture), 색상(Color), 의미 정보(Semantic Information)를 획득하고, 라이다(LiDAR)는 능동 거리 측정(Active Ranging)을 통해 기하학적 구조(Geometric Structure)를 직접 측정합니다. 지표투과레이더(Ground-Penetrating Radar, GPR)는 지각 범위를 가시적인 표면 아래까지 확장하며, 다중모달 융합(Multimodal Fusion)은 이러한 이질적인 관측을 통합하여 주변 환경에 대한 더욱 완전한 표현을 구성합니다.

비전(Vision)은 이미지에 객체(Objects), 표면(Surfaces), 움직임(Motion), 공간적 관계(Spatial Relationships), 맥락적 의미(Contextual Meaning)에 관한 정보가 포함되어 있기 때문에 체화 에이전트가 활용할 수 있는 가장 풍부한 감지 채널 가운데 하나입니다. 현대 비전 시스템(Vision Systems)은 객체 탐지(Object Detection), 의미론적·인스턴스 분할(Semantic and Instance Segmentation), 추적(Tracking), 깊이 추정(Depth Estimation), 옵티컬 플로우(Optical Flow), 자세 추정(Pose Estimation), 장면 이해(Scene Understanding)를 수행할 수 있습니다. 이를 통해 에이전트는 무엇이 존재하는지뿐 아니라 관련 개체들이 어디에 위치하고 시간에 따라 어떻게 변화하는지도 해석할 수 있습니다.

시각적 지각(Visual Perception)은 단안 카메라(Monocular Cameras), 스테레오 구성(Stereo Configurations), 파노라마 시스템(Panoramic Systems), 이벤트 카메라(Event Cameras), 또는 동기화된 다중 시점(Multiple Synchronized Viewpoints)을 활용할 수 있습니다. 단안 비전(Monocular Vision)은 저비용으로 풍부한 정보를 제공하지만 기하학적 정보(Geometric Information)는 간접적으로 얻습니다. 스테레오 및 다중 카메라 구성(Multi-Camera Configurations)은 시점 차이를 이용하여 깊이 추론(Depth Reasoning)을 향상시키며, 시간적 영상 시퀀스(Temporal Sequences)는 체화 플랫폼이 이동하면서 연속 프레임 사이에서 발생하는 변화를 이용해 움직임과 구조를 추정할 수 있도록 합니다.

비전(Vision)은 매우 풍부한 정보를 제공하지만 환경 조건(Environmental Conditions)에 민감합니다. 조명 변화(Illumination Changes), 그림자(Shadows), 눈부심(Glare), 어둠(Darkness), 안개(Fog), 비(Rain), 모션 블러(Motion Blur), 가림(Occlusion), 익숙하지 않은 시각적 외형(Unfamiliar Visual Appearances)은 성능을 저하시킬 수 있습니다. 따라서 강건한 체화 지각(Robust Embodied Perception)은 비전을 완벽한 정보원으로 간주하지 않습니다. 신뢰도 추정(Confidence Estimation), 시간적 일관성(Temporal Consistency), 중복성(Redundancy), 능동 거리 센서(Active Ranging Sensors)와의 융합을 통해 시각적 불확실성이 내비게이션과 제어 결정으로 직접 전파되는 것을 방지합니다.

라이다(Light Detection and Ranging, LiDAR)는 레이저 에너지(Laser Energy)를 능동적으로 방출하고 반사되어 돌아오는 신호를 이용해 거리를 추정합니다. 주변 표면을 반복적으로 샘플링함으로써 라이다 센서는 포인트 클라우드(Point Clouds), 거리 영상(Range Images), 점유 구조(Occupancy Structures), 3차원 지도(Three-Dimensional Maps) 등으로 표현할 수 있는 기하학적 측정값을 생성합니다. 수동형 카메라(Passive Cameras)와 달리 라이다는 명시적인 거리 정보(Explicit Distance Information)를 제공하므로 장애물 탐지(Obstacle Detection), 위치추정(Localization), 매핑(Mapping), 기하학적 장면 재구성(Geometric Scene Reconstruction)에서 중요한 역할을 수행합니다.

서로 다른 라이다 구성(LiDAR Configurations)은 측정 거리(Range), 해상도(Resolution), 시야각(Field of View), 갱신 주기(Update Frequency), 크기(Size), 전력 소비(Power Consumption), 비용(Cost) 사이에서 서로 다른 절충 관계를 제공합니다. 2차원 라이다(Two-Dimensional LiDAR)는 평면 내비게이션(Planar Navigation)과 위치추정에 널리 활용되며, 3차원 라이다(Three-Dimensional LiDAR)는 복잡한 환경의 수직 구조(Vertical Structure)까지 획득합니다. 이동형 체화 플랫폼(Moving Embodied Platforms)은 센서의 움직임과 자세(Pose)를 정확하게 추정할 수 있다면 연속적인 스캔을 시간에 따라 누적하여 상세한 환경 표현을 구축할 수 있습니다.

라이다(LiDAR) 역시 지각 아키텍처(Perception Architecture)에서 고려해야 할 한계를 가지고 있습니다. 장거리에서의 희소한 측정(Sparse Measurements), 반사성 또는 흡수성 재질(Reflective or Absorptive Materials), 악천후(Adverse Weather), 다중경로 효과(Multipath Effects), 운동 왜곡(Motion Distortion)은 신뢰성을 저하시킬 수 있습니다. 또한 원시 포인트 클라우드(Raw Point Clouds)는 직접적인 의미 정보(Semantic Meaning)를 거의 포함하지 않습니다. 따라서 학습 기반 포인트 클라우드 처리(Learned Point-Cloud Processing)와 카메라 정보와의 융합을 활용하여 라이다의 기하학적 정보와 객체 정체성(Object Identity), 장면 맥락(Scene Context), 작업 수준 해석(Task-Level Interpretation)을 연결하는 경우가 많습니다.

지표투과레이더(Ground-Penetrating Radar, GPR)는 표면 아래에 숨겨진 구조를 감지할 수 있기 때문에 다른 형태의 환경 지각(Environmental Perception)을 제공합니다. GPR은 전자기파(Electromagnetic Waves)를 물질 내부로 송신하고 지하의 전자기적 특성(Subsurface Electromagnetic Properties) 변화로 인해 발생하는 반사 신호를 분석합니다. 운용 조건에 따라 매설 객체(Buried Objects), 지하 시설물(Underground Utilities), 물질 경계(Material Interfaces), 공동(Cavities), 기타 지하 구조(Subsurface Structures)를 탐지하는 데 활용할 수 있으며, 이러한 정보는 일반적인 비전이나 라이다만으로는 얻기 어렵습니다.

GPR 측정값(GPR Measurements)은 일반적인 카메라 영상이나 라이다 포인트 클라우드와 근본적으로 다릅니다. 그 해석은 안테나 특성(Antenna Characteristics), 동작 주파수(Operating Frequency), 전파 속도(Propagation Velocity), 토양 또는 물질 특성(Soil or Material Properties), 깊이(Depth), 수분(Moisture), 클러터(Clutter), 신호 감쇠(Signal Attenuation)의 영향을 받습니다. 유용한 구조를 식별하기 전에 신호 처리(Signal Processing)와 공간 정합(Spatial Registration)이 필요한 경우가 많으므로, GPR을 사용하는 체화 시스템은 센서 해석을 정확한 플랫폼 위치추정 및 운동 정보와 연결해야 합니다.

GPR의 포함은 체화 지각(Embodied Perception)의 중요한 원리를 보여줍니다. 에이전트가 이해해야 하는 현실은 직접 보이는 표면에만 제한되지 않습니다. 자율 검사(Autonomous Inspection) 또는 탐사 플랫폼(Exploration Platform)은 관측 가능한 장애물과 숨겨진 구조를 동시에 추론해야 할 수 있습니다. 비전은 가시적인 주변 환경을 분류하고, 라이다는 정밀한 표면 기하학(Precise Surface Geometry)을 제공하며, GPR은 지하 정보를 탐지함으로써 에이전트가 기존의 시각적 장면 이해(Visual Scene Understanding)를 넘어서는 환경 표현을 구축할 수 있도록 합니다.

다중모달 융합(Multimodal Fusion)은 서로 다른 센싱 모달리티(Sensing Modalities)의 측정값을 결합하여 상호 보완적인 장점으로 더욱 신뢰성 높은 환경 표현(Environmental Representation)을 생성합니다. 융합은 센서 수준(Sensor Level)에 가까운 단계에서 수행될 수도 있고, 학습된 특징 표현(Learned Feature Representations) 내부에서 수행되거나, 각각의 지각 모듈이 상위 수준 추정값을 생성한 이후 수행될 수도 있습니다. 적절한 융합 전략(Fusion Strategy)은 동기화 정확도(Synchronization Accuracy), 센서 보정(Sensor Calibration), 계산 자원(Computational Resources), 환경 조건, 후속 계획 및 제어 요구사항에 따라 달라집니다.

초기 융합(Early Fusion)은 개별적인 해석이 상당 부분 진행되기 전에 상대적으로 낮은 수준의 측정값을 결합합니다. 이러한 방식은 상세한 교차 모달 관계(Cross-Modal Relationships)를 보존할 수 있지만 정밀한 공간적·시간적 정렬(Spatial and Temporal Alignment)이 필요합니다. 중간 또는 특징 수준 융합(Intermediate or Feature-Level Fusion)은 서로 다른 센서에서 추출된 신경망 표현(Neural Representations)이 추론 과정에서 상호작용하도록 합니다. 후기 융합(Late Fusion)은 독립적으로 생성된 탐지 결과(Detections), 추적 정보(Tracks), 지도(Maps), 신뢰도 추정값(Confidence Estimates)을 결합하며 높은 모듈성(Modularity)과 상대적으로 쉬운 고장 격리(Fault Isolation)를 제공할 수 있습니다.

효과적인 융합(Effective Fusion)은 단순히 센서 데이터를 연결하는 것 이상의 작업을 요구합니다. 각각의 모달리티는 서로 다른 좌표계(Coordinate System), 샘플링 패턴(Sampling Pattern), 잡음 특성(Noise Process), 지연시간(Latency), 물리적 측정 원리(Physical Mechanism)를 통해 세계를 관측합니다. 외부 보정(Extrinsic Calibration)은 센서 사이의 기하학적 관계를 설정하고, 내부 보정(Intrinsic Calibration)은 개별 센싱 장치의 특성을 정의하며, 시간 동기화(Time Synchronization)는 측정값들이 거의 동일한 물리적 상태를 나타내도록 합니다. 이러한 기반 요소에서 발생한 오류는 잘못된 연관(False Associations)을 만들어 융합 표현의 품질을 저하시킬 수 있습니다.

강건한 융합 시스템(Robust Fusion System)은 신뢰도(Confidence)와 센서 가용성(Sensor Availability)도 함께 추론해야 합니다. 카메라는 어두운 환경에서 신뢰성이 떨어질 수 있지만 라이다는 여전히 유용한 기하학 정보를 제공할 수 있습니다. 반대로 환경적 영향으로 라이다 반환 신호가 저하되는 상황에서도 비전은 의미론적 맥락(Semantic Context)을 유지할 수 있습니다. GPR 역시 특정 표면이나 운용 조건에서만 의미 있는 정보를 제공할 수 있습니다. 동적 가중치(Dynamic Weighting)와 불확실성 인지 융합(Uncertainty-Aware Fusion)은 현재 더 신뢰할 수 있는 모달리티를 시스템이 선택적으로 활용하도록 합니다.

시간적 융합(Temporal Fusion)은 여러 시점의 관측을 통합함으로써 지각 능력을 더욱 확장합니다. 각각의 센서 프레임을 독립적으로 해석하는 대신 체화 에이전트는 관측 사이에서도 지속되는 추적 정보(Tracks), 점유 추정(Occupancy Estimates), 지도(Maps), 잠재 표현(Latent Representations)을 유지할 수 있습니다. 이러한 시간적 연속성(Temporal Continuity)은 일시적인 가림 상태에서 정보를 복구하고, 잡음을 감소시키며, 움직임을 추론하고, 지속적인 환경 구조와 이동 객체 또는 센싱 아티팩트(Sensing Artifacts)가 만들어내는 일시적 측정값을 구분하는 데 도움을 줍니다.

지각 시스템(Perception System)의 궁극적인 목적은 환경에 대해 가능한 한 가장 상세한 설명을 만드는 것이 아니라 효과적인 행동(Action)을 지원하는 정보를 제공하는 것입니다. 내비게이션(Navigation)은 자유 공간(Free Space)과 장애물 정보가 필요하고, 조작(Manipulation)은 객체의 기하학적 구조와 자세(Object Geometry and Pose)가 필요하며, 검사(Inspection)는 상세한 표면 또는 지하 특징을 요구할 수 있습니다. 의사결정(Decision Making)은 의미론적 맥락을 필요로 할 수 있으므로 지각은 체화 에이전트의 작업(Tasks), 동역학(Dynamics), 제어 요구사항(Control Requirements)과 함께 설계되어야 합니다.

비전(Vision), 라이다(LiDAR), 지표투과레이더(GPR), 다중모달 융합(Multimodal Fusion)은 체화 인공지능이 개별적인 센싱(Isolated Sensing)에서 통합된 환경 이해(Integrated Environmental Understanding)로 발전하는 방식을 보여줍니다. 비전은 의미론적 풍부함(Semantic Richness)을 제공하고, 라이다는 명시적인 3차원 기하학(Explicit Three-Dimensional Geometry)을 제공하며, GPR은 관측 범위를 표면 아래까지 확장합니다. 다중모달 융합은 이러한 상호 보완적인 증거를 연결하며, 이들의 통합은 위치추정(Localization), 매핑(Mapping), 계획(Planning), 제어(Control), 궁극적으로 예측형 월드 모델링(Predictive World Modeling)을 지원하는 지각 기반(Perception Foundation)을 형성합니다.

## 01.02. State Estimation

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

상태 추정(State Estimation)은 체화 에이전트(Embodied Agent)가 변화하는 물리적 환경(Physical Environment) 속에서 자신의 상태를 파악할 수 있도록 지속적으로 갱신되는 내부 표현(Internal Description)을 제공합니다. 지각(Perception)은 관측 정보를 제공하지만, 이러한 관측은 불완전하고 잡음이 포함되어 있으며 시간에 걸쳐 분산되어 있습니다. 상태 추정은 센서 측정값(Sensor Measurements), 운동 정보(Motion Information), 이전 추정값(Previous Estimates), 불확실성(Uncertainty)을 통합하여 위치(Position), 자세(Orientation), 속도(Velocity), 환경 구조(Environmental Structure) 등을 추론합니다.

지각-행동 루프(Perception-Action Loop)에서 상태 추정(State Estimation)은 센싱(Sensing)과 지능적 행동(Intelligent Action)을 연결하는 다리 역할을 합니다. 로봇은 자신과 주변 환경에 대한 일관된 추정값(Coherent Estimate)을 유지하지 못하면 경로를 안정적으로 계획하거나, 장애물을 회피하거나, 객체를 조작하거나, 미래 움직임을 예측하기 어렵습니다. 시스템은 각각의 센서 측정값을 독립적으로 처리하는 대신 시간에 걸쳐 관측을 결합하여 일시적인 잡음이나 정보 누락이 계획과 제어를 즉시 불안정하게 만들지 않도록 합니다.

체화 시스템(Embodied System)의 상태(State)는 단순한 직교 좌표계 위치(Cartesian Position)보다 훨씬 많은 정보를 포함할 수 있습니다. 플랫폼에 따라 3차원 자세(Three-Dimensional Pose), 선속도 및 각속도(Linear and Angular Velocity), 가속도(Acceleration), 관절 구성(Joint Configuration), 바퀴 상태(Wheel States), 센서 바이어스(Sensor Biases), 랜드마크(Landmarks), 주변 객체 상태(Nearby Object States), 각 추정값과 관련된 불확실성을 포함할 수 있습니다. 정확한 상태 표현은 환경의 모든 물리적 변수를 모델링하려 하기보다 후속 계획, 예측, 제어 모듈이 필요로 하는 정보에 맞추어 구성해야 합니다.

위치추정(Localization)은 체화 에이전트가 어디에 위치하는가라는 근본적인 질문을 다룹니다. 위치추정은 로컬 지도(Local Map), 전역 좌표계(Global Coordinate System), 건물(Building), 도로망(Road Network), 이전에 관측한 환경과 같은 기준 좌표계(Reference Frame)에 대한 플랫폼의 위치(Position)와 자세(Orientation)를 추정합니다. 신뢰성 높은 위치추정은 서로 다른 시점에 수집된 센서 측정값을 공통된 공간적 맥락(Spatial Context)에 배치하고, 계획된 궤적(Planned Trajectories)을 실제 물리적 움직임과 연결할 수 있도록 합니다.

위치추정(Localization)은 일반적으로 상호 보완적인 운동 정보와 환경 관측(Environmental Observations)을 결합합니다. 관성 측정값(Inertial Measurements)은 빠른 회전 및 병진 운동을 포착할 수 있고, 휠 오도메트리(Wheel Odometry)는 지상 로봇의 점진적인 움직임을 추정할 수 있습니다. 카메라는 시각적 움직임(Visual Motion)을 추론하고 랜드마크를 인식하며, 라이다(LiDAR)는 기하학적 구조를 정합할 수 있고, 위성 항법(Satellite Navigation)은 신호를 사용할 수 있는 환경에서 전역 위치(Global Position)를 제공합니다. 하나의 정보원만으로 모든 환경에서 신뢰성을 보장할 수 없기 때문에 센서 융합(Sensor Fusion)은 실제 위치추정에서 핵심적인 역할을 합니다.

추측 항법(Dead Reckoning)은 알려진 이전 상태에서 점진적인 움직임(Incremental Motion)을 누적하여 현재 자세(Current Pose)를 추정합니다. 빠르고 국소적으로 일관된 갱신을 제공하지만 작은 측정 오차가 반복적으로 누적되므로 필연적으로 드리프트(Drift)가 발생합니다. 따라서 이러한 누적 오차를 보정하기 위해 절대적 또는 환경 기준 관측(Absolute or Environment-Relative Observations)이 필요합니다. 랜드마크, 지도 정합(Map Matching), 시각 특징(Visual Features), 라이다 스캔 정합(LiDAR Scan Matching), 위성항법시스템 관측(GNSS Observations), 기타 외부 기준을 이용하면 추정된 궤적에 제약을 부여하고 장기적인 드리프트를 줄일 수 있습니다.

확률적 추정(Probabilistic Estimation)은 불확실한 정보를 결합하기 위한 체계적인 프레임워크를 제공합니다. 센서 측정값과 운동 예측(Motion Predictions)이 정확하다고 가정하는 대신 추정기는 불확실성을 표현하고 새로운 증거가 들어올 때 자신의 믿음(Belief)을 갱신합니다. 칼만 필터(Kalman Filter) 기반 접근법은 근사적으로 선형이고 가우시안 특성을 가진 시스템에 효과적이며, 확장 칼만 필터(Extended Kalman Filter)와 무향 칼만 필터(Unscented Kalman Filter)는 비선형 동작을 처리합니다. 파티클 필터(Particle Filter)와 최적화 기반 방법(Optimization-Based Methods)은 더욱 복잡한 분포와 추정 구조를 위한 대안을 제공합니다.

현대적인 위치추정(Localization)은 현재 자세만 갱신하기보다 일련의 상태(State Sequence)를 대상으로 최적화를 수행하는 경우가 많습니다. 팩터 그래프(Factor Graph), 포즈 그래프(Pose Graph), 번들 조정(Bundle Adjustment), 슬라이딩 윈도우 최적화(Sliding-Window Optimization)는 여러 시점에 걸쳐 수집된 관측과 운동 제약(Motion Constraints)을 연결할 수 있습니다. 관련 상태들을 공동으로 최적화함으로써 일관성을 향상시키고, 새로운 정보에 의해 이전 궤적 추정이 부정확했다는 사실이 밝혀졌을 때 과거의 추정값까지 수정할 수 있습니다.

매핑(Mapping)은 에이전트 주변에 무엇이 존재하며 환경 구조를 어떻게 표현해야 하는가라는 상호 보완적인 문제를 다룹니다. 지도(Map)는 기하학적 표면(Geometric Surfaces), 자유 공간과 점유 공간(Free and Occupied Space), 랜드마크(Landmarks), 주행 가능성(Traversability), 의미론적 범주(Semantic Categories), 객체(Objects), 또는 이러한 속성의 조합을 표현할 수 있습니다. 적절한 지도 표현(Map Representation)은 작업에 따라 크게 달라지는데, 내비게이션 시스템(Navigation System), 조작 시스템(Manipulation System), 검사 로봇(Inspection Robot), 자율주행 차량(Autonomous Vehicle)이 필요로 하는 환경 정보의 형태가 서로 다르기 때문입니다.

메트릭 지도(Metric Maps)는 명시적인 공간 좌표(Explicit Spatial Coordinates)를 이용해 환경의 기하학적 구조를 표현합니다. 점유 격자(Occupancy Grid)는 공간을 셀(Cell)로 나누어 각 영역이 자유 공간인지 점유 공간인지 추정하며, 복셀 지도(Voxel Map)는 이러한 개념을 3차원으로 확장합니다. 포인트 클라우드 지도(Point-Cloud Map)는 상세한 기하학적 측정값을 보존하고, 표면 또는 메시 표현(Surface or Mesh Representation)은 연속적인 구조를 나타낼 수 있습니다. 이러한 표현은 충돌 검사(Collision Checking), 장애물 회피(Obstacle Avoidance), 기하학적 계획(Geometric Planning), 공간 재구성(Spatial Reconstruction)에 특히 유용합니다.

특징 기반 지도(Feature-Based Maps)는 관측된 모든 표면을 조밀하게 모델링하는 대신 선택된 랜드마크를 표현합니다. 시각적 키포인트(Visual Keypoints), 코너(Corners), 평면(Planes), 기둥(Poles), 에지(Edges), 기타 안정적인 구조는 위치추정을 위한 압축된 기준 정보를 제공할 수 있습니다. 의미론적 지도(Semantic Maps)는 도로(Roads), 벽(Walls), 문(Doors), 차량(Vehicles), 사람(People), 작업 영역(Work Areas)과 같은 범주를 공간 영역과 연결하여 더 높은 수준의 의미를 추가합니다. 메트릭 정보와 의미론적 정보를 결합하면 에이전트는 기하학적 구조와 기능적 의미(Functional Meaning)를 동시에 추론할 수 있습니다.

위치추정(Localization)과 매핑(Mapping)은 서로가 서로를 향상시킬 수 있기 때문에 깊게 결합되어 있습니다. 정확한 위치추정은 측정값을 지도의 올바른 위치에 삽입할 수 있도록 하며, 신뢰할 수 있는 지도는 위치추정을 개선하는 기준 정보를 제공합니다. 이러한 상호 의존성은 자연스럽게 동시적 위치추정 및 지도작성(Simultaneous Localization and Mapping, SLAM)으로 이어지며, SLAM에서는 시스템이 초기에는 알려지지 않았거나 부분적으로 알려진 환경의 표현을 구축하거나 개선하면서 자신의 이동 궤적(Trajectory)을 동시에 추정합니다.

동시적 위치추정 및 지도작성(SLAM)은 누적되는 드리프트와 동일한 장소의 반복 관측을 처리해야 합니다. 에이전트가 이전에 방문했던 영역으로 돌아왔을 때 루프 폐쇄(Loop Closure)는 현재 관측이 과거의 특정 위치와 동일하다는 것을 식별할 수 있습니다. 이는 누적된 궤적 오차를 수정하고 지도를 더욱 전역적으로 일관된 형태로 조정할 수 있는 장거리 제약(Long-Range Constraint)을 생성합니다. 따라서 신뢰성 높은 루프 폐쇄는 넓은 환경에서 장시간 운용(Long-Duration Operation)을 수행하기 위해 매우 중요합니다.

동적 환경(Dynamic Environments)은 기존 지도가 세계를 대체로 정적이라고 가정하는 경우가 많기 때문에 추가적인 문제를 발생시킵니다. 사람(People), 차량(Vehicles), 문(Doors), 장비(Equipment), 식생(Vegetation), 기타 객체는 이동하거나 상태가 변할 수 있습니다. 강건한 매핑 시스템(Robust Mapping System)은 지속적인 구조(Persistent Structure)와 일시적인 관측(Temporary Observations)을 구분해야 하며, 정적 기하학(Static Geometry)과 동적 개체(Dynamic Entities)를 별도의 표현으로 관리할 수도 있습니다. 시간 정보(Temporal Information)를 추가하면 관련 객체가 앞으로 어떻게 이동할 가능성이 있는지도 예측할 수 있습니다.

불확실성(Uncertainty)은 위치추정과 매핑 전체에서 명시적으로 유지되어야 합니다. 시스템이 측정의 모호성(Measurement Ambiguity)을 무시하면 단일 추정 자세나 지도 값이 잘못된 확신(False Confidence)을 만들어낼 수 있습니다. 자세 공분산(Pose Covariance), 확률적 점유(Probabilistic Occupancy), 신뢰도 점수(Confidence Scores), 다중 가설(Multiple Hypotheses), 학습된 불확실성 추정(Learned Uncertainty Estimates)을 이용하면 어떤 지식이 신뢰할 수 있고 어느 영역에서 추가 관측이 필요한지를 나타낼 수 있습니다. 이후 계획 모듈은 추정된 세계를 완벽하게 알려진 것으로 간주하지 않고 이러한 불확실성을 고려할 수 있습니다.

상태 추정(State Estimation)은 보정(Calibration), 동기화(Synchronization), 지연시간 관리(Latency Management)의 정확성에도 크게 의존합니다. 카메라, 라이다, 관성측정장치(Inertial Measurement Unit, IMU), 휠 인코더(Wheel Encoders), 기타 센서에서 생성된 측정값은 일관된 좌표계(Coordinate Frames)로 표현되고 정확한 시간과 연결되어야 합니다. 특히 플랫폼이 환경을 빠르게 이동하는 경우에는 센서 자체가 정확하더라도 타임스탬프(Timestamps)가 서로 맞지 않거나 센서 변환 관계(Sensor Transformations)가 부정확하게 보정되어 있으면 잘못된 상태 추정이 발생할 수 있습니다.

최종적으로 생성되는 상태 추정(State Estimate)은 독립적인 기하학적 결과물로 존재하는 것이 아니라 전체 지각-행동 루프(Perception-Action Loop)를 지원해야 합니다. 위치추정(Localization)은 에이전트의 공간적 기준(Spatial Reference)을 제공하고, 매핑(Mapping)은 환경적 맥락(Environmental Context)을 제공하며, 두 기능의 통합은 예측(Prediction), 경로 계획(Path Planning), 의사결정(Decision Making), 제어(Control)에 필요한 구조화된 상태(Structured State)를 제공합니다. 이후 새로운 행동은 플랫폼의 자세와 센서 관측 시점을 변화시키고, 다시 새로운 측정값을 생성하여 다음 순환에서 위치추정과 매핑을 갱신합니다.

체화 인공지능(Embodied AI)이 예측형 월드 모델(Predictive World Models)로 발전할수록 상태 추정(State Estimation)은 직접적인 관측(Direct Observation)과 내부 시뮬레이션(Internal Simulation)을 연결하는 더욱 중요한 인터페이스가 됩니다. 위치추정과 매핑은 에이전트가 현재 자신과 환경에 대해 무엇을 믿고 있는지를 설정하고, 예측 모델(Predictive Models)은 가능한 행동에 따라 그 상태가 어떻게 변화할지를 추정합니다. 따라서 신뢰성 높은 상태 추정은 체화 에이전트가 미래의 결과를 추론하고 지능적으로 행동할 수 있도록 하는 현실에 기반한 공간적·시간적 토대(Spatial and Temporal Foundation)를 제공합니다.

## 01.03. Action System

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

행동 시스템(Action System)은 체화 에이전트(Embodied Agent)가 가진 세계에 대한 내부 이해(Internal Understanding)를 목적 지향적인 물리적 행동(Purposeful Physical Behavior)으로 변환합니다. 지각(Perception)이 무엇이 일어나고 있는지를 파악하고 상태 추정(State Estimation)이 환경과 에이전트 사이의 현재 관계를 결정한다면, 행동 시스템은 다음에 무엇을 해야 하며 그것을 어떻게 실행해야 하는지를 결정합니다. 따라서 운동 제어(Motion Control), 경로 계획(Path Planning), 의사결정(Decision Making)은 상위 수준 목표(High-Level Goals)와 물리적 구동(Physical Actuation)을 연결하는 긴밀한 계층 구조를 형성합니다.

체화 인공지능(Embodied AI)에서 행동(Action)은 단순히 기호적 출력(Symbolic Output)이나 소프트웨어 예측(Software Prediction)을 생성하는 것과 근본적으로 다릅니다. 물리적 명령(Physical Command)은 환경을 변화시키는 동시에 에이전트가 미래에 관측하게 될 정보도 변화시킵니다. 차량을 조향하거나, 로봇 팔을 움직이거나, 이동 로봇을 가속하거나, 드론의 고도를 변경하면 위치(Position), 관측 시점(Viewpoint), 동역학(Dynamics), 이후의 감각 측정값(Sensory Measurements)이 달라집니다. 따라서 모든 행동은 지속적인 지각-행동 루프(Perception-Action Loop)의 일부가 됩니다.

의사결정(Decision Making)은 행동 시스템에서 가장 높은 개념적 수준에서 작동합니다. 의사결정은 추정된 상태(Estimated State), 임무 목표(Mission Goals), 환경 조건(Environmental Conditions), 제약조건(Constraints), 예상 결과(Expected Consequences)를 바탕으로 어떤 행동, 작업 또는 목표를 수행해야 하는지를 결정합니다. 이 과정에서 로봇은 계속 이동할지, 정지할지, 객체를 검사할지, 위험 지역을 회피할지, 물체를 조작할지, 지원을 요청할지 또는 다른 전략으로 전환할지를 선택할 수 있습니다.

효과적인 의사결정(Decision Making)을 위해서는 현재 상황뿐만 아니라 미래에 대한 추론이 필요합니다. 지능형 에이전트(Intelligent Agent)는 서로 다른 후보 행동(Candidate Actions)이 미래 상태(Future States)를 어떻게 변화시키며, 그러한 결과가 자신의 목표 달성에 얼마나 기여하는지를 평가해야 합니다. 이를 통해 예측(Prediction)이 의사결정 과정에 포함됩니다. 예측 모델(Predictive Model)이나 월드 모델(World Model)은 행동을 실행하기 전에 가능한 결과를 추정하여 기대 보상(Expected Reward), 목표 진행도(Progress), 위험(Risk), 안전(Safety), 에너지 소비(Energy Consumption), 시간(Time) 또는 기타 작업별 기준에 따라 대안을 비교할 수 있도록 합니다.

의사결정(Decision Making)은 세계의 추정 상태가 완벽하게 알려질 수 없기 때문에 불확실성(Uncertainty)도 고려해야 합니다. 장애물이 부분적으로만 관측될 수도 있고, 객체 분류(Object Classification)가 불확실할 수도 있으며, 위치추정(Localization)에 누적 오차가 존재하거나 다른 에이전트가 예측하기 어렵게 행동할 수도 있습니다. 따라서 강건한 의사결정(Robust Decision Making)은 예상 결과뿐만 아니라 그 결과에 대한 신뢰도(Confidence)도 함께 고려하며, 불확실성이 실제 운용에 중요한 수준으로 증가하면 보다 안전하거나 추가 정보를 획득할 수 있는 행동을 선택합니다.

목표나 행동이 선택되면 경로 계획(Path Planning)은 체화 에이전트가 현재 상태에서 원하는 상태(Desired State)까지 어떻게 이동할 수 있는지를 결정합니다. 경로 계획은 장애물(Obstacles), 기하학적 제약(Geometric Constraints), 플랫폼 성능(Platform Capabilities), 임무 요구사항(Mission Requirements)을 고려하면서 환경을 통과할 수 있는 실행 가능한 움직임(Feasible Motion)을 탐색합니다. 시스템에 따라 그 결과는 2차원 경로(Two-Dimensional Route), 3차원 비행 경로(Three-Dimensional Flight Path), 매니퓰레이터 궤적(Manipulator Trajectory), 또는 일련의 중간 구성 상태(Intermediate Configurations)가 될 수 있습니다.

전역 계획(Global Planning)은 일반적으로 비교적 넓은 환경 표현(Environmental Representation)을 기반으로 먼 목표 지점까지의 경로를 결정합니다. 반면 지역 계획(Local Planning)은 짧은 시간 범위에서 주변 장애물, 이동 객체(Moving Objects), 새롭게 관측된 기하학적 구조, 전역 경로에서 발생한 편차에 대응합니다. 두 수준을 결합하면 에이전트는 목적지까지 전략적으로 이동하면서도 사전에 완전히 예측할 수 없었던 환경 변화에 지속적으로 적응할 수 있습니다.

계획된 경로(Planned Path)는 플랫폼이 물리적으로 실행할 수 있어야 합니다. 바퀴형 로봇(Wheeled Robot)은 구동계가 그러한 움직임을 지원하지 않는다면 즉시 측면으로 이동할 수 없으며, 차량은 조향 곡률(Steering Curvature)과 가속도(Acceleration)에 제한이 있습니다. 드론은 비행 동역학(Flight Dynamics)을 따라야 하고, 매니퓰레이터는 관절 한계(Joint Limits)를 준수하면서 특이점(Singularities)과 충돌(Collisions)을 회피해야 합니다. 따라서 경로 계획은 에이전트를 제약 없이 움직이는 점으로 취급하기보다 운동학적·동역학적 제약(Kinematic and Dynamic Constraints)을 포함할 때 더욱 현실적인 결과를 생성할 수 있습니다.

계획(Planning)은 환경 비용(Environmental Cost)에 대한 적절한 표현도 필요로 합니다. 일부 영역은 물리적으로 통과할 수 있더라도 거친 지형(Rough Terrain), 좁은 여유 공간(Narrow Clearance), 낮은 가시성(Poor Visibility), 불확실한 위치추정(Uncertain Localization), 높은 에너지 요구량(High Energy Demand), 안전 위험(Safety Risk) 때문에 바람직하지 않을 수 있습니다. 플래너(Planner)는 이러한 특성을 비용 지도(Cost Map) 또는 관련 표현에 반영하여 거리뿐만 아니라 위험, 효율성(Efficiency), 강건성(Robustness), 기타 운용 목표 사이의 균형을 고려하는 궤적을 탐색할 수 있습니다.

운동 제어(Motion Control)는 원하는 경로(Path), 궤적(Trajectory), 속도(Velocity), 자세(Pose), 구성(Configuration)을 입력받아 물리적 플랫폼이 실행할 수 있는 명령으로 변환합니다. 계획이 비교적 추상적인 수준에서 시스템이 어디로 또는 어떻게 이동해야 하는지를 결정한다면, 제어(Control)는 이러한 의도를 추종하기 위해 필요한 액추에이터 입력(Actuator Inputs)을 지속적으로 계산합니다. 여기에는 바퀴 속도(Wheel Velocities), 조향각(Steering Angles), 모터 토크(Motor Torque), 관절 명령(Joint Commands), 추력(Thrust), 제동력(Braking Force), 기타 플랫폼별 제어 신호가 포함될 수 있습니다.

계획된 움직임과 실제 움직임은 완전히 동일할 수 없기 때문에 피드백(Feedback)은 필수적입니다. 휠 슬립(Wheel Slip), 불규칙한 지형(Uneven Terrain), 액추에이터 지연(Actuator Delay), 기계적 공차(Mechanical Tolerances), 공기역학적 외란(Aerodynamic Disturbances), 페이로드 변화(Payload Changes), 접촉력(Contact Forces), 모델링 오류(Modeling Errors)는 물리적 상태가 명령된 궤적에서 벗어나도록 만들 수 있습니다. 폐루프 운동 제어(Closed-Loop Motion Control)는 원하는 상태와 추정된 상태를 반복적으로 비교하고, 발생한 추종 오차(Tracking Error)를 줄이도록 액추에이터 명령을 조정합니다.

비례-적분-미분 제어(Proportional-Integral-Derivative Control, PID)와 같은 고전적인 피드백 방법은 다양한 저수준 변수(Low-Level Variables)를 조절할 수 있으며, 상태공간 제어(State-Space Control)와 모델 기반 기법(Model-Based Techniques)은 더욱 복잡한 동역학을 통합적으로 제어할 수 있습니다. 모델 예측 제어(Model Predictive Control, MPC)는 제한된 미래 시간 구간(Finite Future Horizon)에 걸쳐 시스템의 동작을 반복적으로 예측하고 제약조건을 만족하도록 제어 입력을 최적화합니다. 학습 기반 제어기(Learned Controllers)는 명시적인 해석 모델로 표현하기 어려운 복잡한 행동을 추가적으로 학습할 수 있습니다.

운동 제어(Motion Control)는 일반적으로 경로 계획(Path Planning)이나 상위 수준 의사결정(High-Level Decision Making)보다 높은 주파수로 동작합니다. 모터 전류와 토크는 매우 빠른 제어가 필요할 수 있고, 차량 속도와 자세는 중간 수준의 주기로 제어될 수 있으며, 계획은 환경 상태가 변화함에 따라 상대적으로 느린 주기로 갱신될 수 있습니다. 의사결정은 작업과 임무 목표를 포함하는 더욱 긴 시간 범위에서 수행될 수 있습니다. 이러한 계층 구조는 빠른 물리적 안정화(Physical Stabilization)를 가능하게 하면서 동시에 숙고적인 목표 지향 행동(Goal-Directed Behavior)을 유지합니다.

의사결정(Decision Making), 경로 계획(Path Planning), 운동 제어(Motion Control) 사이의 경계가 항상 명확하게 분리되는 것은 아닙니다. 지역 플래너(Local Planner)가 차량 동역학을 포함할 수도 있고, 예측 제어기(Predictive Controller)가 단기 궤적 최적화(Short-Horizon Trajectory Optimization)를 수행할 수도 있으며, 학습된 정책(Learned Policy)이 관측이나 잠재 상태(Latent State)를 직접 행동으로 변환할 수도 있습니다. 그럼에도 이러한 기능적 역할을 구분하는 것은 목표가 어떻게 점진적으로 물리적으로 실행 가능한 행동으로 변환되는지, 그리고 제약이나 실패를 어느 단계에서 처리해야 하는지를 이해하는 데 유용합니다.

안전 제약(Safety Constraints)은 행동 시스템의 모든 수준에 영향을 미쳐야 합니다. 의사결정은 위험한 목표를 거부할 수 있고, 경로 계획은 위험 지역을 제외하면서 적절한 안전 여유(Safety Clearance)를 유지할 수 있으며, 운동 제어는 속도, 가속도, 토크, 안정성(Stability), 정지 동작(Stopping Behavior)의 제한을 강제할 수 있습니다. 독립적인 안전 메커니즘(Safety Mechanisms)은 즉각적인 위험이 탐지될 경우 정상적인 명령을 무시하고 개입할 수 있으며, 이를 통해 작업 수행이 기본적인 운용 안전보다 우선하지 않도록 합니다.

행동 시스템(Action System)은 실행 중 변화하는 조건도 처리해야 합니다. 처음 계획할 당시 유효했던 경로가 차단될 수 있고, 목표가 이동하거나, 위치추정 신뢰도(Localization Confidence)가 감소하거나, 액추에이터 성능이 변화할 수 있습니다. 체화 에이전트는 초기 계획에 고정되는 대신 자신의 상태를 반복적으로 재평가하고, 관련 예측을 갱신하며, 필요한 경우 재계획(Replanning)을 수행하고 제어 명령을 수정합니다. 따라서 행동은 일회성 결정이 아니라 지속적으로 적응하는 과정(Continuous Adaptive Process)입니다.

학습(Learning)은 행동 시스템의 세 가지 기능 모두를 향상시킬 수 있습니다. 강화학습(Reinforcement Learning)은 상호작용과 보상(Reward)을 통해 의사결정 정책(Decision Policies)을 발견할 수 있고, 모방학습(Imitation Learning)은 숙련된 작업자가 시연한 행동을 재현할 수 있으며, 학습 기반 플래너(Learned Planners)는 대규모 궤적 데이터에서 습득한 패턴을 활용할 수 있습니다. 데이터 기반 제어(Data-Driven Control)는 복잡한 동역학에 적응할 수 있고, 운용 과정에서 축적된 경험은 특정 행동이나 전략이 성공하거나 실패할 가능성이 높은 상황을 시스템이 인식하도록 지원합니다.

예측형 월드 모델(Predictive World Models)은 물리적으로 행동을 실행하기 전에 후보 행동을 내부적으로 평가할 수 있도록 함으로써 지각(Perception)과 행동(Action)을 더욱 깊게 연결합니다. 추정된 현재 상태를 바탕으로 에이전트는 여러 대안적인 미래 궤적(Future Trajectories)을 내부적으로 예측하고 그 결과를 비교할 수 있습니다. 의사결정은 유망한 목표나 행동을 선택하고, 계획은 해당 목표로 이동하기 위한 실행 가능한 전이(Feasible Transitions)를 결정하며, 제어는 선택된 궤적을 실제로 구현합니다. 이후 새로운 관측은 예측한 결과가 실제로 발생했는지를 검증합니다.

따라서 운동 제어(Motion Control), 경로 계획(Path Planning), 의사결정(Decision Making)은 지각이 완료된 이후 단순히 조립되는 독립적인 알고리즘으로 취급해서는 안 됩니다. 이들은 추정된 상태(Estimated State)가 의도(Intention)로 변환되고, 의도가 계획된 움직임(Planned Motion)으로 변환되며, 계획된 움직임이 액추에이터 명령(Actuator Commands)으로 변환되고, 물리적 결과가 다시 새로운 관측(New Observations)을 생성하는 폐루프 지능 시스템(Closed Intelligent System)의 행동 측면을 구성합니다. 이러한 순환의 지속적인 반복을 통해 체화 에이전트는 지각을 현실 세계와의 적응적이고 안전하며 목표 지향적인 상호작용으로 변환합니다.

## 01.04. Closed Loop Control [w/Code]

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

폐루프 제어(Closed-Loop Control)는 체화 시스템(Embodied System)이 자신의 행동 결과를 지속적으로 관측하면서 행동을 수정할 수 있도록 하는 메커니즘입니다. 시스템은 명령을 내린 뒤 예상한 결과가 발생했다고 가정하는 대신, 결과 상태(Resulting State)를 측정하고 이를 목표 상태(Desired State)와 비교하여 오차(Error)를 계산한 다음 후속 명령을 수정합니다. 이러한 피드백 구조(Feedback Structure)는 지각-행동 루프(Perception-Action Loop)를 구성하는 핵심 요소입니다.

개루프 시스템(Open-Loop System)은 주로 초기 명령(Initial Command)이나 사전에 정의된 시퀀스(Predefined Sequence)를 바탕으로 행동을 결정하며, 실행 결과로 나타나는 상태를 지속적으로 이용하여 행동을 수정하지 않습니다. 환경과 시스템 동역학(System Dynamics)을 매우 정확하게 예측할 수 있다면 이러한 방식도 동작할 수 있지만, 체화 시스템은 외란(Disturbances), 불확실성(Uncertainty), 마찰(Friction), 페이로드 변화(Payload Changes), 센서 잡음(Sensor Noise), 액추에이터 변동(Actuator Variation), 환경과의 상호작용(Environmental Interaction) 속에서 작동합니다. 따라서 실제 세계에서 신뢰성 높은 자율성(Reliable Real-World Autonomy)을 구현하려면 피드백이 필수적입니다.

기본적인 폐루프 구조(Closed-Loop Structure)는 기준값(Reference), 제어기(Controller), 물리 시스템(Physical System), 센서(Sensors), 상태 추정(State Estimate), 피드백 경로(Feedback Path)로 구성됩니다. 기준값은 목표 속도(Target Velocity), 위치(Position), 자세(Orientation), 궤적(Trajectory), 관절각(Joint Angle), 힘(Force)과 같은 원하는 상태를 나타냅니다. 제어기는 이러한 목표와 추정된 현재 상태(Estimated Current State)를 비교하여 목표 행동과 실제 행동 사이의 차이를 줄이기 위한 액추에이터 명령(Actuator Commands)을 생성합니다.

이러한 차이는 일반적으로 제어 오차(Control Error)로 표현됩니다. 이동 로봇(Mobile Robot)이 특정 궤적을 추종하도록 명령받았지만 추정 위치가 해당 궤적에서 벗어나면, 제어기는 추종 오차(Tracking Error)를 이용하여 바퀴 속도(Wheel Velocity)나 조향(Steering)을 조정합니다. 매니퓰레이터(Manipulator)의 관절이 명령된 각도에 도달하지 못하면 모터 토크(Motor Torque)를 수정할 수 있습니다. 따라서 폐루프 제어는 관측된 편차(Observed Deviations)를 교정 행동(Corrective Physical Actions)으로 변환하여 오차가 통제되지 않은 상태로 누적되는 것을 방지합니다.

피드백(Feedback)은 센싱(Sensing)에 의존합니다. 제어기는 관측할 수 없는 행동을 수정할 수 없기 때문입니다. 인코더(Encoders)는 바퀴 또는 관절 움직임을 측정할 수 있고, 관성 센서(Inertial Sensors)는 가속도와 자세를 추정할 수 있으며, 카메라와 라이다(LiDAR)는 환경 기준(Environmental References)을 제공할 수 있습니다. 힘 센서(Force Sensors)나 촉각 센서(Tactile Sensors)는 물리적 상호작용을 측정할 수 있습니다. 필요한 피드백 변수(Feedback Variables)는 제어 대상에 따라 달라지며, 하나의 측정값만으로 충분한 신뢰성을 확보할 수 없을 경우 여러 센서를 융합할 수 있습니다.

상태 추정(State Estimation)은 원시 피드백 측정값(Raw Feedback Measurements)과 제어(Control)를 연결합니다. 센서는 일반적으로 물리적 상태에 대한 완벽한 정보를 제공하는 것이 아니라 잡음이 포함되고 불완전한 관측을 제공합니다. 따라서 위치추정(Localization), 오도메트리(Odometry), 필터링(Filtering), 센서 융합(Sensor Fusion)을 통해 제어기에 필요한 위치, 속도, 자세 또는 기타 변수를 추정할 수 있습니다. 결과적으로 제어 성능은 제어기 설계뿐만 아니라 추정 상태의 정확도(Accuracy), 지연시간(Latency), 갱신 주기(Update Frequency), 불확실성에도 영향을 받습니다.

일반적으로 PID 제어라고 하는 비례-적분-미분 제어(Proportional-Integral-Derivative Control, PID)는 피드백의 기본 원리를 잘 보여줍니다. 비례 항(Proportional Component)은 현재 오차에 반응하고, 적분 항(Integral Component)은 누적된 오차에 반응하며, 미분 항(Derivative Component)은 오차가 얼마나 빠르게 변화하고 있는지를 반영합니다. 적절하게 튜닝(Tuning)되면 이들의 조합은 정확하고 빠른 제어를 제공할 수 있지만, 복잡한 비선형(Nonlinear) 시스템이나 많은 제약조건을 가진 체화 시스템에는 더욱 발전된 접근법이 필요할 수 있습니다.

상태공간 제어(State-Space Control)는 내부 상태 변수(Internal State Variables)를 이용하여 시스템을 표현하고 수학적 모델(Mathematical Model)을 기반으로 적절한 제어 행동을 결정합니다. 이러한 프레임워크는 여러 상태와 액추에이터가 동시에 상호작용하는 다변수 시스템(Multivariable Systems)을 지원합니다. 피드백 이득(Feedback Gains)은 원하는 안정성과 응답 특성(Response Characteristics)을 얻도록 설계할 수 있으며, 관측기(Observers)나 추정기(Estimators)를 이용하면 사용 가능한 센서에서 직접 측정할 수 없는 중요한 상태도 복원할 수 있습니다.

모델 예측 제어(Model Predictive Control, MPC)는 미래의 시스템 동작을 명시적으로 고려함으로써 피드백 제어를 확장합니다. 각각의 제어 주기(Control Cycle)에서 MPC는 후보 제어 입력(Candidate Control Inputs)이 제한된 미래 구간(Finite Horizon) 동안 시스템에 어떤 영향을 미칠지를 예측하고, 제약조건을 만족하면서 목적함수(Objective)를 최적화합니다. 이후 선택된 해의 일부를 실행하고 새로운 관측을 받은 뒤 이 과정을 반복합니다. 이러한 이동 지평 구조(Receding-Horizon Structure)는 예측(Prediction), 최적화(Optimization), 제약조건(Constraints), 피드백을 자연스럽게 결합합니다.

물리적 제약조건(Physical Constraints)은 체화 제어(Embodied Control)에서 특히 중요합니다. 모터에는 토크와 속도 한계가 있고, 차량에는 가속도와 조향 한계가 있으며, 매니퓰레이터에는 관절 한계(Joint Limits)가 있고, 드론에는 추력 제한(Thrust Limitations)이 있습니다. 이동 로봇은 안정성(Stability)과 충돌 여유(Collision Clearance)도 유지해야 합니다. 따라서 제어기는 물리적으로 불가능하거나 안전하지 않은 행동으로 기준값을 추종하려 하기보다 실행 가능한 운용 영역(Feasible Operating Region) 안에서 명령을 생성해야 합니다.

외란 억제(Disturbance Rejection)는 폐루프 제어(Closed-Loop Control)의 주요 장점 가운데 하나입니다. 로봇은 휠 슬립(Wheel Slip), 불규칙한 지형(Uneven Terrain), 예상하지 못한 접촉(Unexpected Contact), 바람(Wind), 페이로드 변화, 기계적 저항(Mechanical Resistance)의 변화 등을 경험할 수 있습니다. 이러한 영향은 실제 행동이 예측된 응답에서 벗어나도록 만듭니다. 피드백은 결과적으로 발생하는 편차를 반복적으로 측정하기 때문에 원래의 시스템 모델에 완벽하게 반영되지 않은 외란도 제어기가 보상할 수 있도록 합니다.

강건성(Robustness)은 모델, 파라미터(Parameters), 측정값, 운용 조건(Operating Conditions)에 불확실성이 존재하더라도 제어 시스템이 허용 가능한 행동을 유지하는 능력을 의미합니다. 이상적인 수학적 모델만을 대상으로 설계된 제어기는 실제 하드웨어에 적용될 때 불안정해지거나 정확도가 저하될 수 있습니다. 따라서 강건 제어(Robust Control)의 원리는 하나의 공칭 운용 조건(Nominal Operating Condition)에 대해서만 최적화하기보다 예상 가능한 다양한 변동 범위에서도 신뢰할 수 있는 성능을 유지하는 것을 목표로 합니다.

안정성(Stability)은 반복적인 교정이 자동으로 안전한 행동을 보장하는 것은 아니기 때문에 기본적인 요구사항입니다. 지나치게 높은 피드백 이득, 부정확한 시스템 모델, 지연(Delay), 잘못 조정된 제어 파라미터(Control Parameters)는 오차를 감소시키는 대신 진동(Oscillation)이나 발산(Divergence)을 발생시킬 수 있습니다. 따라서 제어 설계는 외란과 초기 편차가 적절하게 감소하도록 하면서 과도한 오버슈트(Overshoot), 진동(Vibration), 액추에이터 포화(Actuator Saturation), 여러 제어 루프 사이의 불안정한 상호작용을 방지해야 합니다.

지연시간(Latency)은 체화 시스템에서 특히 중요합니다. 센서 획득(Sensor Acquisition), 통신(Communication), 지각(Perception), 상태 추정(State Estimation), 계획(Planning), 계산(Computation)은 모두 시간을 필요로 하므로 피드백이 실제 명령이 적용되는 시점에는 이미 변화한 과거 상태를 나타낼 수 있습니다. 큰 지연은 정확도를 감소시키거나 제어기를 불안정하게 만들 수 있습니다. 따라서 시간 동기화(Time Synchronization), 예측(Prediction), 효율적인 계산(Efficient Computation), 적절한 제어 주파수(Control Frequencies)는 실제 폐루프 설계에서 핵심적인 요소입니다.

체화 시스템은 일반적으로 서로 다른 시간 척도(Time Scales)에서 동작하는 여러 개의 중첩된 제어 루프(Nested Control Loops)를 포함합니다. 모터 제어기(Motor Controller)는 매우 높은 주파수에서 전류나 토크를 조절할 수 있고, 운동 제어기(Motion Controller)는 상대적으로 느린 주기로 속도나 자세를 제어할 수 있으며, 궤적 제어기(Trajectory Controller)는 계획 모듈이 생성한 경로를 추종할 수 있습니다. 상위 수준의 의사결정 시스템은 더욱 긴 시간 범위에서 작동합니다. 각 계층은 하위 계층에 기준값을 제공하면서 실행 결과와 환경 변화에 대한 피드백을 받습니다.

폐루프 제어는 운동 실행(Motion Execution)과 경로 계획(Path Planning)도 연결합니다. 플래너(Planner)가 이론적으로 실행 가능한 궤적을 생성하더라도 실제 움직임은 외란이나 모델링 오류 때문에 계획과 달라질 수 있습니다. 제어기는 궤적을 추종하려고 시도하며, 지속적인 편차가 발생하면 이를 상위 계층으로 전달하여 궤적 수정(Trajectory Modification)이나 재계획(Replanning)을 유발할 수 있습니다. 따라서 피드백은 저수준 액추에이터를 넘어 점차 높은 수준의 자율 행동에도 영향을 미칠 수 있습니다.

동일한 원리는 의사결정(Decision Making)에도 확장됩니다. 어떤 행동이 예상했던 결과를 만들어내지 못한다면 시스템은 단순한 모터 보정 이상의 대응이 필요할 수 있습니다. 선택한 행동을 다시 검토하고, 다른 경로를 선택하거나, 속도를 낮추거나, 추가 관측을 수집하거나, 안전하지 않게 된 목표를 포기할 수도 있습니다. 따라서 폐루프 자율성(Closed-Loop Autonomy)은 물리적 제어 수준뿐만 아니라 계획과 의사결정이라는 상위 인지 수준(Higher Cognitive Levels)에서도 피드백을 포함합니다.

예측(Prediction)은 시스템이 단순히 반응하는 것을 넘어 상황을 미리 예상할 수 있도록 하여 폐루프 제어를 강화합니다. 동역학 모델(Dynamics Model)은 플랫폼이 제어 입력에 어떻게 반응할지를 추정할 수 있고, 월드 모델(World Model)은 행동 이후 환경이 어떻게 변화할지를 예측할 수 있습니다. 실제 관측 결과를 예측 결과(Predicted Outcomes)와 비교하면 예측 오차(Prediction Error)가 생성됩니다. 이 오차는 상태 추정을 개선하고, 제어 결정을 수정하며, 모델을 갱신하거나 재계획을 시작하기 위한 정보로 활용될 수 있습니다.

학습(Learning)은 반복적인 상호작용을 통해 피드백 행동(Feedback Behavior)을 더욱 향상시킬 수 있습니다. 체화 에이전트는 경험을 이용하여 불확실한 동역학을 추정하고, 제어기 파라미터를 적응시키며, 해석적 모델(Analytical Models)의 잔차 보정(Residual Corrections)을 학습하거나 명시적으로 모델링하기 어려운 상황을 위한 정책(Policies)을 학습할 수 있습니다. 그러나 실제 환경은 학습 당시의 조건과 다를 수 있기 때문에 학습 기반 제어(Learned Control) 역시 배치 이후 지속적인 관측과 교정을 위한 피드백의 이점을 활용합니다.

안전 메커니즘(Safety Mechanisms)은 정상적인 제어 동작을 둘러싸는 또 하나의 폐루프를 형성합니다. 독립적인 모니터(Independent Monitors)는 속도, 근접 거리(Proximity), 힘, 온도, 안정성, 통신 상태(Communication Status), 위치추정 신뢰도(Localization Confidence), 기타 안전 관련 변수를 관측할 수 있습니다. 운용 한계(Operating Limits)를 위반하면 안전 로직(Safety Logic)이 명령을 제한하고, 플랫폼의 속도를 낮추거나, 제어된 정지(Controlled Stopping)를 실행하거나, 정상적인 자율 제어 명령을 무시하고 개입할 수 있습니다. 따라서 피드백은 성능뿐만 아니라 운용 경계(Operational Boundaries)를 지속적으로 유지하는 데에도 기여합니다.

궁극적으로 폐루프 제어(Closed-Loop Control)는 지각-행동 아키텍처(Perception-Action Architecture)를 단방향 처리 파이프라인(One-Way Processing Pipeline)에서 적응형 시스템(Adaptive System)으로 전환합니다. 지각(Perception)은 환경과 에이전트의 물리적 상태를 관측하고, 상태 추정(State Estimation)은 현재 상태를 결정하며, 계획(Planning)과 의사결정(Decision Making)은 원하는 행동을 정의하고, 제어(Control)는 이러한 의도를 물리적 행동으로 변환합니다. 그 결과 발생한 환경 변화(Environmental Change)는 다시 새로운 관측을 생성하여 순환을 닫으며, 시스템이 자신의 행동을 반복적으로 교정하고, 적응하고, 예측하며, 개선할 수 있도록 합니다.

## 01.05. Sensor Fusion [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

센서 융합(Sensor Fusion)은 여러 센싱 소스(Sensing Sources)의 정보를 결합하여 개별 측정값만으로 얻을 수 있는 것보다 더 신뢰성 높은 에이전트 및 환경 표현(Representation)을 생성하는 과정입니다. 지각-행동 루프(Perception-Action Loop)에서 융합은 이질적인 관측(Heterogeneous Observations)을 상태 추정(State Estimation), 계획(Planning), 제어(Control)와 연결합니다. 그 목적은 단순히 더 많은 데이터를 수집하는 것이 아니라 상호 보완적인 정보(Complementary Information)를 활용하면서 모호성(Ambiguity), 잡음(Noise), 불확실성(Uncertainty)을 줄이는 것입니다.

체화 시스템(Embodied Systems)에 센서 융합(Sensor Fusion)이 필요한 이유는 각각의 센싱 모달리티(Sensing Modality)가 물리적 현실(Physical Reality)의 일부만을 관측하기 때문입니다. 카메라(Cameras)는 풍부한 외형 및 의미론적 정보(Semantic Information)를 제공하지만 조명과 가시성에 민감합니다. 라이다(LiDAR)는 명시적인 기하학적 거리 측정값을 제공하지만 희소하거나 불완전한 반환 신호를 포함할 수 있습니다. 관성측정장치(IMU)는 빠른 움직임을 측정하지만 드리프트(Drift)가 누적되며, 위성항법시스템(GNSS)은 전역 위치(Global Position)를 제공할 수 있지만 차폐된 환경에서는 신뢰성이 떨어지거나 사용할 수 없게 될 수 있습니다.

추가적인 센싱 모달리티(Sensing Modalities)는 이러한 상호 보완 관계를 더욱 확장합니다. 휠 인코더(Wheel Encoders)는 지상 로봇(Ground Robots)의 점진적인 움직임을 추정하는 데 유용하지만 휠 슬립(Wheel Slip)과 불규칙한 지형(Uneven Terrain)의 영향을 받습니다. 레이더(Radar)는 광학 센싱(Optical Sensing)의 성능을 저하시키는 환경 조건에서도 효과적으로 작동할 수 있으며, 촉각 센서(Tactile Sensors)와 힘 센서(Force Sensors)는 원거리 관측만으로 신뢰성 있게 추론하기 어려운 물리적 상호작용(Physical Interaction)을 파악합니다. 지표투과레이더(GPR)는 기존의 표면 중심 센서로 얻을 수 없는 지하 정보(Subsurface Information)를 추가적으로 제공할 수 있습니다.

따라서 융합(Fusion)은 단순한 중복성(Redundancy)이 아니라 센서 다양성(Sensor Diversity)을 활용합니다. 동일한 물리량을 측정하는 두 개의 센서는 중복된 증거를 통해 신뢰성을 향상시킬 수 있지만, 서로 다른 물리적 특성을 관측하는 센서들은 상호 보완적인 제약조건(Complementary Constraints)을 제공할 수 있습니다. 카메라는 객체를 식별하고, 라이다는 해당 객체의 3차원 위치를 결정하며, 레이더는 상대 속도(Relative Velocity)를 추정하고, 관성 측정값은 플랫폼 자체의 움직임을 설명할 수 있습니다. 이러한 관측을 결합하면 더욱 풍부한 환경 이해(Environmental Understanding)가 가능해집니다.

측정값을 융합하기 전에 서로 호환 가능한 공간적 관계(Spatial Relationships)로 표현해야 합니다. 내부 보정(Intrinsic Calibration)은 개별 센서의 내부 측정 특성을 정의하며, 외부 보정(Extrinsic Calibration)은 센서 좌표계(Sensor Coordinate Frames) 사이의 변환 관계를 결정합니다. 시스템이 각각의 좌표계가 로봇 본체 및 다른 센서들과 어떻게 연결되는지 이해하지 못한다면 카메라 픽셀(Camera Pixel), 라이다 포인트(LiDAR Point), 레이더 탐지값(Radar Detection), 관성 측정값(Inertial Measurement)을 의미 있게 연관시킬 수 없습니다.

체화 플랫폼과 주변 객체가 지속적으로 움직이기 때문에 시간 정렬(Temporal Alignment) 역시 중요합니다. 아주 짧은 시간 차이를 두고 획득한 측정값이라도 서로 다른 물리적 상태를 나타낼 수 있습니다. 정확한 타임스탬프(Timestamps), 하드웨어 동기화(Hardware Synchronization), 클록 정렬(Clock Alignment), 운동 보상(Motion Compensation)을 통해 융합되는 관측이 거의 동일한 시점에 대응하도록 할 수 있습니다. 각각의 센서가 정상적으로 작동하더라도 동기화가 부정확하면 겉으로는 기하학적 불일치(Geometric Inconsistencies)가 발생할 수 있습니다.

센서 융합(Sensor Fusion)은 여러 표현 수준(Representation Levels)에서 수행될 수 있습니다. 초기 융합(Early Fusion)은 비교적 원시적이거나 최소한으로 처리된 측정값을 결합하여 모달리티 사이의 세부적인 관계를 보존합니다. 특징 수준 융합(Feature-Level Fusion)은 개별 센서 스트림에서 추출된 표현을 결합하며, 주로 학습 모델(Learned Models)을 통해 구현됩니다. 후기 융합(Late Fusion)은 탐지(Detections), 추적(Tracks), 분류(Classifications), 자세(Poses), 점유 추정(Occupancy Estimates)과 같은 상위 수준 출력을 결합합니다. 각각의 방식은 정보 보존, 모듈성(Modularity), 계산 복잡도(Computational Complexity), 강건성(Robustness) 측면에서 서로 다른 절충 관계를 가집니다.

초기 융합(Early Fusion)은 측정값 사이의 세밀한 대응 관계(Fine-Grained Correspondence)를 활용할 수 있지만 높은 수준의 보정 및 동기화 정확도를 요구합니다. 예를 들어 투영된 라이다 측정값(Projected LiDAR Measurements)을 영상 영역(Image Regions)과 연관시키면 기하학적 깊이(Geometric Depth)와 시각적 외형(Visual Appearance)을 함께 처리할 수 있습니다. 센서마다 저수준 데이터 형식과 샘플링 패턴(Sampling Patterns)이 크게 다르기 때문에 의미 있는 교차 모달 관계(Cross-Modal Relationships)를 구성하려면 신중한 전처리(Preprocessing)가 필요한 경우가 많습니다.

특징 수준 융합(Feature-Level Fusion)은 학습 기반 지각 시스템(Learned Perception Systems)에서 점점 중요해지고 있습니다. 개별 인코더(Encoders)는 영상, 포인트 클라우드(Point Clouds), 레이더 관측 또는 기타 센서 데이터를 잠재 표현(Latent Representations)으로 변환하고, 이후 이러한 표현을 정렬하고 결합할 수 있습니다. 어텐션 메커니즘(Attention Mechanisms)과 관련 신경망 아키텍처(Neural Architectures)는 서로 다른 모달리티의 어떤 특징이 상호 관련되어 있는지를 학습함으로써 모든 모달리티가 동일한 원시 측정 구조를 공유하지 않더라도 정보를 통합할 수 있도록 합니다.

후기 융합(Late Fusion)은 각각의 센싱 파이프라인(Sensing Pipeline)이 결과를 결합하기 전에 독립적인 해석을 생성할 수 있기 때문에 더욱 강한 모듈 분리(Modular Separation)를 제공합니다. 카메라 탐지 결과(Camera Detections), 라이다 객체(LiDAR Objects), 레이더 트랙(Radar Tracks), 위치추정 결과(Localization Estimates)는 위치, 정체성(Identity), 확률(Probability), 시간적 일관성(Temporal Consistency)을 기준으로 서로 연관될 수 있습니다. 이러한 아키텍처는 진단(Diagnostics)과 센서 교체를 단순화할 수 있지만, 융합이 수행되기 전에 일부 저수준 정보가 이미 제거되었을 가능성이 있습니다.

확률적 융합(Probabilistic Fusion)은 서로 다른 불확실성 특성(Uncertainty Characteristics)을 가진 측정값을 체계적으로 결합하는 방법을 제공합니다. 모든 관측이 동일한 정확도를 가진다고 가정하는 대신 시스템은 각각의 추정값과 관련된 신뢰도(Confidence) 또는 확률을 표현합니다. 불확실성이 낮은 측정값은 융합된 상태(Fused State)에 더 강하게 영향을 미치고, 불확실한 관측은 상대적으로 적게 반영될 수 있습니다. 이를 통해 잡음이 많거나 성능이 저하된 센서가 더 신뢰성 높은 정보원을 무조건 지배하는 것을 방지할 수 있습니다.

베이지안 추정(Bayesian Estimation)은 이러한 과정의 일반적인 개념적 기반을 제공합니다. 시스템은 자신의 상태에 대한 사전 믿음(Prior Belief)에서 시작하여 해당 상태가 어떻게 변화할지를 예측하고, 새로운 센서 증거(Sensor Evidence)를 받은 다음 그에 따라 믿음을 갱신합니다. 칼만 필터(Kalman Filters)와 비선형 변형(Nonlinear Variants)은 다양한 상태 추정 문제에서 이러한 원리를 구현하며, 파티클 필터(Particle Filters)와 최적화 기반 접근법(Optimization-Based Approaches)은 더욱 복잡한 불확실성, 비선형성(Nonlinearities), 여러 경쟁 가설(Multiple Competing Hypotheses)을 표현할 수 있습니다.

센서 융합(Sensor Fusion)은 위치추정(Localization)에서 특히 중요합니다. 관성측정장치(IMU)는 빠른 단기 운동 정보를 제공하고, 휠 오도메트리(Wheel Odometry)는 점진적인 변위를 추정하며, 카메라는 시각 특징(Visual Features)을 추적하고, 라이다는 기하학적 구조를 정합하며, 위성항법시스템(GNSS)은 사용할 수 있을 때 전역적인 보정(Global Corrections)을 제공합니다. 이러한 정보원을 결합하면 빠른 국소 운동 추정(Local Motion Estimation)을 장기적인 환경 또는 전역 기준에 연결하여 높은 갱신 속도를 유지하면서 누적 드리프트를 줄일 수 있습니다.

매핑(Mapping) 역시 다중모달 융합(Multimodal Fusion)의 직접적인 이점을 얻습니다. 라이다 또는 깊이 센싱(Depth Sensing)은 3차원 기하학을 구축하고, 카메라는 표면과 객체에 의미론적 의미(Semantic Meaning)를 추가하며, 레이더는 가시성이 좋지 않은 조건에서도 관측 정보를 제공할 수 있습니다. 특수 센서(Specialized Sensors)는 일반적인 영상으로 직접 볼 수 없는 속성을 추가할 수 있습니다. 따라서 최종 지도는 기하학(Geometry), 점유 상태(Occupancy), 의미 정보(Semantics), 주행 가능성(Traversability), 동적 객체(Dynamic Objects), 불확실성, 작업별 환경 속성을 함께 포함할 수 있습니다.

융합(Fusion)은 센서 모달리티 사이에서만 수행되는 것이 아니라 시간에 걸쳐서도 수행되어야 합니다. 시간적 융합(Temporal Fusion)은 연속적인 관측에서 증거를 누적하여 시스템이 객체를 추적하고, 지속적인 랜드마크(Persistent Landmarks)를 유지하며, 움직임을 추정하고, 가림(Occlusion)으로 일시적으로 보이지 않는 정보를 복원하도록 합니다. 단일 관측은 모호할 수 있지만 연속된 시퀀스(Sequence)를 이용하면 객체가 정지해 있는지, 접근하는지, 멀어지는지 또는 단순한 일시적 센서 잡음인지를 파악할 수 있습니다.

동적 환경(Dynamic Environments)에서는 데이터 연관(Data Association)이 핵심적인 문제가 됩니다. 시스템은 서로 다른 센서 또는 서로 다른 시점에서 얻어진 관측이 동일한 물리적 개체(Physical Entity)에 해당하는지를 판단해야 합니다. 잘못된 연관은 서로 관련 없는 객체를 하나로 결합하거나 하나의 객체를 여러 트랙으로 분리할 수 있습니다. 공간적 근접성(Spatial Proximity), 외형(Appearance), 운동 일관성(Motion Consistency), 의미론적 정체성(Semantic Identity), 불확실성, 과거 관측(Historical Observations)을 함께 활용하여 어떤 측정값을 융합해야 하는지 판단할 수 있습니다.

강건한 융합(Robust Fusion)은 센서가 고장 나거나 성능이 저하될 수 있다는 사실을 인식해야 합니다. 어둠은 카메라 성능을 저하시킬 수 있고, 반사성 표면은 라이다에 영향을 줄 수 있으며, 휠 슬립은 오도메트리를 왜곡할 수 있고, 위성항법시스템(GNSS)은 차단될 수 있으며, 진동(Vibration)은 관성 측정값에 영향을 줄 수 있습니다. 내고장성 시스템(Fault-Tolerant System)은 일관되지 않은 관측을 탐지하고, 신뢰성이 떨어지는 모달리티의 영향력을 낮추며, 남아 있는 정보가 안전한 행동에 충분하다면 이를 이용하여 계속 작동할 수 있어야 합니다.

따라서 불확실성 인지 융합(Uncertainty-Aware Fusion)은 자율 운용(Autonomous Operation)에 필수적입니다. 융합 결과는 추정된 위치, 객체, 지도 또는 환경 상태뿐만 아니라 해당 추정값을 얼마나 신뢰할 수 있는지도 전달해야 합니다. 이후 계획 및 의사결정 모듈은 이러한 정보를 이용하여 속도를 낮추거나, 안전 여유(Safety Clearance)를 증가시키거나, 추가 관측을 요청하거나, 다른 경로를 선택하거나, 불확실성이 허용 가능한 운용 한계(Operational Limits)를 초과할 경우 정지할 수 있습니다.

현대적인 센서 융합(Sensor Fusion)은 고전적인 추정 기법(Classical Estimation)과 기계학습(Machine Learning)을 점점 더 긴밀하게 결합하고 있습니다. 기하학적 보정(Geometric Calibration), 베이지안 필터링(Bayesian Filtering), 최적화(Optimization), 물리 모델(Physical Models)은 해석 가능한 구조를 제공하고, 신경망(Neural Networks)은 수작업으로 정의하기 어려운 복잡한 교차 모달 관계를 학습할 수 있습니다. 하이브리드 시스템(Hybrid Systems)은 지각을 위해 학습된 표현을 사용하면서 위치추정, 매핑, 계획, 안전 필수 제어(Safety-Critical Control)에는 확률적 상태 추정과 명시적인 제약조건을 유지할 수 있습니다.

궁극적으로 센서 융합(Sensor Fusion)은 전체 지각-행동 루프(Perception-Action Loop)를 강화합니다. 여러 센서는 세계의 상호 보완적인 측면을 관측하고, 보정(Calibration)과 동기화(Synchronization)는 이러한 관측을 정렬하며, 융합은 일관된 표현(Coherent Representation)을 구성하고, 상태 추정(State Estimation)은 이 표현을 시간에 따라 유지합니다. 이후 계획(Planning)과 제어(Control)는 융합된 상태(Fused State)를 기반으로 행동하며, 물리적 행동은 환경을 변화시켜 새로운 다중모달 측정값(Multimodal Measurements)을 생성합니다. 이러한 지속적인 순환을 통해 센서 융합은 적응형 체화 지능(Adaptive Embodied Intelligence)에 필요한 신뢰성 높은 지각 기반(Reliable Perceptual Foundation)을 제공합니다.

## 01.06. Applications

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

응용 계층(Application Layer)은 지각-행동 루프(Perception-Action Loop)가 실제 물리 시스템에서 어떻게 실용적인 지능(Practical Intelligence)으로 구현되는지를 보여줍니다. 자율 로봇(Autonomous Robots), 드론(Drones), 차량(Vehicles)은 서로 다른 동역학(Dynamics), 센싱 구성(Sensing Configurations), 환경(Environment), 임무 요구사항(Mission Requirements)을 가지지만 모두 동일한 기본 순환 구조에 의존합니다. 주변 환경을 지각하고, 상태를 추정하고, 의사결정을 수행하고, 실행 가능한 움직임을 계획하며, 행동을 실행한 뒤 그 결과로 발생하는 변화를 관측하여 행동을 지속적으로 적응시킵니다.

자율 로봇(Autonomous Robots)은 계산에 의한 의사결정이 즉각적인 물리적 결과를 만들어내기 때문에 체화 지능(Embodied Intelligence)의 가장 직접적인 응용 분야 가운데 하나입니다. 이동 로봇(Mobile Robots)은 장애물, 표면, 사람, 객체, 주행 가능 공간(Navigable Space)을 해석하는 동시에 자신의 위치와 움직임을 지속적으로 추정해야 합니다. 이러한 자율성은 지각(Perception), 위치추정(Localization), 매핑(Mapping), 계획(Planning), 운동 제어(Motion Control), 피드백(Feedback)을 독립적으로 운용하는 것이 아니라 긴밀하게 연결함으로써 구현됩니다.

실내 자율 로봇(Indoor Autonomous Robots)은 일반적으로 창고, 공장, 병원, 사무실, 물류센터, 서비스 환경에서 운용됩니다. 카메라, 라이다(LiDAR), 깊이 센서(Depth Sensors), 휠 인코더(Wheel Encoders), 관성 센서(Inertial Sensors)는 내비게이션을 위해 상호 보완적인 정보를 제공할 수 있습니다. 위치추정과 매핑은 공간적 맥락(Spatial Context)을 구축하고, 경로 계획(Path Planning)은 정적 및 동적 장애물을 회피하는 경로를 결정합니다. 이후 폐루프 제어(Closed-Loop Control)는 이동 과정에서 발생하는 휠 슬립(Wheel Slip), 페이로드 변화(Payload Changes), 바닥의 불규칙성(Floor Irregularities), 추종 오차(Tracking Errors)를 보정합니다.

실외 로봇(Outdoor Robots)은 환경 조건이 상대적으로 비구조적이고 예측하기 어렵기 때문에 추가적인 복잡성에 직면합니다. 지형의 기하학적 구조(Terrain Geometry), 경사(Slopes), 식생(Vegetation), 진흙(Mud), 먼지(Dust), 비(Rain), 변화하는 조명(Changing Illumination), 불완전한 지도(Incomplete Maps)는 지각과 이동성 모두에 영향을 줄 수 있습니다. 개별 센싱 모달리티(Sensing Modalities)의 신뢰성이 시간에 따라 크게 달라질 수 있으므로 센서 융합(Sensor Fusion)이 특히 중요합니다. 또한 주행 가능성 추정(Traversability Estimation)은 지각된 지형 특성을 플랫폼의 실제 물리적 이동 능력과 연결해야 합니다.

로봇 조작(Robotic Manipulation)은 지각-행동 루프를 이동(Locomotion)에서 객체와의 물리적 상호작용(Physical Interaction)으로 확장합니다. 매니퓰레이터(Manipulator)는 객체를 탐지하고 식별하며, 자세와 기하학적 구조를 추정하고, 적절한 파지 또는 상호작용 전략(Grasp or Interaction Strategy)을 선택한 뒤 충돌 없는 관절 움직임(Collision-Free Joint Motion)을 계획하고 접촉 과정에서 힘을 제어해야 합니다. 객체 위치, 마찰(Friction), 변형(Deformation), 접촉 조건(Contact Conditions)은 예측과 다를 수 있기 때문에 시각, 촉각, 힘 피드백을 이용하여 조작 행동을 지속적으로 수정할 수 있습니다.

자율 로봇은 이동과 조작을 결합하여 이동형 조작 시스템(Mobile Manipulation Systems)을 구성할 수도 있습니다. 이러한 플랫폼은 안정성(Stability), 도달 가능성(Reachability), 충돌 위험(Collision Risk), 변화하는 관측 시점(Viewpoints)을 고려하면서 내비게이션과 로봇 팔 움직임을 조정해야 합니다. 로봇은 객체에 더 쉽게 접근하기 위해 이동 베이스(Mobile Base)의 위치를 변경하고, 새로운 시점에서 지각 정보를 갱신하고, 조작 계획을 수정한 다음 새로운 행동을 실행할 수 있습니다. 따라서 지능은 하나의 사전 결정된 궤적이 아니라 반복적인 상호작용을 통해 나타납니다.

드론(Drones)은 훨씬 빠르고 강하게 결합된 동역학(Coupled Dynamics) 환경에서 동일한 지각-행동 원리를 적용합니다. 공중 플랫폼(Aerial Platforms)은 안정적인 비행을 유지하는 동시에 3차원 위치, 자세(Orientation), 속도, 환경 구조를 추정해야 합니다. 관성측정장치(IMU), 카메라, 위성항법시스템(GNSS), 라이다, 레이더(Radar), 고도계(Altimeters), 기타 센서를 융합하여 상태 추정값을 유지할 수 있습니다. 이후 제어 시스템은 원하는 궤적을 추력(Thrust), 자세, 추진 시스템(Propulsion)의 빠른 조정으로 변환해야 합니다.

드론 자율성(Drone Autonomy)은 플랫폼이 3차원 공간을 빠르게 이동할 때 짧은 지연도 중요해질 수 있기 때문에 시간적 특성(Timing)에 크게 의존합니다. 따라서 상태 추정(State Estimation)과 제어(Control)는 높은 갱신 주기(Update Rates)로 동작하며, 지각과 계획은 서로 다른 주파수로 실행될 수 있습니다. 중첩된 피드백 루프(Nested Feedback Loops)를 이용하면 저수준 자세 안정화(Attitude Stabilization)가 빠르게 반응하는 동안 상위 시스템은 장애물 회피, 궤적 생성(Trajectory Generation), 탐사(Exploration), 검사(Inspection), 임무 수준 의사결정(Mission-Level Decision Making)을 수행할 수 있습니다.

위성항법시스템(GNSS)의 가용성은 공중 내비게이션(Aerial Navigation)에 큰 영향을 주지만 항상 사용할 수 있다고 가정해서는 안 됩니다. 건물, 지형, 실내 환경, 간섭(Interference), 신호 저하(Signal Degradation)는 위치 정보의 신뢰성을 감소시킬 수 있습니다. 시각-관성 오도메트리(Visual-Inertial Odometry), 라이다-관성 추정(LiDAR-Inertial Estimation), 지도 기반 위치추정(Map-Based Localization), 기타 보완 기법을 이용하면 전역 위치 정보가 불안정해졌을 때에도 국소 내비게이션(Local Navigation)을 유지할 수 있습니다. 이후 전역 기준을 다시 확보하면 센서 융합을 통해 이를 통합하여 누적된 드리프트(Drift)를 보정할 수 있습니다.

드론은 검사(Inspection), 매핑(Mapping), 모니터링(Monitoring), 탐사(Exploration), 지상 플랫폼이 접근하기 어렵거나 위험한 지역에서의 작업에 특히 유용합니다. 공중 관측 시점(Aerial Viewpoint)은 넓은 공간을 관측할 수 있게 하지만 페이로드(Payload), 비행 지속시간(Endurance), 통신(Communication), 센싱 거리(Sensing Range), 에너지 가용성(Energy Availability)에 제약을 발생시킵니다. 따라서 임무 계획(Mission Planning)은 기하학적인 실행 가능성뿐만 아니라 배터리 상태(Battery State), 비행시간, 환경 조건, 통신 품질, 안전한 복귀 방법(Safe Recovery Options)도 고려해야 합니다.

자율주행 차량(Autonomous Vehicles)은 지각-행동 루프의 또 다른 주요 응용 분야로서 고속 이동과 도로, 기반시설(Infrastructure), 보행자(Pedestrians), 자전거 이용자(Cyclists), 다른 차량 사이의 복잡한 상호작용을 결합합니다. 카메라, 라이다, 레이더, 위성항법시스템, 관성측정장치, 휠 속도 센서(Wheel-Speed Sensors), 지도 정보(Map Information)는 상호 보완적인 증거를 제공할 수 있습니다. 이렇게 융합된 상태(Fused State)는 위치추정, 객체 탐지(Object Detection), 추적(Tracking), 예측(Prediction), 경로 계획(Route Planning), 궤적 생성, 차량 제어(Vehicle Control)를 지원합니다.

차량 지각(Vehicle Perception)은 정적인 환경 구조와 동적인 교통 참여자(Traffic Participants)를 모두 구분해야 합니다. 도로 경계(Road Boundaries), 차선(Lanes), 표지판(Signs), 신호등(Signals), 연석(Curbs), 장애물, 주행 가능 영역(Drivable Regions)은 기하학적·의미론적 맥락(Geometric and Semantic Context)을 제공하며, 주변 차량과 취약 도로 이용자(Vulnerable Road Users)는 지속적인 탐지와 추적이 필요합니다. 안전한 행동은 다른 참여자가 어디에 있는지만이 아니라 그 상태가 어떻게 변화하는지에도 의존하므로 시간적 지각(Temporal Perception)이 특히 중요합니다.

예측(Prediction)은 주변 에이전트의 가능한 미래 행동을 추정함으로써 차량 지각과 의사결정(Decision Making)을 연결합니다. 주변 차량이 차선을 변경하거나, 보행자가 도로에 진입하거나, 교통 상황의 변화로 이용 가능한 경로가 달라질 수 있습니다. 이러한 결과에는 불확실성(Uncertainty)이 존재하므로 자율주행 시스템은 하나의 결정론적 미래(Deterministic Future)에만 의존하지 않고 여러 가능성을 평가해야 합니다. 이후 계획 시스템은 가능한 시나리오 전반에서 안전 여유(Safety Margins)를 유지할 수 있는 행동을 선택할 수 있습니다.

차량 계획(Vehicle Planning)은 자연스럽게 계층적 구조(Hierarchical Structure)를 가집니다. 경로 계획(Route Planning)은 도로망을 통해 먼 목적지까지 이동하는 방법을 결정하고, 행동 계획(Behavioral Planning)은 차선 유지(Lane Keeping), 합류(Merging), 양보(Yielding), 정지(Stopping)와 같은 기동을 선택하며, 궤적 계획(Trajectory Planning)은 도로의 기하학적 구조와 차량 제약조건을 만족하는 세부적인 움직임을 결정합니다. 운동 제어(Motion Control)는 이러한 궤적을 조향(Steering), 가속(Acceleration), 제동(Braking) 명령으로 변환하면서 피드백을 지속적으로 활용하여 물리적 편차를 보정합니다.

계획된 궤적 자체가 성공적인 실행을 보장할 수 없기 때문에 폐루프 운용(Closed-Loop Operation)은 자율주행 차량 전체에서 필수적입니다. 타이어 힘(Tire Forces), 노면 마찰(Road Friction), 경사, 바람, 차량 적재 상태(Vehicle Loading), 액추에이터 지연(Actuator Delays), 위치추정 오차는 실제 움직임을 변화시킬 수 있습니다. 제어 시스템은 결과적인 차량 상태를 관측하고 조향 또는 종방향 제어 명령(Longitudinal Commands)을 수정합니다. 중요한 환경 변화가 발생하면 이러한 정보가 아키텍처의 상위 계층으로 전달되어 행동을 다시 검토하거나 재계획(Replanning)을 수행할 수 있습니다.

안전(Safety)은 자율 로봇, 드론, 차량 모두에서 공통적으로 요구되지만 구체적인 위험 요소는 서로 다릅니다. 자율 시스템은 운용 한계(Operational Limits)를 인식하고, 불확실성을 모니터링하며, 센싱 성능 저하(Degraded Sensing)를 탐지하고, 장애물과 적절한 거리를 유지하며, 예상한 행동을 달성할 수 없을 때 안전하게 대응해야 합니다. 중복 센싱(Redundant Sensing), 고장 탐지(Fault Detection), 폴백 행동(Fallback Behavior), 비상 정지 또는 착륙(Emergency Stopping or Landing), 제약 기반 제어(Constrained Control)는 정상적인 자율 의사결정 과정 이외의 추가적인 보호 기능을 제공할 수 있습니다.

이 세 가지 응용 분야는 지각(Perception)과 행동(Action)을 서로 독립적으로 설계할 수 없는 이유도 보여줍니다. 센서 구성(Sensor Configuration)은 의도된 행동에 필요한 정보를 제공하도록 설계되어야 하며, 계획은 플랫폼의 실제 동역학과 센싱 한계를 고려해야 합니다. 지형을 신뢰성 있게 지각하지 못하는 로봇은 공격적인 지형 주행을 계획해서는 안 되고, 위치추정이 불확실한 드론은 정밀 기동(Precision Maneuvers)을 피해야 하며, 지각 성능이 저하된 차량은 그에 적합한 보수적 행동(Conservative Behavior)을 선택해야 합니다.

학습(Learning)과 예측형 월드 모델(Predictive World Models)은 시스템이 경험을 활용하고 미래 결과를 예상할 수 있도록 함으로써 세 가지 응용 영역 모두를 더욱 발전시킬 수 있습니다. 로봇은 상호작용 패턴(Interaction Patterns)을 학습할 수 있고, 드론은 변화하는 조건에서 지각과 제어 성능을 향상시킬 수 있으며, 차량은 복잡한 교통 행동(Traffic Behavior)을 모델링할 수 있습니다. 월드 모델은 후보 행동(Candidate Actions)을 내부적으로 시뮬레이션할 수 있지만, 예측 결과가 실제로 변화하는 물리적 환경과 일치하는지를 확인하기 위해서는 실제 센서 피드백(Real Sensor Feedback)이 계속 필요합니다.

자율 로봇(Autonomous Robots), 드론(Drones), 차량(Vehicles)은 서로 다른 물리적 형태를 가지고 있지만 궁극적으로 공통된 아키텍처 원리(Common Architectural Principle)를 공유합니다. 센서는 관측(Observations)을 제공하고, 융합(Fusion)은 일관된 증거(Coherent Evidence)를 구성하며, 상태 추정(State Estimation)은 내부 표현을 유지합니다. 의사결정은 목표를 선택하고, 계획은 실행 가능한 행동을 구성하며, 제어는 이를 실제로 실행합니다. 이후 피드백은 행동의 결과를 측정하고 다음 순환을 시작함으로써 지능형 시스템과 물리적 세계 사이에 지속적인 적응(Continuous Adaptation)을 만들어냅니다.

이러한 응용 사례들은 체화 지능(Embodied Intelligence)이 특정한 로봇 형태(Robot Morphology), 센서 또는 제어 알고리즘에 의해 정의되는 것이 아니라는 점을 보여줍니다. 체화 지능은 실제 세계의 제약조건 아래에서 지각, 상태(State), 의사결정, 행동, 피드백을 통합하는 방식에 의해 정의됩니다. 지상에서 이동하거나, 객체를 조작하거나, 3차원 공간을 비행하거나, 공공 도로를 주행하는 경우 모두에서 자율 시스템은 센싱(Sensing), 추론(Reasoning), 물리적 행동(Physical Action)을 지속적인 폐루프 방식으로 조정함으로써 지능적인 능력을 구현합니다.
