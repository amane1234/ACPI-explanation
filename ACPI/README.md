# ACPI 기초

### ACPI란 무엇인가?
ACPI는 고급 구성 및 전원 인터페이스(Advanced Configuration & Power Interface)의 약자입니다. 인텔, 마이크로소프트 등 여러 제조업체가 만든 아키텍처 독립적인 전원 관리 및 구성 표준입니다.

모든 컴퓨터 메인보드는 UEFI (혹은 BIOS)에 저장된 ACPI 테이블셋과 함께 제공됩니다. ACPI 테이블의 갯수와 내용은 사용되는 메인보드와 칩셋에 따라 다르며, 서로 다른 UEFI 버전 간에도 차이가 있을 수 있습니다. ACPI는 실제로 사용된 하드웨어에 대한 기본 정보를 운영 체제에 제공하기 위한 텍스트 테이블(이진 코드로 변환된 형태)의 집합입니다..

![acpi-overview](https://user-images.githubusercontent.com/76865553/187380087-3446fc20-75c2-4490-95f9-bfc8043ffb09.png)

ACPI 하위 시스템에서는 플랫폼의 주변 장치와 시스템 하드웨어 기능이 "부팅" 시 로드되는 DSDT (차별화된 시스템 설명 테이블)와 "실행중" 동적으로 로드되는 SSDT (보조 시스템 설명 테이블)에 설명됩니다. ACPI 시스템은 기계의 하드웨어 정보를 .aml 형식으로 설명하며, 자체적인 드라이버 기능은 없습니다.

ACPI은 시스템의 POST 이후에 시작됩니다. 실행 과정은 다음과 같이 진행됩니다(시간 순서대로, 위에서 부터 아래로):
![ACPI_Init](https://github.com/5T33Z0/OC-Little-Translated/assets/76865553/7769db1f-a046-4990-9546-c001fe9f4654)


ACPI 서브시스템 자체는 "데이터 테이블"과 "정의 블록"의 두 가지의 구조로 구성됩니다(아래 그림 참조). 이러한 데이터 구조는 펌웨어와 운영 체제 간의 주요 통신 메커니즘입니다. 데이터 테이블은 일차적 데이터를 저장하며 장치 드라이버에 의해 사용됩니다. 정의 블록은 인터프리터에 의해 실행 가능한 바이트 코드로 구성됩니다.

![acpi-structure](https://user-images.githubusercontent.com/76865553/187380905-e325398d-e65a-4db3-85c2-0d2cdb0b2934.png)</br>

SSDT를 사용하여 필요한 정의 블록을 시스템에 주입(injection)하여 상황에 맞게 변경할 수 있습니다. 가상 장치를 추가하거나 장치 이름을 변경하고, 제어 방법을 변경하거나 버퍼를 수정하는 등의 작업을 수행하여 MacOS가 제대로 작동하도록 할 수 있습니다.

###왜 패치된 DSDT보다 SSDT를 많이 선호 하는가?

해킨토시에서 흔히 발생하는 문제 중 하나는 X86 기반 인텔 및 AMD 시스템에서 macOS를 실행할 때 ACPI 기능이 누락되는 것입니다. 예를 들어, 네트워킹이 작동하지 않거나 USB 포트가 작동하지 않으며, CPU 전원 관리가 올바르게 작동하지 않거나, 뚜껑을 닫았을 때 화면이 꺼지지 않고, Sleep 및 Wake 기능이 작동하지 않거나, 밝기 조절이 작동하지 않는 등의 문제가 있습니다.

이러한 문제는 Windows OS를 염두에 두고 작성된 DSDT와, 애플이 자사의 하드웨어에 대해 ACPI 사양을 100% 준수하지 않는 것에서 비롯됩니다. 이러한 문제는 부팅 중에 원본 DSDT를 대체하기 위해 패치된 DSDT를 덤프, 패치 및 주입함으로써 해결할 수 있습니다.

시스템 펌웨어는 실행 시간 동안 ACPI 테이블을 동적으로 업데이트하므로, 패치된 DSDT를 주입하는 것은 가장 좋은 아이디어가 아닐 수 있습니다. 또한, BIOS 업데이트 시 DSDT가 변경될 수 있으므로, 그 위에 이전에 패치된 DSDT를 주입하면 충돌이 발생하고 macOS 기능이 손상될 수 있습니다.

이러한 이유들 때문에, SSDT를 사용한 동적 패치가 패치된 DSDT를 사용하는 것보다 더 선호되고 훨씬 깔끔합니다.

다음 챕터로 가기, [**ASL Basics**](https://github.com/5T33Z0/OC-Little-Translated/blob/main/00_ACPI/ACPI_Basics/ASL_Basics.md).

## CREDITS and RESOURCES
- Original [**ASL Guide**](https://bbs.pcbeta.com/forum.php?mod=viewthread&tid=944566&archive=2&extra=page%3D1&page=1) by suhetao
- [**ACPI Specifications**](https://uefi.org/specifications)
- ASL Tutorial by acpica.org ([**PDF**](https://acpica.org/sites/acpica/files/asl_tutorial_v20190625.pdf)). Good starting point if you want to get into fixing your `DSDT` with `SSDT` hotpatches.
