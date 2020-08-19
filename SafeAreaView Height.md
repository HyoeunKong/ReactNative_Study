# Safe Area View 의 Height 구하기



### SafeAreaView

safeAreaView 는 Device의 안전한 영역을 구별하는 Component이다. IOS 버전 11 이상을 사용하는 IOS 기기에만 적용된다. Android에서는 사용이 불가능 하다. Navigation Bars, Tab Bars, Toolbars 등등의 Component에서 다루지 않는 부분을 반영하기 위해 패딩을 자동으로 적용한다.



### Status Bar Height 구하기

Status Bar 의 Height는 아이폰의 버전에 따라 달라진다. 하지만 React Native에서 제공해주는 Status Bar 컴포넌트에서 Android만 currentHeight 를 사용 할수 있다. 그래서 IOS의 경우 react-native-status-bar-height 라이브러리를 사용해 쉽게 구할수있다. 

```javascript
yarn add react-native-status-bar-height
```



### Width, Height

React Native에서 Device의 Width, Height는 쉽게 구할 수 있다. 왜냐하면 Dimensions라는 API를 제공하기 때문이다. 아래와 같이 간단하게 구할 수 있다.

```javascript
const Width = Dimensions.get('window').width
const Height = Dimensions.get('window').height
```



### Iphone X 이전의 버전

Iphone X 이전의 버전에서는 상태표시줄을 제외한 부분을 SafeAreaView의 영역이다.그래서 StatusBar의 Height만 제외해 주면 된다.

```javascript
import {getStatusBarHeight} from "react-native-status-bar-height";
const height = Dimensions.get('window').height - getStatusBarHeight()
```



### Iphone X 이후의 버전

Iphone X 이전의 버전에서는 상태표시줄 뿐만이 아니라 Home Indicater 의 부분도 제외를 해줘야 SafeAreaView의 영역이다. 그래서 Status Bar의 Height뿐만이 아니라 Home Indicator의 부분도 제외를 해줘야 한다.

```javascript
yarn add react-native-iphone-x-helper
```

위의 라이브러리는 iphone의 version 을 Iphone X 이전, Iphone X 이 후를 알려주고 Home Indicator의 Height를 구할 수 있는 라이브러리이다.

```javascript
import {getBottomSpace} from "react-native-iphone-x-helper";

const height = Dimemsion.get("window").height - getStatusBarHeight() - getBottomSpace();
```



### 만약 Iphone의 버전을 구별해서 사용하면 다음과 같이 사용하면 된다.

```javascript
import {Dimensions} from "react-native";
import {getStatusBarHeight} from "react-native-status-bar-height";
import {isIponeX, getBottomSpace} from 'react-native-iphone-x-helper';

const status = getStatusBarHeight(true);
const Height = () => {
  if(isIphoneX()){
    return Dimentsions.get("window").height - status - getBottomSpace();
  }else {
    return Dimenstions.get("window").height - status;
  }
}
```

