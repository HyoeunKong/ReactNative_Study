# ResizeMode

Image 컴포넌트는 컴포넌트 크기에 맞게 자동으로 확대를 시킨다. 

컴포넌트 크기에 맞게 이미지를 조절하는 스타일을 resizeMode라고 하며 여러가지 속성을 가지고 있다.



### cover

- 기본속성

- 이미지의 가로 세로 중 좁은 부분이 부모 컴포넌트의 100%를 차지할 때 까지 이미지를 늘림
- 예를들어, 가로가 길고 세로가 짧은 이미지는 세로 영역이 부모 컴포넌트를 차지할 때 까지 늘어남
- 부모 컴포넌트 크기를 꽉 채워야 할 때 사용



### contain

- 주로 사용하는 속성
- cover 와 비슷하지만 가로 세로 중 넓은 부분이 100%를 차지할 때 까지만 이미지를 늘림
- 예를들러, 가로가 길고 세로가 짧은 이미지는 가로 영역이 부모 컴포넌트를 차지할 때 까지만 늘어남
- 본 이미지 전체를 보여줘야 할 때 사용



### Stretch

- 이미지를 주어진 width,height에 꽉 차게 비율 조정
