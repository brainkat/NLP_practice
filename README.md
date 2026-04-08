테스트 계획 및 결과 보고서

1. 개요
테스트 목적: 모델의 응답 정확도 검증, 시스템 안정성 확인 및 비용/속도 최적화 지표 수집
테스트 대상: LLM 엔진 (Ollama/OpenAI 등), RAG 파이프라인, 프롬프트 템플릿

2. 테스트 환경 (Environment)
Model: Llama-3, GPT-4o, BGE-M3 (Embedding)

Framework: LangChain, PyTorch, Streamlit

Infrastructure: Apple M2 Max (32GB RAM), ChromaDB

3. 테스트 지표
| 지표 (Metric) | 설명 | 목표치 |
|------|-------|------|
| Faithfulness | 답변이 제공된 컨텍스트(Retrieved Docs)에 기반했는가? | 0.85 이상 | 
| Relevance | 질문의 의도에 맞는 답변을 생성했는가? | 0.90 이상 | 
| Latency | 첫 번째 토큰 생성까지 걸리는 시간 (TTFT) | 2.0s 이내 | 
| Robustness | 비정상적인 입력(Jailbreak 등)에 대한 방어 여부 | Pass/Fail | 

 
5. 테스트 시나리오 및 결과 (Test Scenarios & Results)
4.1 RAG 성능 테스트 (Retrieval Evaluation)
방법: 질문에 대해 올바른 문서 조각(Chunk)을 불러오는지 확인

결과:

[Case 01] 전문 기술 용어 질문: Pass (Top-k: 3)

[Case 02] 모호한 질문: Fail (문서 검색 실패 → 임베딩 모델 튜닝 필요)

4.2 모델 응답 정성 평가 (Qualitative Results)
질문 (Input Query),기대 답변 (Expected Output),실제 모델 답변 (Actual Output),판정
"""이 제품의 환불 규정은?""","""구매 후 7일 이내 가능합니다.""","""7일 이내에 환불이 가능하다고 명시되어 있습니다.""",Pass
"""현재 주식 시장 전망은?""","""모른다고 답변해야 함""","""전문가들은 현재 시장이..."" (환각 현상 발생)",Fail





















## Getting Started



toy story scripts
https://www.dropbox.com/scl/fo/jsp5e4hugp864opaerp7z/AKfzmVsRI52YCgdG_6nHsVM?e=1&from_auth=register&ignore_new_user_install_redirect=1&rlkey=00st0zjz1rzeoifjumtvsg4bl&dl=0



### EN
| Step | Description |
|------|-------------|
| 1 | Download data: [AI Hub Dataset](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=625) |
| 2 | Unzip the downloaded file |
| 3 | Navigate to: `031.온라인 구어체 말뭉치 데이터/01.데이터/1.Training_220728_add/원천데이터` |
| 4 | Unzip again |
| 5 | Move all `.json` files to the `data/` folder (current directory) |
| 6 | Execute `01_preprocessing.ipynb` code cells in chronological order |

---

### KR
| 단계 | 설명 |
|------|------|
| 1 | 데이터 다운로드: [AI Hub 데이터셋](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=625) |
| 2 | 다운로드한 파일의 압축을 해제합니다 |
| 3 | 경로 이동: `031.온라인 구어체 말뭉치 데이터/01.데이터/1.Training_220728_add/원천데이터` |
| 4 | 다시 압축을 해제합니다 |
| 5 | 모든 `.json` 파일을 `data/` 폴더(현재 디렉토리)로 이동합니다 |
| 6 | `01_preprocessing.ipynb` 코드 셀을 순서대로 실행합니다 |
