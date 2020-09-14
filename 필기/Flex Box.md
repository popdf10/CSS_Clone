# Flex Box

```css
.father{
    display: flex;
}

.child{
    nothing...
}
```

​	flex는 father에서 안에 있는 child를 다 컨트롤 할 수 있다.



## Main Axis & Cross Axis

main axis가 default는 row. cross 는 column

```css
.father{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

​	justify-content 는 메인을 움직이고, align-items는 cross를 움직인다.



## align-self & order

```css
.father{
    display: flex;
}

.child:nth-child(2){
    align-self: flex-end;
}
```

align-self는 align-items처럼 동작하지만 자식 개개를 컨트롤 할 수 있음.



#### order

디폴트는 0, 1이나 -1을 줘서 순서를 바꿔 위치를 조정할 수 있다.



## flex-wrap

```css
.father{
    display: flex;
    flex-wrap: wrap;
}
```

flex-wrap의 디폴트는 nowrap -> 개수가 늘어나면 찌그러듦

wrap으로 바꿔주면 자식들이 고유의 크기를 유지하고 크기에 맞춰 레이아웃이 조정됨.



## flex-direction

```css
.father{
    flex-direction: column-reverse;
}
```

디폴트는 row

row-reverse / column / column-reverse로 방향을 수정할 수 있음.



## align-content

```css
.father{
    align-content: space-between;
}
```

디폴트는 space-around

콘텐츠의 속성이 아닌 콘텐츠 간의 line을 조절함



## flex-shrink

```css
.father{
    display: flex;
}

.child:nth-child(2){
    flex-shrink: 2;
}
```

디폴트는 1, 2로 하면 화면이 찌그러들때 다른 자식보다 2배 더 많이 찌그러듦



## flex-grow

```css
.child:nth-child(2){
    flex-grow: 2;
}

.child:nth-child(3){
    flex-grow: 3;
}
```

디폴트는 0

flex-grow를 한 자식들끼리 자신에게 적힌 값의 비율로 '남은 공간'을 나눠가짐



## flex-basis

flex-direction: row; 일 때는 width와 같이 동작하고, column일 때는 height와 같이 동작

즉, main axis의 방향과 같은 속성을 제어함