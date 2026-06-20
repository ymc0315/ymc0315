# 안녕하세요, RTL 설계자 윤민철입니다 👋

> **RTL → Verification → Synthesis → Timing Closure**
> 5-stage RISC-V 파이프라인을 3·4-stage로 직접 재설계하고, SAED32 공정으로 합성·타이밍 클로징까지 닫아 본 디지털 설계자입니다.
> 정답 파형 없이 클럭 단위로 신호를 통제하며 문제를 끝까지 푸는 방식으로 일합니다.

🎓 Sangmyung University · System Semiconductor Engineering
📫 ymc0315@naver.com

---

## 🛠 Skills

**Design**
`Verilog` · RV32I 파이프라인 마이크로아키텍처 · Hazard 제어(Forward·Stall·Flush) · FSM · Datapath · 통신 IP 설계

**Verification**
`VCS` · `Verdi` · Python 참조값 비교 검증 · ISA / C-test suite 기능 검증 · `ModelSim` · `iverilog` · `GTKWave`

**Synthesis & Tools**
`Design Compiler` · `SAED32` 합성 · SDC 제약 작성 · Timing/Area 분석 · `Formality` 논리 등가성 검증 · `Quartus` · `SignalTap`(FPGA)

---

## 📂 Projects

### 1. RV32I 파이프라인 CPU — 한 설계를 4가지 아키텍처로 ⭐
> `Verilog` `VCS` `Verdi`

단일 5-stage 구현에서 멈추지 않고, 데이터 의존성과 제어 해저드를 분석해 동일 ISA를 **1·5·4·3-stage 네 가지 구조로 재설계**했습니다.

- **Forwarding / Load-use Stall / Branch Flush** 해저드 유닛 직접 설계
- ISA testbench + C-test suite (dhrystone·strcmp·vecadd·fib·cachetest) **전부 PASS**
- Dhrystone 성능 측정: 5-stage 1035 → 4-stage 1052 → 3-stage 1160
- 정답 파형 없는 환경에서 클럭 단위 신호 추적으로 디버깅

🔗 **[riscv-rv32i-cpu →](https://github.com/ymc0315/riscv-rv32i-cpu)**

### 2. 19-tap FIR 필터 ASIC Front-end 합성
> `Design Compiler` `SAED32` `SDC`

RTL을 직접 작성한 SDC 제약으로 합성하고, timing·area 리포트를 읽어 **slack +0.02ns로 타이밍 클로징**.

- Folded Symmetric FIR 구조 (대칭 계수 폴딩으로 곱셈기 수 절감)
- 직접 작성한 SDC 제약(`top.con`)으로 합성 — create_clock·set_input/output_delay·set_clock_groups
- Python 참조값과 Verilog 출력을 3,000 샘플 비교하여 정합성 확인
- Setup Slack +0.02ns / Clock 1.8ns / Total Area 5,109.52 µm²

🔗 **[fir-filter-asic →](https://github.com/ymc0315/fir-filter-asic)**

### 3. 디지털 통신 IP 설계 (FPGA)
> `Verilog` `Quartus` `SignalTap`

SPI Master/Slave + ADC, UART TX를 RTL로 직접 구현하고 실제 FPGA 보드와 SignalTap으로 검증.

- Baud-rate divider · edge detection · FSM 직접 설계
- Altera FPGA 보드 + Pmod ADC로 실시간 동작 확인
- Tera Term으로 UART 프로토콜 동작 검증

🔗 **[fpga-comm-ip →](https://github.com/ymc0315/fpga-comm-ip)**

---

## 🎯 Direction

단기적으로는 RV32I·ASIC 경험을 바탕으로 RTL을 분석하고 병목을 찾아 최적화하는 **즉시 기여 가능한 설계자**가 되는 것이 목표입니다. 이를 위해 SystemVerilog와 UVM을 독학하며 검증 자동화 역량을 넓히고 있습니다.
