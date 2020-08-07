# Live_face_recognition
# 다수의 사람 후보로 등록해 사진속에서 찾기 
Live_face_recognition
1. 프로그램의 목적: 사진을 입력받아 기존에 입력되있는 사진속 인물과 동일인인지를 판별한다. 

2. 프로그램의 앞으로 개발 방향: CCTV의 영상을 지속적으로 입력받아, 사진 속 인물과 동일인이 나타나는지를 판단해주는 프로그램을 제작해야함 


<07/20>
1. face라는 객체에, face_id라는 string 변수 member가 존재하며, 한 사진을 분석시 프로그램이 detected_face는 list의 형태로 저장하는듯함. 
--> 다수의 리스트 멤버가 생길 수 있으므로, 한 변수에 대해 다수의 리스트 멤버를 비교하는게 필요함. 

2. 제공 받는 파일이 다수의 얼굴 (멤버)가 포함되었을 수 있으므로, 이 중에 선택하는 옵션을 넣는게 좋다 사료됨. 

3. 비디오를 계속 캡쳐해서 거기서 해당 멤버의 얼굴 찾아낼 수 있는지 파악가능 (Twice 채영 얼굴 뮤직뱅크 영상에서 파악 가능한 것 확인)

다음 할 일: 
- 이렇게 캡쳐했을때 영상의 시간과 faceid, 이미지 저장 경로 list 만들어 dataframe 만들기. 
- 다수의 후보군을 등록해 다수의 인물과 비교 가능하게 만들기 
            


목표: 전체적인 구조: 반복문 돌리며, 캡쳐하고 이미지 id 만든다음 similar한 후보군을 찾아내기 .
이를 list 형태로 계속 추가해 언제 나왔는지 시간값을 프로그램 종료 후 리턴하게 하기. 해당 좌표도 같이 묶어서 다음과 같이 저장 
list=  [ [시간, 그 시간의 좌표, 이미지파일 경로], ]....

<07/22>
1. 다수의 후보군의 ARRAY를 만들어, 이 사람이 있는지를 프로그램이 찾게하기 . 
(FACE LIST ? 이게 뭐지. 설명서 찾는중.

*add_face_from_stream
1000개의 얼굴까지 등록이 가능함. 
얼굴 등록시 특정 얼굴만 나타나 있어야함. 
(required:  face_list_id (to refer a particular face list, image, target face 지정가능,detection model ) 
face_list id는 어디서 얻지? --> User can define ID.

*test prog의 구상: 여러명 나와잇는 사진 등록하고, face_list를 만든다음 한 장의 사진에서 전부 detect 할 수 있는지를 확인해보자. 

recognition model = 'recognition_03' is recommended

<07/24>
1. 만들어진 FaceListId의 정보를 어떻게 가져오는지? --> face_list_id에 자체적으로 있으므로, similar 함수를 쓰면 알아서 프로그램이 판단해서 걸러줌.  

<07/27>
1. list에서, 웹캠을 통해 동일인물 있는지 없는지를 판단하는 코드 제작함 
--> persisted_id에서 어떤 인물과 비슷한지를 알 수 있음 (similar_face list에 해당정보 저장되어있음) 

<08/07>
1. API 서버에서 사람 얼굴 등록/삭제하는 코드 만들었음. 
