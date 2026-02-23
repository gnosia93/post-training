기본 설치된 CUDA 12.8용 PyTorch 대신, CUDA 13.0 환경에서 빌드된 PyTorch 2.9.1 버전을 설치한다.
PyTorch와 CUDA 런타임 버전을 일치시켜야 드라이버 충돌이나 성능 저하 없이 GPU 연산을 수행할 수 있다.
```bash 
pip3 install torch==2.9.1 torchvision --index-url https://download.pytorch.org/whl/cu130

sudo apt-get -y install libopenmpi-dev

# Optional step: Only required for disagg-serving
sudo apt-get -y install libzmq3-dev
```
