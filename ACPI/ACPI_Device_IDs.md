# ACPI Device IDs

Plug and Play ID | 설명
-----------------|------------
`PNP0C08` | **ACPI**. ACPI 에서 장치로 정의되지 않은 ID. 이 아이디는 OSPM에서 ACPI 고정 레지스터가 차지한 하드웨어 리소스와 AML 코드가 사용하는 연산 영역에 사용됨.
`PNP0A05` | **Generic Container Device**.  ACPI 리소스 정보에 의해 완전히 제어되어 장치나 버스별 드라이버 지원이 필요 없는 장치. Child에 사용할 리소스를 생성하지 않는 컨테이너에만 사용해야 하고,'_CRS' 개체가 할당되었을시 그 컨테이너 안에서만 사용이 되어야함. 안그러면 오류가 발생.
`PNP0A06`| **Generic Container Device**. PNP0A05와 같음.
`PNP0C09`| **Embedded Controller Device**. Embedded Controller Device. I/O 장치들 (마우스,키보드 터치패드등..), LED, 배터리, 블루투스 연결, Watchdog Timer, Wake-on-Lan 등이 Embedded Controller에 제어가 된다.
`PNP0C0A` | **Control Method Battery**. 배터리 설정
`PNP0C0B` | **Fan**. D0 상태일시, 시스템팬 제어
`PNP0C0C` | **Power Button Device**. 전원버튼.
`PNP0C0D`| **Lid Device**. 노트북의 덮개 상태 제어.
`PNP0C0E`| **Sleep Button Device**. Sleep 버튼, 전원 버튼 옆에 따로 Sleep 버튼이 있을경우 이로 인하여 Sleep 기능이 제대로 작동을 하지 않을 경우가 있다.
`PNP0C0F`| **PCI Interrupt Link Device**. 
`PNP0C80`| **Memory Device.** 메모리 하위 시스템
`ACPI0001`| **SMBus 1.0 Host Controller.** An SMBus host controller (SMB-HC) compatible with the embedded controller-based SMB-HC interface (see Section 12.9), and implementing the SMBus 1.0 Specification.
`ACPI0002`|Smart Battery Subsystem. The Smart battery Subsystem specified in Section 10, “Power Source Devices.”
`ACPI0003`|**Power Source Device.** The Power Source device specified in Section 10, “Power Source Devices.” This can represent either an AC Adapter (on mobile platforms) or a fixed Power Supply.
`ACPI0004`| **Module Device**. Bus Node 역할을 하는 컨테이너 개체._CRS, _PRS 및 _SRS Method 가 없다면 일반 컨테이너 장치(PNP0A05 또는 PNP0A06)와 동일하게 동작. _CRS Method 가 포함 되어 있는 경우, 하위 장치 (Child devices)에서 사용 가능한 리소스는 보통 _CRS에 포함된것만 사용이 가능하다._CRS Method를 지원하는 경우, _PRS 및 _SRS Method를 지원할 수 있음.
`ACPI0005`| **SMBus 2.0 Host Controller**. An SMBus host controller (SMB-HC compatible with the embedded controller-based SMB-HC interface (see Section 12.9), and implementing the SMBus 2.0 Specification.
`ACPI0006`|**GPE Block Device**. This device allows a system designer to describe GPE blocks beyond the two that are described in the FADT.
`ACPI0007`|**Processor Device**. This device provides an alternative to declaring processors using the processor ASL statement. See Section 8.4 for more details.
`ACPI0008`|Ambient Light Sensor Device. This device is an ambient light sensor. See Section 9.3.
`ACPI0009`| **I/OxAPIC Device**. This device is an I/O unit that complies with both the APIC and SAPIC interrupt models.
`ACPI000A`|**I/O APIC Device**. This device is an I/O unit that complies with the APIC interrupt model.
`ACPI000B`|**I/O SAPIC Device**. This device is an I/O unit that complies with the SAPIC interrupt model.
`ACPI000C`|**Processor Aggregator Device**. This device provides a control point for all processors in the platform. See Section 8.5.
`ACPI000D`|**Power Meter Device**. This device is a power meter. See Section 10.4.
`ACPI000E`|**Time and Alarm Device**. This device is a control method-based real-time clock and wake alarm. See Section 9.17.
`ACPI000F`|**User Presence Detection Device**. This device senses user presence (proximity). See Section 9.15)
`ACPI0010`|**Processor container device**. Used to declare hierarchical processor topologies (see Section 8.4.2, and Section 8.4.2.1).
`ACPI0011`|**Generic Buttons Device**. This device reports button events corresponding to Human Interface Device (HID) control descriptors (see Section 9.18).
`ACPI0012`|**NVDIMM Root Device.** This device contains the NVDIMM devices. See Section 9.19 and Table 5.126.
`ACPI0013`|**Generic Event Device**. This device maps Interrupt-signaled events. See Section 5.6.9.
`ACPI0014`|**Wireless Power Calibration Device**. This device uses user presence and notification.
`ACPI0015`| **USB4 host interface device**. See Links to ACPI-Related Documents under the heading “USB4 Host Interface Specification”
`ACPI0016`| **Compute Express Link Host Bridge**. 
`ACPI0017`| **Compute Express Link Root Object**. This device represents the root of a CXL capable device hierarchy. It shall be present whenever the platform allows OSPM to dynamically assign CXL endpoints to a platform address space.
`ACPI0018` | **Audio Composition Device**. This is an ACPI-enumerated device that describes audio component logical connection information within a system.

**출저**: [**ACPI Specs**](https://uefi.org/specifications), **Chpt. 5.6.7**: "Device Class-Specific Objects"
