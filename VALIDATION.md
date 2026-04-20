# Validation

## Baseline

- Target: RV32 five-stage pipeline RTL.
- Simulation entry: `tb/tb_panda_risc_v/test_isa_vcs.py`.
- Test images: `tb/tb_panda_risc_v/inst_test/rv32ui-p-*.txt`.
- Checked-in image set: RV32UI text images only.
- Recorded result: `39 passed, 0 failed`.

## Command

```sh
cd tb/tb_panda_risc_v
python3 test_isa_vcs.py --pattern 'rv32ui-p-*.txt' --build-dir /tmp/competition_vcs_rv32ui
```

## Notes

- Requires VCS.
- `competition_5stage_vcs.f` is the filelist used by the regression runner.
- The build directory can be placed under `/tmp`.
