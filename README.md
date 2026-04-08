테스트 계획 및 결과 보고서

1. 개요
테스트 목적: 모델의 응답 정확도 검증, 속도 최적화 지표 수집 ?????
테스트 대상: LLM 엔진 (Ollama ebdm/gemma3-enhanced:12b), RAG, 프롬프트 템플릿, 멀티 에이전트

2. 테스트 환경 (Environment)
Model: Llama-3, GPT-4o, BGE-M3 (Embedding)
Framework: LangChain, PyTorch, Streamlit


3. 테스트 지표

| 지표 (Metric) | 설명 | 목표치 /5 |
|--------------|-----|---------|
| 응답 정확성 | 생성된 답변이 참조 (Retrieved Docs, RDB) 답변과 비교해서 정확한 정보 추출하는지 평가에 기반했는가? | 5 | 
| 관련성 | 질문의 의도에 맞는 답변을 생성했는가? | 4 | 
| 지연 시간 | 첫 번째 토큰 생성까지 걸리는 시간 (TTFT) | ????? | 
| UX 흐름 | UX 흐름이 원활한지 평가 | 4 | 

 
4. 테스트 시나리오 및 결과 (Test Scenarios & Results)
**멀티 에이즌트**
 모델 응답 정성 평가 (Qualitative Results)

| 서비스 | 질문 (Input Query) | 기대 답변 예시 | 실제 모델 답변 (Actual Output) | 판정 |
|------|-------------------|-------------|----------------------------|-----|
| 멀티 에이즌트 | "펜실베니아 대학교 학비 알려줘." | "펜실베니아 대학교 학비는 8만 1,990달러입니다." | "펜실베니아 대학교 학비는 연간 8만 1,990달러입니다. 이 금액은 수업료, 수수료, 그리고 필수 부교재비를 포함하고 있어요. 기숙사비와 식비 등 생활비는 별도로 고려해야 합니다. 더 자세한 내용은 펜실베니아 대학교 재정 지원 홈페이지에서 확인하실 수 있습니다." | Pass |
| 입시지원 챗봇 | "UCLA대학교에 입학에 필요한 서류를 알려줘." | "UCLA대학교에서 필요한 서류는 성적표, 테스트 걸과 서류, 등등이 필요합니다." | "UCLA 대학교 입학에 필요한 서류는 다음과 같습니다.\n\n*   지원서: Common Application 또는 Coalition Application을 통해 제출합니다.\n*   고등학교 성적 증명서: 정식 증명서 원본을 제출해야 합니다.\n*   SAT/ACT 점수: UCLA는 Test-Free 정책을 시행하고 있지만, 점수를 제출하는 것은 선택 사항입니다.\n*   영어 능력 시험 점수: TOEFL, IELTS 등 공인 영어 시험 점수가 필요합니다.\n*   추천서: 고등학교 교사 2명으로부터 추천서를 받아야 합니다.\n*   에세이: UCLA에서 요구하는 에세이를 작성해야 합니다.\n*   경력 및 활동 내용: 지원자의 경험과 활동을 보여주는 자료를 제출해야 합니다.\n\n자세한 내용은 UCLA 입학처 홈페이지에서 확인하실 수 있습니다." | Pass |


| 서비스 |  질문 (Input Query) | 기대 질문 예시 | 실제 모델 질문 (Actual Output) | 판정 |
|------|--------------------|-------------|----------------------------|-----|
| 비자 모의면접 | - | "Why did you choose computer science and why University of California Berkley? " | "Considering your program start date of August 27, 2025, and your major in Computer Science at the University of California Berkeley, can you briefly describe your initial plans for your studies upon arrival?" | Pass |
| 비자 모의면접 | - |  "What is your planned course of study?" | " Considering your acceptance to the University of California Berkley to study Computer Science, can you elaborate on specific coursework or research opportunities within the program that particularly excite you?" | Pass |
| 비자 모의면접 | - |  "Tell me about who is funding your studies?" | "Given your funding sources include personal funds and funds from another source, could you please explain the specific arrangement you have with this other source to ensure consistent financial support throughout your Computer Science program at the University of California Berkley?" | Pass |



 Considering your acceptance to the University of California Berkley to study Computer Science, can you elaborate on specific coursework or research opportunities within the program that particularly excite you?
User: I am especially looking forward to doing research and learning more about AI.  I believe AI is the future and will be an integral part of the future.  I truely believe that AI is and will continue to touch almost every aspect of our lives and my goal is to contribute positively to that. 

Officer: Given your funding sources include personal funds and funds from another source, could you please explain the specific arrangement you have with this other source to ensure consistent financial support throughout your Computer Science program at the University of California Berkley?


























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
















테스트 계획 및 결과 보고서

1. 개요
테스트 목적: 모델의 응답 정확도 검증, 속도 최적화 지표 수집 ?????
테스트 대상: LLM 엔진 (Ollama ebdm/gemma3-enhanced:12b), RAG, 프롬프트 템플릿, 멀티 에이전트

2. 테스트 환경 (Environment)
Model: Llama-3, GPT-4o, BGE-M3 (Embedding)
Framework: LangChain, PyTorch, Streamlit


3. 테스트 지표

| 지표 (Metric) | 설명 | 목표치 |
|--------------|-----|------|
| 응답 정확성 | 생성된 답변이 참조 (Retrieved Docs, RDB) 답변과 비교해서 정확한 정보 추출하는지 평가에 기반했는가? | ????? | 
| 관련성 | 질문의 의도에 맞는 답변을 생성했는가? | ????? | 
| 지연 시간 | 첫 번째 토큰 생성까지 걸리는 시간 (TTFT) | ????? | 
| UX 흐름 | UX 흐름이 원활한지 평가 | ????? | 

 
4. 테스트 시나리오 및 결과 (Test Scenarios & Results)
**비자 모의면접**
 모델 응답 정성 평가 (Qualitative Results)
| 서비스 | 질문 (Input Query) | 기대 답변 예시 | 실제 모델 답변 (Actual Output) | 판정 |
|------|-------------------|-------------|----------------------------|-----|
| 멀티 에이즌트 | "펜실베니아 대학교 학비 알려줘." | "펜실베니아 대학교 학비는 [실제 데이터] 입니다." | "펜실베니아 대학교 학비는 연간 8만 1,990달러입니다. 이 금액은 수업료, 수수료, 그리고 필수 부교재비를 포함하고 있어요. 기숙사비와 식비 등 생활비는 별도로 고려해야 합니다. 더 자세한 내용은 펜실베니아 대학교 재정 지원 홈페이지에서 확인하실 수 있습니다." | Pass |
| 입시지원 챗봇 | "UCLA대학교에 입학에 필요한 서류를 알려줘." | "UCLA대학교에서 필요한 서류는 성적표, 테스트 걸과 서류, 등등이 필요합니다." | "UCLA 대학교 입학에 필요한 서류는 다음과 같습니다.\n\n*   지원서: Common Application 또는 Coalition Application을 통해 제출합니다.\n*   고등학교 성적 증명서: 정식 증명서 원본을 제출해야 합니다.\n*   SAT/ACT 점수: UCLA는 Test-Free 정책을 시행하고 있지만, 점수를 제출하는 것은 선택 사항입니다.\n*   영어 능력 시험 점수: TOEFL, IELTS 등 공인 영어 시험 점수가 필요합니다.\n*   추천서: 고등학교 교사 2명으로부터 추천서를 받아야 합니다.\n*   에세이: UCLA에서 요구하는 에세이를 작성해야 합니다.\n*   경력 및 활동 내용: 지원자의 경험과 활동을 보여주는 자료를 제출해야 합니다.\n\n자세한 내용은 UCLA 입학처 홈페이지에서 확인하실 수 있습니다." | Fail |

**비자 모의면접**
| 서비스 | 기대 질문 예시 | 실제 모델 질문 (Actual Output) | 판정 |
|------|-------------------|-------------|----------------------------|-----|
| 비자 모의면접 | "Why did you choose computer science and why University of California Berkley? " | "Considering your program start date of August 27, 2025, and your major in Computer Science at the University of California Berkeley, can you briefly describe your initial plans for your studies upon arrival?" (환각 현상 발생)" | Fail |
| 비자 모의면접 | "What is your planned course of study?" | "Given your enrollment in the Computer Science program at the University of California Berkeley, could you elaborate on your anticipated coursework and research interests during your studies?" (환각 현상 발생)" | Fail |
| 비자 모의면접 | "What are your plans of employment during your study?" | "Considering your program start date of August 2025 at the University of California Berkeley, can you briefly describe your initial plans for your first semester as a Computer Science student?" (환각 현상 발생)" | Fail |






























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

