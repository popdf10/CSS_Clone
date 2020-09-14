# CSS grid

## grid-template-columns

```css
.father{
    display: grid;
    grid-template-columns: 10px 30px 25px 100px
}
```

| 10px | 30px | 25px | 100px                     |
| ---- | ---- | ---- | ------------------------- |
|      |      |      | (최소 2행이어야 되나봄..) |

이런 모양의  1row / 4column의 grid가 만들어진다.

콘텐츠가 더해지면 4column 밑으로 계속 추가가 된다.



## column-gap & row-gap

각 column, row간의 gap을 설정해줄 수 있음

동시에 적용하고 싶다면 `gap`



## repeat

```css
.father{
    grid-tempate-columns: repeat(4, 100px);
}
```

100px을 4번 반복하라는 함수



## grid-template-areas

```css
.father{
    display: grid;
    grid-template-columns: repeat(4, 100px);
    grid-template-rows: repeat(4, 100px);
    grid-template-areas:
    "header header header header"
    "content content content nav"
    "content content content nav"
    "footer footer footer footer";
}

.header{
    grid-area: header;
}

.content{
    grid-area: content;
}

.nav{
    grid-area: nav;
}

.footer{
    grid-area: footer;
}
```

직접 레이아웃을 지정해줄 수 있음 



## auto

```css
.father{
    grid-template-columns: auto 100px 100px;
}
```

100px 100px 지정한 열 말고 나머지를 남은 공간을 채워줌



## grid-column-start & end

```css
.child{
    grid-column-start: 1;
    grid-column-end: 5;
}
```

child를 어느 줄(line)에서 시작해서 어느 줄에서 끝낼 건지 선택할 수 있음

##### `grid-row-start` 와 `grid-row-end`도 있음



#### shortcut

`grid-column` 이나 `grid-row`를 써서 한꺼번에 나타낼 수 있음

```css
.child{
    grid-column: 1 / -1;
    grid-row: 2 / 4;
}
```

```css
.child{
    grid-column: 1 / span 2;
    grid-row: span 3 / -1;
}
```



## fr

###### fr = fraction(부분)

`px`이나 `em`처럼 단위로 쓰임. 
비율이라고 생각하면 쉬울 듯. 

```css
.father{
    grid-template-columns: repeat(4, 1fr);
}
```

화면 전체를 1 : 1 : 1 : 1 비율로 나눠가지겠다는 의미

`1fr 2fr 3fr;` 이면 1 : 2 : 3으로 나눠가짐



## grid-template

```css
.father{
    grid-template:
    "header header header header" 1fr
    "content content content nav" 2fr
    "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr;
}
```

첫 행에 올 요소를 적어주고 행의 높이를 적는다.
두 번째, 세 번째도 마찬가지.
마지막에 `/`를 하고 각 열의 크기를 적어준다.



## place-items

```css
.father{
    justify-items: center;
    align-items: end;
}
```

각각 `-items`의 디폴트는 `stretch`임 : grid 안의 콘텐츠가 알아서 grid 안을 위,옆으로 늘려서 꽉 채운다는 의미

##### content의 크기를 정해주면(width, height) stretch가 자동으로 안 되고 고유의 크기를 유지함.



### shortcut

```css
.father{
    place-items: end center;   // (위 옆);
}
```



## place-content

```css
.father{
    justify-content: center;
    align-content: end;
}
```

`place-items`와는 다르게 grid 전체를 옮긴다.



### shortcut

```css
.father{
    place-content: end center;   // (위 옆);
}
```



## place-self

각 개별 grid에 위치값을 적용해줌



## grid-auto-rows

```css
.father{
    grid-template-rows: repeat(4, 100px);
    grid-template-columns: repeat(4, 100px);
    grid-auto-rows: 100px
}
```

요소 개수가 4x4를 넘어서면 grid 적용이 안 된다.

`grid-auto-rows`를 써주면 그 크기만큼 늘어나는 요소에 row를 적용해 붙여줌

#### `grid-auto-columns`는 반대로 붙여줌



## minmax()

```css
.father{
    grid-template-coulmns: repeat(4, minmax(100px, 1fr));
}
```

화면을 줄여도 최소한의 크기를 보장해주고 싶을 때 `minmax(min, max)`



## auto-fill & auto-fit

```css
.grid{
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}
```

`auto-fill`은 남는 공간에 '빈' grid를 생성해줌



```css
.grid{
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
```

`auto-fit`은 남는 공간 없이 너비를 꽉 채워준다. 요소가 추가가 되면 그만큼 채우고 공간을 나눠가짐



## min-content & max-content

```css
.grid{
    grid-template-columns: min-content max-content;
}
```

`min-content`는 콘텐츠의 크기가 작아질 수 있는 최소한의 크기에 맞추는 것

`max-content`는 콘텐츠의 크기에 맞춰 커질 수 있을 만큼 커지는 것