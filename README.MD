# Tiny4412 U-Boot

用于 FriendlyARM Tiny4412 开发板、对应 SDK1506 的 U-Boot 源码，基于 **U-Boot 2010.12**，面向 Samsung Exynos4412 / ARM 平台。

配套内核：[Tiny4412 Linux Kernel](https://github.com/Chris-Geeky/tiny4412-linux-kernel)。

## 获取源码

```bash
git clone https://github.com/Chris-Geeky/tiny4412-uboot.git
cd tiny4412-uboot/uboot_tiny4412-sdk1506
```

默认分支为 `master`，U-Boot 源码位于 `uboot_tiny4412-sdk1506/` 子目录。

## 目录说明

| 路径 | 内容 |
| --- | --- |
| [uboot_tiny4412-sdk1506/](uboot_tiny4412-sdk1506/) | U-Boot 源码与构建入口 |
| [board/samsung/tiny4412/](uboot_tiny4412-sdk1506/board/samsung/tiny4412/) | Tiny4412 板级初始化代码 |
| [include/configs/tiny4412.h](uboot_tiny4412-sdk1506/include/configs/tiny4412.h) | Tiny4412 板级配置 |
| [sd_fuse/](uboot_tiny4412-sdk1506/sd_fuse/) | SD 卡引导镜像工具、脚本和相关文件 |
| [doc/](uboot_tiny4412-sdk1506/doc/) | U-Boot 文档 |

## 编译入口

使用与 SDK1506 匹配的 Linux 编译环境及 ARM 交叉编译工具链。在 `uboot_tiny4412-sdk1506/` 目录下执行：

```bash
make tiny4412_config
make CROSS_COMPILE=arm-linux- -j4
```

请先将匹配的工具链加入 `PATH`，或将 `arm-linux-` 替换为实际工具链前缀。构建目标包含 `u-boot.bin`；环境要求及更多选项见原始 [U-Boot README](uboot_tiny4412-sdk1506/README)。

## 已有修改

[sd_fusing.sh](uboot_tiny4412-sdk1506/sd_fuse/tiny4412/sd_fusing.sh) 中的 SD 卡容量上限检查已注释，保留介质存在性检查。另一个脚本 `fast_fuse.sh` 仍包含容量上限检查。

烧写脚本会直接写入块设备，使用前请确认目标 SD 卡设备并备份其中的数据。

## 问题与贡献

欢迎通过 [GitHub Issues](https://github.com/Chris-Geeky/tiny4412-uboot/issues) 反馈问题，或提交 Pull Request。请附上开发板版本、工具链版本，以及相关编译或串口日志。

## 许可与原始文档

许可信息见仓库根目录的 [LICENSE](LICENSE)、U-Boot 源码目录的 [COPYING](uboot_tiny4412-sdk1506/COPYING)、[COPYING.txt](uboot_tiny4412-sdk1506/COPYING.txt) 及各源码文件中的声明。
