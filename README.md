## ✏️  간략한 소개

---

비트캠프에서 주관하는 [네이버클라우드] full-stack 개발자 과정에서 미니프로젝트를 진행하였습니다.

1. **프로젝트 제작**: 전체 프로젝트의 방향과 목표를 설정하고 계획을 수립
2. **요구사항정의서 제작**: 프로젝트가 무엇을 해야 하는지, 어떻게 동작해야 하는지 명확히 정리하고 문서화.
3. **ERD(Entity-Relationship Diagram), UseCase 설계**: 데이터베이스 설계와 관련된 중요한 작업으로, 효율적인 데이터 관리와 처리를 위한 구조 설계
4. **싸이월드 클론코딩과 Hello_World 진행**: 기본 개념을 익히고 실력을 향상시키기 위해 싸이월드를 클론코딩 하면서 전체적인 웹 개발 프로세스를 이해하기 위해 주제를 선정.

## 💡  개발 문서

<img
  src="img/11.png"
   width="100%"
  height="80%"
/>
<img
  src="img/22.png"
   width="100%"
  height="80%"
/>
<img
  src="img/33.png"
   width="100%"
  height="80%"
/>
## 🔎  상세 내용

---

<img
  src="img/44.png"
   width="100%"
  height="80%"
/>
### 회원정보 [프로필 이미지]

<img
  src="img/55.png"
   width="100%"
  height="80%"
/>

<aside>
🐦

1. **프로필 사진 변경 기능 구현**: 사용자가 자신의 프로필 사진을 변경할 수 있도록 이미지 경로를 생성하고, 해당 경로에 업로드된 이미지를 프로필 사진으로 사용하게끔 구현했습니다. 이를 통해 사용자는 원하는 이미지를 자신의 프로필 사진으로 설정할 수 있게 되었습니다.
2. **전체 유저 리스트와 미니홈피 이동 기능 구현**: 회원가입한 전체 유저의 리스트를 출력하는 기능을 구현하고, 리스트 내의 각 유저 이름 옆에 바로가기 링크를 제공하여 클릭하면 해당 유저의 미니홈피로 이동할 수 있게끔 구현했습니다.
</aside>

### 방명록

<img
  src="img/66.png"
   width="100%"
  height="80%"
/>
<aside>
🐦

- **로그인 유저로 기본 작성자 지정**: 사용자가 로그인한 후에는 해당 사용자의 세션 정보가 저장되어 있어, 글을 작성할 때 로그인한 사용자가 기본 작성자로 지정됩니다. 이는 로그인한 사용자만이 글을 작성할 수 있도록 하고, 작성자의 정보을 확인하는 데 사용됩니다.
- **다른 사람의 미니홈피 방문 시 세션 분리**: 로그인한 사용자가 다른 사람의 미니홈피를 방문하여 글을 작성할 때도, 세션 정보는 분리되어 관리됩니다. 따라서 로그인한 사용자가 다른 사람의 방명록에 글을 작성하더라도, 글의 작성자는 로그인한 사용자로 정확히 기록되고 표시됩니다.
</aside>

### 일촌 신청

<img
  src="img/77.png"
   width="100%"
  height="80%"
/>

<aside>
🐦

- **일촌 맺기**: 사용자가 다른 사람의 미니홈피에 접속해 일촌을 맺고 싶다고 요청하는 기능입니다.
- **일촌 승인 알림**: 상대방이 로그인 했을 때, 일촌 요청을 받았다는 알림을 받습니다. 이 알림을 통해 사용자는 요청을 승인하거나 거부할 수 있습니다.
- **파도타기 목록, 일촌 리스트 업데이트**: 일촌 요청이 승인되면, 해당 사용자는 파도타기 목록이나 일촌 리스트에 추가됩니다.
</aside>

### 파도타기

<img
  src="img/88.png"
   width="100%"
  height="80%"
/>

<aside>
🐦

1. **일촌 조회 및 미니홈피 이동**: 일촌이 된 유저만 조회가 가능하고, 그 유저를 클릭하면 해당 유저의 미니홈피로 이동할 수 있게 했습니다.
2. **로그인 세션 유지**: 유저 세션을 분리해서 창을 이동해도 로그인한 유저의 정보가 사라지지 않도록 구현했습니다. 사용자가 서비스를 이용하는 동안 지속적으로 인증 상태를 유지하기 위해 중요한 기능이여서 세션 분리에 유의했습니다.
</aside>

### 세션 관리 (A → B 이동시 로그인세션, 타겟 세션 유지)

<img
  src="img/99.png"
   width="100%"
  height="80%"
/>

<aside>
🐦

1. **요청 파라미터로 `userid` 받기**: 클라이언트에서 요청을 보낼 때 **`userid`**를 파라미터로 전달하게 되면, 서버 측에서 **`@RequestParam`** 어노테이션을 사용하여 해당 값을 받을 수 있습니다.
    
    ```java
    
    @RequestMapping("/visit")
    public String visitMiniHomepage(@RequestParam String userid, HttpSession session) {
        
    }
    
    ```
    
2. **세션 유지**: 사용자가 로그인한 상태에서 다른 사람의 미니홈피를 방문할 때, 해당 사용자의 로그인 세션 정보를 유지해야 합니다. 이를 통해 사용자가 자신의 아이디로 인증된 상태를 유지하면서 다른 사람의 미니홈피를 탐색할 수 있게 됩니다.
3. **다른 사람의 미니홈피 방문**: **`userid`** 값을 통해 특정 사용자의 미니홈피에 접근할 수 있으며, 로그인한 사용자의 세션 정보를 유지하면서 해당 미니홈피를 탐색하고 상호작용할 수 있습니다.
</aside>

## 📖  사용 기술

---

<img
  src="img/10.png"
   width="100%"
  height="80%"
/>

---

## 📝  담당한 기능

- **조장 (전체 기능 구현의 30% 담당)**: 프로젝트의 총괄적인 관리와 진행을 담당하면서, 전체 기능의 약 30%를 구현했습니다.
- **회원 정보 [프로필 이미지]**: 사용자의 프로필 이미지 관리 기능을 개발했습니다. 사용자는 자신의 프로필 이미지를 업로드하거나 수정할 수 있습니다.
- **방명록**: 사용자가 서로 메시지를 남길 수 있는 방명록 기능을 구현했습니다.
- **일촌 맺기**: 서비스 내에서 사용자들이 일촌(친구)을 맺을 수 있는 기능을 개발했습니다.
- **파도타기**: 다양한 사용자 간의 소통을 위한 '파도타기' 기능을 구현했습니다. 서로 다른 사용자끼리 쉽게 접근하고 소통할 수 있게 해주는 기능입니다.
- **세션 관리 (A → B 이동 시 로그인 세션, 타겟 세션 유지)**: 사용자가 A 페이지에서 B 페이지로 이동할 때 로그인 세션과 타겟 세션을 유지할 수 있도록 세션 관리 기능을 구현했습니다. 이를 통해 사용자 경험을 향상시켰습니다.

## 📝  회고

---

- **세션 관리의 중요성**: 초기에 세션에 대한 이해가 부족해서 로그인 유저와 홈페이지 방문자의 세션을 구분하지 못한 **실수**를 했습니다. 이로 인해 로그인만 하면 모든 정보가 공개되는 **치명적인 문제**가 발생했습니다. 이 문제를 인식하고 세션의 **중요성**을 ****깊이 느꼈으며, 즉시 세션을 분리해 정보를 세션별로 제공하도록 **개선**했습니다.
- **조장으로서의 역할과 반성**: 첫 프로젝트에서 **조장**을 맡아서 **프로젝트의 완성**과 **퀄리티**에 초점을 맞추다 보니, 코드에 대한 깊은 이해나 개발에는 상대적으로 **집중을 하지 못했습니다**. 프로젝트가 끝난 후에는 본인이 작성한 코드를 **복기**하면서 '왜 이렇게 했을까?', '어떻게 개선할 수 있을까?' 등의 질문을 계속해서 던져보았습니다. 부족한 부분이나 수정해야 할 사항이 발견되면, 다음에는 같은 실수를 반복하지 않도록 복기하고 **개선하려 노력했습니다.**
