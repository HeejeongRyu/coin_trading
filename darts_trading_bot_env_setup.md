# 🛠️ Python 개발 환경 설정 (Darts 기반 트레이딩 봇용)

이 문서는 **Windows 기준**으로 Python을 설치하고, Darts 기반 트레이딩 봇 개발을 위한 **가상환경 구성** 과정을 정리한 것입니다.

## 1. Python 설치

1. [Python 공식 홈페이지](https://www.python.org/downloads/) 접속
2. 최신 **Python 3.10+** 설치 파일 다운로드
3. 설치 시 아래 옵션 확인:
   - ✅ Add Python to PATH (꼭 체크)
   - ✅ Customize installation → pip, venv 등 필수 모듈 설치 확인

설치 완료 후 아래 명령어로 정상 설치 여부 확인:
```bash
python --version
pip --version
```

## 2. 가상환경 생성 및 실행

### 2-1. 프로젝트 디렉토리 생성
```bash
mkdir trading-bot
cd trading-bot
```

### 2-2. 가상환경 생성
```bash
python -m venv venv
```

### 2-3. 가상환경 활성화

- **Windows (CMD):**
```cmd
venv\Scripts\activate
```

- **Windows (PowerShell):**
```powershell
.\venv\Scripts\Activate.ps1
```

- **Mac/Linux:**
```bash
source venv/bin/activate
```

> 🔁 활성화 후 `(venv)` 프롬프트가 나타나야 함

## 3. 필수 패키지 설치

```bash
pip install --upgrade pip
pip install darts[torch] pandas matplotlib python-dotenv
```

> `darts[torch]`는 NBEATS 등 시계열 모델 학습에 필요한 PyTorch까지 포함합니다.

## 4. .env 파일 구성 (Binance API용)

```bash
touch .env
```

```env
BINANCE_API_KEY=your_api_key_here
BINANCE_API_SECRET=your_api_secret_here
```

> 키는 바이낸스 API 관리 페이지에서 발급 가능  
> `.env`는 `.gitignore`에 추가하여 보안 유지

## 5. 테스트 실행

아래 코드를 `main.py`로 저장하고 실행 테스트:
```python
from dotenv import load_dotenv
import os

load_dotenv()
print("API KEY:", os.getenv("BINANCE_API_KEY"))
```

```bash
python main.py
```

## ✅ 마무리

이제 가상환경에서 본격적으로 Darts 기반 트레이딩 봇을 개발할 준비가 되었습니다.  
다음 단계는 **CSV 로드 → 시계열 데이터 전처리 → 모델 학습 → 예측 → 자동매매 로직 구현**입니다.