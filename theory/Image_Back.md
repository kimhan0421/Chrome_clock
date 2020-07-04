Part.8
========

이미지 다운 후, 폴더에 넣기

랜덤으로 숫자생성 => JS의 math모듈 사용
Math.floor => Math.floor(3.9)로 쓰면, 3으로 결과를 출력함
> cell은 올림, floor은 버림

const IMG_NUMBER => 이미지 개수대로 지정

const image = new Image(); => object생성

img.src = '/images/${imgNumber + 1}.jpg' 
> img는 이미지를 넣은 폴더 의미.
> +1은 Math.random()함수가 0을 줄 수 있기 때문


임의의 숫자들이 있는 곳에 배경을 추가
> body.prepend(image);

CSS에서
@keyframes

