# jlink_auto_flash

J-Link SWD 自动烧录工具，当前默认目标为 GD32C103CB。本仓库保留现有烧录脚本、固件和随附的 Windows 运行依赖。

## 使用

Windows 下双击 `flash.bat`，它会调用同目录的 `flash.ps1`。脚本优先使用 `env/JLink.exe`，并持续检测仿真器与目标板；检测到目标板后按现有流程擦除、烧录 Boot 和 App，随后等待更换目标板。

`firmware/` 是默认扫描的固件目录：

- Boot：`dgm_boot_released_*.bin`，写入地址 `0x08016800`。
- App：`dgm_app_released_*.bin`，写入地址 `0x08000000`。

当前提供 Boot 133 和 App 143。现有脚本每类选取第一项，替换固件时每类保留一份。

## 目录

- `flash.bat`：启动入口。
- `flash.ps1`：检测和自动烧录流程。
- `firmware/`：当前烧录固件。
- `env/`：项目现有的 J-Link Commander 和 Windows DLL。
- `temp/`：现有历史固件副本，不参与默认扫描。

`flash.jlink`、`detect.jlink` 和日志由运行过程生成，保留在本机，不提交到仓库。
