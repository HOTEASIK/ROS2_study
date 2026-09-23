■ 과제 주제 : ROS 2 DDS 미들웨어의 개념과 QoS 설정에 따른 통신 특성 조사

■ 조사 및 학습 요약 :
본 조사는 ROS 2의 핵심 네트워크 미들웨어인 DDS(Data Distribution Service)의 아키텍처를 이해하고, 데이터 통신 품질을 결정짓는 QoS(Quality of Service) 프로필의 설정별 특성을 분석하여 로봇 시스템의 통신 안정성을 확보하기 위해 진행되었다.

1. DDS 미들웨어의 핵심 개념
  • 데이터 중심 아키텍처: 분산 시스템 환경에서 중앙 서버 없이 노드 간 직접 통신(P2P)을 지원하여 단일 장애점(SPOF)을 제거함.
  • ROS 2 RMW(ROS Middleware): DDS 벤더(eProsima FastDDS, CycloneDDS 등)의 API를 ROS 2 추상화 계층에 연결하여 개발자가 미들웨어를 유연하게 교체할 수 있도록 지원함.

2. 주요 QoS(통신 품질) 설정 및 특성 분석
  • History (Keep Last / Keep All): 데이터를 큐(Queue)에 유지하는 방식으로, 최신 N개의 데이터만 유지하거나 시스템 메모리가 허용하는 한 모든 데이터를 보관하도록 제어함.
  • Reliability (Reliable / Best Effort): Reliable은 데이터 손실 시 재전송을 보장하여 신뢰성을 높이고(제어 명령에 적합), Best Effort는 재전송 없이 빠른 전송을 우선함(센서 데이터 및 영상 스트리밍에 적합).
  • Durability (Transient Local / Volatile): 노드가 늦게 켜졌을 때, 이전 데이터를 재전송받을지(Transient Local) 혹은 연결된 시점 이후의 데이터만 받을지(Volatile)를 결정함.

3. 기술적 시사점 및 실무 적용 방향
  • QoS 설정이 서로 일치하지 않는 노드 간에는 통신이 이루어지지 않는 'QoS 호환성 문제(Compatibility)'가 발생하므로 설계 시 프로필 매칭이 필수적임.
  • 추후 자율주행 로봇 가동 시, 네트워크 환경(Wi-Fi, LTE 등)과 데이터의 중요도에 맞춰 QoS를 최적화하여 패킷 손실 및 지연(Latency) 문제를 최소화할 계획임.
