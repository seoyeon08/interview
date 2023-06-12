# Computer의 이해

- 컴퓨터는 크게 3가지 계층을 가진다고 이해하면 됩니다.
    - User 계층 : User가 사용하는 환경을 의미합니다.
    - Kernel 계층 : Kernel은 OS의 핵심적인 부분으로 H/W와 S/W간 통신을 담당합니다.
    - H/W 계층 : 물리적인 구성요소를 의미합니다.
- H/W 계층은 실제로 Physical한 부분이고, 나머지 User와 Kernel은 Logical(Virtual)한 부분입니다.
- User와 Kernel 계층은 OS와 Platform으로 이루어져 있다고 할 수 있습니다.
- OS는 단순한 S/W이지만 User 계층에서 Application과 같은 Process가 잘 동작하도록 Support하고 H/W 구성요소를 관리하고 제어하는 역할을 합니다.
- OS를 이해하려면 H/W에 대한 일정 수준의 지식이 필요합니다.
- Computer는 CPU와 주변기기로 이루어지는데, 이때 주변기기는 키보드, 마우스, 모니터와 같은 입출력장치를 의미합나다.
- 이런 입출력 장치와 통신하여 동작하는데 이 과정에서 Interrupt가 발생하고 잠시 Wait이 된 사이 통신을 진행합니다.
- 컴퓨터가 다양한 작업을 동시에 수행할 수 있게 하는 기본 메커니즘 중 하나가 Interrupt입니다. 예를 들어, 키보드의 키를 누르면 키보드 컨트롤러는 CPU에 인터럽트를 보내어 CPU가 현재 작업을 일시 중지하고 키 누름 Event를 처리하도록 합니다.

---

<br>

# Computer적 관점에서 Hello World

- 가장 기초가되는 Hello World를 출력하는 코드는 단순하게 생각하면 통신입니다.
- User 계층에서 print(”hello world”)를 실행하게 되면, Kernel 계층에 미리 API로서 정의된 System Call을 호출합니다. (User to Kernel)
- System Call을 받은 Kernel은 내부적으로 해당 System Call에 적절한 OS Service 또는 Driver에 전달합니다. (Kernel)
- OS Service 또는 Driver는 알맞은 IRQ(Intrrupt Request)를 발생시키고, 그것을 CPU가 감지하여 잠시 Interrupt가 발생한 순간 적절한 요청을 Device에 지시합니다. (Kernel to H/W)
- 요청을 받은 Device는 해당 요청을 처리하고 결과를 다시 Interrupt로 요청을 한 Service 또는 Driver에게 결과를 돌려줍니다. (H/W to Kernel)
- 그 결과를 전달받아 최초에 요청한 User 계층까지 도달합니다. (Kernel to User)
- 이때 요청을 처리하는 동안 결과를 기다리면 Blocking이고, 계속 흐름이 진행되면 Non-Blocking이라고 할 수 있습니다.

---

<br>

### Reference
[널널한 개발자 TV](https://www.youtube.com/@nullnull_not_eq_null/)
