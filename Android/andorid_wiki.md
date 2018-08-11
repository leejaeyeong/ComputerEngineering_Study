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
design pattern은 coding을 하는데에 있어서 일종의 약속과 같은 역할을 한다. 기존에 작성했던 코드를 수정하기 위해서는 구조를 다시 파악해야하고 이 과정에서 많은 시간을 필요로한다. 이러한 시간적 소모를 줄이기 위한 것이 패턴화이다. 즉, 프로젝트를 구조화 시킴으로서 다른 사람이 보더라도 바로 파악이 가능하게 하는 것이 design pattern이다.  
### MVC Pattern
MVC란 Model, View, Controller의 합성어이다. 사용자가 Controller에게 요청을 보내면 Controller는 Model을 통해서 데이터를 가져오고 그 정보를 바탕으로 시각적인 표현을 담당하는 View를 제어해서 사용자에게 전달하게 된다.
 - **각각의 역할**  
Model : 백그라운드에서 동작하는 로직처리  
View : 사용자가 보게 될 결과 화면을 출력  
Controller : 사용자의 입력 처리와 흐름 제어를 담당  

- **특징**  
MVC pattern은 Model, View, Controller의 세 영역으로 구분하여 영역 간의 결합도를 소화한 패턴이다. MVC 패턴의 가장 중요한 장점 중 하나는 비즈니스 logic과 presentation 로직이 분리되었다는 것이다. 즉, 디자이너와 개발자들의 영역이 분리됨으로써 서로 각자의 영역에 더 집중할 수 있다는 장점이 있다.


### MVP Pattern https://www.slideshare.net/madvirus/mvp-63161829
MVP란 Model View Presenter의 약자로 MVC pattern을 보완한 design pattern이다. 동작 방식은 Model과 View는 Presenter만 알고 있으면 서로 의존성이 없고 Android에 가장 많이 적용되는 desing pattern이다.

  - **각각의 역할**  
  Model : 백그라운드에서 동작하는 로직처리  
  View : 사용자가 보게 될 결과 화면을 출력  
  Presenter : 사용자의 입력 처리와 흐름 제어를 담당    


 - **동작**  
 1. View로 부터 사용자의 입력  
 2. View -> Presenter로 작업 요청  
 3. Presenter -> Modle로 data 요청
 4. Model -> Presenter로 요청한 data 응답
 5. Presenter -> View로 data 응답
 6. View는 Presenter로부터 받은 data를 화면에 나타낸다.

## Open Source

### 오픈 소스 라이브러리란 무엇인가?
오픈 소스 라이브러리란 공개된 소스코드를 말한다. 개인 또는 단체가 작성한 소스코드를 공개함으로서 다양한 사람들이 이를 보완하고 수정하여 완성도를 높여간다.
### Butterknife
Butterknife란 Android의 대표적인 오픈 소스 라이브러리이다. Butterknife liberary를 사용하면 기존에 button을 구현하기 위해 작성해야했던 code 간소화하여 작성할 수 있다.
 - **사용 방법**  
  1. Gradle Setting
  ```gradle
  dependencies {
  compile 'com.jakewharton:Butterknife:[version]'  
  annotationProcessor 'com.jakewharton:Butterknife-compiler:[version]'  }
  ```  
  2. onCreate() 내에 code 추가  
  ```  
  ButterKnife.bind(this);
  ```  
  3. 기존에 findViewByld(viewID) 대신 @Bind keyword를 사용한다.  
  ```
  @Bind(R.id.tv_info) TextView tv_info;  
  ```  
  4. ButterKnife를 이용하여 button을 한 번에 처리하는 예  
  ```
  @OnClick({R.id.btn_method, R.id.btn_listener, R.id.btn_implements})   
  void buttonEvents(View v) {   
      //에빈트를 처리할 로직
    }  
  ```

### Okhttp3
Okhttp3란 효율적인 HTTP 통신을 처리하기 위한 오픈 소스 프로젝트를 말한다.  
 - **사용 방법**
  1. Gradle 추가  
  ```
  compile 'com.squareup.okhttp3:okhttp:3.8.0'

    ```  
  2. Okhttp3 객체 생성  
  ```  
  RequestBody body = new FormBody.Builder()
                        .add("Id", id)
                        .build();  
                        ```  
  3. 객체를 요청할 목적지 설정  
  ```  
  Request request = new Request.Builder()
                        .url(url)
                        .post(body)
                        .build();
                       ```  
  4. client에 요청  
 ```  
 client.newCall(request).enqueue(callback);  
 ```

### Retrofit2
Retrofit2란 API 통신을 위해 만들어진 liberary를 말한다. Retrofit2을 사용하면 server에 request를 보내고 xml 방식으로 파싱을 해야하는 불편함을 덜 수 있다.  
 - **사용 방법**  
  1. Gradle 추가  
    ```Xml  
    compile 'com.squareup.retrofit2:retrofit:2.0.2'
    compile 'com.squareup.retrofit2:converter-gson:2.0.0-beta4'  
    ```
  2. AndroidManifest 파일에 내용 추가  
  ```Xml  
  <uses-permission android:name="android.permission.INTERNET" />  
  ```  
  3.   


## 난독화
Software 난독화란 Software의 Source Code를 난독화하여 사람 또는 분석 tool이 이해하거나 분석하기 힘들게 변환하는 것을 말한다.
### Proguard  
Proguard는 무료료 사용할 수 있는 난독화 tool이다. Proguard를 Source Code에 적용하면 변수의 이름을 의미없는 이름으로 짧게 바꿔 난독화를 해주는 것을 확인할 수 있다. 하지만 Open source liberary인 만큼 난독화는 되지만 낮은 수준의 난독화를 한다.  
예) Proguard를 통해 난독화한 Java Code는 디컴파일을 통해 원래의 Source Code를 확인할 수 있음.
