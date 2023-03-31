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
    - 전일 seq_length 작업 마무리 
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
  - reg / topic roof문으로 embedding값 구하기 
    - kw / 가족 데이터로 진행 
    - embedding 값으로 (=100) 유사도 측정 
      - 문장간 유사도 matrix
      - numpy.diag_indices() 
    - 같은 문장의 유사도 값을 구한 부분을 제외하고 min/max 값 구하기 
      - matrix 대각선 값의 avg
      - https://numpy.org/doc/stable/reference/generated/numpy.diag_indices.html
  
  
- 0314 : 
  - 당일 계획 공유 
    - embedding값으로 유사도 측정 
  - 오늘에서야 알게된 소름돋는 사실 
      -git push를 할 때마다 readme가 수정 전 상태로 돌아가서 화가 났는데 알고보니 git pull을 안해서 업데이트가 안된 파일을 계속 push로 올렸던것... ! 
  - konlpy.okt로 한문장씩 넣어서 유사도를 측정 해보려고 했다 
    - list라서 readline() 함수가 적용이 안됨 
    - list를 txt 파일로 변경하려고 해봤는데 실패 
  - 승용님이 참고하라고 주신 코드로 matrix로 만들어서 embedding값 구함 
  - 유사도
  - EDA : 우리 데이터에 대한 특성 심층적으로 분석
	  - Tokenizer 마다 가장 많은 빈도를 갖은 token은 무엇일까?
	  - Tokenizer 마다 토큰화 결과에 어떤 차이점들이 두두러지게 나타날까?
	  - 우리 모델은 어떤 길이로 최종 분석하면 좋을지?
	  - 우리 데이터의 잘못된 데이터들이 있을까?
	  - etc.
	  
- 0315 :
	- 당일 계획 공유 
		- 데이터 EDA 
		- 효원님이랑 pair해서 질문에 대한 답 찾을 수 있도록 준비 
		- model 팀이 데이터를 돌릴 수 있도록 여러 데이터 준비 
		- 데이터 관련한 질문들 준비해보기 > 공유 
		- 전 날 작업한 유사도 작업 승용님이랑 공유 
	- meta > reg 분류 작업 완료 
		- for문으로 40개나 되는 topic을 어떻게 나눠야할까? 
   	- 회의 
		- Multilingualism translation / raw resource > 문제점 
		- EDA 데이터 씹뜯맛즐 
		- EDA 관련 자료 검색 
			- 데이터에 어떤 문제가 있는지 
			- 그 데이터를 갖고 어떤 방식으로 진행해야하는지 
		
  - 0316 : 
  	- 당일 계획 공유 
		- 멘토님께서 주신 논문 읽고 질문 생각
		- 15시 멘토링 

- 0317 :
	- EDA
		- 토크나이저(split, spm, mecab, mec + spm) 사투리 특징을 잘 잡아내는 토큰이 어떤 것인지 확인 및 시각화 
	
- 0321 : 
	- 멘토링 
		- eng dial 번역 성능
		- tokenizer보다는 일단 eng <> dial 번역 성능에 문제가 있는게 보임 
		- 사투리적 특성이 잘 나타나는 도메인이 있기도하고 없기도 함  
		- 사투리 특성이 많이 드러날수록 bleu가 떨어지는 거 같음 
		- 사투리 특성이 잘나타는것보다는 번역성능에 문제 
			- pretrained 모델 사용하면 번역 성능이 좋음 	
			- pretrained model 이 어떤게 있고 사이즈가 어떻게 되는지 
			- pretrained model 파인튜닝 하는게 좋은지 Vanilla transformer에 집중하는게 좋은지 빠르게 확인해보는게 좋을듯 
			- pair하게 비교하려면 전처리 조건을 동일하게 맞춰놓고 진행
				- 대조군을 실험체계에 넣어서 비교를 해보기 
				- Vanilla transformer랑 kobert랑 조건을 동일하게해서 비교해보고 kobert는 파인튜닝 해보기  


		- 2차 분석 요청 
			- 5개의 데이터를 합쳐서 진행 
			- n-gram별이 각 지역별로 출연빈도의 분산
    			- 지역별로 분산이 크면 특정 지역에만 집중적으로 나타남을 의미 
    			- 분산값을 크게하는 토크나이저가 무엇인지 
       				- 지역특성을 잘 잡아낸다 라는걸 볼 수 있음 

	- 2차 분석 요청하신거 작업 진행
		- pickle 파일 toknize한 뒤 spm , msp 진행 후 seaborn.kdeplot으로 시각화 
		- 1 ~ 5 , 2500에서 그래프가 급격하게 치솟음 
			- 스페이스바 , 문장기호 등 확인 작업 
			- remove 했는데도 그래프에 큰 변화가 없음 
				- 확인 작업 필요 

- 0322 : 
    - spm , msp 데이터 n-gram ( unigram , bigram , Trigram ) 사용하여 kdeplot으로 시각화 
        - 지역별로 어떤 값에서 분산이 큰지 확인하기위해 
        - Bigram , Trigram에서 지역별로 차이가 확실하게 보임 
          
    - 코드작성에 어려움이 있어서 승용님께서 도와주심 
    
- 0323 : 
    - push를 깜빡하고 안했더니 파일이 다 날아가서 다시 작성중 .. 
        - Trigrams, Bigrams 두 그래프 순서 변경 
        - 색상 변경 요청 > cc, jd 구별 필요 
    - 이전 작업 후 추가된 파일에 대해서 3가지 작업 진행 
        - 추가된 파일 : custom_msp, msp_8000 data 
        - 진행 작업 : unk count, subword fertility , proportion of continued words 
            - 결과값과 그래프상 숫자 일치여부 확인 
            - unk count > 8000data > spm값이 23259088 > 확인 필요 
    - Unigram , Trigrams, Bigrams 결과물 막대그래프 > 워드 클라우드로 작업
        - 발표자료에 막대그래프가 다 안들어가서 워드클라우드로 작업 요청 
            
- 0324 : 
    - 멘토링 
    - https://jamboard.google.com/d/158KoSUYsTH3wGbBFM2-ZxREvDSLPXyGCCnXUcXRVg6Q/viewer?f=3
    
- 0327 ~ 0328 
    - vocab_size : 8000만 사용 
    - test_data , train_data 다시 만들어주셔서 그 데이터로 데이터 EDA진행 
    - EDA 
        - 지역별 데이터 분포 
        - topic별 데이터 분포 
        - 문장 최대 길이 
        - reg, topic, tok_len 평균
        - spm , msp , custom_msp 
            - unigram, Bigrams, Trigrams 
            - kdeplot 
            - wordcloud 
                - wordcloud > Bigrams, Trigrams 잘 안나와서 명일 승용님한테 질문 예정 
     - 효원님 피드백 
         - kdeplot legend부분 크기 조절 
         - 데이터 EDA 자료 
         
 - 0329 : 
     - 멘토링 
     - wordcloud 승용님이 코드 수정해서 주신거 코드 돌려봄 
         - cloud에서 자꾸 ValueError: We need at least 1 word to plot a word cloud, got 0. 에러 발생 
             - css가 비어있고 , unigram에서 사용했던 regs가 밑에 코드로 내려옴 
                 - regs = df_train.reg.unique() 넣어서 오류 잡아줌 
        - bigrams, Trigrams 에서 지역별 사투리 특성을 잘 나타내주는 토큰들이 있다고는 보이지 않음 
    
 - 0330 : 
     - 구글 슬라이드에 올라온 피드백 반영해서 시각화 다시 하기 
         - kdeplot > 첫 행은 unigram, 두번째는 bigram, 세번째는 trigram
         - wordcloud
             - 토크나이저 별로 결과가 어떻게 다르게 나오는지 / 토큰별로 비교할 수 있게 
         - Train , test data 데이터 개수 / per
             - 한 그래프에 길이랑 퍼센트가 다 나오는 방식
         - len distribution
             - y축 범위를 동일하게 해서 출력
         - Count by Topic(%) 제목 수정
         - 히트맵 같은 경우 seq length > char len로 그래프로 시각화 
    
    
    
 - 0331 : 
 	- EDA 파일 잘못 불러와서 spm16000데이터 경로 재설정 후 그래프 재출력
 	- 아이펠톤 발표 완료 
		- https://docs.google.com/presentation/d/1gCV6pQudUJVnuIDKXRbhF84OROsjF8IuY0kQGD7U-mE/edit#slide=id.g228d6ddd591_2_0
	- https://padlet.com/jungwooil/1-88n1vak9ohu1qsna
	- 한 달 동안 아이펠톤 하면서 많이 배웠는데 이 배움을 잊지않으려면 더 열심히 공부해야겠다 ! :) 

![saturi](https://user-images.githubusercontent.com/103499697/229083431-a0f4292b-2249-447d-a0b9-dbddc253ce4e.jpg)
