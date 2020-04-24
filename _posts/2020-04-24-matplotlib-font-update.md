---
title: "Matplotlib에 새로 설치한 폰트 추가하기"
categories: etc
---

`matplotlib`을 처음 설치한 뒤, 새로 폰트를 설치하면 이 폰트를 불러오지 못하고는 했다.

이번엔 [Noto Sans KR](https://fonts.google.com/specimen/Noto+Sans+KR)을 쓰려고 했는데 그게 안보이더라.

원래 `matplotlib`에서 사용 가능한 트루타입 폰트(`.ttf`) 목록은 `matplotlib.font_manager.fontManager.ttflist`를 쓰면 볼 수 있다.

하지만 새로 설치된 목록은 아무리 위 함수를 써도 보이지 않았다.

웃기는게 시스템에 설치된 모든 폰트를 보여주는 함수 `matplotlib.font_manager.findSystemFonts()`를 쓰면 설치된 [Noto Sans KR](https://fonts.google.com/specimen/Noto+Sans+KR)이 나오는 거였다.

이유를 대충 찾아보니, 시스템 폰트를 설치 당시 캐싱한 뒤에 그 목록이 업데이트 되지 않아서 그런 거였다.

폰트 캐싱 목록은 JSON 형식 파일로 `$HOME/.matplotlib` 폴더 안에 들어있다.

`matplotlib.font_manager._rebuild()` 한번 해주면 새 목록이 형성된다.

리빌드 한번 해주고 나니 새 JSON 파일이 생성된 것이 보였다. 비교해보니 예전 파일에는 새로 설치된 폰트들이 보이지 않았다.

리빌드 후 다시 jupyter를 켜보면 새로 설치된 폰트 목록이 보일 것이다.

그 다음엔 알아서 쓰면 된다.
