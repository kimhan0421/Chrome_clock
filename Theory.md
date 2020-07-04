Part.1
=======
js-clock이라는 class이름을 찾는다
```
document.querySelector(".js-class");
```

querySelector => element의 자식을 탐색

다음은 같은 의미다.
```
<h1 class="js-clock"></h1>
```
```
<h1>00:00</h1>
```

두개의 const를 깔끔하게 하고 싶어요
```
const clockContainer = document.querySelector(".js-class");
const clockTitle= clockContainer.querySelector("h1");
```
```
const clockContainer = document.querySelector(".js-class"),
 clockTitle= clockContainer.querySelector("h1");
```

콘솔창
```
const data = new Date();
date.getDay()
=> 1 (월요일)
date.getDate()
=> 29
date.getHours()
=> 13
date.getMinutes()
=> 44 (이때의 date는 new Date했을 때의 값을 가져오니 업데이트 안됨)
```

inner text => 객체 안에 텍스트를 넣기 위함
사용할 문자열 만들기 위하기 때문에 벡틱(`)를 사용.

Part.2
==========
setInterval 함수 => 두 인자 값을 받음
> 첫번째 인자 = 실행할 함수 받음
> 두번째 인자 = 실행할 시간 간격

function init 초기화 함수에서
>  getTime으로 시간을 먼저 얻고
> interval설정

```
setInterval(getTime,1000);
```
시간을 얻는 부분 (init)+ 얻은 시간을 갖고 시계 부분 HTML을 변경(getTime)

Part.3
========
querySelector => 원하는 셀렉터 다 가져옴. 클래스, css방식... \
queryselectorAll => 모든 걸 가져옴. 클래스 명에 따른 element가져옴. array로 하는데, 여기서는 하나의 element를 가져오는 것이 귀찮으니 다른 방법을 사용했음. 

get element by tag name => 태그로 element를 가져옴. input, body, html, div, section...

local storage => 작은 정보(작은 JS정보들)를 user컴퓨터에 저장하는 방법

function loadName() => 로컬 스토리지에서 정보를 가져옴 \
current user = local stroage

local stroage에 user가 있다 => paint greeting함수 부름 + 로컬 스토리지에서 가져온 텍스트

텍스트를 색칠할 것이라면, 폼은 숨겨야 함.

Part.4
========
currentUser가 없을 때 => askForName()로 user의 이름 요청 \
WEB => 이름 입력 후 Enter 하면, form에 넣은 것과 같음

form.addEventListener => 어떤 것을 form에 submit하면 handleSubmit의 함수를 처리하길 원해요

function handleSubmit(event) => event의 preventDefault. event가 발생하면 root에서 일어나고, form에서 일어남.

event는 버블! \
form을 제출하는 event가 발생하면, event는 document까지 올라가는데 이 document의 이벤트는 프로그램 되어진 다른 곳으로 보내려고 해서 페이지가 새로고침 됨. \
=> 이런 기본 값을 막고 싶어요! \
==> preventDefault를 작성해요

기본값 막는 1단계! 
> preventDefault를 작성하기 전에는 Enter를 누르면 새로고침했지만, 작성후에는 Enter를 눌러도 그대로.

=> 현재 value가 필요해요 \
==> const currentValue = input.value;로 저장해요. \
이를 확인하고 싶다면 console.log(currentValue);로 확인 가능

paintGreeting함수의 역할 
> form을 지우고, greeting을 보여주고, text를 넣을 것
> 따라서, 이 함수는 text를 필요로 함
>   >여기서는, (currentValue)로 현재의 text값을 줄 것

=> 그런데 입력한 값을 저장을 못하니, 저장하고 싶어요
==> saveName함수를 만들어요.

Part.5 
========
to-do-list
----------
todolist.js에 const로 input을 만들면, greeting.js와 충돌.

function init() => 어떤 것을 load해야 하는데, 이것은 로컬스토리지에서 온것 임.

때문에, function loadToDos()에서 사용.

function loadToDos()의 if(toDos === null)  \
=> toDos가 null과 같다면, 아무것도 안함. \
따라서, if(toDos !== null)을 이용할 것임.

=> Enter를 눌렀을 때 todo를 생성하고 삭제하고 싶어요 
> function handleSubmit(event)에 toDoInput.value="";를 추가해요.

li.appendChild(span); => father element안에 넣음.

function paintToDo(text) \
> 비어있는 li와 버튼, span을 만듦. 
> span을 li에 넣고, 버튼을 li에 넣음. 
즉, span과 delet버튼을 li에 넣고, 마지막으로 li를 ul에다 넣음

JS에 이모지를 넣고 싶어요
------------------------
HTML의 head에 넣기 
```
<meta charset="utf-8" />
```

주석
----
html의 주석
```
<!---내용--->
```

JS의 주석
```
//내용 
/*내용 */
```

CSS의 주석
```
/*내용*/
```

Part.6
========
화면에 띄워보자
---------------
todo를 저장하는 것부터가 시작!
이것은 array가 되어야 함 ) 할일이 많아질 수 있기 때문

li에 id가 없으니 추가
=> 후에, 버튼 클릿기 어떤 li를 지워야 하는지 알 수 있음

이런식으로 하는 이유?
> local storage에도 todo를 저장해두어야 하기 때문

function saverToDos() => toDos를 가져와서 로컬에 저장

주의!
local storage는 JS의 data를 저장할 수 없음. \
JS의 string만 가능
=> 따라서, JSON.stringify를 사용

array기능 중, forEach
> 기본적으로 함수를 실행.
> array에 담겨있는 것들 각각 한번씩 함수 실행해줌


Part.7
========
local storage에서 to do를 하나 지우고 저장.
HTML에서도 지워야 함

function deleteToDo(event) => 지우기.
> console.log(event.target);로 어느 버튼 지웠는지 알려줌.
> console.dir(event.target);로 해당 버튼의 father을 가리키는 것을 찾음
> > parentNode 찾았다!
> console.log(event.target. parentNode);로 바꿔줌

const li = btn.parentNode; => 지워야 할 버튼

=> 새로고침 하면 삭제한 것이 삭제되지 않음.

function filtter() => forEach에서 function을 실행하는 것과 같은 방식. 각각의 item과 같이 실행될 것임. \
function filtter(toDo) => true인 것들인 toDos만 return. id값이 1인 경우 \
filters = array의 모든 아이템을 통해 함수를 실행, ture인 아이템들만 가지고 새로운 array를 만듦

cleanToDos => filterFn이 체크가 안된 아이템들의 array를 줌 \
=> 그런데, li에 없는 id인 toDos를 체크하고 싶어요. \
==> toDos.filter(function(toDo))로 함수를 만들어요.

li.id => string 이니, parseInt로 숫자로 바꿔야 함.

toDos는 이전 것, cleanToDos는 새로운 것 \
=> toDos는 const로 했었는데, 바꿀 수 없으니 let toDos로 바꿔야 함

fifter, forEach => list에 있는 모든 item을 위한 함수를 실행하는 것
