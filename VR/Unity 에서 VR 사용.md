# Unity 에서 VR 사용


## 생성


![alt_text](https://user-images.githubusercontent.com/71301248/168506995-0f7c7f63-d5eb-4020-adbf-91c5b00a5487.png)


먼저 3D코어를 이용하여 프로젝트를 생성한다.


## VR 사용 설정

생성된 프로젝트에서 VR 설정을 위해


![alt_text](https://user-images.githubusercontent.com/71301248/168507000-1938cb55-8c94-45fa-9bca-ece15e457f47.png)


편집의 프로젝트 설정으로 들어간다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507004-0f66e6d6-f439-4011-b744-b6af4d6a590a.png)


가장 아래에 XR 플러그인 관리 메뉴로 들어가서 XR 플러그인 관리 설치 버튼을 클릭한다.


### 데스크탑 VR 플러그인 설정

데스크탑에서 빌드를 설정하는 이유는 개발중 실행 버튼을 눌렀을 때 VR기기로 테스트를 하기위해서 설정을 한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507006-ee0c8107-c17c-4766-abb3-6141d92f24d9.png)


설치 후 OpenXR을 적용한다. 여기서 Oculus가 아닌 OpenXR을 사용하는 이유는 Oculus를 사용하면 Oculus에만 적용이 되는데 OpenXR은 SteamVR과 같은 다른 VR장치로 연결해주는 미들웨어 역할을 해주기 때문에 OpenXR을 쓰는것이 더 범용성이 좋아 OpenXR을 사용한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507007-bd1b40dd-089a-4cf9-9361-24f3f9023dad.png)


그렇게 되면 새로운 input 정보가 추가 된다고 경고가 나오는데 yes를 누르면 업데이트 후 유니티가 재시작 된다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507014-853ced6c-93f4-4c65-aad3-061d2ed8550b.png)


재시작 후에 다시 화면을 보면 경고 표시가 되어있는데 노란색 경고 표시를 더블 클릭해보자


![alt_text](https://user-images.githubusercontent.com/71301248/168507018-c2fd798e-9c72-4aa5-b670-d2b7574bdfa9.png)


이렇게 해당 이슈에 대해서 보여주는데 여기서는 상호작용 추가가 안되어있어 그런 것 이므로 이 부분을 수정해 준다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507021-676934d2-fb5a-449f-9a70-7eda05c9479f.png)


에딧 버튼을 누르면 추가한 OpenXR 관련 설정으로 들어오게 된다. 상호작용을 추가하려면 여기서 Interaction Profile 부분을 추가해야한다. 해당 부분의 + 버튼을 누르면


![alt_text](https://user-images.githubusercontent.com/71301248/168507048-1fc93ff2-17c7-425a-b861-98a753dbdd0c.png)


이렇게 여러가지 종류들의 VR 기기 컨트롤러가 나오는데 지금 사용하는 VR기기는 Oculus 이므로 여기서 추가 해야 할것은 Oculus Touch Controller Profiile 이다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507051-97a7c682-7f46-4998-a9f3-a53f52278cfe.png)


그 후에 Render Mode를 설정해야한다. 지금 적용중인 Single Pass Instanced는 화면을 한번 랜더링 하고 그 영상을 양쪽 눈으로 나눠서 전송하는 방식이고, Multi-pass 방식은 양쪽 따로 따로 영상을 랜더링하여 사용하는 방식이다. Multi-pass 방식이 랜더링을 두번해서 그래픽을 더 많이 사용하지만 더 높은 퀄리티의 VR 영상을 사용할 수 있다.


### 안드로이드 VR 플러그인 설정

이부분은 이제 개발이 완료 된 후 VR에 설치를 해야 할 때 사용하기 위해 설정하는 부분이다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507056-1163a81e-b4a1-4987-9739-5046b94ea565.png)


여기서는 OpenXR이 아닌 Oculus를 설정한다. 위의 부분에서 OpenXR을 사용한 이유는 빌드를 PC에서 하고 Oculus Link를 통해 OpenXR을 사용하여 PC에서 Oculus로 전송을 하기 위해서 OpenXR을 사용 하였는데 Oculus에 바로 설치 할 꺼면 해당 변환 작업 없이 바로 Oculus를 사용하는 것이 더 퍼포먼스가 좋게 나온다. 사용하는 기기가 Oculus가 아니면 그대로 OpenXR을 사용하는 것이 좋다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507061-e2e78bdc-7b59-42ac-be83-b9ee0ba1096a.png)


Oculus를 눌러 새롭게 추가된 Oculus 메뉴로 들어간다. 여기서 타겟 디바이스와 랜더링 모드를 수정 할 수 있다. 사용기기는 Quest 2이고, 렌더링 모드는 아까와 같이 Multiview를 사용하였다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507103-4e1b3420-92e9-440e-962f-5d3f40da406b.png)


설정을 완료하고 Assets 폴더를 보면 XR 폴더가 생겼는데 여기 폴더에 추가된 프로파일을 이용하여 VR을 이용한 컨트롤 설정을 추가 할 수 있다.


## VR 적용 패키지 사용


### 패키지 설치


![alt_text](https://user-images.githubusercontent.com/71301248/168507110-2bcfe4e4-4453-4d1d-9c9b-1176e4452802.png)


창의 패키지 관리자(패키지 매니저)로 들어간다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507114-8353b459-12fb-45dc-b1f2-58ca11b165aa.png)


이곳에서는 방금 추가한 Oculus XR Plugin, OpenXR Plugin, XR Plugin Management를 확인 할 수 있다.

이 곳에서 추가로 설치해야 할 패키지는 Unity XR interaction toolkit인데 이 toolkit을 정식 출시된 버전이 아니다. 그래서 해당 패키지를 보기 위해 설정을 해야한다. 이 패키지에 대한 자세한 정보는 [여기](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.1/manual/installation.html)에서 찾아 볼 수 있다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507119-0404eb48-8421-46db-8e0a-b69c9634fc5a.png)


고급 프로젝트 설정을 클릭한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507123-48f38a62-195a-41ab-9547-dd5ccb2a65d6.png)


Pre relase Packages를 클릭한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507129-37e9d11d-9f0a-475d-8176-3c25cf451cfc.png)


이해함을 누른다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507133-c3858b3c-c40d-48af-bf6f-08bb1e2ee735.png)


범위를 Unity 레지스트리로 바꾸어 전체 목록을 확인한다. 그래도 해당 패키지가 존재 하지 않기 때문에 git URL에서 직접 다운을 받아야 한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507137-bac7ceaa-84c7-4393-9e3d-01598e4a7dd8.png)



![alt_text](https://user-images.githubusercontent.com/71301248/168507141-af1b245b-4149-48b3-b25d-4e16690e4140.png)


com.unity.xr.interaction.toolkit을 입력한뒤 추가한다.

추가가 완료되면 이런메시지가 나오는데


![alt_text](https://user-images.githubusercontent.com/71301248/168507143-96534eb3-bc76-4eb1-aaf1-fd98b1e68e3c.png)


Go Ahead를 누른다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507145-ca1a97bf-662f-4fd3-9b0e-0ab62452d7e5.png)


설치가 완료되면 아래에 있는 샘플에서 Starter Assets를 임포트 해준다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507148-9fa01724-5c8d-4f55-b1d1-a094c28a6d78.png)


임포트 한 파일을 찾아보면 이렇게 5개의 프리셋 파일과 하나의 액션파일이 추가된 것을 확인 할 수있는데 각각 컨트롤러의 움직임을 나타내는 파일이다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507150-3d01f1cd-c48d-486d-a276-a06c5bfc8b43.png)


프리셋 파일을 클릭 후 인스펙터 부분을 보면 기본 ActionBasedCountinousMoveProvider에 추가 라는 버튼이 있는데 5개 모두 추가해 준다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507156-a8b49c6f-782c-4fdb-ae86-e10f27d09f36.png)


액션 파일을 확인해 보면 액션 맵들을 확인할 수 있다.

다시 프로젝트 설정으로 가서


![alt_text](https://user-images.githubusercontent.com/71301248/168507157-e0a7934a-659f-46cc-9f72-053b82f01f3e.png)


프리셋 관리자로 들어가면 아까 추가한 5개의 프리셋 파일을 확인 할 수 있다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507160-2b9b5232-cad2-4b4b-97d8-0cf478593680.png)


각 액션컨트롤러들은 왼쪽과 오른쪽이 따로 구별되지 않아서 필터에 직접 분류할수 있게끔 추가해 주어야 한다.


## VR Scene


### 시야 설정

이제 기본설정이 끝났다. VR을 다룰 수 있도록 씬을 구성해보자.

먼저 간단한 바닥부터 추가해야한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507166-91c7d1a5-55e5-438a-8662-4a97fcc19b00.png)


계층 구조에서 새 평면을 추가해주고 이름을 Ground라고 짓는다.

그리고 이제 VR 사용시 시점을 추가한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507175-429eafa3-ffed-4514-95a5-76833541af15.png)


XR Origin이 2개 있는데 Action-based를 추가해야한다. 일반 XR Origin은 컨트롤러로 조작하는 것이 아닌 머리의 움직임으로 조작하는 것이기 때문에 컨트롤러를 이용해서 조작하려면 Action-based를 추가해야한다.

추가를 했을경우 XR Origin 이외에


![alt_text](https://user-images.githubusercontent.com/71301248/168507181-2faedc3e-3b5b-4dbf-aac1-c75a69033d6d.png)


XR Interaction Manager또한 같이 추가 된다. 같이 추가된 XR Interaction Manager를 통해 컨트롤러 액션을 받아서 Origin을 움직이게 만들어야 한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507186-4d70f25e-f8de-463c-91ea-151774b5ddca.png)


XR Interaction Manager의 인스펙터로 가서 input Action Manager를 추가해 준다.

그다음 Action Assets으로 가서


![alt_text](https://user-images.githubusercontent.com/71301248/168507191-9b97242b-6034-4246-9d5c-2e344ddd9566.png)


+버튼을 눌러 요소 0를 추가하고 Starter Assets으로 다운받은 액션(XRI Default Input Actions)을 추가한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507194-06cccc09-a600-4c7b-befd-e758894509c4.png)


이제 XR Origin으로 다시가서


![alt_text](https://user-images.githubusercontent.com/71301248/168507199-e4681e0b-ae32-41f5-9cad-26257bea8048.png)


카메라 정보와 각종


![alt_text](https://user-images.githubusercontent.com/71301248/168507203-d6dc210d-4f49-44d4-bebd-86d423600c60.png)


컨트롤러에 대해서 확인 할 수 있다.

이제 설정이 제대로 되었는지 확인해 보자. 실행 버튼을 누르고 VR을 착용하면 VR에서 화면을 볼 수 있다.


### 움직임 추가


![alt_text](https://user-images.githubusercontent.com/71301248/168507205-3cd59ac1-1a44-4147-997d-7e2e4f5117c3.png)


이제 움직임에 따라 VR시점을 이동할 수 있도록 Locomotion System을 추가해 준다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507209-e22d65f4-3315-4410-b37d-200f9ac80440.png)


인스펙터 부분을 보면 Locomotion System과 Teleportation Provider, Snape Turn Provider가 있다. 먼저 Locomotino System의 XR Origin에 지금까지 설정한  XR Origin을 넣는다.


#### Teleportation 사용 이동


![alt_text](https://user-images.githubusercontent.com/71301248/168507210-6d3b5bc2-c265-4d33-acaa-08d532e38280.png)


그라운드 부분에 Teleportation Area 부분을 추가시켜준다.

그리고 Ground의 색상을 변경시켜줘야 한다. 흰색이라 잘 보이지가 않는다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507212-6f51914d-2d75-4e5b-8e35-464cf6fc2ec9.png)


에셋에서 머티리얼을 추가하고, 생성된 머티리얼을 드래그해서 그라운드에 넣는다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507217-1455c540-83c3-41eb-992a-b53ca16e0b2c.png)


머티리얼의 인스펙터에서 알베도를  클릭해서 적절한 색상을 선택해 주면 된다.

그 후 아까처럼 플레이 해 보았다.

[영상](https://youtube.com/shorts/GsjYHOxG4g8?feature=share)


#### 컨트롤러 이용 이동


![alt_text](https://user-images.githubusercontent.com/71301248/168507219-e2baee1b-9496-4b06-8431-b49eef94f1a1.png)


Locomotion System으로 가서 Teleportation Provider와 Snap Turn Provider를 비활성화 하고, Continous Move Provider, Continous Turn Provider를 추가한다.

그리고 왼손으로는 이동을 하고, 오른손으로는 회전을 하기 위해서 Move에서는 오른손을 비활성화 하고, Turn에서는 왼손을 비활성화 한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507223-6ccfe1dd-2b81-43f8-b683-20e26d92a122.png)


이제 실행 해본다.

[영상](https://youtube.com/shorts/su6e_3_Pk20?feature=share)


#### Grab 추가

VR을 이용하여 실제 손처럼 사용하기 위해서 Grab을 추가한다.

먼저 잡을 블럭을 하나 추가한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507228-9d935e5f-d2dc-417b-8413-a442bea4b88f.png)


Transform을 위처럼 맞추어 준다.

XR Grab Interactable을 추가해 잡는 기능을 블럭에 추가시킨다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507229-ecde2c65-3c64-4999-a0bf-98e331acc708.png)


그 후 리지드 바디에서 충돌 검사 부분을 연속 동적으로 변경한다.


![alt_text](https://user-images.githubusercontent.com/71301248/168507236-3c9d1be9-2e7e-4bf0-8748-bc6cab09fa3a.png)


XR Grab Interactable로 가서 Smooth Postion과, Smooth Rotation을 켜준 뒤 이동 타입을 Velocity Tracking으로 바꿔준다. 이렇게 바꾸면 움직일 때 힘을 받아 실제 물체처럼 움직인다.

[영상](https://youtube.com/shorts/dGiTltvTzjI?feature=share)

영상을 보면 양손의 컨트롤러를 통해 움직일 때 물체가 같이 돌아가거나 움직이는게 보이는데 이것을 막기 위해서는


![alt_text](https://user-images.githubusercontent.com/71301248/168507237-27dc7c55-2be6-4e67-a30c-b616910b26b4.png)


양손 컨트롤러를 동시에 선택 한 후


![alt_text](https://user-images.githubusercontent.com/71301248/168507242-7876b199-3b3d-4272-8ac8-4e05a3dd3782.png)


XR Ray Interactor에서 Anchor Control을 꺼주면 된다.

[영상](https://youtube.com/shorts/8o1Wy8gr5pE?feature=share)