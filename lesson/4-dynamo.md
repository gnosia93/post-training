## NVIDIA Dynamo (차세대 분산 추론 프레임워크) ##
Triton Inference Server의 후속 기술로, 대규모 분산 환경에서 생성형 AI 및 추론 모델을 효율적으로 배포하는 하이레벨 프레임워크.

### 주요 특징 ###
* 대규모 분산 환경: 수천 개의 GPU에서 LLM을 구동할 때 필요한 오케스트레이션(요청 라우팅, GPU 스케줄링)을 처리.
* Disaggregated Serving: 프리필(prefill, 프롬프트 분석)과 디코드(decode, 토큰 생성) 단계를 분리하여 GPU 자원을 최적화.
* 엔진 Agnostic: TensorRT-LLM, vLLM, SGLang 등 다양한 고속 추론 엔진을 백엔드로 유연하게 선택 가능.
