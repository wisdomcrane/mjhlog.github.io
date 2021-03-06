---
title: "리액트 네이티브 앱 구글 플레이 스토어에 올릴 준비"
date: 2021-03-02 00:00:00
categories: journal
---

오늘은 빌드를 마무리하고 구글 플레이스토어에 올릴 준비를 했다. 주말에 쉰 날을 제외하고 정말 딱 한달 걸렸다.

구글에 개발자 등록을 했는데 무려 25불이다. 처음 등록할 때만 낸다. 예전에는 안 받았던거 같은데... 열심히 해야겠다.

플레이 스토어에 바로 올리는 게 아니라 테스트와 여러 준비를 하려고 한다. 아직 앱 아이콘도 없고 설명도 없고 스크린샷도 없고 아무것도 없다.

# 앱 아이콘 만들기

그래서 오늘은 안드로이드 앱 아이콘을 만들었다.

안드로이드 스튜디오에서 [이미지 생성 기능인 image-asset-studio](https://developer.android.com/studio/write/image-asset-studio)이 있어서 활용해서 만들었다.

매트리얼 아이콘의 svg를 다운 받아서 Inkscape로 간단하게 편집을 해서 아이콘을 생성해 주었다.

빌드 할 때 에러가 나서 봤더니 원인은 두 가지였다.

- 아이콘을 생성할 때 main에만 생성을 해주고 debug에 생성을 해주지 않아 에러가 났다.

- 특정 XML에 android:fillColor="@android:color/white" 부분에서 에러가 났다. 이 부분은 안드로이드가 color/white 같은 문자로 바로 레퍼런스하는게 안되기 때문인데 android:fillColor="#FFFFFFFF" 로 바꾸어주니 됐다. 그런데 빌드할 때 마다 다시 원래대로 돌아가서 결국 build.gradle 설정에서 다음과 같이 조치를 했다. 그랬더니 에러가 안났다.

```
defaultConfig{
    vectorDrawables.useSupportLibrary = true
}
```

# 앱 이름 바꾸기

안드로이드 앱 이름은 android/app/src/main/res/values/strings.xml 에서 displayName을 바꿔주면 된다. Object Note 라고 띄어쓰기를 했더니 에러가 나서 ObjectNote라고 했다.

일단 이름은 프로젝트명 그대로 object note로 하기로 했다. 한글로는 목표 노트이다.

# 개발자 이름 만들기

플레이스토어에 등록할 때 앱 개발자 이름을 정하는게 있었는데 Product one으로 정했다. 매일 한걸음씩만 나아가자는 의미와 최고의 제품을 만들자는 뜻을 담았다. 뭐 다른게 떠오르지 않았기 때문이기도 하고... 이름 짓는건 어렵다.

# 한달간의 마케팅 프로젝트 진행

이 단계를 뭐라고 해야할지 몰라서 마케팅 프로젝트라고 정하고 한달간 진행하기로 했다. 일단 좋은 앱이 좋은 마케팅이라고 생각해서 테스트 기간을 천천히 잡고 살 생각이다. 좀 뭔가 앱 설명서 같은 것도 써서 붙여놓고 관련해서 좋은 지식들도 정리해서 앱에 넣어볼 생각이다. 천천히 가자~!
