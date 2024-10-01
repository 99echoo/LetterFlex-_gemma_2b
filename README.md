# LetterFlex-_gemma_2b
Personal statement proofreading service utilizing Gemma_2b.

![Header Image](https://github.com/user-attachments/assets/7b00ea66-5ce3-4c0a-9dba-5bb3ffbf181c)

**Gemma API를 활용한 자소서 교정 서비스**

## 프로젝트 주제
생성형 AI 프레임워크를 활용하여 자소서를 주제에 맞게 변환해주는 서비스 기획

---

## 사용 기술

- **Gemma 2bit (LLM)**  
  젬마는 트랜스포머 디코더 아키텍처를 기반으로 사전 학습된 모델입니다. 다른 거대 자연어 모델과 달리 Google의 자체 기술로 경량화된 자연어 모델입니다.

- **RAG (Retrieval-Augmented Generation)**

  ![RAG 방법론](https://github.com/user-attachments/assets/14844b8e-3a24-44a1-91bb-1e60c72548a8)
  
  [RAG 방법론 설명](https://proceedings.neurips.cc/paper_files/paper/2020/file/6b493230205f780e1bc26945df7481e5-Paper.pdf)

---

## 개발 구성
### 아키텍처
![모델 아키텍처](https://github.com/user-attachments/assets/1356c9f7-acce-4cfa-9061-7f07b8b5177c)


### 1. Gemma-2bit 모델 불러오기
먼저, 사전 훈련된 **Gemma-2bit** 모델을 불러옵니다. 이 모델은 자소서 생성에 필요한 자연어 처리 기능을 제공합니다.

### 2. 파이프라인 및 파라미터 설정
모델을 기반으로 파이프라인을 설정하고, 필요한 파라미터를 구성합니다. 파라미터 설정은 모델의 성능 및 텍스트 생성 방식을 제어하는 중요한 단계입니다.

### 3. RAG 파이프라인 불러오기: RAG-Sequence 모델
자연어 검색 및 생성 기능을 제공하는 **RAG (로버스트 문서 검색 및 생성) 모델**을 불러옵니다. RAG는 사전 훈련된 문서에서 관련 정보를 추출하는 데 사용됩니다.

#### 3-1. 문서 분할기 설정
대량의 문서를 효율적으로 처리하기 위해 문서를 적절한 크기로 나누는 **문서 분할기**를 설정합니다.

#### 3-2. 벡터 스토어 및 저장소 설정
문서에서 추출한 정보를 저장하고 빠르게 검색할 수 있도록 **벡터 스토어**를 설정합니다. 이를 통해 주제와 관련된 문단을 효과적으로 검색할 수 있습니다.

#### 3-3. Topic에 맞는 문단 및 텍스트 추출
설정된 벡터 스토어를 활용해, 특정 주제에 맞는 **문단 및 텍스트**를 추출합니다. 이 과정은 자소서의 내용을 주제에 맞게 작성하는 데 필수적입니다.

### 4. 프롬프트 템플릿 설정
자소서 작성에 필요한 **프롬프트 템플릿**을 설정합니다. 템플릿에는 지원자의 정보와 작성해야 할 자소서 항목이 포함됩니다.

### 5. 자소서 작성 생성
위에서 설정한 모델, 파이프라인, 템플릿을 사용하여 **자소서**를 자동으로 생성합니다. 생성된 자소서는 템플릿과 주제에 맞추어 작성됩니다.

---

## 향후 발전 과제
Gemma는 영어에 대해서만 사전 훈련되어 있기 때문에 영어 이외의 작업에 대해서 최적화된 성능을 보장할 수 없다는 한계가 있습니다. 해당 모델에 추가 이력서 관련 데이터 셋을 학습시켜 '자기 소개서 작성'이라는 주제에 부합한 챗봇이 될 수 있도록 발전시키는 것이 목표입니다.

[RAG 관련 이론 참고 블로그](https://inblog.ai/moondb/13538)

[Gemma 기술 문서](https://storage.googleapis.com/deepmind-media/gemma/gemma-report.pdf)

[Gemma 캐글](https://www.kaggle.com/models/google/gemma/)
