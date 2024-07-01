프로젝트(Project)
하나의 게임, 콘텐츠, 애플리케이션을 뜻한다.
프로젝트 창
씬(Scene)
게임의 장면이나 상태를 저장하는 단위
하나의 거대한 게임을 씬 단위로 관히 및 코드를 이용하여 이동이 가능하다.
사진 설명을 입력하세요.
게임오브젝트(GameObject)
씬에 배치되는 하나의 물체를 지징하는 단위
모든 게임 오브젝트는 위치/회전/크기를 제어하는 "Transform' 컴포넌트를 가지고 있다.
게임 오브젝트는 컴포넌트를 묶어서 관리하고, 접근할 수 있는 수단
GameObject에 원하는 컴포넌트를 추가하여 다양한 오브젝트 제작 가능
EX) 적 오브젝트, 공격 이펙트, 다양한 효과음 등
GameObject
Unity 화면에서 GameObject가 보여질 수 있는 이유는 렌더러 컴포넌트 덕분입니다.
컴포넌트(Component)
게임 오브젝트에 부착할 수 있는 C# 스크립트 파일을 지징하는 단위입니다.
게임 오브젝트에 컴포넌트를 부착하여 게임 오브젝트에 여러 기능을 부여할 수 있습니다.

2D : Sprite Renderer 컴포넌트
2차원의 이미지를 화면에 출력됩니다.
Sprite 변수에 이미지의 셋을 등록을 하게 되면 이미지가 씬 화면에 보여지게 됩니다.
3D : Mesh Renderer 컴포넌트
3 차원의 오브젝트(물체)를 화면에 출력됩니다.

Audio Suorce 컴포넌트
AudioClip 변수에 등록된 사운드 에셋을 재생할 수 있습니다.
에셋 (Asset)
프로젝트 내부에서 사용하는 모든 리소스를 지칭하는 단위
Audio, 3D model, Animation, texture, Script, Prefab, Etc 등등
에셋 스토어(Asset Store)를 운영하여 다양한 에셋을 가져올 수 있습니다.
Discover the best assets for game making. Choose from our massive catalog of 2D, 3D models, SDKs, templates, and tools to speed up your game development process.
assetstore.unity.com
초기 에셋 상태 / 에셋 스토어
프리팹(Prefab)
Hierarchy View에 잇는 게임 오브젝트를 파일 형태로 저장하는 단위
주로 게임 중간에 생성되는 게임 오르젝트를 프리팹으로 저장해두고 사용한다.
프리팹의 장점
동일한 게임 오브젝트를 여러 Scane이나 게임 원드 특정 장소에 배치할 때 Project View에 저장되어 있는 프리팹을 Drag & Drop하여 배치할 수 있다.
기회상의 변경이 있을 때 프리팹 원분을 갱신하게 되면 모든 씬에 복사되어 배치된 게임 오브젝트들도 원본과 동일하게 업데이트 된다.
사진 설명을 입력하세요.
유니티 프로젝트를 보게 되면 다음과 같이 상호작용을 하는 것을 확인할 수 있습니다.
관계
Unity 좌표
Unity 에서 사용하고 있는 좌표는 왼손 좌표계를 기준으로 x,y,z,축을 나타낼 수 있다.
2차원의 경우 x,y 축을 사용하며, 3차원의 경우 , x,y,z축을 사용합니다.
왼쪽의 사진은 2D인 경우 / 오른쪽 사진은 3D인 경우
사진 설명을 입력하세요.
게임 오브젝트 메뉴
게임 오브젝트를 생성하는 메뉴와 게임 오브젝트를 제어하는 메뉴로 나눌 수 있습니다.
사진 설명을 입력하세요.
빈 오브젝트 (Empty Object)
모든 오브젝트가 가지는 Treansform 컴포넌트만 붙어있는 오브젝트
2D Object
게임 화면에 배치할 수 있는 2D 오브젝트
Sprite
게임 화면에 2D 이미지를 보이게 하는 게임 오브젝트
Sprite 변수에 에셋을 Drag & Drop하여 적용할 수 있습니다.
3D Object
게임 화면에 배치할 수 있는 3D 오브젝트
Cube
한 변의 길이가 1이고, 6개의 면으로 이루어진 육면체
텍스처를 적용하면 모든 면에 동일한 이미지가 표현된다.
Mesh Filter 컴포넌트 : 3차원 오브젝트의 외형
Mesh 변수에 등록된 데이터에 따라 외형이 다르게 구성된다.
Mesh Renderer 컴포넌트 : 3차원 오브젝트의 표면 색상
Materials과 Light 정보를 바탕으로 표면의 질감이 표현된다.
Box Collider컴포넌트
게임 오브젝트의 충돌 범위를 설정
사진 설명을 입력하세요.
카메라(Camera)
플레이어가 게임 화면을 볼 수 있는 눈 역할을 담당합니다.
사진 설명을 입력하세요.
카메라 오브젝트는 씬에 최소 1개 이상 존재해야합니다.
여러 개의 카메라를 이용해 분할된 화면을 관찰하는 것도 가능합니다.
카메라에 이동 or 회전 애니메이션을 추가해 장면의 연출 효과를 주기도 합니다.
Clear Flags
오브젝트가 존재하지 않는 빈 배경을 어떻게 채울지 결정하는 요소
주로 2D 게임은 Solid Color, 3D 게임은 Skybox를 사용합니다
카메라를 동시에 여러대 사용할 때 Depth only, Don't Clear 옵션도 사용합니다
Depth only, Don't Clear 옵션을 사용할 경우
이동할 때 기존 위치의 잔상이 남아있게 됩니다.
Background
Clear Flags가 "Solid Color" 일 대 배경화면의 색상을 나타내는 변수
Projection
카메라의 시점을 나타내는 역할을 합니다
2D : Projection - > Orthographic 설정
Size가 카메라 시야 범위가 됩니다.
3D : Projection - > Perspective 설정
Field of View가 카메라 시야 범위
FOV Axis는 시야 범위를 넓히는 방향(vertical, Horizontal)
Clipping Planes
카메라가 오브젝트를 볼 수 있는 시야 거리
Near는 시작 지점(default 0.3), Far는 끝 지점(dafault 1000)
Far 거리를 늘리면 카메라가 볼 수 있는 시야 거리가 늘어난다
단, 시야가 늘어나는 만큼 그리는 오브젝트 수가 많아져 성능에 영향을 미칠 수 있다.
Viewport Rect
카메라가 본 것을 화면에 출력하는 영역 설정(min 0, max 1)
x, y는 출력을 시작하는 위치 좌표, width, heigh는 출력하는 화면 크기
Light
완전한 암흑 공간을 만들고 싶을 때
메뉴에서 window - Rendering - Lighting Settings를 선택해 Lighting View를 열어서 환경광과 주변광을 어둡게 설정합니다.
카메라의 Clear Flags를 어두운 검은 화면으로 설정
