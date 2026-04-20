# CPU ISA Simulation

本目录保留当前五级流水线 CPU 的系统级 ISA 仿真入口。

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

`competition_5stage_vcs.f` 是当前 VCS filelist。测试镜像来自 `inst_test/`。

这里的测试镜像不是图片文件，而是指令存储器初始化文本。脚本会把每个 `rv32ui-p-*.txt` 复制成 `rv32ui-current.txt`，仿真顶层再读取这个文件执行测试程序。

当前记录的 RV32UI 基线为 `39 passed, 0 failed`。

## RTL Source

当前 CPU RTL 位于 `../../rtl`。
