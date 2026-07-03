# EasyXMRig 빠른 시작 가이드

## 📦 준비물

1. **Python 3.9 이상** (빌드할 때만 필요)
2. **PyInstaller** (exe 만들기 위함)
3. **XMRig 실행 파일** (채굴할 때 필요)

---

## 🚀 1단계: exe 파일 만들기 (처음 한 번만)

```bash
# 1. PyInstaller 설치
pip install pyinstaller

# 2. build_exe.py가 있는 폴더에서 실행
python build_exe.py

# 3. dist 폴더에 exe 파일이 생성됨
#    → dist/easyxmrig_en.exe (영어)
#    → dist/easyxmrig_kr.exe (한국어)
```

**완료!** 이제 exe 파일을 어디든 옮겨도 됩니다.

---

## 🔧 2단계: XMRig 다운로드

1. https://github.com/xmrig/xmrig/releases 방문
2. **Releases** 탭에서 최신 `xmrig-*.zip` 다운로드 (Windows 버전)
3. 임의 폴더에 압축 해제
4. `xmrig.exe` 파일이 나오는지 확인

**예시:**
```
C:\Mining\
  ├─ xmrig.exe
  ├─ libuv.dll
  └─ ... (기타 파일들)
```

---

## ⛏️ 3단계: 채굴 시작

### 1. easyxmrig_kr.exe 실행
![Start](./img/step1.png)

### 2. XMRig 경로 선택
- **Browse...** 클릭
- 위에서 다운로드한 `xmrig.exe` 파일 선택

### 3. 지갑 주소 입력
- MoneroOcean 계정의 모네로 지갑 주소 입력
- **형식**: `4ABC...XYZ` (95자 정도)
- 잘못되면 에러 메시지가 뜸

### 4. CPU 스레드 수 (선택사항)
- 비워두면 자동 (모든 코어 사용)
- 예: `4` 입력 → 4개 스레드만 사용
- 게임 하면서 채굴할 때 스레드 수를 줄이면 좋음

### 5. Start Mining 클릭
- 확인 메시지 뜸
- **지갑 주소와 수수료 비율 재확인** 후 Yes 클릭
- 로그창에 채굴 시작 메시지 보임

---

## 📊 4단계: 모니터링

### 로그 창에서 보는 정보
```
[user] 2024-07-03 14:22:15 * READY (CPU): 3.5 H/s
[user] 2024-07-03 14:22:30 * Accepted share 1/1
[user] 2024-07-03 14:22:45 * Accepted share 2/2
```

- **H/s**: 해시레이트 (높을수록 좋음)
- **Accepted share**: 채굴 풀에 제출된 검증된 작업
- **Rejected share**: 거부된 작업 (가능한 0)

### 온라인 모니터링
1. MoneroOcean 사이트 방문
2. 본인 지갑 주소로 검색
3. 실시간 채굴 현황 확인

---

## ⚙️ 주요 설정값

| 설정 | 설명 | 예시 |
|-----|------|------|
| **Wallet address** | 모네로 지갑 (필수) | `4ABC...` |
| **Password / worker id** | 워커 구분용 | `worker1`, `x` |
| **CPU threads** | 사용할 CPU 스레드 | `4`, `8`, `16` |
| **Donate level** | 개발자 기부 비율 | `1` (권장) |

---

## 🛑 5단계: 채굴 중지

### 방법 1: 버튼으로 중지
- **Stop Mining** 클릭

### 방법 2: 창 닫기
- 창의 X 버튼 클릭
- "Mining is running. Stop and quit?" → Yes

---

## ❓ FAQ

### Q: 채굴이 안 시작돼요
**A:**
- xmrig.exe 경로가 맞는지 확인
- 지갑 주소가 올바른지 확인 (에러 메시지 보기)
- xmrig.exe를 직접 더블클릭해 실행되는지 테스트

### Q: 해시레이트가 너무 낮아요
**A:**
- CPU 온도 확인 (과열되면 성능 저하)
- 다른 프로그램이 CPU를 많이 쓰지 않는지 확인
- CPU 스레드 수를 더 늘려보기

### Q: 채굴 중에 스레드 수를 바꾸려면?
**A:**
- Stop Mining → 스레드 수 변경 → Start Mining
- 또는 CPU threads 필드 수정 후 채굴 중단/재시작

### Q: 다른 풀로 바꾸고 싶어요
**A:**
- 이 버전은 MoneroOcean으로 고정되어 있습니다
- 다른 풀을 사용하려면:
  1. `easyxmrig_en.py` 또는 `easyxmrig_kr.py` 열기
  2. 상단의 `POOL_URL = "gulf.moneroocean.stream:20128"` 수정
  3. `python build_exe.py` 실행해 새로운 exe 생성

### Q: 코인을 어디서 받나요?
**A:**
- MoneroOcean의 대시보드에서 채굴 현황 확인
- 일정 금액(보통 0.3 XMR) 도달 시 지정한 지갑으로 자동 송금

---

## 💡 팁

### 1. 24/7 채굴 설정
```
1. 채굴 PC를 항상 켜두기
2. 절전 모드 비활성화 (전원 설정 → 절전 안 함)
3. 매일 수익 확인
```

### 2. 게임하면서 채굴하기
```
1. CPU threads를 절반 이상 줄이기
   예: 16코어 → 4스레드로 설정
2. Start Mining으로 백그라운드 채굴
3. 게임 시작 → 채굴도 계속됨 (CPU 로드 분산)
```

### 3. 채굴 결과 추적
```
- 매월 MoneroOcean 대시보드 확인
- 스프레드시트에 해시레이트/수익 기록
- 6개월 후 채굴기 업그레이드 여부 판단
```

---

## 🔒 보안 및 윤리

✅ **이 도구는 안전합니다:**
- Windows Defender 회피 없음
- 레지스트리 수정 없음
- 백그라운드 프로세스 숨김 없음
- 모든 설정이 화면에 표시됨

⚠️ **반드시 지킬 것:**
- 본인 소유 컴퓨터에서만 실행
- 회사/학교 PC에서 절대 사용 금지
- 남의 지갑 주소로 채굴 금지

---

## 📞 도움말

### 문제가 있으면
1. README.md의 "트러블슈팅" 섹션 읽기
2. XMRig 공식 문서: https://xmrig.com/docs
3. MoneroOcean 지원: https://moneroocean.stream

### 소스코드 수정
```python
# 기부 비율 변경: 5% → 0%로
FEE_PERCENT = 0

# 기부 지갑 변경 (본인 주소로)
FEE_WALLET = "47Jifd3..."

# 풀 주소 변경
POOL_URL = "다른.풀.주소:포트"
```

수정 후 `python build_exe.py` 실행!

---

**행운을 빕니다! 💰⛏️**
