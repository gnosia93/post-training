
* [1. EKS 클러스터 생성하기]
 
* [2. Quantization](https://github.com/gnosia93/post-training/blob/main/lesson/2-quantization.md)

* [3. NVIDIA Dyanmo](https://github.com/gnosia93/post-training/blob/main/lesson/3-dynamo.md)
  - [로컬 Docker 배포하기](https://github.com/gnosia93/interence-on-eks/blob/main/lesson/3-dynamo-docker.md) 
  - [EKS 배포하기](https://github.com/gnosia93/interence-on-eks/blob/main/lesson/3-dynamo-eks.md) 

* [4. 엔드포인트 성능 테스트하기]

* [5. 모델 Quntization 성능 테스트하기] 



```
# 1. 저장소 클론
git clone https://github.com/coder/code-server
cd code-server

# GPU 리소스 요청
resources:
  requests:
    nvidia.com/gpu: 1
  limits:
    nvidia.com/gpu: 1

# GPU 노드 선택
nodeSelector:
  nvidia.com/gpu: "true"

# Taint 처리 (필요시)
tolerations:
  - key: nvidia.com/gpu
    operator: Exists
    effect: NoSchedule


# 2. LoadBalancer + 비밀번호 설정
helm upgrade --install code-server ci/helm-chart \
  --set service.type=LoadBalancer \
  --set extraArgs="{--auth,password}" \
  --set-string extraEnvVars[0].name=PASSWORD \
  --set-string extraEnvVars[0].value="yourpassword"

# GPU 설정으로 설치
helm install vscode-gpu ci/helm-chart \
  -f vscode-gpu-simple.yaml \
  --namespace vscode \
  --create-namespace

kubectl exec -n vscode -it $(kubectl get pod -n vscode -o jsonpath='{.items[0].metadata.name}') -- nvidia-smi

```


## 레퍼런스 ##

* https://github.com/NVIDIA/Model-Optimizer/tree/main 
* https://github.com/huggingface/accelerate









