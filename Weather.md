Part.9
=======
날씨 보여주기
------------
user의 location좌표 정보를 읽어서 정보 저장 

function askForCoords() => 좌표 요청하는 함수

getCurrentPosition
> 첫번째 ) 좌표를 가져오는데 성공 했을 때 처리하는 함수 \
> 두번째 ) 좌표를 가져오는데 실패 했을 때 처리하는 함수

function handleGeoSucces
> 위도, 경도 저장 \
> 한번 위치 허용하면 새로고침 시 묻지 않음.

JS tip!
> 객체의 변수이름과 객체의 key의 이름을 같게 저장하고 싶어요 \
> latitude: latitude => latitude, 로 할 수 있다

Part.10
=======
fetch() => 데이터 가져오기

local storage에 아무것도 없으면 
> askForCoords함수 실행되는데, 이 함수 안에서 정상적으로 위치 정보를 가져오면, handleGeoSuccess가 실행되는데, 이곳에서 API가 최종적으로 호출됨

WEB
> network패널 = request,response 한 내용을 보여줌


&unit=metric => 미터법으로 하고 싶어요 \
function getWeahter(lat,lng)의 then => 데이터가 들어오는데 시간이 걸리는 경우가 있으니, then사용
> 기본적으로 함수를 호출하는 것이지만 데이터가 완전히 들어온 다음 호출하는 것.
> 때문에, fetch() 다음에 then을 사용해서 fetch가 끝난 뒤 then으로 호출하는 함수를 실행.
