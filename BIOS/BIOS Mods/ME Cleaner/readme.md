# Erasing Intel ME via internal flashing with me_cleaner & Intel FPT (MSI H81M-P33)

## Requirements

- Python
- me_cleaner v1.2 - [corna/me_cleaner](https://github.com/corna/me_cleaner/releases)
- Intel ME System Tools - [mostav02/Remove_IntelME_FPT](https://github.com/mostav02/Remove_IntelME_FPT/tree/master/Intel_ME_System_Tools)

## Instructions

1. Make a full flash dump 

```PowerShell
.\FPTW64.exe -D FullDump.bin
```

2. Erase me_cleaner with `-s` on a full flash memory dump `FullDump.bin`

```PowerShell
python me_cleaner.py -s -O Modifiled_FullDump.bin FullDump.bin
```

3. Flashing full rom back with FPT

```PowerShell
.\FPTW64.exe -F Modifiled_FullDump.bin
```

4. Dump Flash Descriptor image

```PowerShell
.\FPTW64.exe -DESC -D myFD.bin
```

5. Flashing Flash Descriptor imageT

```PowerShell
.\FPTW64.exe -DESC -F myFD.bin
```


> Make sure to check ME version from the start. For example, `MSI H81M-P33` comes with ME version `9.0`.
> So you'll need to download `Intel ME System Tools v9.1 r7` [according to this](https://github.com/mostav02/Remove_IntelME_FPT/tree/master/Intel_ME_System_Tools#intel-me-system-tools-collection).

To check ME version, you can use either [HWiNFO64](https://www.hwinfo.com/download/) or [ME Analyzer](https://github.com/platomav/MEAnalyzer).

![img](https://i.imgur.com/n9prhyS.png)

## Results

```PowerShell
.\MEInfoWin64.exe -verbose
```

![img](https://i.imgur.com/WUIPPb1.png)