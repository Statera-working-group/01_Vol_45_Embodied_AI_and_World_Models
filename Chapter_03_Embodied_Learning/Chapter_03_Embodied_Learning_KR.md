**Volume 45. Embodied AI and World Models**

# Chapter 03. Embodied Learning

## 03.00. Overview

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

체화 학습(Embodied Learning)은 지능형 에이전트(Intelligent Agent)가 자신의 신체(Body), 센서(Sensors), 행동(Actions), 환경(Environment) 사이의 지속적인 상호작용을 통해 지식과 행동을 획득하는 과정을 설명합니다. 지능을 정적인 데이터에 대한 독립적인 계산으로 보는 대신, 체화 학습은 지각(Perception)과 행동이 함께 학습 가능한 내용을 형성한다고 봅니다. 경험(Experience)은 현실 세계에서 행동하고 그 결과를 관측하며, 이러한 상호작용을 바탕으로 이후의 행동을 적응시키는 과정에서 형성됩니다.

신체(Body)는 에이전트가 환경을 어떻게 감지하고 변화시킬 수 있는지를 물리적 구조가 결정하기 때문에 이러한 학습 과정에서 능동적인 역할을 합니다. 바퀴형 로봇(Wheeled Robot), 4족 보행 로봇(Quadruped), 매니퓰레이터(Manipulator), 드론(Drone), 자율주행 차량(Autonomous Vehicle)은 서로 다른 행동 공간(Action Spaces), 센싱 기하 구조(Sensing Geometries), 동역학적 제약조건(Dynamic Constraints), 상호작용 가능성을 가집니다. 따라서 학습은 물리적 형태와 독립적으로 이루어지는 것이 아니라 체화(Embodiment)가 만들어내는 가능성과 한계 안에서 이루어집니다.

체화 학습은 자연스럽게 지각-행동 루프(Perception-Action Loop)를 중심으로 구성됩니다. 센서는 환경과 에이전트의 내부 상태에 대한 관측(Observations)을 제공하고, 지각은 이러한 신호를 의사결정(Decision Making)에 유용한 표현(Representations)으로 변환합니다. 에이전트가 행동을 선택하고 실행하면 자신의 상태와 외부 환경이 모두 변화합니다. 새로운 관측은 그 행동의 결과를 보여주며 다시 학습과 적응(Adaptation)의 기회를 제공합니다.

이러한 상호작용은 시간적으로 연결된 관측-행동 시퀀스(Observation-Action Sequences)의 형태로 경험을 생성합니다. 서로 독립적인 샘플로 구성된 정적 데이터셋(Static Datasets)과 달리 체화 경험은 행동에 의해 상태가 어떻게 변화하는지를 기록합니다. 이러한 시간적 구조(Temporal Structure)를 통해 에이전트는 지각, 행동, 물리 동역학(Physical Dynamics), 결과 사이의 관계를 학습할 수 있으며, 이는 예측(Prediction), 제어(Control), 계획(Planning), 강화학습(Reinforcement Learning), 내부 월드 모델(World Models) 구축의 기반을 제공합니다.

상호작용을 통한 학습은 자연스러운 형태의 지도 신호(Supervision)도 제공합니다. 로봇이 이동하거나 객체를 조작하거나 환경을 탐색하면 이후의 관측을 통해 이전 행동 이후 실제로 어떤 일이 발생했는지를 확인할 수 있습니다. 따라서 모든 사례에 사람이 직접 레이블(Label)을 부여하지 않아도 미래 상태가 이전 상태에 대한 학습 목표가 될 수 있습니다. 이러한 특성으로 인해 자기지도학습(Self-Supervised Learning)은 대량의 체화 경험을 지속적으로 수집하는 시스템에서 특히 중요합니다.

강화학습(Reinforcement Learning)은 체화 학습을 위한 또 하나의 주요 메커니즘입니다. 에이전트는 단순히 어떤 일이 발생할지를 예측하는 것에 그치지 않고 어떤 행동이 바람직한 결과를 만들어내는지를 학습합니다. 보상(Rewards), 비용(Costs), 작업 성공(Task Success), 안전 위반(Safety Violations), 에너지 소비(Energy Consumption), 기타 피드백 신호(Feedback Signals)가 행동을 안내할 수 있습니다. 반복적인 상호작용을 통해 시스템은 상태와 행동을 단기 및 장기적인 결과와 점진적으로 연결합니다.

모방 학습(Imitation Learning)은 체화 에이전트가 모든 기술을 독립적인 탐색(Exploration)을 통해 발견하는 대신 시연(Demonstrations)으로부터 행동을 습득하도록 합니다. 인간 운용자(Human Operators), 전문가 정책(Expert Policies), 다른 로봇이 성공적인 행동과 궤적(Trajectories)의 예시를 제공할 수 있습니다. 학습자는 이러한 시연에서 유용한 행동을 재현하려 하며, 이를 통해 복잡한 조작, 내비게이션(Navigation), 이동(Locomotion), 운용 작업을 학습하는 과정에서 위험하거나 비효율적인 탐색의 양을 줄일 수 있습니다.

그러나 시연만으로는 실제 배치(Deployment) 과정에서 나타나는 모든 상황을 포괄하기 어렵습니다. 작은 오차로 인해 에이전트가 시연 데이터에 존재하지 않았던 상태로 이동하면 추가적인 오차가 누적될 수 있습니다. 따라서 체화 학습은 모방과 실제 상호작용을 결합함으로써 이점을 얻을 수 있으며, 초기 시연으로 습득한 행동을 추가 경험을 통해 수정하고 확장할 수 있습니다. 강화학습, 교정 피드백(Corrective Feedback), 온라인 적응(Online Adaptation)은 시연 기반 초기화를 보완할 수 있습니다.

탐색(Exploration)은 체화 에이전트가 충분히 다양한 상태와 행동을 경험하지 않고서는 중요한 환경 관계를 학습할 수 없기 때문에 필수적입니다. 무작위 탐색(Random Exploration)은 시뮬레이션에서는 허용될 수 있지만 실제 물리 하드웨어에서는 비효율적이거나 위험할 수 있습니다. 보다 구조화된 탐색은 충돌, 불안정성, 장비 손상, 위험한 행동을 방지하는 제약조건을 준수하면서 익숙하지 않은 상태, 정보 가치가 높은 상호작용, 불확실한 동역학(Uncertain Dynamics), 새로운 객체를 탐색할 수 있습니다.

능동 지각(Active Perception)은 행동 자체가 어떻게 학습과 환경 이해를 향상시킬 수 있는지를 보여줍니다. 에이전트는 현재의 센서 관측 시점(Sensory Viewpoint)을 수동적으로 받아들일 필요가 없습니다. 카메라를 회전하거나, 객체 주변으로 이동하거나, 특정 영역에 접근하거나, 고도를 변경하거나, 객체를 조작하여 더 많은 정보를 포함하는 관측을 획득할 수 있습니다. 따라서 지각은 불확실성을 감소시키고 내부 표현의 품질을 향상시키기 위해 행동을 선택하는 상호작용적 과정(Interactive Process)이 됩니다.

표현 학습(Representation Learning)은 원시 체화 관측(Raw Embodied Observations)이 일반적으로 고차원적이고 다중모달(Multimodal)이기 때문에 필수적입니다. 카메라, 라이다(LiDAR), 레이더(Radar), 촉각 센서(Tactile Sensors), 고유수용감각(Proprioception), 힘 측정(Force Measurements), 오디오(Audio), 지도(Maps), 언어(Language)는 서로 보완적인 정보를 제공할 수 있습니다. 학습된 표현은 이러한 관측을 특징(Features)이나 잠재 상태(Latent States)로 압축하여 원시 센서 입력의 불필요한 변화를 줄이면서 예측과 행동에 필요한 정보를 유지합니다.

강력한 체화 표현(Embodied Representation)은 단순한 외형 이상의 정보를 포착해야 합니다. 객체 정체성(Object Identity), 기하학(Geometry), 움직임(Motion), 공간적 관계(Spatial Relationships), 접촉(Contact), 어포던스(Affordances), 에이전트 상태(Agent State), 작업 관련성(Task Relevance)은 모두 미래 행동에 영향을 미칠 수 있습니다. 또한 관측 시점, 조명, 센서 가시성(Sensor Visibility), 물리적 구성이 변하더라도 객체나 환경 특징의 의미가 유지되도록 시간적 연속성(Temporal Continuity)을 보존해야 합니다.

어포던스 학습(Affordance Learning)은 지각을 가능한 행동과 직접 연결합니다. 객체를 단순히 범주(Category)나 시각적 외형으로 표현하는 대신 에이전트는 해당 객체가 파지 가능한지(Graspable), 이동 가능한지(Movable), 주행 가능한지(Traversable), 열 수 있는지(Openable), 밀 수 있는지(Pushable), 또는 작업 수행에 다른 방식으로 활용될 수 있는지를 학습할 수 있습니다. 어포던스는 환경뿐만 아니라 신체의 능력에도 의존하므로 순수한 시각적 속성이 아니라 본질적으로 체화된 관계(Embodied Relationships)입니다.

기술 학습(Skill Learning)은 반복적으로 성공하는 상호작용 패턴을 체계화하는 방법을 제공합니다. 저수준 모터 명령(Low-Level Motor Commands)은 도달하기(Reaching), 파지하기(Grasping), 회전하기(Turning), 오르기(Climbing), 도킹하기(Docking), 추종하기(Following), 회피하기(Avoiding)와 같은 재사용 가능한 행동으로 결합될 수 있습니다. 일단 학습된 기술은 계획을 위한 상위 수준 행동(High-Level Actions)으로 사용될 수 있으며, 계층적 구성(Hierarchical Organization)은 장기 작업에서 모든 액추에이터 명령을 직접 추론할 필요성을 줄여 확장 가능한 행동 학습을 지원합니다.

체화 학습은 동역학(Dynamics)도 고려해야 합니다. 동일한 명령이라도 페이로드(Payload), 지형(Terrain), 마찰(Friction), 배터리 상태(Battery Condition), 접촉 상태(Contact State), 액추에이터 특성(Actuator Characteristics), 외부 외란(External Disturbances)에 따라 서로 다른 결과를 생성할 수 있습니다. 반복적인 상호작용을 통해 에이전트는 다양한 조건에서 자신의 신체가 어떻게 반응하는지를 학습하고 이에 따라 제어를 적응시킬 수 있습니다. 이를 통해 물리적 행동을 사전에 완전하게 모델링하기 어려운 경우 학습이 해석적 모델(Analytical Models)을 보완할 수 있습니다.

시뮬레이션(Simulation)은 실제 물리적 상호작용이 비용이 많이 들고 속도에 제한이 있기 때문에 체화 경험을 획득하기 위한 중요한 환경을 제공합니다. 로봇은 실제 하드웨어를 손상시키지 않고 다양한 시뮬레이션 환경에서 내비게이션, 조작, 이동, 협력(Coordination)을 반복적으로 연습할 수 있습니다. 또한 시뮬레이션에서는 드문 실패(Rare Failures)와 극한 조건(Extreme Conditions)을 안전하게 탐색할 수 있으므로 실제 환경에서 의도적으로 생성하기 어렵거나 허용할 수 없는 학습 경험을 만들 수 있습니다.

그러나 시뮬레이션에서 획득한 경험이 자동으로 현실에 전이되는 것은 아닙니다. 센싱(Sensing), 접촉, 마찰, 액추에이터 응답(Actuator Response), 기하학, 렌더링(Rendering), 환경 변동성(Environmental Variability)의 차이는 시뮬레이션-현실 격차(Simulation-to-Reality Gap)를 발생시킵니다. 도메인 랜덤화(Domain Randomization), 시스템 식별(System Identification), 실제 세계 미세조정(Real-World Fine-Tuning), 학습된 잔차 동역학(Learned Residual Dynamics), 지속적인 적응을 통해 학습자가 다양한 조건을 경험하도록 하고 실제 배치 이후 잘못된 가정을 수정함으로써 이러한 격차를 줄일 수 있습니다.

월드 모델(World Models)은 축적된 상호작용을 예측 지식(Predictive Knowledge)으로 변환함으로써 체화 학습의 또 다른 중요한 구성요소가 됩니다. 에이전트는 상태가 어떻게 변화하고 행동이 미래 조건에 어떤 영향을 미치는지를 학습한 뒤 이 내부 모델을 사용하여 가능한 경험을 상상할 수 있습니다. 물리적인 시행착오에 전적으로 의존하는 대신 후보 행동을 내부적으로 평가하고 예측된 궤적을 활용하여 계획, 정책 학습(Policy Learning), 탐색을 지원할 수 있습니다.

메모리(Memory)는 체화 학습을 즉각적인 센서 정보의 범위를 넘어 확장합니다. 단기 메모리(Short-Term Memory)는 움직임이나 숨겨진 상태(Hidden State)를 추론하는 데 필요한 최근 관측과 행동을 유지할 수 있으며, 장기 메모리(Long-Term Memory)는 장소, 객체, 이전 상호작용, 기술, 작업 결과에 대한 지식을 보존할 수 있습니다. 메모리를 통해 에이전트는 각각의 관측을 매번 독립적이고 새로운 상황으로 처리하는 대신 시간에 걸쳐 축적된 경험을 활용할 수 있습니다.

체화 시스템이 장기간 운용될 경우 지속 학습(Continual Learning)이 필요해집니다. 환경은 변화하고, 하드웨어는 노후화되며, 페이로드가 달라지고, 새로운 작업이 등장하고, 이전에는 알지 못했던 객체나 조건을 만나게 됩니다. 배치 전에 한 번 학습된 고정 모델(Fixed Model)만으로는 미래의 모든 상황을 표현할 수 없습니다. 따라서 학습 시스템은 유용한 새로운 경험을 통합하면서 기존에 습득한 능력을 치명적 망각(Catastrophic Forgetting)이나 불안정한 적응(Unstable Adaptation)으로부터 보호해야 합니다.

다중 작업 학습(Multi-Task Learning)은 에이전트가 서로 관련되지만 다양한 목표를 경험하도록 함으로써 체화 지능을 향상시킬 수 있습니다. 내비게이션, 객체 상호작용(Object Interaction), 검사(Inspection), 배송(Delivery), 조작, 탐색은 지각 표현과 물리적 지식을 공유할 수 있습니다. 여러 작업에 걸쳐 학습하면 각각의 행동을 위한 별도의 시스템을 구축하는 대신 재사용 가능한 특징과 기술을 형성할 수 있습니다. 이러한 공유 구조(Shared Structure)는 변화하는 임무에서 동작해야 하는 범용 로봇(General-Purpose Robots)에 특히 중요합니다.

전이 학습(Transfer Learning)은 이러한 원리를 서로 다른 환경과 플랫폼으로 확장합니다. 하나의 건물, 지형 유형, 로봇 구성, 작업에서 학습한 지식은 다른 환경에서도 유용한 출발점이 될 수 있습니다. 성공적인 전이를 위해서는 일반화 가능한 구조(Generalizable Structure)와 체화에 특화된 세부사항(Embodiment-Specific Details)을 구분해야 합니다. 공유된 지각이나 세계 지식은 재사용할 수 있지만, 제어 정책(Control Policies)과 동역학 표현은 서로 다른 센서, 액추에이터, 형태(Morphology), 운용 조건에 맞게 적응해야 할 수 있습니다.

안전(Safety)은 실수가 실제 물리 세계에서 발생하기 때문에 체화 학습에 강력한 제약조건을 부여합니다. 탐색과 온라인 적응은 충돌 한계(Collision Limits), 안정성 요구사항(Stability Requirements), 액추에이터 제약조건, 인간 안전 영역(Human Safety Zones), 운용 규칙(Operational Rules)을 준수해야 합니다. 시뮬레이션, 시연, 안전 필터(Safety Filters), 제약 최적화(Constrained Optimization), 불확실성 추정(Uncertainty Estimation), 감독 메커니즘(Supervisory Mechanisms)을 활용하면 시스템이 상호작용을 통해 새로운 지식을 획득하면서도 위험을 줄일 수 있습니다.

궁극적으로 체화 학습(Embodied Learning)은 지능을 수동적인 패턴 인식(Passive Pattern Recognition)에서 센싱(Sensing), 행동(Acting), 예측(Predicting), 평가(Evaluating), 적응(Adapting)이 지속적으로 반복되는 과정으로 전환합니다. 에이전트의 신체는 현실과 어떻게 상호작용할 수 있는지를 결정하고, 경험은 이러한 상호작용의 결과를 가르칩니다. 지각, 자기지도학습, 모방 학습, 강화학습, 월드 모델, 메모리, 시뮬레이션, 지속적인 적응을 결합함으로써 체화 시스템은 점진적으로 더욱 높은 수준의 능력과 유연성을 갖춘 물리 지능(Physical Intelligence)을 발전시킬 수 있습니다.

## 03.01. Embodied Reinforcement Learning

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

체화 강화학습(Embodied Reinforcement Learning)은 강화학습(Reinforcement Learning)을 신체(Body)를 통해 물리적 또는 가상 환경과 상호작용하면서 학습하는 에이전트(Agent)로 확장합니다. 에이전트는 단순히 추상적인 상태(State)를 행동(Action)에 매핑하는 것이 아니라 감각 관측(Sensory Observations)을 받고, 운동 명령(Motor Commands)을 생성하며, 물리적 결과를 경험하고, 피드백(Feedback)을 이용하여 행동을 개선합니다. 따라서 학습은 지각(Perception), 행동, 환경(Environment), 적응(Adaptation)을 연결하는 폐쇄형 상호작용 루프(Closed Interaction Loop)에서 발생합니다.

에이전트의 체화(Embodiment)는 강화학습 문제의 구조를 결정합니다. 바퀴형 로봇(Wheeled Robot), 4족 보행 로봇(Quadruped), 매니퓰레이터(Manipulator), 드론(Drone), 자율주행 차량(Autonomous Vehicle)은 서로 다른 센서, 액추에이터(Actuators), 운동 제약조건(Motion Constraints), 동역학(Dynamics), 행동 공간(Action Spaces)을 가집니다. 따라서 동일한 환경 목표라도 형태(Morphology)에 따라 근본적으로 다른 정책(Policies)이 필요할 수 있습니다. 체화 강화학습은 플랫폼의 물리적 능력과 한계에 적합한 행동을 학습해야 합니다.

각각의 상호작용 단계에서 에이전트는 현재 상황의 일부를 설명하는 관측(Observations)을 받습니다. 이러한 관측에는 이미지, 라이다(LiDAR), 레이더(Radar), 촉각 측정(Tactile Measurements), 관절 위치(Joint Positions), 속도(Velocities), 힘(Forces), 관성 측정(Inertial Measurements), 지도(Maps), 작업 정보(Task Information)가 포함될 수 있습니다. 센서는 불완전하고 잡음이 포함된 정보를 제공하기 때문에 관측이 항상 실제 환경 상태와 동일하지는 않습니다. 따라서 정책은 종종 연속적인 관측으로부터 유용한 숨겨진 상태(Hidden State)를 추론해야 합니다.

이후 에이전트는 자신의 정책(Policy)에 따라 행동을 선택합니다. 행동은 휠 속도(Wheel Velocities), 조향 명령(Steering Commands), 관절 토크(Joint Torques), 목표 자세(Target Poses), 비행 제어(Flight Controls), 파지 명령(Grasp Commands), 또는 상위 수준 기술(High-Level Skills)에 해당할 수 있습니다. 행동이 실행되면 환경은 새로운 상태로 전이되고 또 다른 관측을 생성합니다. 강화학습은 그 결과로 발생한 보상(Reward) 또는 비용(Cost)을 이용하여 선택된 행동이 바람직한 단기 및 장기 결과에 기여했는지를 판단합니다.

보상 설계(Reward Design)는 물리적 행동이 일반적으로 여러 목적을 포함하기 때문에 체화 강화학습에서 특히 중요합니다. 내비게이션 로봇(Navigation Robot)은 목적지에 도달하는 동시에 충돌을 피하고, 에너지를 최소화하고, 안정성을 유지하며, 운용 경계(Operational Boundaries)를 준수해야 할 수 있습니다. 매니퓰레이터는 작업 완료(Task Completion), 접촉력(Contact Force), 정밀도(Precision), 실행 시간(Execution Time), 하드웨어 안전(Hardware Safety)을 균형 있게 고려해야 합니다. 잘못 설계된 보상은 의도된 작업을 위반하면서도 기술적으로 보상만 최대화하는 예상치 못한 행동을 만들 수 있습니다.

희소 보상(Sparse Rewards)은 성공적인 결과가 긴 행동 시퀀스 이후에만 나타날 수 있기 때문에 또 다른 문제를 발생시킵니다. 로봇은 멀리 떨어진 목표에 도달하거나 복잡한 조작 작업을 완료한 이후에야 의미 있는 긍정적 피드백을 받을 수 있습니다. 중간 진행 신호(Intermediate Progress Signals), 시연(Demonstrations), 커리큘럼 학습(Curriculum Learning), 계층적 기술(Hierarchical Skills), 목표 조건부 학습(Goal-Conditioned Learning), 학습된 보상 모델(Learned Reward Models)은 장기적인 신용 할당(Long-Horizon Credit Assignment)을 보다 쉽게 수행할 수 있도록 추가적인 구조를 제공할 수 있습니다.

신용 할당(Credit Assignment)은 이전의 어떤 행동이 이후의 성공이나 실패에 영향을 주었는지를 결정합니다. 물리적 작업에는 지연된 결과(Delayed Consequences)가 존재할 수 있습니다. 예를 들어 불안정한 발 디딤(Unstable Foothold)은 몇 단계 이후 넘어짐을 발생시킬 수 있고, 잘못된 파지(Poor Grasp)는 객체를 들어 올린 이후에야 실패할 수 있습니다. 강화학습 알고리즘은 경험을 통해 정보를 이전 시점으로 전달하여 정책이 초기 의사결정과 최종적인 결과 사이의 관계를 점진적으로 학습하도록 해야 합니다.

탐색(Exploration)은 에이전트가 다양한 대안을 시도하지 않고서는 유용한 행동을 발견할 수 없기 때문에 필요합니다. 그러나 물리 시스템에서 제한되지 않은 탐색은 문제가 될 수 있습니다. 무작위 행동(Random Actions)은 충돌, 낙상, 과도한 액추에이터 부하(Actuator Loads), 객체 손상, 인간과의 위험한 상호작용을 일으킬 수 있습니다. 따라서 체화 강화학습은 탐색을 제약조건(Constraints), 안전 필터(Safety Filters), 시연, 시뮬레이션(Simulation), 보수적 정책(Conservative Policies), 불확실성 추정(Uncertainty Estimates)과 결합하여 위험한 실험을 제한하는 경우가 많습니다.

시뮬레이션은 실제 물리 하드웨어를 지속적으로 작동시키지 않고도 수백만 번의 상호작용을 생성할 수 있기 때문에 대규모 강화학습을 위한 실용적인 환경을 제공합니다. 여러 시뮬레이션 에이전트를 병렬로 실행하여 경험을 수집하면 정책 학습 속도를 크게 높일 수 있습니다. 또한 시뮬레이션에서는 실제 로봇으로 반복적으로 재현하기에는 비용이 많이 들거나 위험한 희귀한 실패(Rare Failures), 극한 조건(Extreme Conditions), 랜덤화된 환경(Randomized Environments)을 통제된 방식으로 경험할 수 있습니다.

그러나 시뮬레이션에서 학습된 정책은 시뮬레이션-현실 격차(Simulation-to-Reality Gap)를 해결해야 합니다. 마찰(Friction), 접촉(Contact), 액추에이터 응답(Actuator Response), 센서 잡음(Sensor Noise), 지연시간(Latency), 기하학(Geometry), 조명(Lighting), 지형(Terrain), 기타 물리적 속성의 차이로 인해 시뮬레이션에서 성공한 행동이 실제 배치(Deployment) 이후 실패할 수 있습니다. 도메인 랜덤화(Domain Randomization)는 학습 과정에서 정책을 다양한 조건에 노출시키며, 시스템 식별(System Identification)과 실제 환경 적응(Real-World Adaptation)은 특정 물리 플랫폼과의 차이를 줄일 수 있습니다.

실제 환경 강화학습(Real-World Reinforcement Learning)은 시뮬레이션이 완벽하게 재현할 수 없는 정보를 제공합니다. 물리적 상호작용은 기계적 유연성(Mechanical Compliance), 마모(Wear), 백래시(Backlash), 진동(Vibration), 변화하는 접지력(Traction), 센서 아티팩트(Sensor Artifacts), 복잡한 접촉 행동과 같은 모델링되지 않은 효과를 드러냅니다. 따라서 실용적인 학습 아키텍처는 대규모 시뮬레이션 학습으로 시작한 뒤 신중하게 제한된 실제 경험을 이용하여 정책을 실제 운용 조건에 맞게 보정(Calibrate), 개선(Refine), 적응시킬 수 있습니다.

실제 체화 경험은 비용이 많이 들기 때문에 샘플 효율성(Sample Efficiency)이 매우 중요합니다. 로봇에서 하나의 상호작용에는 수초 또는 수분이 필요할 수 있지만 동일한 과정은 시뮬레이션에서 훨씬 빠르게 수행할 수 있으며, 기계 부품의 운용 수명도 제한되어 있습니다. 수집된 궤적(Trajectories)을 재사용하고, 예측 모델(Predictive Models)을 학습하고, 시연을 활용하거나, 오프라인 학습(Offline Learning)을 수행하는 알고리즘은 각각의 물리적 상호작용에서 더 많은 정보를 추출하여 필요한 하드웨어 실험량을 줄일 수 있습니다.

오프라인 강화학습(Offline Reinforcement Learning)은 환경과 즉시 상호작용하지 않고 이전에 수집된 경험을 이용하여 정책을 학습할 수 있도록 합니다. 로봇 운용 로그(Operation Logs), 시연, 원격조작(Teleoperation), 시뮬레이션, 이전 정책으로부터 얻은 데이터는 상태-행동-전이 시퀀스(State-Action-Transition Sequences)를 제공할 수 있습니다. 대규모 과거 데이터셋을 안전하게 활용할 수 있다는 점에서 체화 시스템에 매력적이지만, 학습된 정책이 사용 가능한 데이터에 포함된 분포에서 지나치게 벗어난 행동을 선택하지 않도록 해야 합니다.

모방 학습(Imitation Learning)과 강화학습은 서로 매우 보완적입니다. 시연은 이미 의미 있는 행동을 수행할 수 있는 강력한 초기 정책(Initial Policy)을 제공할 수 있으며, 강화학습은 이후 상호작용과 작업 피드백을 통해 성능을 향상시킬 수 있습니다. 이를 통해 에이전트가 기본적인 행동을 무작위 탐색만으로 발견해야 하는 필요성을 줄일 수 있습니다. 따라서 인간 시연(Human Demonstrations)은 더욱 자율적인 적응이 시작될 수 있는 행동 사전지식(Behavioral Priors)의 역할을 할 수 있습니다.

월드 모델(World Models)은 행동이 미래 상태에 어떤 영향을 미치는지를 학습함으로써 체화 강화학습을 더욱 향상시킬 수 있습니다. 모든 행동 가설(Behavioral Hypotheses)을 실제 물리적 실행으로 평가하는 대신 에이전트는 후보 미래를 내부적으로 시뮬레이션할 수 있습니다. 모델 기반 강화학습(Model-Based Reinforcement Learning)은 이러한 예측을 계획(Planning)이나 정책 개선(Policy Improvement)에 사용하며, 모델 프리 강화학습(Model-Free Reinforcement Learning)은 경험으로부터 직접 행동을 학습합니다. 하이브리드 아키텍처(Hybrid Architectures)는 예측적 추론(Predictive Reasoning)과 빠르게 실행되는 학습된 정책을 결합할 수 있습니다.

잠재 월드 모델(Latent World Models)은 관측에 고차원 감각 데이터가 포함될 때 특히 유용합니다. 이미지, 포인트 클라우드(Point Clouds), 촉각 측정, 고유수용감각(Proprioception)을 행동과 관련된 정보를 보존하는 압축된 잠재 상태(Latent States)로 인코딩할 수 있습니다. 학습된 동역학 모델(Learned Dynamics Model)은 이 잠재 공간(Latent Space)에서 상태 전이를 예측하여 모든 센서 측정값을 다시 생성하지 않고도 가상 롤아웃(Imagined Rollouts)을 수행할 수 있도록 합니다. 강화학습은 실제 경험과 내부적으로 생성된 경험을 모두 이용하여 정책을 최적화할 수 있습니다.

환경이 부분 관측 가능(Partially Observable)할 때는 메모리(Memory)가 중요해집니다. 로봇은 일시적으로 객체를 보지 못하거나, 시각적으로 유사한 장소를 만나거나, 이전에 받은 지시를 기억해야 할 수 있습니다. 순환 신경망(Recurrent Networks), 트랜스포머(Transformers), 외부 메모리(External Memory), 명시적 상태 추정기(Explicit State Estimators)는 시간에 걸쳐 관측을 통합할 수 있습니다. 이를 통해 형성된 내부 상태(Internal State)는 강화학습 정책이 순간적인 센서 입력뿐만 아니라 과거의 상호작용 이력을 바탕으로 행동을 선택하도록 합니다.

계층적 강화학습(Hierarchical Reinforcement Learning)은 여러 추상화 수준에서 행동을 구성합니다. 저수준 정책(Low-Level Policies)은 이동, 조향, 파지, 안정화(Stabilization)를 제어하고, 상위 수준 정책(High-Level Policies)은 재사용 가능한 기술(Skills)이나 하위 목표(Subgoals)를 선택할 수 있습니다. 이동 매니퓰레이터(Mobile Manipulator)는 먼저 객체 근처로 이동하고, 베이스 위치를 조정하고, 팔을 뻗고, 객체를 파지한 뒤 운반할 수 있습니다. 계층적 구성은 실질적인 계획 깊이(Planning Depth)를 줄여 장기 체화 작업(Long-Horizon Embodied Tasks)을 보다 쉽게 처리하도록 합니다.

목표 조건부 강화학습(Goal-Conditioned Reinforcement Learning)은 원하는 목표를 정책 입력의 일부로 제공하여 하나의 정책이 서로 다른 목적을 수행하도록 합니다. 목표는 공간적 위치(Spatial Positions), 객체 구성(Object Configurations), 목표 이미지(Target Images), 의미론적 조건(Semantic Conditions), 작업 지시(Task Instructions)를 나타낼 수 있습니다. 각각의 목적에 대해 완전히 별도의 정책을 학습하는 대신 시스템은 현재 상태, 원하는 상태, 행동 사이의 관계를 학습하여 관련된 여러 작업에서 경험을 재사용할 수 있습니다.

다중 작업 강화학습(Multi-Task Reinforcement Learning) 역시 서로 다른 행동 사이에서 공유 가능한 지식을 학습하는 것을 목표로 합니다. 내비게이션(Navigation), 검사(Inspection), 조작(Manipulation), 배송(Delivery), 탐색(Exploration), 도킹(Docking)은 공통적인 지각 및 운동 능력을 활용할 수 있습니다. 공동 학습(Joint Learning)을 통해 새로운 작업의 학습을 가속하는 재사용 가능한 표현과 기술을 형성할 수 있습니다. 중요한 과제는 서로 충돌하는 목표들이 학습을 방해하지 않도록 하면서 실제로 전이 가능한 지식을 유지하는 것입니다.

커리큘럼 학습(Curriculum Learning)은 에이전트의 능력이 발전함에 따라 작업 난이도를 점진적으로 증가시킬 수 있습니다. 이동 정책(Locomotion Policy)은 단순한 평지에서 시작하여 경사면, 장애물, 느슨한 지면, 외란이 있는 환경으로 발전할 수 있습니다. 조작 에이전트는 독립된 객체를 파지하는 것부터 시작하여 복잡하게 객체가 배치된 환경을 처리할 수 있습니다. 이러한 단계적 학습은 탐색 난이도를 낮추고 이전에 습득한 기술을 더 복잡한 체화 행동의 기반으로 사용할 수 있도록 합니다.

지속 강화학습(Continual Reinforcement Learning)은 초기 학습 이후에도 적응을 계속하도록 확장합니다. 수개월 또는 수년 동안 운용되는 로봇은 변화하는 환경, 페이로드(Payload), 하드웨어 특성, 사용자, 임무 요구사항을 경험하게 됩니다. 학습 시스템은 기존 기술을 파괴하지 않으면서 유용한 새로운 경험을 통합해야 합니다. 리플레이(Replay), 정규화(Regularization), 모듈형 정책(Modular Policies), 기술 라이브러리(Skill Libraries), 통제된 파라미터 갱신(Controlled Parameter Updates)은 새로운 학습을 위한 가소성(Plasticity)과 기존 행동을 보존하기 위한 안정성(Stability)의 균형을 지원할 수 있습니다.

안전(Safety)은 체화 강화학습을 규정하는 핵심 제약조건 가운데 하나입니다. 정책은 학습 중에도 충돌 한계(Collision Limits), 액추에이터 운용 범위(Actuator Envelopes), 안정성 조건(Stability Conditions), 인간 안전 요구사항(Human Safety Requirements), 운용 규칙(Operational Rules)을 준수해야 합니다. 안전 계층(Safety Layers)은 위험한 행동을 차단할 수 있고, 제약 강화학습(Constrained Reinforcement Learning)은 명시적인 제한을 포함할 수 있으며, 불확실성 인지 시스템(Uncertainty-Aware Systems)은 익숙하지 않은 상황에서 더욱 보수적으로 행동할 수 있습니다. 학습 성능은 물리적 위험 관리(Physical Risk Management)와 분리될 수 없습니다.

수치적인 보상 함수를 명확하게 정의하기 어려운 경우에는 인간 피드백(Human Feedback)이 체화 강화학습을 안내할 수도 있습니다. 운용자는 행동의 우선순위를 평가하거나, 교정(Corrections)을 제공하거나, 선호하는 행동을 시연하거나, 에이전트가 위험한 상태에 접근할 때 개입할 수 있습니다. 학습된 선호 모델(Preference Models)이나 보상 모델은 이러한 피드백을 학습 신호로 변환할 수 있습니다. 이를 통해 수작업으로 정의하기 어려운 부드러움(Smoothness), 유용성(Usefulness), 예측 가능성(Predictability), 사회적으로 적절한 행동(Socially Appropriate Behavior)과 같은 특성을 최적화할 수 있습니다.

궁극적으로 체화 강화학습(Embodied Reinforcement Learning)은 물리적 상호작용(Physical Interaction)을 행동 지식(Behavioral Knowledge)으로 변환합니다. 에이전트는 환경을 지각하고, 자신의 신체를 통해 행동하며, 결과를 관측하고, 피드백을 받은 뒤 정책을 갱신합니다. 시뮬레이션, 시연, 월드 모델, 메모리, 계층적 기술, 오프라인 데이터, 지속 학습, 안전 메커니즘(Safety Mechanisms)은 이러한 순환을 더욱 실용적으로 만듭니다. 반복적인 경험을 통해 시스템은 단순히 데이터에 기반한 정책이 아니라 물리 세계에서 실제로 행동했을 때 발생하는 결과에 기반한 정책을 점진적으로 발전시킵니다.

## 03.02. Imitation Learning [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

모방 학습(Imitation Learning)은 체화 에이전트(Embodied Agent)가 인간, 전문가 제어기(Expert Controllers), 또는 이전에 학습된 에이전트가 생성한 시연(Demonstrations)을 관찰하여 행동을 습득할 수 있도록 합니다. 학습자는 강화학습(Reinforcement Learning)과 시행착오 탐색(Trial-and-Error Exploration)을 통해 모든 행동을 스스로 발견하는 대신, 시연된 상태-행동 관계(State-Action Relationships)를 구조화된 경험(Structured Experience)으로 활용합니다. 이를 통해 위험한 실험을 크게 줄이고 로보틱스(Robotics)와 자율 시스템(Autonomous Systems)에서 복잡한 행동의 습득을 가속할 수 있습니다.

체화 환경(Embodied Settings)에서 시연은 이미지, 라이다 관측(LiDAR Observations), 고유수용감각 측정(Proprioceptive Measurements), 객체 상태(Object States), 로봇 구성(Robot Configurations), 행동(Actions), 시간에 따른 작업 결과(Task Outcomes)를 포함할 수 있습니다. 이러한 시연에는 어떤 행동이 선택되었는지뿐만 아니라 그 행동이 어떤 맥락(Context)에서 적절했는지도 포함됩니다. 따라서 학습 문제는 고정된 궤적(Trajectory)을 단순히 재생하는 것이 아니라 새로운 관측에서도 유용한 행동을 재현할 수 있는 정책(Policy)이나 목적(Objective)을 추론하는 것입니다.

행동 복제(Behavioral Cloning)는 가장 직접적인 형태의 모방 학습입니다. 전문가 시연을 지도학습 데이터(Supervised Learning Data)로 취급하고, 관측된 상태나 감각 입력(Sensory Input)으로부터 전문가 행동을 예측하도록 정책을 학습합니다. 데이터셋에 관측과 시연 행동의 쌍이 포함되어 있다면 정책은 자신이 예측한 행동과 시연자가 선택한 행동 사이의 차이를 최소화하여 관측에서 행동으로의 매핑(Mapping)을 학습합니다.

연속적인 로봇 제어(Continuous Robot Control)에서 행동 복제는 조향각(Steering Angles), 휠 속도(Wheel Velocities), 관절 목표값(Joint Targets), 토크(Torques), 말단장치 명령(End-Effector Commands), 기타 연속 행동을 예측할 수 있습니다. 이산적 의사결정(Discrete Decision) 문제에서는 이동(Move), 정지(Stop), 파지(Grasp), 해제(Release), 회전(Turn), 또는 재사용 가능한 기술(Skill)의 선택과 같은 행동을 예측할 수 있습니다. 정확한 출력 표현(Output Representation)은 시연이 신뢰할 수 있는 행동 정보를 제공하는 수준과 물리적 제어기(Physical Controller)가 요구하는 명령 수준에 맞아야 합니다.

일반적인 행동 복제 파이프라인(Behavioral-Cloning Pipeline)은 시연을 수집하고 이를 관측-행동 샘플(Observation-Action Samples)로 변환하는 것에서 시작합니다. 센서 관측은 전처리(Preprocessing)되거나 인코딩(Encoding)되고, 그 결과로 생성된 표현이 정책 네트워크(Policy Network)에 입력됩니다. 네트워크는 행동을 예측하며, 이 예측값을 적절한 지도 손실(Supervised Loss)을 사용하여 시연 행동과 비교합니다. 이후 기울기 기반 최적화(Gradient-Based Optimization)를 통해 네트워크 파라미터를 조정하여 예측 행동이 점차 전문가 행동과 유사해지도록 합니다.

코드(Code)에서 이러한 과정은 일반적인 지도학습(Supervised Training)과 유사한 형태로 구현됩니다. 데이터셋 로더(Dataset Loader)는 관측과 전문가 행동을 포함하는 배치(Batches)를 제공하고, 신경망(Neural Network)은 예측 행동을 계산하며, 손실 함수(Loss Function)는 예측 오차를 측정합니다. 연속 행동에는 평균 제곱 오차(Mean Squared Error)를 사용할 수 있고 이산 선택에는 교차 엔트로피(Cross-Entropy)를 사용할 수 있습니다. 최적화기(Optimizer)는 이러한 모방 목적함수(Imitation Objective)에서 계산된 기울기를 이용하여 정책을 반복적으로 갱신합니다.

행동 복제의 단순성은 표준 딥러닝 파이프라인(Standard Deep-Learning Pipelines)을 이용하여 대규모 시연 데이터셋을 활용할 수 있게 한다는 점에서 중요한 장점입니다. 충분한 표현력을 가진 지각 인코더(Perception Encoders)를 사용할 경우 고차원 관측(High-Dimensional Observations)으로부터 직접 학습할 수도 있습니다. 카메라, 다중모달 센서 특징(Multimodal Sensor Features), 언어 지시(Language Instructions), 로봇 상태를 정책 입력으로 결합하여 시연을 통해 통합된 지각-행동(Perception-to-Action) 행동을 학습할 수 있습니다.

그러나 행동 복제는 분포 이동(Distribution Shift) 문제를 가집니다. 학습 중에는 정책이 주로 전문가가 방문한 상태를 관측하지만 실제 배치(Deployment)에서는 작은 예측 오차만으로도 에이전트가 익숙하지 않은 상태로 이동할 수 있습니다. 그러면 해당 상황이 시연에서 충분히 표현되지 않았기 때문에 정책이 더 큰 오차를 발생시킬 수 있습니다. 이러한 편차가 시간에 따라 누적되면서 오차 누적 문제(Compounding-Error Problem)가 발생하며, 이는 특히 장기 체화 작업(Long-Horizon Embodied Tasks)에서 심각할 수 있습니다.

데이터셋 다양성(Dataset Diversity)을 증가시키면 서로 다른 환경, 초기 상태(Starting States), 객체 구성(Object Configurations), 외란(Disturbances), 복구 상황(Recovery Situations)에 대한 시연을 수집하여 이러한 문제를 줄일 수 있습니다. 이상적인 작업 실행뿐만 아니라 교정 행동(Corrective Behavior)도 시연에 포함하는 것이 바람직합니다. 로봇이 정렬 오차(Misalignment), 휠 슬립(Wheel Slip), 불완전한 파지(Imperfect Grasp), 예상하지 못한 장애물 움직임으로부터 전문가가 어떻게 복구하는지를 학습했다면 자율 운용 과정에서 발생하는 편차에 더 효과적으로 대응할 수 있습니다.

상호작용형 모방 학습(Interactive Imitation Learning)은 학습자의 정책이 실제로 방문하는 상태에서 전문가 지도를 수집하여 분포 불일치(Distribution Mismatch)를 더욱 직접적으로 해결할 수 있습니다. 고정된 오프라인 데이터셋(Offline Dataset)에만 의존하는 대신 시스템이 현재 정책을 실행하고 필요할 때 교정이나 전문가 행동을 제공받습니다. 따라서 학습 분포(Training Distribution)는 학습자 자신의 행동으로 발생하는 상황까지 점진적으로 확장되며, 정책은 자신의 오차에 더욱 강건(Robust)해질 수 있습니다.

행동 복제는 전문가 행동이 직접적인 학습 목표로 관측 가능하고 의미가 있을 때 특히 적합합니다. 그러나 많은 상황에서는 서로 다른 개별 행동들이 동일한 근본적 목표를 달성할 수 있기 때문에 전문가의 행동도 다양하게 나타날 수 있습니다. 단순히 행동만 복제하면 그러한 행동이 선택된 이유를 이해하지 못한 채 표면적인 행동만 재현할 수 있습니다. 이러한 문제는 행동 매핑만 학습하는 대신 시연의 기반이 되는 목적(Objective)이나 선호(Preference)를 추론하는 방법의 필요성을 제기합니다.

역강화학습(Inverse Reinforcement Learning)은 시연된 행동으로부터 보상 함수(Reward Function)를 추론하여 이러한 문제를 해결하려 합니다. 일반적인 강화학습은 보상이 이미 알려져 있다고 가정하고 이를 최대화하는 정책을 탐색합니다. 역강화학습은 이 관계를 반대로 적용합니다. 먼저 시연을 관측한 뒤 학습자는 시연된 행동이 합리적이거나 준최적(Near-Optimal)인 것으로 설명될 수 있는 보상 또는 비용 구조(Cost Structure)를 찾습니다.

추론된 보상(Inferred Reward)은 수작업으로 명시하기 어려운 선호를 표현할 수 있습니다. 예를 들어 인간 운전자는 안전(Safety), 진행성(Progress), 부드러움(Smoothness), 여유 거리(Clearance), 편안함(Comfort), 환경 규칙 준수 등을 동시에 고려할 수 있습니다. 로봇 운용자는 속도, 힘(Force), 안정성(Stability), 객체 보호(Object Protection)를 암묵적으로 균형 있게 고려하는 조작 전략을 시연할 수 있습니다. 역강화학습은 이러한 모든 선호를 명시적으로 설계하도록 요구하는 대신 행동으로부터 목적을 복원하려 합니다.

보상 모델(Reward Model)이 추론되면 강화학습이나 계획(Planning)을 사용하여 해당 보상에 따라 정책을 최적화할 수 있습니다. 이를 통해 모방 과정은 개념적으로 두 단계로 분리됩니다. 먼저 시연자가 무엇을 중요하게 생각하는지를 이해하고, 이후 추론된 선호를 만족하는 행동을 찾는 것입니다. 따라서 학습된 정책은 시연에 포함된 정확한 궤적을 그대로 재현하는 것으로 제한되지 않습니다.

이러한 차이는 일반화(Generalization)를 향상시킬 수 있습니다. 전문가가 장애물을 우회하는 하나의 경로를 시연한다면 행동 복제는 주로 관측된 조향 패턴(Steering Pattern)을 재현하도록 학습할 수 있습니다. 반면 역강화학습은 중요한 목적이 장애물을 피하고 적절한 안전 여유(Safety Margin)를 유지하면서 목표에 도달하는 것임을 추론할 수 있습니다. 이후 환경의 기하 구조가 변경되면 플래너는 기존 시연과 다른 경로이지만 동일하게 유효한 궤적을 발견할 수 있습니다.

그러나 여러 보상 함수가 동일한 시연 행동을 설명할 수 있기 때문에 보상 추론(Reward Inference)에는 모호성(Ambiguity)이 존재합니다. 관측된 전문가 궤적만으로는 전문가가 거리(Distance), 에너지(Energy), 안전, 편안함 또는 이러한 요소들의 조합 가운데 무엇을 우선했는지를 고유하게 결정할 수 없습니다. 따라서 역강화학습에는 어떤 추론 목적을 타당한 것으로 간주할지를 제한하는 가정(Assumptions), 정규화(Regularization), 특징 표현(Feature Representations), 확률적 공식화(Probabilistic Formulations)가 필요합니다.

최대 엔트로피 공식화(Maximum-Entropy Formulations)는 전문가가 항상 하나의 완벽한 최적 궤적만 선택한다고 가정하는 대신 전문가 행동을 확률적으로 다루는 대표적인 접근법입니다. 높은 보상을 갖는 시연에는 더 높은 확률을 부여하면서도 다른 행동의 가능성을 유지합니다. 이를 통해 인간이나 로봇 전문가가 비슷한 목표를 추구하면서도 항상 정확히 동일한 행동을 선택하지는 않는다는 실제적인 행동 변동성(Behavioral Variation)을 표현할 수 있습니다.

심층 역강화학습(Deep Inverse Reinforcement Learning)은 수작업으로 정의된 상태 특징(State Features)만으로 충분하지 않은 환경으로 보상 추론을 확장합니다. 신경망을 사용하여 이미지, 공간 표현(Spatial Representations), 객체 관계(Object Relations), 기타 복잡한 관측으로부터 보상 함수를 학습할 수 있습니다. 이를 통해 역강화학습을 체화 지각(Embodied Perception)에 더욱 적합하게 만들 수 있지만, 결과로 생성되는 보상 모델의 해석 가능성(Interpretability)이 낮아질 수 있으며 시연 데이터셋의 편향(Biases)이나 한계를 그대로 학습할 가능성도 있습니다.

따라서 행동 복제(Behavioral Cloning)와 역강화학습(Inverse Reinforcement Learning)은 상호 보완적인 접근법으로 볼 수 있습니다. 행동 복제는 현재 상황에서 전문가가 어떤 행동을 수행할지를 묻는 반면, 역강화학습은 전문가의 행동을 설명할 수 있는 목적이 무엇인지를 묻습니다. 행동 복제는 더 단순하고 직접적인 경우가 많지만, 역강화학습은 학습된 시스템이 새로운 상태나 계획 상황에서 전문가의 의도(Expert Intent)를 적응시켜야 할 때 더 큰 유연성을 제공할 수 있습니다.

하이브리드 시스템(Hybrid Systems)은 두 방법을 결합할 수 있습니다. 행동 복제는 시연된 능력을 빠르게 재현하는 초기 정책(Initial Policy)을 제공하고, 이후 역강화학습이나 강화학습이 추론된 목적에 따라 행동을 추가로 개선할 수 있습니다. 복제된 정책(Cloned Policy)은 보상 기반 최적화(Reward-Driven Optimization)가 시작되기 전에 필요한 탐색량을 감소시키는 유용한 초기화(Initialization) 역할도 할 수 있습니다.

월드 모델(World Models)은 행동의 예측 결과를 표현함으로써 모방 학습을 더욱 강화할 수 있습니다. 에이전트는 단순히 관측에서 행동으로의 직접적인 매핑만 학습하는 대신 전문가 행동이 시간에 따라 환경을 어떻게 변화시키는지를 시연으로부터 이해할 수 있습니다. 이후 후보 행동을 내부적으로 시뮬레이션하고 시연된 목표나 추론된 보상에 따라 비교함으로써 모방 학습을 예측 계획(Predictive Planning) 및 모델 기반 강화학습(Model-Based Reinforcement Learning)과 연결할 수 있습니다.

전문가 시연은 독립적인 상태-행동 쌍이 아니라 시퀀스(Sequences)이기 때문에 시간적 모델링(Temporal Modeling)이 특히 중요합니다. 이전 행동은 이후 관측에 영향을 미치며 올바른 의사결정은 작업 이력(Task History)에 의존할 수 있습니다. 순환 신경망(Recurrent Networks), 트랜스포머(Transformers), 상태 추정기(State Estimators), 명시적 메모리 시스템(Explicit Memory Systems)은 이러한 맥락을 표현하여 모방 정책이 시연된 작업의 진행 상황, 이전 행동, 숨겨진 상태(Hidden State), 장기 의존성(Long-Term Dependencies)을 추론할 수 있도록 합니다.

다중모달 시연(Multimodal Demonstrations)은 로봇 상태, 비전(Vision), 언어(Language), 인간 입력(Human Input)을 결합하여 더욱 풍부한 지도 신호를 제공할 수 있습니다. 언어 지시는 목표를 설명하고 시연은 물리 시스템이 이를 어떻게 달성하는지를 보여줄 수 있습니다. 비전은 환경적 맥락을 제공하고 고유수용감각(Proprioception)은 신체의 구성을 나타냅니다. 다중모달 정책(Multimodal Policy)은 지시, 지각, 체화, 행동 사이의 관계를 학습하여 여러 작업에서 더욱 유연한 일반화를 지원할 수 있습니다.

안전(Safety)은 물리 시스템에서 모방 학습을 사용하는 가장 강력한 동기 가운데 하나입니다. 시연은 에이전트가 자율적인 탐색을 시작하기 전에 성공적인 행동 사례를 제공하여 초기 학습 과정에서 위험한 무작위 행동이 필요한 가능성을 줄입니다. 그러나 시연된 행동이 모든 새로운 상황에서 자동으로 안전한 것은 아닙니다. 실제 배치에서는 여전히 불확실성 추정(Uncertainty Estimation), 안전 제약조건(Safety Constraints), 충돌 검사(Collision Checking), 폴백 행동(Fallback Behavior), 시연 분포 밖 상태(Out-of-Distribution States)에 대한 모니터링이 필요합니다.

모방 학습의 품질은 궁극적으로 시연의 품질(Demonstration Quality)과 범위(Coverage)에 의존합니다. 일관성이 없거나 준최적인 시연, 또는 시간 동기화가 잘못된 데이터는 바람직하지 않은 행동을 학습시킬 수 있으며, 제한된 데이터셋은 익숙한 조건을 벗어난 환경에서 정책 실패를 발생시킬 수 있습니다. 따라서 시연 데이터 수집에서는 전문가 숙련도(Expert Competence), 센서 보정(Sensor Calibration), 행동 타이밍(Action Timing), 환경 다양성(Environment Diversity), 실패 복구(Failure Recovery), 드물지만 운용상 중요한 상황의 포함 여부를 고려해야 합니다.

궁극적으로 모방 학습(Imitation Learning)은 체화 시스템이 전문가의 경험(Expert Experience)을 재사용 가능한 행동 지식(Reusable Behavioral Knowledge)으로 변환할 수 있도록 합니다. 행동 복제(Behavioral Cloning)는 관측에서 시연 행동으로의 직접적인 매핑을 학습하고, 역강화학습(Inverse Reinforcement Learning)은 이러한 행동에 의미를 부여하는 목적을 추론합니다. 상호작용(Interaction), 월드 모델, 강화학습, 메모리(Memory), 안전 메커니즘(Safety Mechanisms)과 결합하면 모방 학습은 인간 또는 전문가 시연으로부터 점점 더 자율적이고 적응적인 물리 지능(Physical Intelligence)으로 발전하기 위한 실용적인 경로를 제공합니다.

## 03.03. Self Supervised Learning

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

자기지도학습(Self-Supervised Learning)은 모든 관측에 사람이 직접 레이블(Label)을 부여하지 않아도 체화 에이전트(Embodied Agent)가 원시 경험(Raw Experience)으로부터 유용한 표현(Representations)과 예측 지식(Predictive Knowledge)을 학습할 수 있도록 합니다. 외부에서 제공되는 주석(Annotations)에 의존하는 대신 학습 시스템은 감각 데이터(Sensory Data) 자체에 이미 존재하는 관계로부터 지도 신호(Supervisory Signals)를 구성합니다. 따라서 시간적 연속성(Temporal Continuity), 다중모달 대응 관계(Multimodal Correspondence), 공간 구조(Spatial Structure), 행동 결과(Action Consequences)가 학습 신호가 될 수 있습니다.

이 원리는 로봇이 운용되는 동안 막대한 양의 레이블 없는 데이터(Unlabeled Data)를 지속적으로 생성하기 때문에 체화 지능(Embodied Intelligence)에서 특히 중요합니다. 카메라는 이미지 시퀀스(Image Sequences)를 수집하고, 라이다(LiDAR)는 기하학적 측정값(Geometric Measurements)을 생성하며, 고유수용감각 센서(Proprioceptive Sensors)는 신체 움직임을 나타내고, 행동은 관측 가능한 환경 변화를 만들어냅니다. 이러한 연속적인 데이터 스트림(Data Stream)을 사람이 직접 레이블링하는 것은 지나치게 많은 비용이 필요하지만, 자기지도학습에서는 경험 자체가 학습 목표를 제공할 수 있습니다.

핵심 아이디어는 이용 가능한 정보의 한 부분으로부터 다른 부분을 예측하도록 학습 문제를 구성하는 것입니다. 모델은 이전 관측으로부터 미래 관측을 예측하거나, 누락된 정보를 복원하거나, 두 측정값이 동일한 물리적 상황에 대응하는지를 판단하거나, 행동이 환경을 어떻게 변화시키는지를 추정할 수 있습니다. 이러한 대리 과제(Proxy Tasks)를 해결하는 과정에서 내부 표현은 이후의 지각(Perception), 계획(Planning), 제어(Control)에 유용한 구조를 포착하도록 학습됩니다.

시간적 예측(Temporal Prediction)은 체화 시스템에서 가장 자연스러운 자기지도 목적함수(Self-Supervised Objective) 가운데 하나를 제공합니다. 시간 t의 관측과 실행된 행동이 주어지면 모델은 시간 t+1의 관측 또는 잠재 상태(Latent State)를 예측할 수 있습니다. 이후 실제 미래 관측이 자동으로 학습 목표가 됩니다. 이러한 과정을 대규모 궤적(Trajectories)에 반복적으로 적용하면 사람이 레이블을 명시적으로 제공하지 않아도 환경 상태, 에이전트 움직임, 행동, 물리 동역학(Physical Dynamics) 사이의 관계를 학습할 수 있습니다.

예측은 반드시 원시 감각 공간(Raw Sensory Space)에서 직접 수행될 필요는 없습니다. 미래 이미지의 모든 픽셀이나 라이다 스캔의 모든 포인트를 생성하려면 많은 연산이 필요하며 행동과 관련 없는 세부정보까지 지나치게 강조할 수 있습니다. 대신 관측을 압축된 잠재 표현(Latent Representations)으로 인코딩하고 미래의 잠재 상태를 예측하도록 학습할 수 있습니다. 이를 통해 시스템은 지속적이며 행동적으로 의미 있는 환경 구조에 더 집중할 수 있습니다.

마스킹 예측(Masked Prediction)은 또 다른 강력한 자기지도 메커니즘(Self-Supervised Mechanism)을 제공합니다. 이미지, 센서 시퀀스, 포인트 클라우드(Point Cloud), 잠재 표현의 일부를 의도적으로 가린 뒤 모델이 나머지 맥락(Context)으로부터 누락된 정보를 복원하거나 예측하도록 학습합니다. 이 문제를 해결하기 위해 네트워크는 고립된 국소 특징에만 의존하는 대신 객체, 기하학(Geometry), 시간적 맥락, 주변 관측 사이의 관계를 학습해야 합니다.

대조 학습(Contrastive Learning)은 어떤 관측들이 서로 관련되어야 하고 어떤 관측들은 구별되어야 하는지를 학습하여 표현을 형성합니다. 동일한 객체의 서로 다른 관측 시점(Views), 하나의 궤적에서 시간적으로 가까운 프레임, 여러 센서에서 동기화된 측정값은 양의 관계(Positive Relationships)를 형성할 수 있습니다. 서로 관련되지 않은 장면이나 시간적으로 멀리 떨어진 경험은 대조 사례가 될 수 있습니다. 학습된 표현은 의미적 또는 물리적으로 관련된 경험을 서로 가깝게 배치하면서 서로 다른 상황의 구별은 유지합니다.

체화 시스템은 에이전트의 움직임이 동일한 물리 세계에 대한 여러 관측 시점을 자연스럽게 생성하기 때문에 대조 학습을 위한 특히 풍부한 기회를 제공합니다. 로봇이 객체에 접근하면 객체의 정체성(Object Identity)은 유지되지만 크기와 관측 시점은 변화합니다. 이러한 관측들을 서로 연관시켜 학습하면 표현이 표면적인 시각 변화에는 덜 민감해지고 물리적 상호작용에 중요한 지속적인 환경 속성에는 더욱 민감해질 수 있습니다.

다중모달 자기지도학습(Multimodal Self-Supervision)은 서로 다른 센서 사이의 대응 관계를 활용합니다. 같은 시점에 기록된 카메라 이미지와 라이다 측정값은 동일한 환경의 서로 중첩되는 측면을 나타내며, 시각적 움직임(Visual Motion)은 관성 측정값(Inertial Measurements)이나 고유수용감각 측정값과 대응될 수 있습니다. 따라서 사람이 생성한 레이블 없이 하나의 모달리티(Modality)가 다른 모달리티를 지도할 수 있습니다. 이러한 교차 모달 학습(Cross-Modal Learning)은 외형, 기하학, 움직임, 신체 상태를 결합한 표현을 형성할 수 있습니다.

행동(Action)은 체화 학습을 수동적인 관측과 구별하는 추가적인 지도 정보의 원천을 제공합니다. 에이전트가 운동 명령(Motor Command)을 내리면 이후의 감각 변화가 해당 행동의 결과를 보여줍니다. 시스템은 현재 상태와 행동으로부터 미래 상태를 예측하여 순방향 동역학(Forward Dynamics)을 학습하거나, 관측된 상태 전이를 만들어낸 행동을 예측하여 역동역학(Inverse Dynamics)을 학습할 수 있습니다. 두 목적함수 모두 환경에서 제어 가능한 요소를 포착하는 표현의 학습을 촉진합니다.

역동역학 목적함수(Inverse Dynamics Objectives)는 행동과 관련된 정보를 식별하는 데 특히 유용할 수 있습니다. 로봇의 움직임으로 인해 두 관측 사이에 차이가 발생했다면, 해당 움직임을 만들어낸 행동을 예측하기 위해 표현은 운동과 제어 가능한 상태 변화를 포착해야 합니다. 행동과 관련이 없는 특징의 중요성은 상대적으로 감소할 수 있습니다. 이를 통해 통계적으로 두드러지지만 운용에는 중요하지 않은 시각적 세부정보와 물리적 상호작용에 중요한 정보를 구별할 수 있습니다.

순방향 모델(Forward Model)과 역방향 모델(Inverse Model)을 함께 학습할 수도 있습니다. 순방향 모델은 행동 이후 어떤 일이 발생할지를 학습하고, 역방향 모델은 관측된 두 상태를 연결하는 행동이 무엇인지를 학습합니다. 두 모델을 결합하면 환경 동역학과 제어 가능성(Controllability)을 모두 포착하는 표현을 형성할 수 있습니다. 이러한 표현은 모델 기반 강화학습(Model-Based Reinforcement Learning), 계획, 내비게이션(Navigation), 조작(Manipulation), 적응형 제어(Adaptive Control)를 위한 유용한 기반이 됩니다.

자기지도 표현 학습(Self-Supervised Representation Learning)은 작업별 레이블 데이터셋(Task-Specific Labeled Datasets)에 대한 의존성을 크게 줄일 수 있습니다. 지각 인코더(Perception Encoder)는 먼저 수천 시간의 레이블 없는 로봇 운용 데이터로 학습한 뒤 훨씬 적은 양의 레이블 데이터로 적응할 수 있습니다. 객체 탐지(Object Detection), 지형 분류(Terrain Classification), 주행 가능성 추정(Traversability Estimation), 조작, 내비게이션 등의 작업은 광범위한 체화 경험으로부터 획득한 일반적인 표현을 재사용할 수 있습니다.

따라서 사전학습(Pretraining)과 다운스트림 적응(Downstream Adaptation)은 중요한 학습 워크플로를 형성합니다. 사전학습 과정에서는 예측(Prediction), 복원(Reconstruction), 대조 목적함수(Contrastive Objectives), 다중모달 대응 관계 등을 통해 광범위하게 활용 가능한 구조를 학습합니다. 이후 다운스트림 학습에서는 작업별 지도 신호(Task-Specific Supervision)를 사용하여 표현을 조정하거나 특화된 예측 헤드(Prediction Heads)를 추가합니다. 이러한 분리를 통해 비용이 많이 드는 체화 데이터를 각각의 응용마다 별도로 수집하지 않고 여러 작업에 활용할 수 있습니다.

자기지도학습은 월드 모델(World Model) 구축도 지원합니다. 월드 모델은 상태 정보를 보존하는 표현과 이러한 상태가 어떻게 변화하는지를 예측하는 동역학을 필요로 합니다. 시간적 및 행동 조건부 목적함수(Action-Conditioned Objectives)는 자연스럽게 두 요소를 모두 제공합니다. 미래 잠재 상태를 반복적으로 예측하고 이를 실제 관측과 비교함으로써 시스템은 경험된 상태 전이에 기반한 내부 예측 모델(Internal Predictive Model)을 점진적으로 학습할 수 있습니다.

장기 예측(Longer-Horizon Prediction)은 예측 범위가 미래로 확장될수록 불확실성이 증가하기 때문에 추가적인 문제를 발생시킵니다. 작은 모델링 오차가 누적될 수 있으며 여러 미래 결과가 모두 가능한 상황도 존재합니다. 따라서 자기지도 월드 모델(Self-Supervised World Models)은 확률적 표현(Probabilistic Representations), 불확실성 추정(Uncertainty Estimation), 다단계 예측 목적함수(Multi-Step Prediction Objectives), 또는 예측 불가능한 모든 감각적 세부사항을 표현하려 하지 않는 추상적인 잠재 상태(Abstract Latent States)를 활용할 수 있습니다.

현재 관측만으로 자기지도 목적함수를 해결하는 데 충분한 정보를 얻을 수 없는 경우에는 메모리(Memory)가 중요해집니다. 객체가 가려지거나, 로봇이 이전 장소를 다시 방문하거나, 중요한 사건이 수초 전에 발생했을 수 있습니다. 순환 신경망(Recurrent Networks), 트랜스포머(Transformers), 명시적 메모리 시스템(Explicit Memory Systems)은 시간에 걸쳐 정보를 통합하여 표현이 체화 경험에서 지속적인 상태(Persistent State)와 장기 의존성(Long-Term Dependencies)을 포착하도록 할 수 있습니다.

명시적인 의미론적 레이블(Semantic Labels)이 없어도 공간 학습(Spatial Learning)이 이루어질 수 있습니다. 로봇의 움직임은 관측 사이의 기하학적 관계를 제공하고, 깊이 센서(Depth Sensors), 오도메트리(Odometry), 관측 시점 변화(Viewpoint Changes)는 3차원 구조에 대한 정보를 제공합니다. 자기지도 목적함수는 이러한 관계를 이용하여 깊이(Depth), 움직임(Motion), 대응 관계(Correspondence), 점유 상태(Occupancy), 공간 표현(Spatial Representations)을 학습할 수 있습니다. 이러한 지식은 의미론적 주석이 제한된 경우에도 위치추정(Localization), 매핑(Mapping), 내비게이션, 조작을 지원합니다.

자기지도학습은 개별 센서 프레임에서 전체 궤적(Trajectories)으로 확장될 수도 있습니다. 하나의 궤적에는 에이전트가 어디로 이동했는지, 어떤 행동을 수행했는지, 어떤 상태를 다시 방문했는지, 이후 어떤 결과가 발생했는지에 대한 정보가 포함됩니다. 모델은 작업 진행(Task Progress), 환경 맥락(Environmental Context), 행동 단계(Behavioral Phases)를 인코딩하는 시퀀스 수준 표현(Sequence-Level Representations)을 학습할 수 있습니다. 이러한 표현은 이후 장기 계획(Long-Horizon Planning)과 계층적 의사결정(Hierarchical Decision Making)을 지원할 수 있습니다.

시뮬레이션(Simulation)은 자기지도 목적함수를 개발하기 위한 확장 가능한 경험의 원천을 제공합니다. 다양한 환경, 로봇 구성, 상호작용에서 대규모 다중모달 궤적을 생성할 수 있습니다. 자기지도학습은 사람이 직접 작성한 주석을 요구하지 않기 때문에 시뮬레이션과 실제 환경의 궤적에 유사한 학습 목적함수를 적용할 수 있습니다. 이후 실제 환경 경험을 사용하여 시뮬레이션에 존재하지 않았던 센서 특성과 물리 현상에 맞게 표현을 적응시킬 수 있습니다.

지속 자기지도학습(Continual Self-Supervised Learning)을 사용하면 실제 배치된 로봇이 운용 데이터로부터 자신의 표현을 지속적으로 개선할 수 있습니다. 새로운 환경, 조명 조건(Lighting Conditions), 지형, 객체, 페이로드(Payload), 센서 특성은 계속해서 새로운 경험을 제공합니다. 이러한 데이터를 폐기하는 대신 시스템은 예측 오차(Prediction Errors)와 교차 모달 일관성(Cross-Modal Consistency)을 지속적인 학습 신호로 사용할 수 있습니다. 이를 통해 운용 수명 전체에 걸쳐 적응하는 모델로 발전할 수 있습니다.

그러나 지속적인 적응(Continual Adaptation)은 신중하게 제어해야 합니다. 최근 경험을 지나치게 공격적으로 학습하면 표현이 드리프트(Drift)하거나 이전에 유용했던 지식을 잊을 수 있습니다. 리플레이 버퍼(Replay Buffers), 정규화(Regularization), 고정된 파운데이션 구성요소(Frozen Foundation Components), 모듈형 적응(Modular Adaptation), 선택적 갱신(Selective Updates)을 활용하여 안정적인 능력을 보존하면서 새로운 환경 정보를 통합할 수 있습니다. 목표는 새로운 학습을 위한 가소성(Plasticity)과 신뢰할 수 있는 운용을 위한 안정성(Stability)의 균형을 유지하는 것입니다.

자기지도학습은 지도학습(Supervised Learning), 모방 학습(Imitation Learning), 강화학습(Reinforcement Learning)의 필요성을 제거하지 않습니다. 대신 이러한 학습 방법이 더욱 효율적으로 작동할 수 있도록 광범위한 표현 기반(Representational Foundation)을 제공합니다. 자기지도학습은 세계가 어떻게 구성되어 있고 어떻게 변화하는지를 학습할 수 있으며, 모방 학습은 바람직한 행동의 사례를 제공하고, 강화학습은 어떤 행동이 가치 있는 결과를 생성하는지를 결정합니다.

자율 로봇(Autonomous Robots)에서는 이러한 결합을 통해 강력한 학습 계층(Learning Hierarchy)을 구성할 수 있습니다. 지속적으로 수집되는 레이블 없는 경험은 지각 및 예측 표현을 발전시키고, 시연(Demonstrations)은 유용한 기술(Skills)을 학습시키며, 강화학습은 행동 결과를 바탕으로 정책을 개선하고, 월드 모델은 내부 시뮬레이션(Internal Simulation)과 계획을 지원합니다. 각각의 학습 메커니즘은 서로 다른 형태의 정보를 제공하면서 동일한 체화 경험에 기반한 표현을 공유할 수 있습니다.

자기지도학습의 보다 광범위한 중요성은 일상적인 로봇 운용 자체를 지속적인 지식의 원천으로 변환할 수 있다는 데 있습니다. 모든 움직임은 시간적 관계를 생성하고, 모든 행동은 결과를 만들어내며, 모든 센서 조합은 교차 모달 대응 관계를 제공하고, 모든 새로운 관측은 이전 예측을 검증할 수 있습니다. 따라서 로봇은 실제 배치 과정에서 발생하는 모든 유용한 학습 사건마다 사람이 명시적인 주석을 제공할 필요가 없습니다.

궁극적으로 자기지도학습(Self-Supervised Learning)은 원시 체화 경험(Raw Embodied Experience)을 구조화된 내부 지식(Structured Internal Knowledge)으로 변환하기 위한 확장 가능한 메커니즘을 제공합니다. 예측, 마스킹(Masking), 시간적 연속성, 다중모달 대응 관계, 공간적 일관성(Spatial Consistency), 행동 조건부 상태 전이(Action-Conditioned Transitions)를 활용함으로써 에이전트는 지각, 월드 모델링(World Modeling), 계획, 제어를 지원하는 표현을 학습할 수 있습니다. 경험은 지능을 위한 입력(Input)이 되는 동시에 그 지능이 지속적으로 향상되도록 만드는 지도 신호(Supervision)가 됩니다.

## 03.04. Multimodal Learning

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

다중모달 학습(Multimodal Learning)은 체화 지능 시스템(Embodied Intelligent Systems)이 여러 감각 및 기호 모달리티(Sensory and Symbolic Modalities)의 정보를 결합하여 더욱 풍부한 표현(Representations)을 구축할 수 있도록 합니다. 로봇은 하나의 센서만으로 환경을 이해하는 경우가 거의 없습니다. 비전(Vision), 라이다(LiDAR), 레이더(Radar), 오디오(Audio), 촉각 센싱(Tactile Sensing), 고유수용감각(Proprioception), 언어(Language), 지도(Maps), 행동 이력(Action History)은 상호 보완적인 관점을 제공하며, 이를 함께 활용하면 물리 세계와 에이전트 사이의 관계를 더욱 완전하게 표현할 수 있습니다.

각각의 모달리티(Modality)는 환경의 서로 다른 속성을 포착하며 고유한 장점과 한계를 가집니다. 카메라는 외형(Appearance), 질감(Texture), 색상(Color), 의미론적 정보(Semantic Information)를 제공하고, 라이다는 기하학적 구조(Geometric Structure)와 거리를 측정합니다. 레이더는 악천후나 가시성이 낮은 조건에서도 효과적으로 작동할 수 있으며, 촉각 또는 힘 센서(Force Sensors)는 물리적 접촉을 감지합니다. 고유수용감각은 상호작용 과정에서 로봇의 내부 구성(Internal Configuration), 움직임(Motion), 액추에이터 상태(Actuator State)를 나타냅니다.

다중모달 학습은 이러한 이질적인 정보원(Heterogeneous Sources)에서 유용한 정보를 보존하면서 모달리티 사이의 관계를 발견하는 표현을 학습하는 것을 목표로 합니다. 각각의 모달리티를 독립된 채널로 처리하는 대신 시스템은 센서와 시간에 걸쳐 관측들이 어떻게 서로 대응하는지를 학습합니다. 시각적으로 탐지된 차량은 라이다 포인트 군집(LiDAR Point Cluster) 및 레이더 반사(Radar Return)에 대응할 수 있으며, 차량의 움직임은 동시에 옵티컬 플로우(Optical Flow), 거리 측정, 미래 위치 예측에 영향을 미칠 수 있습니다.

따라서 센서 융합(Sensor Fusion)은 다중모달 학습과 밀접하게 관련되어 있지만 두 개념이 완전히 동일한 것은 아닙니다. 전통적인 센서 융합은 명시적으로 설계된 확률적 모델(Probabilistic Models)이나 기하학적 모델(Geometric Models)을 이용하여 측정값을 결합하는 경우가 많습니다. 반면 다중모달 학습은 데이터로부터 대응 관계(Correspondence), 가중치(Weighting), 상호작용 패턴(Interaction Patterns)을 직접 학습할 수 있습니다. 현대의 체화 시스템은 물리적 보정(Physical Calibration) 및 추정(Estimation)과 학습된 특징 수준 또는 표현 수준 융합을 함께 사용하는 경우가 많습니다.

다중모달 처리는 아키텍처(Architecture)의 여러 단계에서 수행될 수 있습니다. 초기 융합(Early Fusion)은 광범위한 독립적 처리가 이루어지기 전에 비교적 저수준 센서 정보를 결합합니다. 중간 융합(Intermediate Fusion)은 먼저 각 모달리티에 특화된 특징을 추출한 뒤 이를 공유 표현(Shared Representation)으로 통합합니다. 후기 융합(Late Fusion)은 개별 모델이 각각 예측을 생성한 뒤 이를 결합합니다. 하이브리드 아키텍처(Hybrid Architectures)는 하나의 융합 지점에 의존하지 않고 여러 계층에서 반복적으로 정보를 교환할 수 있습니다.

초기 융합은 강한 압축(Compression)이 이루어지기 전에 정보를 결합하기 때문에 세밀한 교차 모달 관계(Cross-Modal Relationships)를 보존할 수 있습니다. 그러나 원시 센서 스트림(Raw Sensor Streams)은 일반적으로 서로 다른 차원, 샘플링 속도(Sampling Rates), 좌표계(Coordinate Systems), 잡음 특성(Noise Characteristics), 물리적 의미를 가집니다. 따라서 카메라 픽셀, 포인트 클라우드(Point Clouds), 관성 측정값(Inertial Measurements), 기타 신호를 직접 결합하기는 어렵습니다. 실제 시스템에서는 관측을 호환 가능한 공간 표현이나 학습된 표현으로 변환한 후 심층적인 통합을 수행하는 경우가 많습니다.

중간 융합(Intermediate Fusion)은 모달리티별 인코더(Modality-Specific Encoders)가 각각의 센서에서 유용한 특징을 먼저 추출할 수 있기 때문에 체화 인공지능(Embodied AI)에 특히 적합합니다. 비전 인코더(Vision Encoder)는 외형과 의미론적 구조를 식별하고, 포인트 클라우드 인코더(Point-Cloud Encoder)는 기하학을 표현하며, 관성 인코더(Inertial Encoder)는 움직임을 포착할 수 있습니다. 이후 이러한 특징들은 연결(Concatenation), 어텐션(Attention), 교차 어텐션(Cross-Attention), 공유 잠재 공간(Shared Latent Spaces), 기타 학습 메커니즘을 통해 상호작용하면서 통합 상태(Integrated State)에 어떤 정보가 영향을 주어야 하는지를 결정할 수 있습니다.

어텐션 메커니즘(Attention Mechanisms)은 다중모달 통합을 위한 유연한 방법을 제공합니다. 모든 센서에 고정된 중요도를 부여하는 대신 네트워크는 현재 맥락에 관련된 정보를 동적으로 강조할 수 있습니다. 의미론적 인식(Semantic Recognition)이 필요할 때는 비전이 더 중요한 역할을 할 수 있고, 정밀한 기하학이 필요할 때는 라이다가 더 중요해질 수 있습니다. 조명이 좋지 않은 상황에서는 모델이 조건에 따른 신뢰도 변화를 학습했다면 레이더나 다른 강건한 센서가 더욱 큰 역할을 수행할 수 있습니다.

교차 어텐션(Cross-Attention)은 하나의 모달리티가 다른 모달리티에 포함된 정보를 질의(Query)할 수 있도록 합니다. 객체와 관련된 시각 특징은 동일한 영역을 나타내는 기하학적 특징에 어텐션할 수 있으며, 작업을 설명하는 언어 토큰(Language Tokens)은 장면에서 관측되는 객체에 어텐션할 수 있습니다. 이러한 상호작용을 통해 시스템은 서로 독립적인 센서 특징을 단순히 연결하는 대신 의미론적 의미(Semantic Meaning), 물리적 기하학(Physical Geometry), 작업 지시(Task Instructions), 가능한 행동 사이의 관계를 형성할 수 있습니다.

여러 센서가 동일한 물리적 환경을 관측할 때 공간 정렬(Spatial Alignment)은 기본적인 요구사항입니다. 카메라, 라이다, 레이더, 로봇 좌표계(Robot Coordinate Frames)는 일반적으로 서로 다른 원점과 방향을 가집니다. 따라서 측정값 사이의 대응 관계를 형성하려면 보정(Calibration)과 기하학적 변환(Geometric Transformation)이 필요합니다. 학습된 다중모달 표현은 강건성을 향상시킬 수 있지만 물리적 위치추정(Localization), 매핑(Mapping), 제어(Control)가 미터법적 일관성(Metric Consistency)에 의존하는 경우 정확한 공간 관계의 필요성을 제거하지는 못합니다.

시간 정렬(Temporal Alignment)도 동일하게 중요합니다. 서로 다른 센서는 서로 다른 주파수로 동작할 수 있으며 처리 또는 통신 지연(Communication Delays)도 서로 다를 수 있습니다. 카메라 프레임, 라이다 스캔, 관성 샘플, 액추에이터 명령은 미세하게 서로 다른 물리적 시점을 나타낼 수 있습니다. 동기화(Synchronization), 타임스탬프(Timestamping), 보간(Interpolation), 버퍼링(Buffering), 지연 보상(Latency Compensation)을 통해 서로 다른 시점의 측정값을 잘못 결합하는 대신 융합된 관측이 일관된 상태를 나타내도록 할 수 있습니다.

공유 잠재 표현(Shared Latent Representations)은 다중모달 학습을 위한 또 다른 전략을 제공합니다. 모달리티별 관측은 서로 비교하거나 결합할 수 있는 공통 잠재 공간(Common Latent Space)으로 인코딩됩니다. 이상적으로 동일한 물리 상태에 대응하는 표현은 서로 다른 센서에서 생성되더라도 연관성을 유지해야 합니다. 이를 통해 비전, 기하학, 움직임, 언어, 행동이 지각과 의사결정에 함께 기여할 수 있는 공통 내부 언어(Common Internal Language)를 형성할 수 있습니다.

자기지도학습(Self-Supervised Learning)은 동기화된 센서가 자연스럽게 대응 관계 신호를 제공하기 때문에 이러한 공유 공간을 구축하는 데 특히 유용합니다. 동일한 장소와 시간에서 수집된 카메라 및 라이다 측정값은 사람이 직접 주석을 제공하지 않아도 동일한 환경을 나타냅니다. 모델은 서로 대응하는 관측을 연결하고 관련되지 않은 사례를 구별하도록 학습할 수 있습니다. 따라서 일반적인 로봇 운용 과정에서 생성되는 대규모 데이터를 다중모달 학습 데이터로 자동 활용할 수 있습니다.

다중모달 학습에서는 하나의 모달리티를 이용하여 다른 모달리티를 지도(Supervise)할 수도 있습니다. 라이다의 깊이 측정값(Depth Measurements)은 시각 표현을 위한 기하학적 학습 신호를 제공할 수 있으며, 고유수용감각이나 관성 측정값은 시각 모델이 움직임을 학습하도록 지원할 수 있습니다. 시연(Demonstrations)과 연결된 언어는 관측된 행동에 의미론적 구조를 제공할 수 있습니다. 이러한 교차 모달 지도(Cross-Modal Supervision)를 통해 학습 시 사용할 수 있는 정보가 이후 운용 과정에서 일부 모달리티를 사용할 수 없더라도 표현의 품질을 향상시킬 수 있습니다.

모달리티 누락(Missing Modalities)은 실제 로봇 센서가 고장 나거나, 가려지거나, 통신을 잃거나, 신뢰성이 저하될 수 있기 때문에 중요한 실용적 문제입니다. 항상 모든 센서를 사용할 수 있다고 가정하는 다중모달 모델은 하나의 입력이 사라졌을 때 심각하게 실패할 수 있습니다. 모달리티 드롭아웃(Modality Dropout), 센서 손상(Sensor Corruption), 부분 관측(Partial Observations), 신뢰도 추정(Reliability Estimation)을 포함하여 학습하면 시스템이 남아 있는 정보원에 대한 의존도를 동적으로 재분배하면서 유용한 행동을 유지하도록 할 수 있습니다.

따라서 모든 측정값을 동일하게 신뢰하는 대신 센서 불확실성(Sensor Uncertainty)을 표현해야 합니다. 비(Rain), 안개(Fog), 먼지(Dust), 눈부심(Glare), 진동(Vibration), 다중경로 효과(Multipath Effects), 가림(Occlusion), 하드웨어 고장(Hardware Faults)은 서로 다른 센서를 서로 다른 방식으로 저하시킬 수 있습니다. 불확실성 인지 다중모달 시스템(Uncertainty-Aware Multimodal System)은 개별 모달리티나 특징에 대한 신뢰도를 추정하고 신뢰성이 감소하면 그 영향력을 줄일 수 있습니다. 강건한 융합(Robust Fusion)은 정보를 결합하는 것뿐만 아니라 어떤 정보를 신뢰하지 않아야 하는지를 판단하는 능력에도 의존합니다.

언어(Language)가 포함되면 다중모달 학습은 더욱 강력해집니다. 언어는 목표(Goals)를 지정하고, 객체를 설명하며, 제약조건(Constraints)을 전달하고, 공간 관계(Spatial Relationships)를 설명하거나, 상위 수준 지시(High-Level Instructions)를 제공할 수 있습니다. 비전-언어 모델(Vision-Language Models)은 텍스트 개념과 시각적 관측을 연결하고, 비전-언어-행동 아키텍처(Vision-Language-Action Architectures)는 이러한 관계를 물리적 행동으로 확장합니다. 따라서 체화 에이전트는 자신이 보는 것, 지시받은 것, 수행할 수 있는 행동을 서로 연결할 수 있습니다.

언어 기반화(Language Grounding)를 위해서는 언어적 개념이 물리적 객체, 상태, 행동과 연결되어야 합니다. 특정 객체를 향해 이동하라는 지시는 에이전트가 해당 객체를 식별하고, 로봇과 객체 사이의 공간 관계를 판단하고, 적절한 행동을 선택할 수 있을 때만 의미가 있습니다. 다중모달 학습은 기호적 지시(Symbolic Instructions)를 감각 관측 및 체화된 행동 가능성(Embodied Action Possibilities)과 연결하는 표현적 가교(Representational Bridge)를 제공합니다.

행동(Action) 자체도 하나의 모달리티로 취급할 수 있습니다. 센서 관측은 에이전트가 무엇을 지각하는지를 설명하고 행동 시퀀스(Action Sequences)는 에이전트가 환경과 어떻게 상호작용하는지를 나타냅니다. 관측과 행동을 함께 모델링하면 시스템은 어떤 환경 특징이 제어 가능한지, 운동 명령이 물리적 상태를 어떻게 변화시키는지를 학습할 수 있습니다. 이러한 관계는 체화 월드 모델(Embodied World Models), 모방 학습(Imitation Learning), 강화학습(Reinforcement Learning), 예측 제어(Predictive Control)의 핵심입니다.

다중모달 월드 모델(Multimodal World Models)은 여러 센서로부터 공유 상태 표현(Shared State Representation)을 학습하고 행동에 따라 해당 상태가 어떻게 변화하는지를 예측함으로써 이 원리를 확장합니다. 미래 이미지, 포인트 클라우드, 로봇 자세(Robot Poses), 기타 측정값을 각각 별도로 예측하는 대신 모델은 관련 미래 정보를 추론할 수 있는 압축된 잠재 월드 상태(Latent World State)를 예측할 수 있습니다. 이를 통해 지각, 동역학(Dynamics), 행동을 연결하는 통합 예측 표현(Unified Predictive Representation)을 형성합니다.

정보를 일시적으로 사용할 수 없는 상황에서는 메모리(Memory)가 다중모달 일관성(Multimodal Coherence)을 유지하는 데 도움이 됩니다. 이전 카메라 프레임에서 보이던 객체가 이후 가려지더라도 라이다 또는 공간 메모리(Spatial Memory)는 해당 객체의 존재를 계속 나타낼 수 있습니다. 마찬가지로 이전에 전달된 음성 또는 언어 지시는 오랜 시간이 지난 이후에도 관련성을 유지할 수 있습니다. 순환 신경망(Recurrent Networks)과 트랜스포머(Transformers) 같은 시간 모델(Temporal Models)은 이러한 관계를 시간에 걸쳐 보존하고 현재 관측을 이전의 다중모달 맥락과 통합할 수 있습니다.

다중모달 학습은 공간 지능(Spatial Intelligence)도 지원합니다. 시각적 의미론(Visual Semantics)은 객체가 무엇인지를 식별하고, 라이다는 객체의 3차원 기하학을 설명하며, 위치추정 시스템(Localization Systems)은 객체가 어디에 있는지를 결정하고, 지도는 현재 센서 범위를 넘어 이러한 관계를 보존할 수 있습니다. 이러한 정보원을 결합하면 단순한 개별 탐지(Isolated Detections)를 넘어 기하학, 의미론(Semantics), 움직임, 점유 상태(Occupancy), 주행 가능성(Traversability), 작업 관련성(Task Relevance)을 포함하는 더욱 풍부한 장면 표현(Scene Representation)을 구축할 수 있습니다.

자율 내비게이션(Autonomous Navigation)에서 다중모달 표현은 외형, 기하학, 움직임, 위치추정, 지도 정보를 결합하여 더욱 안전한 경로 선택(Path Selection)을 지원할 수 있습니다. 조작(Manipulation)에서는 비전을 이용해 객체를 식별하고 깊이 및 촉각 센싱을 통해 기하학과 접촉 정보를 획득할 수 있습니다. 이동 조작(Mobile Manipulation)에서는 로봇이 이동하고, 위치를 조정하고, 팔을 뻗고, 접촉하며, 변화하는 물리적 조건에 맞춰 행동을 적응시키는 과정에서 이러한 능력들이 통합적으로 작동해야 합니다.

다중모달 시스템을 학습하려면 센서 품질, 보정, 동기화, 환경 다양성(Environmental Diversity)이 어떤 관계를 학습할 수 있는지에 직접적인 영향을 주기 때문에 신중한 데이터셋 설계(Dataset Design)가 필요합니다. 대규모 데이터셋은 다양한 관측 시점, 운용 조건, 객체, 지형, 상호작용, 센서 성능 저하 시나리오를 포함해야 합니다. 잘못 동기화되거나 보정된 데이터는 잘못된 교차 모달 관계를 학습시킬 수 있으며, 이러한 문제는 시스템이 까다로운 물리 환경에 배치되기 전까지 발견되지 않을 수도 있습니다.

시뮬레이션(Simulation)은 센서 구성과 환경 조건을 체계적으로 변화시킬 수 있는 확장 가능한 다중모달 데이터를 제공할 수 있습니다. 카메라, 깊이 센서(Depth Sensors), 라이다, 레이더, 고유수용감각, 행동을 정확한 공간 관계와 함께 생성할 수 있습니다. 그러나 실제 센서에는 시뮬레이션이 정확하게 재현하지 못할 수 있는 잡음, 지연시간, 아티팩트(Artifacts), 고장 모드(Failure Modes)가 존재하기 때문에 실제 데이터(Real-World Data)도 필수적입니다. 따라서 시뮬레이션과 실제 경험을 결합하면 데이터 규모(Scale)와 현실성(Realism)을 모두 향상시킬 수 있습니다.

궁극적으로 다중모달 학습(Multimodal Learning)은 체화 지능이 현실에 대한 하나의 표현에만 의존하는 한계를 넘어설 수 있도록 합니다. 서로 다른 센서, 언어, 메모리, 행동은 동일한 물리 세계에 대한 상호 보완적인 증거를 제공합니다. 이러한 정보원들이 어떻게 정렬(Align)되고, 서로를 강화(Reinforce)하고, 오류를 보정(Correct)하며, 필요할 경우 서로를 대체(Substitute)할 수 있는지를 학습함으로써 에이전트는 지각, 월드 모델링(World Modeling), 계획, 제어, 적응형 물리 상호작용(Adaptive Physical Interaction)을 위한 더욱 완전하고 강건한 내부 표현(Internal Representations)을 구축할 수 있습니다.

## 03.05. Transfer and Meta Learning

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

전이 학습(Transfer Learning)은 체화 지능 시스템(Embodied Intelligent System)이 하나의 작업(Task), 환경(Environment), 센서 구성(Sensor Configuration), 또는 로봇 플랫폼(Robot Platform)에서 획득한 지식을 다른 학습 문제에 재사용할 수 있도록 합니다. 모든 능력을 처음부터 다시 학습하는 대신 이전에 학습된 표현(Representations), 동역학(Dynamics), 정책(Policies), 기술(Skills)을 초기 기반으로 활용합니다. 이러한 재사용은 새로운 물리 작업을 위해 필요한 데이터, 계산량, 상호작용, 인간 지도(Human Supervision)를 크게 줄일 수 있습니다.

전이 학습의 핵심 가정은 서로 다른 학습 문제들이 유용한 구조를 공유하는 경우가 많다는 것입니다. 하나의 환경에서 객체를 인식하도록 학습된 시각 인코더(Visual Encoder)는 다른 환경에서도 의미 있는 특징을 제공할 수 있으며, 한 건물에서 학습한 내비게이션 지식(Navigation Knowledge)은 다른 장소에서의 이동에도 도움이 될 수 있습니다. 마찬가지로 하나의 로봇 팔에서 학습한 조작 기술(Manipulation Skills)은 다른 체화 구조로 적응한 이후에도 유용한 운동 패턴이나 객체 관계를 포함할 수 있습니다.

전이는 체화 아키텍처(Embodied Architecture)의 여러 수준에서 발생할 수 있습니다. 저수준 지각 표현(Low-Level Perceptual Representations)은 여러 작업에서 재사용될 수 있고, 중간 수준의 공간적 또는 의미론적 표현(Spatial or Semantic Representations)은 다양한 다운스트림 기능(Downstream Capabilities)을 지원할 수 있습니다. 상위 수준의 정책, 기술, 보상 모델(Reward Models), 월드 모델(World Model)의 구성요소도 재사용할 수 있습니다. 어떤 수준에서 전이할지는 소스 도메인(Source Domain)과 타깃 도메인(Target Domain)의 유사성과 두 영역 사이에서 어떤 속성이 불변(Invariant)으로 유지되는지에 따라 달라집니다.

표현 전이(Representation Transfer)는 가장 일반적인 접근법 가운데 하나입니다. 먼저 크고 다양한 데이터셋으로 모델을 사전학습(Pretraining)한 뒤 학습된 인코더를 새로운 작업에서 재사용합니다. 초기에는 인코더를 고정(Frozen)한 상태에서 새로운 작업별 헤드(Task-Specific Head)만 학습할 수도 있고, 이후 일부 파라미터를 미세조정(Fine-Tuning)할 수도 있습니다. 이를 통해 일반적인 시각적, 기하학적, 언어적 또는 다중모달 특징(Multimodal Features)을 특화된 체화 응용에 활용할 수 있습니다.

미세조정(Fine-Tuning)은 타깃 작업이나 환경에서 수집한 데이터를 이용하여 사전학습된 파라미터를 적응시킵니다. 소스와 타깃 도메인이 밀접하게 관련되어 있다면 비교적 작은 갱신만으로도 충분할 수 있습니다. 전체 미세조정(Full Fine-Tuning)은 대부분 또는 모든 파라미터를 수정하는 반면, 파라미터 효율적 접근법(Parameter-Efficient Approaches)은 선택된 계층, 어댑터(Adapters), 저랭크 구성요소(Low-Rank Components), 프롬프트(Prompts), 작업별 모듈만 갱신합니다. 후자의 방식은 공유 지식을 보존하면서 계산량과 파라미터 손상의 위험을 줄일 수 있습니다.

도메인 이동(Domain Shift)은 전이 학습의 핵심 과제입니다. 하나의 분포(Distribution)에서 학습된 모델이 실제 배치 이후 서로 다른 조명, 날씨, 지형, 객체, 센서 잡음, 카메라 배치, 동역학, 운용 조건을 만나면 성능이 저하될 수 있습니다. 작업의 개념 자체는 비슷하더라도 이러한 차이가 모델의 동작에 영향을 줍니다. 성공적인 전이를 위해서는 어떤 학습 속성을 안정적으로 유지해야 하고 어떤 부분을 타깃 도메인에 맞게 적응해야 하는지를 구분해야 합니다.

시뮬레이션-현실 전이(Sim-to-Real Transfer)는 실제 하드웨어를 위험에 노출시키지 않고 대규모 경험을 생성할 수 있기 때문에 피지컬 인공지능(Physical AI)에서 특히 중요합니다. 정책과 표현은 먼저 시뮬레이션 환경에서 학습된 뒤 실제 로봇으로 전이될 수 있습니다. 그러나 외형, 접촉 동역학(Contact Dynamics), 액추에이터 응답(Actuator Response), 지연시간(Latency), 마찰(Friction), 센서 잡음, 모델링되지 않은 물리 효과의 차이는 시뮬레이션-현실 격차(Simulation-to-Reality Gap)를 발생시키므로 실제 배치 과정에서 이를 보정해야 합니다.

도메인 랜덤화(Domain Randomization)는 학습 중 시뮬레이션 조건을 의도적으로 다양화하여 이러한 격차를 줄이려는 방법입니다. 질감(Textures), 조명, 객체 특성(Object Properties), 센서 잡음, 마찰, 질량(Mass), 액추에이터 특성, 환경 기하학(Environmental Geometry)을 랜덤하게 변화시켜 학습자가 하나의 특정 시뮬레이션 설정에 지나치게 의존하지 않도록 합니다. 목표는 실제 환경에서 나타날 수 있는 다양한 조건을 포함하는 폭넓은 분포에서 작동 가능한 표현이나 정책을 학습하는 것입니다.

도메인 적응(Domain Adaptation)은 소스와 타깃의 표현 또는 예측을 명시적으로 정렬하여 또 다른 해결책을 제공합니다. 타깃 도메인의 레이블이 부족하거나 전혀 없는 경우에도 관측을 이용하여 특징 분포(Feature Distribution)를 조정할 수 있습니다. 자기지도 목적함수(Self-Supervised Objectives), 적대적 정렬(Adversarial Alignment), 특징 정규화(Feature Normalization), 의사 레이블링(Pseudo-Labeling), 일관성 제약(Consistency Constraints)을 활용하면 소스에서 학습한 유용한 지식을 유지하면서 내부 표현을 새로운 도메인에 맞게 적응시킬 수 있습니다.

교차 작업 전이(Cross-Task Transfer)는 하나의 목표에서 학습한 지식이 다른 목표를 지원할 때 발생합니다. 내비게이션을 통해 학습한 표현은 탐색(Exploration), 매핑(Mapping), 객체 탐색(Object Search)에 유용한 공간 정보를 포함할 수 있으며, 조작 경험은 이후 작업 계획에 필요한 객체 어포던스(Object Affordances)를 학습시킬 수 있습니다. 전이는 하나의 고정된 목적에 과도하게 특화된 표현보다 재사용 가능한 구조(Reusable Structure)를 학습할 때 더 효과적입니다.

교차 체화 전이(Cross-Embodiment Transfer)는 서로 다른 물리 구성을 가진 로봇 사이로 이러한 원리를 확장합니다. 로봇은 휠베이스(Wheelbase), 로봇 팔 기하학(Arm Geometry), 관절 한계(Joint Limits), 페이로드(Payload), 센서 배치, 액추에이터 동역학, 이동 방식(Locomotion Mechanism)이 서로 다를 수 있습니다. 따라서 저수준 명령을 그대로 복사하는 것은 불가능할 수 있습니다. 대신 공유 작업 표현(Shared Task Representations), 객체 중심 좌표(Object-Centered Coordinates), 정규화된 행동(Normalized Actions), 기술 추상화(Skill Abstractions), 체화 조건부 정책(Embodiment-Conditioned Policies)을 통해 작업 의도(Task Intent)와 플랫폼별 실행을 분리할 수 있습니다.

지식 전이(Knowledge Transfer)와 행동 전이(Behavior Transfer)는 구분할 필요가 있습니다. 지식 전이는 지각, 의미론(Semantics), 공간 표현, 동역학, 보상 구조(Reward Structure)를 재사용할 수 있는 반면, 행동 전이는 정책이나 기술 자체를 재사용하려 합니다. 지식은 물리 행동보다 더 넓은 범위에서 전이되는 경우가 많습니다. 객체가 어디에 있는지에 대한 일반적 표현은 쉽게 전이될 수 있지만 해당 객체까지 도달하는 정확한 모터 명령(Motor Commands)은 체화 구조에 따라 달라질 수 있습니다.

메타 학습(Meta-Learning)은 이와 연관되지만 더 야심찬 목표를 다룹니다. 즉, 효율적으로 학습하는 방법 자체를 학습하는 것입니다. 하나의 고정된 학습 작업에서 성능을 최대화하는 대신 여러 작업의 분포에 걸쳐 학습하여 새로운 작업을 만났을 때 빠르게 적응할 수 있도록 합니다. 결과적으로 모델은 어떤 종류의 해결책, 표현, 파라미터 갱신(Parameter Updates)이 새로운 문제에서 유용할 가능성이 높은지에 대한 사전 지식(Prior Knowledge)을 포함하게 됩니다.

일반적인 메타 학습 과정은 내부 적응 과정(Inner Adaptation Process)과 외부 메타 최적화 과정(Outer Meta-Optimization Process)으로 구성됩니다. 내부 적응 단계에서 모델은 특정 작업에 대한 소량의 데이터나 경험을 이용하여 자신을 갱신합니다. 이후 외부 과정은 적응된 모델의 성능을 평가하고 초기 파라미터나 학습 메커니즘을 수정하여 이후 새로운 작업에서 더 빠르고 효과적으로 적응할 수 있도록 합니다.

기울기 기반 메타 학습(Gradient-Based Meta-Learning)은 빠른 적응이 가능하도록 모델 파라미터를 직접 최적화합니다. 학습 과정에서 시스템은 반복적으로 여러 작업을 샘플링하고 소수의 기울기 갱신(Gradient Updates)을 사용하여 각각에 적응한 뒤 성능을 평가합니다. 초기 파라미터는 새로운 작업에서 적은 수의 갱신만으로도 높은 성능을 낼 수 있도록 점진적으로 조정됩니다. 이는 타깃 작업 데이터를 확보하기 어려운 경우 소수 샷 적응(Few-Shot Adaptation)을 지원할 수 있습니다.

거리 기반 메타 학습(Metric-Based Meta-Learning)은 새로운 예제를 기존 경험과 효과적으로 비교할 수 있는 표현 공간(Representation Space)을 학습하는 다른 접근법을 사용합니다. 전체 모델을 크게 수정하는 대신 학습된 공간에서의 유사성(Similarity)을 기반으로 분류, 검색, 행동 선택을 수행할 수 있습니다. 이는 새로운 객체, 환경, 작업 범주를 소수의 시연만으로 인식해야 하는 경우 특히 유용할 수 있습니다.

메모리 기반 메타 학습(Memory-Based Meta-Learning)은 순환 신경망(Recurrent Networks), 트랜스포머(Transformers), 명시적 메모리(Explicit Memory)를 사용하여 최근 경험으로부터 새로운 작업의 구조를 추론합니다. 적응을 파라미터 갱신만으로 표현하는 대신 작업 관련 정보를 내부 상태나 컨텍스트(Context)에 인코딩할 수 있습니다. 시연, 보상, 실패, 성공적인 상호작용은 현재 작업의 특성을 파악하고 행동을 동적으로 수정하기 위한 증거가 됩니다.

소수 샷 학습(Few-Shot Learning)은 체화 시스템이 제한된 타깃 데이터만으로 새로운 작업을 습득해야 하는 경우가 많기 때문에 메타 학습과 밀접하게 연결됩니다. 로봇은 새로운 조작 작업에 대한 몇 개의 시연만 받거나 익숙하지 않은 객체에 대한 소수의 예제만 제공받을 수 있습니다. 메타 학습된 사전지식(Meta-Learned Prior)은 이러한 제한된 예제가 의미 있는 적응으로 이어지도록 하여 수천 번의 새로운 학습 에피소드가 필요한 상황을 줄일 수 있습니다.

원샷 적응(One-Shot Adaptation)은 하나의 시연이나 경험만으로 일반화하려는 더 어려운 목표입니다. 하나의 궤적만으로는 가능한 모든 변화를 표현할 수 없기 때문에 물리 시스템에서 특히 어렵습니다. 효과적인 원샷 적응을 위해서는 이전에 학습한 구조가 매우 중요합니다. 학습자는 새로운 예제를 구성적으로 해석할 수 있을 정도로 객체, 기하학, 행동, 시간 관계(Temporal Relationships), 작업 패턴(Task Patterns)을 이미 이해하고 있어야 합니다.

전이 학습과 메타 학습은 다중모달 표현(Multimodal Representations)과 결합될 때 특히 강력해집니다. 새로운 작업은 언어(Language)를 통해 지시되고, 행동으로 시연되며, 비전(Vision)으로 관측되고, 고유수용감각(Proprioception)이나 기하학을 통해 물리적으로 기반화(Grounded)될 수 있습니다. 공유된 다중모달 표현은 한 형태에서 습득한 지식이 다른 형태의 적응을 지원하도록 하며, 각각의 작업에서 모든 관계를 다시 학습할 필요성을 줄여줍니다.

월드 모델(World Models)은 일반적인 환경 동역학과 작업별 목적을 분리함으로써 전이를 지원할 수 있습니다. 객체가 어떻게 움직이고, 충돌이 어떻게 발생하며, 로봇 행동이 상태를 어떻게 변화시키는지를 이해하는 예측 모델은 여러 작업에서 재사용될 수 있습니다. 새로운 목표가 주어졌을 때 전체 물리 구조를 다시 학습하는 대신 계획(Planning), 보상(Reward), 정책 구성요소만 적응하면 될 수 있습니다.

기술 라이브러리(Skill Libraries)는 효율적인 전이를 위한 또 하나의 메커니즘을 제공합니다. 복잡한 행동은 접근하기(Approach), 파지하기(Grasp), 들어 올리기(Lift), 배치하기(Place), 추종하기(Follow), 회피하기(Avoid), 검사하기(Inspect), 도킹하기(Dock)와 같은 재사용 가능한 기본 기술로 분해할 수 있습니다. 새로운 작업은 저수준 행동을 처음부터 모두 생성하는 대신 기존 기술을 선택하고, 순서를 정하고, 파라미터화하여 학습할 수 있습니다. 메타 학습은 이러한 기술을 얼마나 빠르게 선택하고 적응할 수 있는지도 향상시킬 수 있습니다.

소스 지식이 타깃 문제에 적합하지 않은 경우에는 전이가 오히려 실패할 수 있습니다. 부정적 전이(Negative Transfer)는 이전에 학습한 표현이나 정책을 재사용한 결과 처음부터 새롭게 학습했을 때보다 성능이 저하되는 경우를 의미합니다. 환경, 동역학, 목적, 체화 구조가 크게 다를 때 이러한 문제가 발생할 수 있습니다. 따라서 전이 시스템은 유사성을 측정하고, 불확실성을 추정하며, 재사용 가능한 구성요소를 선택하고, 기존 지식을 언제 수정하거나 무시해야 하는지를 판단해야 합니다.

지속 학습(Continual Learning)은 체화 에이전트가 새로운 작업을 순차적으로 계속 만나기 때문에 추가적인 과제를 제기합니다. 새로운 작업에 적응하는 과정에서 이전에 습득한 능력이 파괴되어서는 안 됩니다. 리플레이(Replay), 정규화(Regularization), 모듈형 네트워크(Modular Networks), 파라미터 격리(Parameter Isolation), 확장 가능한 아키텍처(Expandable Architectures), 메모리 시스템을 이용하면 지식 보존과 새로운 적응 사이의 균형을 유지할 수 있습니다. 이때 전이는 이전 경험이 이후 학습의 기반이 되는 연속적인 과정으로 발전합니다.

따라서 평가(Evaluation)는 최종 작업 성능만 측정해서는 충분하지 않습니다. 적응 속도(Adaptation Speed), 필요한 시연 수(Number of Demonstrations), 상호작용 비용(Interaction Cost), 이전 작업에 대한 성능 유지(Retained Performance), 도메인 이동에 대한 강건성(Robustness), 보지 못한 조건에서의 일반화(Generalization)도 중요합니다. 물리 시스템에서는 새로운 능력을 학습하는 과정 자체가 위험한 탐색을 요구한다면 빠른 적응의 가치가 감소하기 때문에 적응 과정의 안전성(Safety)도 함께 평가해야 합니다.

실제 체화 인공지능(Embodied AI)에서 전이 학습(Transfer Learning)과 메타 학습(Meta-Learning)은 서로 보완적인 적응 계층을 형성합니다. 전이 학습은 기존 지식을 새로운 문제에 어떻게 재사용할지를 다루고, 메타 학습은 앞으로의 적응에 필요한 데이터와 경험을 줄이도록 학습 과정 자체를 어떻게 최적화할지를 다룹니다. 두 방법을 결합하면 작업별로 반복적으로 처음부터 학습하는 시스템에서 벗어나 재사용 가능한 능력(Reusable Competence)과 새로운 기능의 빠른 습득(Rapid Capability Acquisition)으로 발전할 수 있습니다.

궁극적으로 전이 및 메타 학습(Transfer and Meta-Learning)은 고정된 실험실 환경을 넘어 운용되어야 하는 물리 지능(Physical Intelligence)에 필수적입니다. 로봇은 운용 수명 동안 익숙하지 않은 객체, 환경, 임무(Missions), 센서, 페이로드, 하드웨어 플랫폼을 계속 만나게 됩니다. 표현, 월드 지식(World Knowledge), 정책, 기술을 재사용하면서 효율적인 적응 전략을 함께 학습함으로써 체화 에이전트는 축적된 경험을 점점 더 일반적이고 유연한 지능(General and Flexible Intelligence)으로 전환할 수 있습니다.

## 03.06. Lifelong Learning

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

평생 학습(Lifelong Learning)은 체화 지능 시스템(Embodied Intelligent System)이 초기 학습 이후 고정된 상태로 유지되는 것이 아니라 전체 운용 수명(Operational Lifetime)에 걸쳐 지속적으로 지식을 습득하고, 개선하며, 재구성할 수 있도록 합니다. 수개월 또는 수년 동안 배치되는 로봇은 새로운 환경, 객체, 사용자, 작업, 센서 조건, 하드웨어 변화를 계속 경험하게 됩니다. 평생 학습은 이러한 경험을 지속적인 적응(Continued Adaptation)의 기회로 활용할 수 있도록 합니다.

학습과 배치를 분리하는 기존의 학습 파이프라인(Conventional Training Pipelines)과 달리 평생 학습은 학습 자체를 실제 운용(Operation)에 통합합니다. 에이전트는 새로운 상황을 관측하고, 행동을 수행하며, 결과를 평가하고, 내부 모델(Internal Models)의 선택된 부분을 갱신합니다. 이를 통해 실제 환경에서 수집된 경험이 지각(Perception), 예측(Prediction), 의사결정(Decision Making), 물리적 상호작용(Physical Interaction)을 점진적으로 향상시키는 지속적인 학습 사이클(Persistent Learning Cycle)이 형성됩니다.

핵심 과제는 안정성(Stability)과 가소성(Plasticity)의 균형을 유지하는 것입니다. 가소성은 시스템이 새로운 지식을 학습하고 변화하는 조건에 적응할 수 있도록 하며, 안정성은 이전에 습득한 유용한 능력을 보호합니다. 가소성이 지나치게 높으면 기존 기술을 덮어쓸 수 있고, 안정성이 지나치게 높으면 의미 있는 적응이 어려워집니다. 따라서 평생 학습에서는 무엇을 변경하고, 무엇을 안정적으로 유지하며, 갱신을 어느 정도의 강도로 적용할지를 결정하는 메커니즘이 필요합니다.

치명적 망각(Catastrophic Forgetting)은 평생 학습에서 가장 중요한 문제 가운데 하나입니다. 신경망 모델(Neural Model)이 새로운 작업이나 환경에서 학습될 때 파라미터 갱신(Parameter Updates)이 이전 능력을 지원하던 표현을 파괴할 수 있습니다. 새로운 지형에서 이동하는 방법을 학습한 로봇이 이전에 익숙했던 환경에서의 능력을 의도치 않게 잃을 수도 있습니다. 기존 능력을 반복적으로 대체하는 것이 아니라 지속적으로 축적해야 하는 시스템에서는 이러한 손실을 방지하는 것이 필수적입니다.

리플레이(Replay)는 치명적 망각을 줄이기 위한 실용적인 메커니즘을 제공합니다. 시스템은 최근 경험만으로 학습하는 대신 이전 작업이나 환경에서 선택된 사례를 주기적으로 다시 학습합니다. 이러한 사례는 경험 버퍼(Experience Buffer)에 직접 저장하거나 학습된 모델을 이용하여 생성할 수 있습니다. 리플레이는 새로운 경험을 통합하는 동시에 네트워크가 이전 지식을 다시 학습하도록 하여 변화하는 데이터 분포(Data Distributions)에서도 기존 성능을 유지하도록 지원합니다.

정규화 방법(Regularization Methods)은 중요한 파라미터가 이후 학습 과정에서 지나치게 변화하지 않도록 제한하여 기존 지식을 보호합니다. 이전에 습득한 능력에 크게 기여하는 파라미터에는 변경에 대한 더 강한 페널티(Penalty)를 적용하고, 상대적으로 중요하지 않은 파라미터는 더 자유롭게 적응하도록 할 수 있습니다. 이러한 접근법은 모든 과거 데이터를 저장하고 반복적으로 다시 학습하지 않고도 기존 지식을 보존하는 것을 목표로 합니다.

모듈형 아키텍처(Modular Architectures)는 능력을 독립적으로 갱신할 수 있는 여러 구성요소로 분리하는 또 다른 전략을 제공합니다. 새로운 작업에서는 하나의 공유 네트워크 전체를 광범위하게 수정하는 대신 새로운 어댑터(Adapters), 전문가 모듈(Expert Modules), 기술(Skills), 메모리 구조(Memory Structures)를 추가하거나 활성화할 수 있습니다. 모듈형 학습(Modular Learning)은 작업 사이의 간섭을 줄이고 전문화된 지식을 보존하면서 공유 표현을 지속적으로 개선하기 쉽게 만들어줍니다.

동적 또는 확장형 아키텍처(Dynamic or Expandable Architectures)는 필요할 때 모델 용량(Model Capacity)을 증가시킴으로써 이러한 원리를 더욱 확장합니다. 기존 구성요소만으로 과거 지식과 충돌하지 않으면서 새로운 작업을 표현하기 어렵다면 새로운 파라미터나 모듈을 추가할 수 있습니다. 이러한 확장은 축적되는 경험과 함께 학습 용량을 증가시킬 수 있지만 실제 시스템에서는 메모리 사용량, 연산량, 라우팅 복잡성(Routing Complexity), 장기간 사용되지 않는 구성요소의 유지관리도 함께 제어해야 합니다.

이전 경험이 새로운 상황을 해석하기 위한 맥락(Context)을 제공하기 때문에 메모리(Memory)는 평생 학습의 핵심 요소입니다. 일화 기억(Episodic Memory)은 특정 사건, 궤적(Trajectories), 실패, 성공을 저장할 수 있고, 의미 기억(Semantic Memory)은 환경, 객체, 작업에 관한 더욱 일반적인 지식을 보존합니다. 절차 기억(Procedural Memory)은 재사용 가능한 기술과 정책(Policies)을 유지할 수 있습니다. 이러한 여러 형태의 메모리를 결합하면 새로운 경험을 시간에 걸쳐 축적된 지식과 통합할 수 있습니다.

체화 에이전트가 저장하거나 재학습할 수 있는 양보다 훨씬 많은 데이터를 생성할 수 있기 때문에 경험 선택(Experience Selection)이 중요해집니다. 시스템은 어떤 사건이 보존할 만큼 충분한 정보적 가치를 가지는지를 결정해야 합니다. 드문 실패(Rare Failures), 특이한 지형 상호작용, 새로운 객체, 성공적인 복구 행동(Recovery Behaviors), 큰 예측 오차(Prediction Errors)와 관련된 관측은 반복적인 일상 운용 데이터보다 높은 우선순위를 가질 수 있습니다.

새로움 탐지(Novelty Detection)는 실제로 언제 적응이 필요한지를 결정하는 데 도움을 줍니다. 로봇은 모든 작은 변화나 센서 변동에 반응하여 자신의 모델을 지속적으로 수정해서는 안 됩니다. 대신 현재 관측과 익숙한 경험 사이의 차이를 평가하여 의미 있는 분포 이동(Distribution Shift)을 식별할 수 있습니다. 새로움 신호(Novelty Signals)는 추가 학습, 불확실성 추정(Uncertainty Estimation), 데이터 기록(Data Logging), 외부 지도(External Supervision) 요청 등을 활성화할 수 있습니다.

불확실성(Uncertainty)은 평생 적응을 제어하기 위한 또 다른 메커니즘을 제공합니다. 높은 불확실성은 현재 모델이 익숙한 경험의 범위를 벗어나 동작하고 있음을 의미할 수 있습니다. 시스템은 이에 대응하여 속도를 낮추고, 더 많은 관측을 수집하며, 보다 안전한 정책으로 전환하거나, 추가 학습 데이터를 기록할 수 있습니다. 신뢰할 수 있는 지도 신호가 확보되면 불확실한 경험을 통합하면서도 통제되지 않은 온라인 갱신(Online Updates)이 안전성을 훼손하지 않도록 관리할 수 있습니다.

자기지도학습(Self-Supervised Learning)은 지속적인 센서 스트림이 광범위한 수작업 레이블링 없이도 학습 목표를 생성하기 때문에 평생 운용에 자연스럽게 적합합니다. 미래 관측은 시간적 예측(Temporal Prediction)을 지도할 수 있고, 동기화된 센서는 교차 모달 일관성(Cross-Modal Consistency)을 제공하며, 실행된 행동은 상태 전이(State Transitions)에 관한 정보를 제공합니다. 따라서 명시적인 작업 레이블이나 인간 피드백이 없더라도 일상적인 운용 과정에서 표현과 월드 모델(World Models)을 지속적으로 개선할 수 있습니다.

월드 모델은 예측된 결과와 실제 관측된 결과 사이의 불일치(Discrepancies)를 측정함으로써 핵심적인 역할을 수행할 수 있습니다. 로봇이 특정 운동 응답을 예상했지만 실제로 다른 결과를 경험했다면 예측 오차는 동역학(Dynamics), 지형 조건, 페이로드(Payload), 하드웨어 특성이 변화했음을 나타내는 증거가 될 수 있습니다. 반복적으로 발생하는 예측 오차는 모델 적응(Model Adaptation)을 활성화하고 시스템의 물리 환경에 대한 내부 이해를 점진적으로 개선할 수 있습니다.

하드웨어 노화(Hardware Aging)는 평생 학습이 체화 시스템에서 특히 중요한 이유 가운데 하나입니다. 타이어가 마모되고, 관절에 백래시(Backlash)가 발생하며, 배터리가 열화되고, 카메라 보정값이 드리프트(Drift)하며, 페이로드가 변화하고, 액추에이터의 응답 특성도 장기간 사용 이후 달라질 수 있습니다. 배치 초기의 제어기(Controller)는 시간이 지날수록 부정확해질 수 있습니다. 지속적인 시스템 식별(System Identification)과 적응을 통해 이러한 점진적인 물리적 변화를 보상하면서 운용 성능을 유지할 수 있습니다.

환경 변화(Environmental Change) 역시 비슷한 요구사항을 발생시킵니다. 창고의 배치가 변경되고, 실외 지형은 날씨와 계절에 따라 달라지며, 도로 조건과 인간 활동 패턴도 변화할 수 있습니다. 로봇 자체에 변화가 없더라도 고정된 지각 모델이나 계획 모델(Planning Model)은 시간이 지나면서 현실과 맞지 않게 될 수 있습니다. 평생 학습을 통해 표현, 지도(Maps), 예측 모델, 정책이 변화하는 환경 조건을 지속적으로 반영하도록 할 수 있습니다.

새로운 작업(New Tasks)은 시스템의 행동 능력(Behavioral Competence)을 확장하도록 요구합니다. 초기에는 내비게이션만 학습한 로봇이 이후 검사(Inspection), 배송(Delivery), 조작(Manipulation), 협업 행동(Collaborative Behaviors)을 수행해야 할 수 있습니다. 전이 학습(Transfer Learning)은 기존에 습득한 지각과 월드 지식을 재사용할 수 있게 하고, 기술 라이브러리(Skill Libraries)는 기존 행동 프리미티브(Behavioral Primitives)를 제공합니다. 평생 학습은 새로운 능력이 기존 능력을 대체하지 않고 보완하도록 이러한 추가 학습을 조직합니다.

지속 강화학습(Continual Reinforcement Learning)은 이러한 과정을 정책과 가치 함수(Value Functions)로 확장합니다. 작업이나 운용 조건이 변화함에 따라 에이전트는 새로운 보상과 결과를 받고 이에 맞게 행동을 적응시킵니다. 그러나 제약 없는 강화학습 갱신은 이전에 신뢰할 수 있었던 행동을 불안정하게 만들 수 있습니다. 리플레이, 보수적 정책 갱신(Conservative Policy Updates), 모듈형 기술(Modular Skills), 안전 제약조건(Safety Constraints), 오프라인 평가(Offline Evaluation)를 활용하면 성능 퇴행(Performance Regression)의 위험을 줄일 수 있습니다.

지속 모방 학습(Continual Imitation Learning)도 인간이나 전문가 시스템이 새로운 시연(Demonstrations)을 간헐적으로 제공할 수 있는 환경에서 적응을 지원합니다. 운용자는 새롭게 필요한 작업을 시연하거나 특수한 상황에서 행동을 교정할 수 있습니다. 이러한 시연은 시스템 전체를 처음부터 다시 구축하지 않고 기존 정책에 통합할 수 있습니다. 핵심 과제는 새로운 사례를 흡수하면서 이전에 시연을 통해 습득한 행동 능력을 유지하는 것입니다.

메타 학습(Meta-Learning)은 시스템이 효율적으로 적응하도록 사전에 준비시킴으로써 평생 학습을 향상시킬 수 있습니다. 새로운 상황을 모두 서로 무관한 문제로 학습하는 대신 모델은 작업과 환경이 어떤 패턴으로 변화하는지를 학습할 수 있습니다. 이러한 사전 지식(Prior Knowledge)은 이후 적응에 필요한 데이터 양을 줄이고, 익숙하지 않은 조건을 만났을 때 어떤 파라미터, 기술, 표현을 수정해야 하는지를 결정하는 데 도움을 줄 수 있습니다.

작업, 환경, 체화 구조(Embodiments) 사이의 지식 전이(Knowledge Transfer)는 축적된 경험의 가치를 더욱 높여줍니다. 객체 기하학(Object Geometry), 공간 관계(Spatial Relationships), 지형 특성(Terrain Characteristics), 작업 구조(Task Structure)에 대한 정보는 하드웨어나 목표가 변경된 이후에도 유용할 수 있습니다. 따라서 평생 학습 시스템은 광범위하게 재사용할 수 있는 지식과 플랫폼별 제어 세부사항(Platform-Specific Control Details)을 구분하여 경험이 미래 능력을 최대한 효과적으로 지원하도록 해야 합니다.

평가(Evaluation)는 적응(Adaptation)과 유지(Retention)를 모두 고려해야 합니다. 가장 최근의 작업에서는 높은 성능을 보이지만 이전 능력을 상실하는 시스템은 성공적인 평생 학습 시스템이라고 할 수 없습니다. 중요한 평가 지표에는 이전 및 새로운 작업에서의 성능, 적응 속도(Adaptation Speed), 메모리 및 연산 요구량, 역방향 전이(Backward Transfer), 순방향 전이(Forward Transfer), 분포 이동에 대한 강건성(Robustness), 연속적인 학습 단계 이후의 망각 정도(Degree of Forgetting)가 포함됩니다.

안전(Safety)은 물리 시스템에서 평생 학습이 이루어지는 방식에 엄격한 제약을 부여합니다. 새로운 파라미터는 충돌 제약조건(Collision Constraints), 액추에이터 한계(Actuator Limits), 안정성 조건(Stability Conditions), 인간 안전 규칙(Human Safety Rules)을 위반하지 않는지 검증하기 전에 즉시 실제 시스템에 적용해서는 안 됩니다. 갱신된 모델은 실제 운용에 적용하기 전에 시뮬레이션, 섀도 모드(Shadow Mode), 제한된 평가 환경(Constrained Evaluation Environments)에서 먼저 검증할 수 있습니다. 또한 적응 결과가 예상하지 못한 행동을 발생시킬 경우를 대비하여 신뢰할 수 있는 폴백 정책(Fallback Policies)을 유지해야 합니다.

궁극적으로 평생 학습(Lifelong Learning)은 체화 에이전트를 고정된 학습 결과물에서 지속적으로 진화하는 지능 시스템(Evolving Intelligent System)으로 변화시킵니다. 로봇은 지속적으로 경험을 수집하고, 의미 있는 변화를 탐지하며, 가치 있는 기존 지식을 보호하고, 새로운 표현과 기술을 학습하고, 적응 결과를 실제 사용 전에 검증합니다. 메모리, 리플레이, 정규화, 모듈성(Modularity), 자기지도학습, 월드 모델, 전이 학습, 메타 학습, 안전 메커니즘을 결합함으로써 평생 학습은 물리 에이전트의 전체 운용 수명에 걸쳐 지속적으로 발전하는 지능을 지원합니다.

## 03.07. Applications

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

체화 학습(Embodied Learning)은 그 원리가 물리 세계와 디지털 세계에서 지속적으로 작동하는 시스템으로 구현될 때 실질적인 가치를 갖게 됩니다. 로보틱스(Robotics), 스마트 디바이스(Smart Devices), 자율 에이전트(Autonomous Agents)의 응용은 공통적으로 변화하는 조건을 인식하고, 상호작용으로부터 학습하며, 행동을 적응시키고, 배치 전에 설정된 고정 규칙에만 의존하는 대신 축적된 경험을 재사용해야 한다는 요구사항을 공유합니다.

로보틱스(Robotics)는 로봇이 폐루프 상호작용(Closed Interaction Loop) 안에서 센싱(Sensing), 의사결정(Decision Making), 학습(Learning), 물리적 행동(Physical Action)을 결합하기 때문에 가장 직접적인 응용 분야 가운데 하나입니다. 이동 로봇(Mobile Robots), 매니퓰레이터(Manipulators), 휴머노이드(Humanoids), 4족 보행 로봇(Quadrupeds), 산업용 로봇(Industrial Robots), 서비스 로봇(Service Robots)은 주변 환경을 지속적으로 관측하고 자신이 수행한 행동의 결과를 경험합니다. 체화 학습은 이러한 경험을 활용하여 이후의 지각, 계획, 제어, 작업 실행 능력을 향상시킬 수 있습니다.

이동 로봇(Mobile Robot)은 개발 단계에서 완전히 정의하기 어려운 환경 특성을 학습할 수 있습니다. 서로 다른 바닥, 경사, 실외 노면, 장애물, 조명 조건, 보행자 행동은 내비게이션에 영향을 미치는 다양한 변화를 발생시킵니다. 로봇은 축적된 운용 경험(Operational Experience)을 통해 주행 가능성 추정(Traversability Estimation), 위치추정(Localization), 움직임 예측(Motion Prediction), 경로 선택(Route Selection), 복구 행동(Recovery Behavior)을 개선하면서 실제 운용 환경에 맞게 내부 표현을 적응시킬 수 있습니다.

조작 로봇(Manipulation Robots)은 물리적 상호작용에 접촉(Contact), 힘(Force), 불확실성(Uncertainty), 객체 변화(Object Variation)가 포함되기 때문에 또 다른 중요한 사례입니다. 로봇은 인간 시연(Human Demonstrations), 강화학습(Reinforcement Learning), 자기지도 상호작용(Self-Supervised Interaction), 또는 이들을 결합한 방법을 통해 파지(Grasping)와 조작을 학습할 수 있습니다. 전이 학습(Transfer Learning)은 기존 기술을 새로운 객체에 활용할 수 있도록 하며, 촉각 및 시각 피드백(Tactile and Visual Feedback)은 실제 접촉 결과가 예상과 다를 때 행동을 수정하도록 지원합니다.

체화 학습은 내비게이션과 조작을 완전히 독립적인 기능으로 취급할 수 없는 이동 조작(Mobile Manipulation)에서 특히 중요합니다. 로봇은 객체에 접근하고, 자신의 몸체 위치를 조정하며, 도달 가능성(Reachability)을 추정하고, 목표물을 조작하며, 예상하지 못한 변화에 대응해야 합니다. 전체 상호작용 궤적(Interaction Trajectories)을 학습함으로써 공간 지각, 이동(Locomotion), 조작, 메모리(Memory), 작업 추론(Task Reasoning)을 동일한 물리적 목표를 중심으로 조정할 수 있습니다.

산업용 로보틱스(Industrial Robotics)는 체화 학습을 이용하여 정교하게 구조화된 환경에서의 반복적인 작업을 넘어설 수 있습니다. 전통적인 자동화는 기하학, 타이밍(Timing), 객체가 예측 가능한 상태로 유지될 때 매우 높은 성능을 제공하지만 유연 생산(Flexible Production)에서는 제품과 공정이 지속적으로 변화합니다. 학습 시스템은 안전 제약조건(Safety Constraints)과 검증된 저수준 제어(Low-Level Control)를 유지하면서 검사, 핸들링(Handling), 조립, 물류, 협업 행동을 적응시킬 수 있습니다.

서비스 로봇(Service Robots)은 병원, 사무실, 호텔, 매장, 공공시설, 가정과 같이 더욱 비정형적인 환경에서 작동합니다. 이러한 공간에는 변화하는 배치, 예측하기 어려운 사람의 움직임, 이동 가능한 객체, 다양한 방식으로 표현되는 작업 요청이 존재합니다. 다중모달 학습(Multimodal Learning)을 통해 서비스 로봇은 비전(Vision), 언어(Language), 지도(Maps), 고유수용감각(Proprioception), 상호작용 이력(Interaction History)을 통합하여 상위 수준의 요청을 물리적으로 실행 가능한 행동과 연결할 수 있습니다.

많은 실제 작업은 수학적으로 명세하는 것보다 직접 보여주는 것이 쉽기 때문에 인간 시연(Human Demonstration)은 이러한 응용에서 특히 유용합니다. 운용자는 객체를 배송하거나, 장비를 검사하거나, 물품을 정리하거나, 어려운 상황에서 복구하는 방법을 로봇에게 보여줄 수 있습니다. 모방 학습(Imitation Learning)은 이러한 시연을 초기 행동으로 변환하고, 이후 강화학습과 실제 환경 피드백(Real-World Feedback)을 통해 성능과 강건성(Robustness)을 향상시킬 수 있습니다.

자기지도학습(Self-Supervised Learning)은 배치된 로봇이 일반적인 운용 과정에서 생성되는 막대한 양의 레이블 없는 데이터(Unlabeled Data)를 활용할 수 있도록 합니다. 센서 스트림(Sensor Streams)은 시간적 예측(Temporal Prediction), 마스킹 복원(Masked Reconstruction), 교차 모달 대응 관계(Cross-Modal Correspondence), 행동 조건부 예측(Action-Conditioned Prediction)을 통해 표현을 학습하는 데 사용될 수 있습니다. 따라서 사람이 명시적으로 레이블이나 시연을 제공하지 않더라도 일상적인 내비게이션, 조작, 관측 자체가 학습의 원천이 됩니다.

평생 학습(Lifelong Learning)은 이러한 능력을 로봇의 전체 운용 수명(Operational Lifetime)으로 확장합니다. 환경이 변화하고, 하드웨어가 노화하며, 페이로드(Payload)가 달라지고, 배치 이후 새로운 임무가 추가될 수 있습니다. 평생 학습 로봇 시스템은 의미 있는 변화를 식별하고, 중요한 기존 지식을 보존하면서 모델이나 기술을 선택적으로 적응시킬 수 있습니다. 리플레이(Replay), 모듈형 아키텍처(Modular Architectures), 메모리, 정규화(Regularization), 안전 검증(Safety Validation)은 새로운 학습이 기존 능력을 파괴하는 것을 방지하는 데 도움을 줍니다.

스마트 디바이스(Smart Devices)는 더욱 광범위한 체화 시스템 또는 환경 내 위치한 시스템(Environmentally Situated Systems)을 나타냅니다. 웨어러블 디바이스(Wearable Devices), 홈 어시스턴트(Home Assistants), 지능형 가전(Intelligent Appliances), 모바일 디바이스(Mobile Devices), 스마트 카메라(Smart Cameras), 증강현실 시스템(Augmented-Reality Systems), 연결형 센서(Connected Sensors)는 사용자 및 주변 환경과 지속적으로 상호작용합니다. 많은 시스템이 로봇처럼 이동하지는 않지만 다중모달 관측을 수집하고, 맥락을 유지하며, 사용자 의도를 추론하고, 반복적인 상호작용을 기반으로 반응을 적응시킵니다.

개인화(Personalization)는 스마트 디바이스 학습의 주요 응용 가운데 하나입니다. 범용 모델(Generic Model)은 유용한 초기 능력을 제공할 수 있지만 개별 사용자는 일상 패턴, 어휘, 선호도, 환경, 상호작용 방식에서 서로 차이가 있습니다. 전이 학습을 통해 사전학습된 모델(Pretrained Model)이 광범위한 지식을 제공하고, 경량 적응(Lightweight Adaptation)을 통해 선택된 구성요소를 개인 환경에 특화할 수 있습니다. 이를 통해 각각의 디바이스나 사용자마다 완전히 독립적인 모델을 처음부터 학습할 필요성을 줄일 수 있습니다.

스마트 디바이스가 카메라, 마이크, 관성 센서(Inertial Sensors), 터치 인터페이스(Touch Interfaces), 위치 맥락(Location Context), 환경 센서(Environmental Sensors), 언어를 점점 더 많이 결합하기 때문에 다중모달 학습은 특히 중요합니다. 이러한 모달리티(Modality)는 현재 상황에 대해 서로 보완적인 증거를 제공합니다. 예를 들어 웨어러블 시스템은 움직임, 시각적 맥락, 사용자 명령을 결합하여 개별 센서만 사용할 때보다 사용자의 활동을 더욱 신뢰성 있게 구분할 수 있습니다.

온디바이스 학습(On-Device Learning)은 적응 과정에서 자주 변화하는 로컬 정보(Local Information)를 다룰 때 추가적인 장점을 제공할 수 있습니다. 선택된 학습 과정은 원시 관측을 지속적으로 원격 인프라로 전송하는 대신 엣지 하드웨어(Edge Hardware)에서 직접 수행될 수 있습니다. 이를 통해 통신 요구량과 지연시간(Latency)을 줄이고 로컬 변화에 빠르게 대응할 수 있습니다. 실제 배치에서는 연산량, 에너지 소비, 메모리, 프라이버시(Privacy), 갱신 안정성(Update Stability)을 신중하게 관리해야 합니다.

자율 에이전트(Autonomous Agents)는 체화 학습을 개별 로봇이나 디바이스를 넘어 장기간 목표를 추구하는 시스템으로 확장합니다. 이러한 에이전트는 환경을 관측하고, 내부 상태(Internal State)를 유지하며, 행동을 선택하고, 결과를 평가하며, 이후의 행동을 수정합니다. 환경은 물리적 환경, 시뮬레이션 환경, 디지털 환경 또는 이들의 조합일 수 있지만 근본적인 학습 문제는 관측(Observation), 행동(Action), 결과(Consequence), 메모리 사이의 관계에 기반합니다.

많은 목표는 하나의 관측만으로 완료할 수 없기 때문에 메모리는 자율 에이전트에서 특히 중요합니다. 에이전트는 이전 위치, 지시사항, 실패한 시도, 성공적인 전략, 발견한 객체, 중간 작업 상태(Intermediate Task States)를 기억해야 할 수 있습니다. 일화 기억(Episodic Memory)과 의미 기억(Semantic Memory)은 경험을 보존하고, 절차 기억(Procedural Memory)은 재사용 가능한 기술을 유지합니다. 이들을 결합하면 긴 상호작용 시퀀스에서도 일관성 있는 행동을 유지할 수 있습니다.

월드 모델(World Models)은 자율 에이전트가 행동을 실행하기 전에 가능한 행동의 결과를 평가할 수 있는 내부 예측 메커니즘(Internal Predictive Mechanism)을 제공합니다. 현재 관측에만 반응하는 대신 후보 행동(Candidate Actions)이 미래 상태를 어떻게 변화시킬지를 추정할 수 있습니다. 학습된 표현 및 메모리와 결합하면 이러한 능력은 계획(Planning), 반사실적 추론(Counterfactual Reasoning), 위험 추정(Risk Estimation), 대안 전략 사이의 선택을 지원하며 모든 가능성을 실제 환경에서 직접 시험할 필요성을 줄여줍니다.

강화학습(Reinforcement Learning)은 행동을 장기적인 결과와 연결함으로써 자율 행동을 개선할 수 있습니다. 에이전트는 지연된 결과(Delayed Consequences)를 고려하면서 어떤 의사결정이 유용한 결과를 생성하는지를 학습합니다. 모델 기반 접근법(Model-Based Approaches)은 학습된 월드 모델을 이용하여 가능한 궤적을 시뮬레이션할 수 있으며, 모델 프리 접근법(Model-Free Approaches)은 정책이나 가치 함수(Value Functions)를 보다 직접적으로 학습합니다. 실제 자율 시스템에서는 연산 및 안전 요구사항에 따라 두 전략을 결합할 수 있습니다.

전이 및 메타 학습(Transfer and Meta-Learning)은 자율 에이전트가 초기 학습 과정에서 명시적으로 포함되지 않았던 작업을 만날 때 중요해집니다. 이전에 획득한 표현, 기술, 월드 지식(World Knowledge)은 새로운 환경에 적응하기 위한 출발점을 제공할 수 있습니다. 메타 학습은 소수의 시연이나 상호작용을 효율적으로 해석할 수 있도록 에이전트를 준비시켜 새로운 상황마다 광범위한 재학습을 수행하지 않고도 새로운 능력을 습득하도록 지원할 수 있습니다.

언어(Language)는 자율 에이전트와 인간의 목표 사이를 연결하는 중요한 인터페이스를 제공합니다. 자연어 지시(Natural-Language Instructions)를 사용하면 사용자가 저수준 제어 시퀀스를 직접 명시하지 않고도 작업, 제약조건, 선호도, 수정사항을 설명할 수 있습니다. 언어가 다중모달 지각 및 행동과 기반화(Grounded)되면 하나의 지시를 관련 객체, 공간 관계, 하위 목표(Subgoals), 실행 가능한 기술로 변환하여 추상적인 인간 의도(Human Intent)를 구체적인 에이전트 행동과 연결할 수 있습니다.

자율 에이전트는 서로 협력하여 동작할 수도 있습니다. 여러 로봇이나 지능형 디바이스가 관측, 지도, 학습된 표현, 작업 상태, 경험을 서로 교환할 수 있습니다. 하나의 에이전트가 획득한 지식은 전이 또는 공유 모델(Shared Models)을 통해 다른 에이전트의 학습을 가속할 수 있습니다. 그러나 하드웨어, 센싱, 환경적 맥락, 신뢰성의 차이 때문에 전이된 지식이 다른 에이전트에도 적용 가능한지를 판단하는 메커니즘이 필요합니다.

안전(Safety)은 로보틱스, 스마트 디바이스, 자율 에이전트 전체에서 기본적인 요구사항입니다. 학습 시스템은 적응을 운용 제약조건을 위반해도 된다는 의미로 해석해서는 안 됩니다. 물리적 한계(Physical Limits), 충돌 회피(Collision Avoidance), 접근 권한(Access Permissions), 검증된 행동(Validated Behaviors), 인간 개입 메커니즘(Human Override Mechanisms), 불확실성 임계값(Uncertainty Thresholds), 폴백 정책(Fallback Policies)은 학습이 이루어질 수 있는 경계를 정의할 수 있습니다. 새로운 행동은 검증된 기존 운용 능력을 대체하기 전에 평가되어야 합니다.

시뮬레이션(Simulation)과 디지털 트윈(Digital Twins)은 이러한 평가를 수행하기 위한 보호된 환경을 제공할 수 있습니다. 새로운 정책, 적응 결과, 복구 전략을 실제 배치 전에 다양한 시나리오에서 시험할 수 있습니다. 어렵거나 위험한 상황도 물리 시스템을 손상시키지 않고 반복적으로 재현할 수 있습니다. 이후 실제 환경 경험을 통해 시뮬레이션 격차(Simulation Gaps)를 식별하고 모델을 갱신함으로써 시뮬레이션 학습, 실제 운용, 관측, 개선으로 이어지는 순환 구조를 형성할 수 있습니다.

지능 시스템이 더욱 연결되고 다중모달화되면서 이 세 가지 응용 영역은 점차 융합되고 있습니다. 하나의 로봇이 스마트 카메라, 웨어러블 디바이스, 클라우드 또는 온프레미스 에이전트(Cloud or On-Premise Agents), 환경 센서, 인간 인터페이스와 협력할 수 있습니다. 정보는 엣지 디바이스(Edge Devices)와 더 큰 학습 시스템 사이에서 이동할 수 있으며, 각각의 구성요소는 지각, 메모리, 계획, 제어, 적응에 대해 서로 다른 역할을 담당할 수 있습니다.

궁극적으로 체화 학습(Embodied Learning)의 응용은 지능을 정적인 모델(Static Model)에서 경험과 연결된 적응형 과정(Adaptive Process)으로 변화시킵니다. 로봇은 물리적 상호작용을 통해 학습하고, 스마트 디바이스는 지속적인 맥락 관측(Contextual Observation)을 통해 적응하며, 자율 에이전트는 목표 지향적 경험(Goal-Directed Experience)과 메모리를 통해 개선됩니다. 자기지도학습(Self-Supervised Learning), 모방 학습(Imitation Learning), 강화학습, 다중모달 학습, 전이 학습, 메타 학습(Meta-Learning), 평생 학습(Lifelong Learning)은 이러한 시스템이 실제로 운용되는 환경에 기반하면서 점진적으로 더욱 높은 능력을 획득하도록 하는 핵심 메커니즘을 함께 제공합니다.
