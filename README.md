# 프로그램 사용방법

1. 로그파일 경로를 아래 위치에 입력합니다.

 ![image](https://github.com/user-attachments/assets/7e973b7a-c8b5-4385-aea6-832270fec625)
  



</br>
</br>
</br>

   
2. 버튼을 1초동안 누를시 해당 버튼기능이 동작합니다
   
![image](https://github.com/user-attachments/assets/efdadb86-6dfe-484f-ba01-c9b4e403c3a6)

- Generate : 2개 제품 생성
- Forward : 1초마다 전진
- Backward : 1초마다 후진
- Stop : 정지


 


## 프로그램 구조
![image](https://github.com/user-attachments/assets/49727c3a-f4dd-4854-a892-14059fc303f1)

# Function Block
## FB_unit
![image](https://github.com/user-attachments/assets/0189b78e-4286-40ae-aba6-82770c20bdf8)

**Var**
- Step : 시퀀스 제어를 위한 변수
- Command : 현재 실행되고 있는 지령을 나타냄
- fbTon : 1초마다 전진 혹은 후진을 위한 TON
- bInit : FB_Unit이 Initalized가 됐는지 확인하는 Flag
- i : FOR을 위한 변수
- LED : Visu의 램프와 맵핑된 변수
- LEDLocation : LED의 위치를 나타내는 변수
- GenerateButton : Visu Generate버튼과 연결된 FB
- ForwardButton : Visu Forward버튼과 연결된 FB
- BackwardButton : Visu Backward버튼과 연결된 FB
- StopButton : Visu Stop버튼과 연결된 FB

**Method**
- Initalize : FB_Unit을 Initalized하기 위한 메소드이며 완료시 bInit = TRUE
- TurnOnTwoLED : 두 LEDLocation을 입력받아 해당위치의 LED를 On시킴

  
## FB_Button
![image](https://github.com/user-attachments/assets/d773389b-f255-45be-9bc2-0da72119962c)

**Var**
- sButtonName : Visu 버튼 Text와 맵핑된 변수
- bExecute : Visu 버튼이 눌리면 True가 됨
- ExecuteCounter : bExecute가 TRUE일시 카운터가 올라가며 1초동안 눌리는지 카운팅하는 변수
- refCommand : FB_Unit의 Command를 참조함
- InputCommand : Visu에서 어떠한 버튼이 눌리는지 확인하는 변수
- iLog : 버튼 눌리는 것을 기록하기 위한 인터페이스
- RTrig : 버튼이 눌릴때 라이징 엣지로 한번 감지

## FB_Logger
![image](https://github.com/user-attachments/assets/8dca5ee1-3f3b-47da-89a5-946eebfeb315)

**Var**
- arrLog : Log를 기록하는 배열
- fbLocalTime : 로컬시간 체크하는 기능
- sCurrentTime : 로컬시간을 String으로 받아옴
- fbRingBuffer : 10개 넘는 로그 발생시 버퍼에 넣고 File에 씀
- buffer : RingBuffer를 위한 버퍼
- fbFileWrite : File Write 기능
- fbFileOpen : File Open 기능
- fbFileClose : File Close 기능

**Method**
- AddLog : 로그 추가
- Write : 로그 10개 이후부터 File형태로 저장
