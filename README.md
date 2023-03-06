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
  - meta_data_included_raw 데이터 전처리 작업 • • •🏃‍
    - topic 분류가 제대로 되어있는지? or 제대로 되어있지 않은지?
    - 되어있다면 그 부분에 대한 근거 or 안되어있다면 그 부분에 대한 근거
  - 문장과 단어간의 유사도 확인하기 
    - topic별 랜덤하게 추출하여 비교하기 
    - 문장내에 특정 단어가 나오는지 빈도수 검사 
      - 전체적인 내용을 보면 일상적인 대화가 이어지는 내용이랑 문장안에 특정 단어가 자주 나오지 않음 > 어려울거라 예상 
      - 문장을 input으로 넣으면 관련된 topic을 추출하는 방식? 
        - https://github.com/lovit/KR-WordRank
    - ddobokki model로 유사도 측정 
