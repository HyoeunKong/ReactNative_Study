# keychain

- react-native-keychain를 사용하면 Keychain(ios)/Keystore(Android)에 Access할 수 있다.
- 모바일 앱에서 매우 중요한 데이터는 Keychain/Keystore에서 생성된 키를 사용하여 암호화하여 저장한다. 

```javascript
import * as Keychain from "react-native-keychain"

//데이터 저장
const setItem = awync(key,value) => {
  await Keychain.setInternetCredentials(
  key,
  key,
  value)
}
//데이터 조회
const getItem = awync (key) => {
  const result = await Keychain.getInternetCredentials(key)
  return result.password;
}

export default{
  setItem,
  getItem
}

```


## ios - keychain

### keychian 이란?
하나의 암호화된 컨테이너 이며 keychain services API는 이처럼 민감한 데이터를 암호화하고 복호화하며 재사용하는 행위를 보다 쉽고 안전하게 사용할 수 있게끔 API를 제공한다.
![keychain1](/Users/konghyoeun/Desktop/Study/docx/ReactNative/image/keychain1.png)

기본적으로 디바이스를 잠그면 (Lock) keychain 역시 잠기고 디바이스를 풀면(Unlock) keychain 역시 풀린다. 이렇게 keychain 이 잠긴 상태에서는 item들에 접근할 수도 복호화할 수도 없다. 또한 풀린 상태에서도 해당 item을 생성하고 저장한 어플리케이션에서만 접근이 가능하다. 하지만 지정된 그룹에 속한 어플리케이션끼리는 데이터에 접근할 수 있다.



### keychain items

![keychain2](/Users/konghyoeun/Desktop/Study/docx/ReactNative/image/keychain2.png)

민감한 정보를 저장할 때 해당 데이터를 keychain Item으로 패키징한다. 이렇게 패키징된 Item안에는 저장하려는 데이터뿐만 아니라 해당 데이터의 속성(Attributes) 또한 같이 저장된다. 이 속성으로 데이터의 접근 가능성을 제어하고 해당 Item이 검색에 노출되게끔 공개적으로 보여주는 속성이다. (해당 데이터의 특징과 속성을 보여주는 것이지 데이터에 접근하는 것은 접근 제어에 해당하는 프로세스만 접근 가능)

그리고 추후에 검증된 프로세스(같은 그룹에거나 해당 데이터를 저장한 어플리케이션)가 Item에 접근할 때 속성의 검색을 통해 해당 데이터를 찾고 접근할 수 있다. 



### keychain wrappers

기본적으로 제공되는 keychain sercives API도 존재하지만 이를 보다 편하고 안전하게 이용할 수 있게끔 해주는 라이브러리 들이 존재한다. 대표적인 라이브러리

SwiftKeychainWrapper

SAMKeychain -(Obj - C)

LockSmith

