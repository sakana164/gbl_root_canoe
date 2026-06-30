# 小米与一加系统更新安全警告

## 小米

目前小米在 **300** 修复了 GBL 漏洞，但是截止 **306**，XBL 都有启动旧版 abl 来间接加载 EFISP 的能力。

**OTA 方式：**
OTA 模块（release 里）在重启前使用模块刷写一次旧版本 abl，只要 abl 的 anti-rollback 版本不变，理论上可以一直使用。

**⚠️ 严重风险：**
一旦 abl avb 版本变化，该方法会**黑砖**。

**建议：**
- 使用**雹**冻结系统更新
- **非必要 / 主力机器不要更新**
- **非必要 / 主力机器不要更新**
- **非必要 / 主力机器不要更新**
- **非必要 / 主力机器不要更新**
- 如果一定更新，请确保检查 abl 的 anti-rollback 版本，或等待前人测试过

**版本信息：**
- 修复加载 efisp 的 abl 版本：OS3.0.300
- 当前测试最高使用模块成功更新版本：3.0.306


## 一加

目前暂未修复漏洞，但是鉴于之前熔断事件，依旧建议使用雹冻结系统更新。

**⚠️ 警告：**
- **非必要 / 主力机器不要更新**
- **非必要 / 主力机器不要更新**
- **非必要 / 主力机器不要更新**
- **非必要 / 主力机器不要更新**
- 如果一定更新，请确保检查 abl 的 anti-rollback 版本，或等待前人测试过，或确认新版本 GBL 漏洞未修复
- 也可使用模块 OTA

**版本信息：**
- 版本 **761** 修复


## 关于未来熔断 anti-rollback 版本

如果后续真的开始熔断 ABL anti-rollback 版本，建议直接放弃更新，或者只更新 **HLOS**。

### 提取 HLOS 方法

1. 解压 `payload.bin` 到 `images` 目录
2. 使用以下脚本检查 `images` 目录下的文件是否包含 AVB0 头，如果包含则认为是 HLOS，否则认为是非 HLOS

```python
#!/usr/bin/env python3
img_dir = "./images"
import os
for img in os.listdir(img_dir):
    with open(os.path.join(img_dir, img), "rb") as f:
        if b"AVB0" in f.read():
            print(f"{img} is an hlos image")
```

3. 使用 fastboot 刷写这些分区


## 关于模块

模块只有中文，作者懒得搞多语言了，见谅。国外用户可以使用屏幕翻译功能。
