# 🎇 Aiffelthon : 기획안 개발 축제(PoC Lab)
개인 페이지: <a href="https://www.notion.so/0611ec61a62e4513b987ffa89dec0a96?pvs=4" target="_blank"><img src="https://img.shields.io/badge/Notion-000000?style=flat-square&logo=Notion&logoColor=white"/></a>
<br></br> 협업페이지 : <a href="https://www.notion.so/macondo0101/Final-Project-6c0b745a8a5a4bb99d1073a1d0473675?pvs=4" target="_blank"><img src="https://img.shields.io/badge/Notion-000000?style=flat-square&logo=Notion&logoColor=white"/></a>
- 16 / Feb / 2023 : 최종 기획안 발표
- 16 / Feb / 2023 ~ 24 / Feb / 2023 : Mini Aiffelthon 
- 24 / Feb / 2023 ~ 29 / Mar / 2023 : Aiffelthon • • •🏃‍
- 30 / Mar / 2023 : 최종 결과보고서 제출
- 31 / Mar / 2023 : 최종 발표

---
- 0215 : 팀빌딩 진행 
- 0216 ~ 0221 : 자료 searching 
- 0222 : backtranslation data 각 reg별 100개씩 추출 후 test_set 으로 합치기 완료
- 0223 :
  - raw set에서 test set 걸러낸 후 train set 생성 완료 
  - 말뭉치 넣었을 때 가장 유사한 topic을 추출하는 model setting 
  - NLI model 허깅페이스에서 searching > https://github.com/snunlp/KR-SBERT
- 0224 : 
  - 승용님이 주신 KR-SERT model 세팅하고 돌려보는 작업 
- 0227 :
  - sentence_transformers download 
  - 3개 NLI model 돌려보고 비교 작업 ( ddobokki / snunlp/KR-SBERT / Huffon/klue ) 
 - 0228 :
   - 다른 NLI model 찾아보기  
      - https://huggingface.co/klue/roberta-large
      - https://github.com/jjonhwa/KLUE-NLI
- 0305 :
  - 전체 회의 없음 
  - meta_data_included_raw 데이터 전처리 작업 
    - topic 분류가 제대로 되어있는지? or 제대로 되어있지 않은지?
    - 되어있다면 그 부분에 대한 근거 or 안되어있다면 그 부분에 대한 근거
  - 문장과 단어간의 유사도 확인하기 
    - topic별 랜덤하게 추출하여 비교하기 
    - 문장내에 특정 단어가 나오는지 빈도수 검사 
      - 전체적인 내용을 보면 일상적인 대화가 이어지는 내용이랑 문장안에 특정 단어가 자주 나오지 않음 > 어려울거라 예상 
      - 문장을 input으로 넣으면 관련된 topic을 추출하는 방식? 
        - https://github.com/lovit/KR-WordRank
    - ddobokki model로 유사도 측정 
- 0306 : 
  - 전체 회의 없음 ( 당일 계획 공유 ) 
  - 전 날 작업하면서 궁금했던 질문들 승용님께 공유드림 
    - topic을 어느 부분에 인자로 넣어야하는지 
    - sentence 인자를 topic으로 변경해야 하는가? 
    - encoder니까 topic이 들어가지 않는데 맞지 않을까? 
      - 문장하고 topic의 유사도를 반환하면 되는 문제이기 때문에 encoder에 표준어랑 topic을 input으로 넣어준다
      - 사투리랑 영어를 input으로 넣지 않는 이유는? 
        - ddobokki model이 한국어 표준어만 학습된 모델이기 때문에 
  - 승용님이 코드 봐주심 
    - 궁금했던 부분은 해결을 했는데 100만개의 데이터를 작업하려면 8시간 소요 , 시간 단축 필요 
      - ONNX를 사용하여 동적 프로그램 > 정적 프로그램으로 변경  
      
- 0307 : 
  - 전체 회의 없음 ( 당일 게획 공유 ) 
  - ONNX 부분 승용님께 인계 
  - 창호 퍼실님이 slack에 올려주신 의견을 해소할 수 있는 작업 진행 
    - 5개의 사투리 셋에서 토픽별로 분포를 EDA , 어떤 주제의 사투리가 많고 적은지 확인 
    - EDA 결과에 따라 집중해야할 도메인을 몇개로 추려서 번역 성능이 높이는데 집중 
      - 어떤 도메인에 집중해야할지 결정 
  - metadata EDA 작업 진행 
    - meta_topic_dial_distribution file 
    - metadata에서 topic별로 분포를 확인 
    - reg별로 topic의 분포를 확인 
    - 각 분포를 확인 후 시각화 진행 
    - 5개의 지역에서 공통적으로 높은 분포를 가진 topic top_3를 추출 
  - 작업 완료 후 승용님께 컨펌 
    - top_3 topic을 포함하여 총 5개의 topic을 추출하는 작업 진행 
    
- 0308 :
  - 당일 계획 공유 
    - 기존 작업 진행 후 data augmentation 진행 
      - 추출된 5개의 topic 위주로 데이터를 늘리는 작업 
      - 기존에 존재하는 한국어 번역기를 사용 
      - 100만개 데이터가 승용님 작업 후 5만개로 줄어서 data augmentation 필요 
  - topic 5개를 추출하는 작업 진행 
  - 창호퍼실님과 회의 진행 
    - data distribution 작업 내용 공유 
      - seq 길이 확인 우선 진행 
      - 어떤 topic의 시퀀스가 긴지 확인 
      - tail 부분을 어떤 기준으로 자를지 고민 
        - 상위 5개를 뽑는다고해도 tail부분의 topic들의 개수가 2만개 정도인데 그 정도이면 굉장히 많은 데이터 
        - tail 부분의 topic들을 확인해보면 정치 이하의 데이터들을 개수가 5천 미만 
      - 정치 이하의 topic들을 제외하고는 사용을 했으면 좋겠다 
        - 시퀀스 확인 후 문맥이 보존된채로 길이를 늘이는게 가능한지 확인 ( topic 병합 가능 여부 )  

- 0309 : 
  - 당일 계획 공유 
    - 전일 seq_length 작업 마무리 • • •🏃‍
  - 15시 멘토 meeting 진행 
  - 궁금점 생김 명일 승용님께 질문하기 
  
- 0310 : 
  - 당일 계획 공유 
  - 궁금했던점 승용님께 질문 
    - 다른 topic끼리 묶어서 문장을 길게 늘리지 말고 같은 topic안에 있는 문장들을 늘리기 
      - topic별 문장길이 
      - 지역 > topic 문장길이 
    - topic별 유사도 확인 
      - 지역 > topic에서 문장들끼리 비교를 해서 유사도가 얼마나 나오는지 확인하기 
      - https://www.sbert.net/  > 영어로 된 페이지를 주셨다... 부담 

- 0313 : 
  - 당일 계획 공유 
    - 유사도 확인 작업 오후 2시까지 마무리 
    - 3시부터 GCP관련 미팅 
  - 
  

