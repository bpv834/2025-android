
# 액티비티 생명주기(Activity Lifecycle)
<img width="550" height="671" alt="images_its-mingyu_post_ef359ab0-12d5-442c-8349-60119eecfe25_image" src="https://github.com/user-attachments/assets/c27c7adb-7080-4208-8191-987b51974b84" />


# 📱 Android Activity 생명주기 (Lifecycle)

Android Activity의 상태 변화에 따라 호출되는 주요 콜백(Callback) 메서드들을 정리했습니다.



---

## 1. `onCreate()` 
* **호출 시점:** Activity가 **생성**되면 가장 먼저 호출됨.
* **특징:**
    * 생명주기 통틀어서 **단 한 번**만 수행되는 메소드.
    * Activity 최초 실행에 해야 하는 작업을 수행하기에 적합함.
* **주요 구현 내용:**
    * 화면 Layout 정의, View 생성 및 초기화, Data Binding 등.

---

## 2. `onStart()` 
* **호출 시점:** Activity가 화면에 **표시되기 직전**에 호출됨.
* **특징:**
    * 화면에 진입할 때마다 실행되어야 하는 작업을 이곳에 구현함.

---

## 3. `onResume()` 
* **호출 시점:** Activity가 화면에 보여지는 **직후**에 호출됨.
* **특징:**
    * 현재 Activity가 사용자에게 **포커스인(Focus-in)** 되어있는 상태.

---

## 4. `onPause()` 
* **호출 시점:** Activity가 화면에 보여지지 않은 **직후**에 호출됨.
* **특징:**
    * 현재 Activity가 사용자에게 **포커스아웃(Focus-out)** 되어있는 상태.
    * 다른 Activity가 호출되기 전에 실행되기 때문에 **무거운 작업을 수행하지 않도록 주의**해야 함.
    * **영구적인 Data**는 이곳에 저장.

---

## 5. `onStop()` 
* **호출 시점:** Activity가 다른 Activity에 의해 **100% 가려질 때** 호출되는 메소드.
* **예시:** 홈 키를 누르는 경우, 다른 액티비티로 완전히 이동이 있는 경우.
* **특징:**
    * 이 상태에서 Activity가 호출되면, **`onRestart()`** 메소드가 호출됨.

---

## 6. `onDestroy()` 
* **호출 시점:** Activity가 **완전히 종료되었을 때** 호출되는 메소드.
* **종료 원인:**
    * **사용자:** `finish()`, `onBackPressed()` (기존 액티비티의 `onResume()`까지 호출된 후 `onDestroy()` 호출).
    * **시스템:** 메모리 부족(프로세스 종료).
* **주의:**
    * `onStop()`, `onDestroy()` 메소드는 **메모리 부족**이 발생하면 스킵될 수 있음.

---

## 7. `onRestart()` 
* **호출 시점:** **`onStop()`**이 호출된 이후에 다시 기존 Activity로 돌아오는 경우에 호출되는 메소드.
* **특징:**
    * `onRestart()`가 호출된 이후 이어서 **`onStart()`가 호출**됨.
