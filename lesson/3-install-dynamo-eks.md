## Dyanmo ##

### NIXL(NVIDIA Inference Transfer Library)의 작동 원리 ###
* 연산 자원의 분리: NIXL은 통신을 위해 GPU의 연산 유닛(SM)을 사용하는 기존 NCCL 방식과 달리, GPU 내부의 전용 복사 엔진(Copy Engine)을 직접 제어하여 추론 연산과 데이터 전송을 완벽하게 병렬화.
* 커널 오버헤드 제거: 데이터를 보낼 때마다 GPU 커널을 매번 실행(Launch)하지 않고, CPU가 하드웨어를 직접 조작하는 비동기 방식을 채택하여 짧은 메시지를 빈번하게 주고받는 추론 환경에서 지연 시간을 획기적으로 줄임.
* 직통 데이터 경로(P2P & RDMA): 서버 내부에서는 NVLink를 통한 GPU 간 직접 접근(P2P)을, 서버 간에는 GPUDirect RDMA를 활용하여 CPU 메모리 거침 없이 GPU HBM 간의 고속도로를 생성.
* 하드웨어 레벨의 메모리 관리: 전송할 메모리 영역을 물리적으로 고정하는 Pinning과 물리 주소를 하드웨어에 직접 전달하는 Memory Registration을 통해, OS나 GPU SM의 간섭 없이도 안전하고 정확한 데이터 이동을 보장.
* 추론 효율의 극대화: 결과적으로 데이터 전송 중에도 GPU가 연산에만 100% 집중할 수 있게 하여, 특히 LLM의 KV Cache 전송이나 분산 추론 시 기존 대비 약 30~50% 이상의 성능 향상.


## 레퍼런스 ##

* [Microservices Communication with NATS](https://www.geeksforgeeks.org/advance-java/microservices-communication-with-nats/)
