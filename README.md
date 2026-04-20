# Five-Stage RISC-V CPU RTL

本仓库保留五级流水线 CPU 的 RTL 和一个最小系统级仿真入口，便于查看、综合前检查和基础 ISA 回归。

## Contents

- `rtl/`: CPU、cache、debug、peripheral 等 RTL。
- `tb/tb_panda_risc_v/`: 系统级 ISA 仿真入口。
- `tb/tb_panda_risc_v/inst_test/`: RV32UI 测试镜像，仿真时作为指令存储器初始化内容。
- `VALIDATION.md`: 当前基础验证记录。

## Pipeline

当前 CPU 按 `IF / ID / EX / MEM / WB` 五级组织，主要边界如下：

- `rtl/ifu/panda_risc_v_if_id_pipe.v`
- `rtl/decoder_dispatcher/panda_risc_v_id_ex_pipe.v`
- `rtl/exu/panda_risc_v_ex_mem_pipe.v`
- `rtl/exu/panda_risc_v_wb_pipe.v`

CPU 顶层入口为 `rtl/panda_risc_v.v`。

## Quick Check

```sh
cd tb/tb_panda_risc_v
python3 test_isa_vcs.py --list-only --max-tests 3
```

## VCS Regression

```sh
cd tb/tb_panda_risc_v
python3 test_isa_vcs.py --pattern 'rv32ui-p-*.txt' --build-dir /tmp/competition_vcs_rv32ui
```

当前记录的 RV32UI 基线为 `39 passed, 0 failed`。
