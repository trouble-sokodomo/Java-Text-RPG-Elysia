# ⚔️ Elysia (Java 객체지향 텍스트 RPG)

![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=white)
![OOP](https://img.shields.io/badge/OOP-FF5722?style=for-the-badge&logo=object-oriented-programming&logoColor=white)

> **자바(Java) 객체지향 패러다임의 핵심 원리(상속, 다형성, 캡슐화)를 깊이 있게 적용하여 설계한 콘솔 기반 턴제 RPG 프로젝트입니다.**

<br>

## 📸 프로젝트 메인 화면
*(여기에 게임 시작 메인 화면이나 텍스트 전투가 진행되는 콘솔 창 캡처를 넣어주세요)*

<br>

## 💡 주요 기능 (Features)

* **다형성(Polymorphism) 기반 전투 시스템:** 모든 전투 객체(플레이어, 몬스터, 보스)를 상위 추상 클래스(Entity)로 묶어, 하나의 전투 메서드로 다양한 형태의 공격/피격 로직을 처리하도록 설계했습니다.
* **캡슐화(Encapsulation)를 통한 상태 무결성:** 캐릭터의 HP, MP, 경험치 등의 핵심 데이터를 `private`으로 철저히 은닉하고, 검증된 데미지 계산 메서드를 통해서만 접근하도록 하여 게임 상태의 무결성을 보장했습니다.
* **인터페이스(Interface) 아이템 시스템:** 무기, 방어구, 소모품 등 다양한 아이템을 인터페이스로 추상화하여, 새로운 아이템 타입이 추가되더라도 기존 코드를 수정할 필요가 없는 유연한 구조를 만들었습니다.

<br>

## ⚙️ 클래스 설계 구조 (Class Architecture)
* **`Character` (Abstract Class):** 공통 속성(HP, ATK, DEF) 및 공통 메서드(attack, takeDamage) 정의
  * ➡️ **`Player` (Class):** 직업별 스킬, 인벤토리, 레벨업 시스템 구현
  * ➡️ **`Monster` (Class):** 몬스터별 고유 패턴 및 드랍 테이블(Drop Table) 구현
* **`Usable` / `Equipable` (Interface):** 아이템의 사용 및 장착 행동 규약 정의

<br>

## 🛠️ 핵심 트러블슈팅 (Troubleshooting)

**🔴 문제 상황 (코드 중복 및 유지보수성 저하):** 초기 개발 시, 플레이어가 고블린을 공격할 때, 오크를 공격할 때, 드래곤을 공격할 때의 메서드를 각각 따로 작성하여 코드가 기하급수적으로 길어지고 새로운 몬스터 추가가 매우 어려웠습니다.

**🟢 해결 방법 (추상화와 다형성 적용):** 모든 몬스터 클래스가 상속받는 최상위 `Monster` 추상 클래스를 설계하고, 플레이어의 공격 메서드 파라미터를 개별 몬스터 타입이 아닌 `Monster target`으로 통일하는 **업캐스팅(Upcasting)**을 적용했습니다. 

그 결과, 수십 개의 공격 메서드를 단 **1개의 공통 메서드로 통합**하였고, 새로운 몬스터를 추가할 때 메인 전투 로직을 단 한 줄도 수정할 필요가 없는 완벽한 **OCP(개방-폐쇄 원칙)** 구조를 달성했습니다.
