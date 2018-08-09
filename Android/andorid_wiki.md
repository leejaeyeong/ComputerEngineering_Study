# Android

KAP의 3가지 플랫폼 중 하나인 Android에 대해 기본적인 학습 커리큘럼을 표시한 위키이다.

기술 스택의 변화에 따라 상시 변경이 가능하며, 기본적으로 꼭 알아야할 사안들만 작성한다.

## Android란 무엇인가?
Android는 mobile device를 위한 플랫폼이다. 운영체제와 미들웨어, 사용자 인터페이스, 어플리케이션, MMS 서비스 등을 하나로 묶어 서비스를 제공하며 다양한 Application을 만들어 설치하면 실행될 수 있도록 구성되어 있다. Linux를 기반으로 제작되었고 언어는 Java를 사용한다.

- 특징
 - 자바기반
 - 오픈소스
 - 완벽한 컴포넌트
 - 높은 점유율
 - 높은 이식성
 - 쉬운 연동


- XML 이란?
  - eXtensible Markup Language
  - what is difference with http and xml?
   - http는 이미 만들어서 제공되는 태그만 사용
   - XML 태그는 사용자임의로 만들 수 있으며 어떠한 데이터를 설명하기 위해 이름을 임의로 지은 태그로 데이터를 감싼다.


## 기본 Widget들
Text View나 Button같이 View 중에서 컨드롤 역할을 하는 것을 **widget**이라고 부른다.
**widget**에 대한 여러가지 속성을 속성할때  **android:속성**형태로 XML코드에 선언할 수 있다.

- **TextView**
 - **text**: 텍스트뷰에 보이는 실제 문자열을 설정
 - **textColor** : 텍스트 뷰안에 정의된 문자열의 색상을 결정하는 속성
 - **textSize** : 텍스트 뷰에 표시되는 문자열 크기 설정 크기 단위는 dp, sp, ps
 - **textStyle** : 텍스트뷰에 표시되는 문자열의 스타일 속성을 설정
 - **singleLine** : 텍스트뷰에 표시하는 문자열을 한 줄로만 표시하도록 설정
 - ex)

  ```xml
 <TextView
    android:text="문자열 입력"
    android:textSize="22dp"
    android:textStyle="bold|italic"
    android:textColor="#88ff8888"
    android:typeface="serif"
    android:singleLine="true"/>
 ```

- **Button**
 - TextView를 상속하여 XML코드의 태그를 Button으로만 변경해줄 경우 바로 사용 가능
 - click이 발생할 경우 이벤트 처리를 위해 Onclick 속성에서 이벤트 처리 함수를 등록해야 한다.

  ```xml
<Button
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:layout_gravity="center_horizontal"
   android:gravity="center"
   android:text="선택 버튼"/>
```

- **CheckBox**
 - 해당 아이템이 선택/해제 되어있는지 여부를 표시
 - 필요한 class => CompoundButton

  ```xml
 <CheckBox
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="false"/>
 ```

- **RadioButton**
  - 하나의 아이템이 선택될 경우 다른 아이템의 체크 상태를 해제 해야 하므로 **RadioGroup**안에 있는 **RadioButton**은 모두 같은 그룹으로 인식

  ```xml
  <RadioGroup
     android:layout_width="wrap_conten"
     android:layout_height="wrap_content"
     android:layout_gravity="center_horizontal">
  <RadioButton
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
     android:text="선택1"/>
  <RadioButton
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
     android:text="선택2"/>
  </RadioGroup>
```

- **EditText**

 - 안드로이드에서 특정한 문자열을 입력받고 싶을 때 사용
 - 입력을 받을 문자열 종류 (문자열, 숫자, 주소, 이메일)
   - android:inputType
 - 어떤 내용을 입력해야하는지 힌트를 주기위할때
   - android:hint="write the name"

  ```xml
 <EditText
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:inputType="textCapWords"
 android:hint="write the name"/>
```

- **ImageView**

 - image를 화면에 표시하기 위한 위젯
 - 직접 로딩하기 위해 **/res/drawable** 폴더 밑에 이미지 복사
 - **android:src** : 원본 이미지 저장
 -  **android:maxWidth(maxHeigh)** : 이미지가 표현되는 최대 크기를 설정
 -  **scaleType** : 이미지를 확대/축소할 때 어떤 방식으로 보여줄지 설정

  ```xml
   <ImageView
      android:layout_width="match_parent"
      android:layout_height="wrap_content"
      android:layout_gravity="center"
      android:background="@drawable/picuture"
      android:contentDescription="this is picture"/>

 ```

### 1. Activity
Activity란 사용자에게 제공되는 UI를 말한다. Application은 적어도 하나 이상의 Activity를 갖고 다른 Activity와의 관계에 따라 Active, Pasused, Stopped 라는 세 가지 상태를 갖는다. Activity의 상태에 따라 Network나 Database 등과 같이 컴퓨팅을 요구하는 작업은 중단하고 Activity가 다시 화면에 보여질 때 필요한 리소스들을 가져와서 작업을 적절히 다시 실행하는 것이 중요하다.

 - Status
 Main Activity에서 다른 Activity를 실행할 경우 다른 Activity를 실행하고 실행된 Activity는 Stack에 저장한다.(Main Activity Stopped 상태) 만약 뒤로가기를 누를 경우 Stack에 Top을 제거하고 이전에 있던 Main Activity를 실행한다.
   - Active(활성) : 현재 화면에 Activity가 표시되는 상태, 사용자와 상호작용이 가능한 상태
   - Paused(일시정지) : 화면에 Activity가 보이지만 사용자와 상호작용을 할 수 없는 상태
   - Stopped(정지) : 다른 Activity에 의해 완전히 가려진 상태

### 2. Fragment
Fragment란 하나의 Activity에서 여러 화면을 표현하기 위한 개념이다. 하나의 Activity는 여러 개의 Fragment 화면을 가질 수 있다.

### 3. Button / ImageView
- **Button**
 Button은 기본적으로 TextView를 상속하여 정의 되었기 때문에 TextView의 속성을 사용할 수 있다. Button의 종류로는 Button, RadioButton, CheckBox 등이 있다.
  - Button
  - RadioButton
  - CheckBox

- **ImageView**
ImageView는 이미지를 삽입하는 기능을 가진 Wedget이다. 정상적으로 구현 되기 위해서는 res-drawable 경로에 해당 이미지 파일을 위치시키고 .xml에  android = "@drawable/파일명"이라는 코드를 추가해야한다.

 - android:src : 해당 이미지를 설정한다.
 예시) android:src="@drawable/파일명"
 - android:tint : ImageView에 불러온 Image에 색상을 적용한다.
 예시) android:tint="#80ff0000"
 - android:scale : Image의 크기 조절 방식을 설정한다.
 - android:maxWidth, android maxHeight : 이미지의 최대 크기를 설정한다.

### 4. ListView / GridView
- **ListView**
사용자가 정의한 data 목록을 화면에 구성할 수 있게 해주는 Widget이다. ListView에 표시되는 아이템은 단순히 Text만 출력하는 구조가 될 수 있고, Image, Button, CheckBox 등 여러 View의 조합으로 구성되는 좀 더 복잡한 Custom 형태가 될 수도 있다.

- **GridView**
GridView란 data 목록을 바둑판 형식으로 표현 할 수 있게 해주는 Widget을 말한다. GridView는 ListView와 유사하게 구현할 수 있다.

 - Adapter
ListView를 사용하기 위해서는 data와 UI를 연결해주는 Adapter를 사용해야한다.

 - View 구성
     - View의 xml 코드 작성
     - View에 표시할 item 정의(Button, TextView  )
     - Adapter 생성 후 View에 지정

### 5. RecyclerView
RecyclerView란 ListView가 향상되고 유연해진 것이다. 기존에 ListView로는 다양한 형태의 list를 표현하거나 costom ListView를 만드는데 한계가 있었으나 RecyclerView Widget으로 이러한 점을 보완할 수 있다.

- **Adapter**
기존에 ListView는 data에 따라 BaseAdapter, ArrayAdapter, CursorAdapter, SimpleAdapter 등으로 구분하여 사용했지만 RecyclerView는 Universal Adapter 하나만 사용하여 data를 처리할 수있다. 이를 위해선 3가지 interface를 구현해야한다.

 - onCreateViewHolder(ViewGroup parent,int viewType)
 ViewHolder를 생성하고 View를 연결
 - onBindViewHolder(ListItemViewHolder holder, int position)
 재활용 되는 View를 호출하여 실행되는 method
 - getItemCount()
 데이터의 개수를 반환한다.


- **RecyclerView.LayoutManager Class**
RecyclerView.LayoutManager Class를 통해 수직 뿐만 아니라 수평스크롤 또한 구현할 수 있고 다양한 Type의 data list를 사용할 수 있다.

 - LinearLayoutManager
 수평, 수직 스크롤을 지원하는 list를 만들 수 있다.
 - StaggeredGridLayouManager
 View 마다 크기를 다양하게 지정할 수 있다.
 - StaggeredGridLayouManager
 GridView 형태의 list를 구현한다.

### 6. Navigation Drawer
Navigation Drawer란 화면에 나타날 때 서랍을 여는 듯한 animation으로 나타나는 design pattern을 말한다.

- DrawerLayout
DrawerLayout은 자신의 영역 안에 있는 자식 View가 Drawer와 같은 동작을 수행할 수 있도록 하는 Layout이다.

## 디자인 패턴이란 무엇인가?

### MVC Pattern

### MVP Pattern
- 참고 : [Android Architecture Blueprints](https://github.com/googlesamples/android-architecture)

## Open Source

### 오픈 소스 라이브러리란 무엇인가?

### Butterknife

### Okhttp3

### Retrofit2

## 난독화

### Proguard
