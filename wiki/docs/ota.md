# Xiaomi & OnePlus System Update Security Warning

## Xiaomi

Currently, Xiaomi fixed the GBL vulnerability in version **300**, but as of version **306**, XBL retains the ability to boot an old version of abl to indirectly load EFISP.

**OTA method：**
The OTA module (in release) flashes an old abl version once before reboot. As long as the abl's anti-rollback version remains unchanged, it can theoretically be used continuously.

**⚠️ Critical risk：**
If the abl avb version changes, this method will cause a **hard brick**.

**Recommendation：**
- Use **Hail** to freeze system updates
- **Do NOT update unless necessary / on a primary device**
- **Do NOT update unless necessary / on a primary device**
- **Do NOT update unless necessary / on a primary device**
- **Do NOT update unless necessary / on a primary device**
- If you must update, ensure you check abl's anti-rollback version, or wait for others to have tested it

**Version info：**
- Fixed abl version (loading efisp)：OS3.0.300
- Highest version successfully updated using the module in testing：3.0.306


## OnePlus

The vulnerability is not yet fixed, but given the previous "fuse" incident, it is still recommended to use Hail to freeze system updates.

**⚠️ Warnings：**
- **Do NOT update unless necessary / on a primary device**
- **Do NOT update unless necessary / on a primary device**
- **Do NOT update unless necessary / on a primary device**
- **Do NOT update unless necessary / on a primary device**
- If you must update, ensure you check abl's anti-rollback version, wait for others to have tested it, or confirm that the new version still has the GBL vulnerability
- You can also use the module for OTA

**Version info：**
- version **761** is fixed


## Regarding future fuse of abl anti-rollback versions

If abl anti-rollback versions are really being fused in the future, it is recommended to abandon updates entirely, or only update **HLOS**.

### How to extract HLOS

1. Extract `payload.bin` to the `images` directory
2. Use the following script to check if files in the `images` directory contain the `AVB0` header. If yes, it is considered an HLOS image； otherwise non-HLOS.

```python
#!/usr/bin/env python3
img_dir = "./images"
import os
for img in os.listdir(img_dir):
    with open(os.path.join(img_dir, img), "rb") as f:
        if b"AVB0" in f.read():
            print(f"{img} is an hlos image")
```

3. Flash these partitions using fastboot


## About the module

The module is only in Chinese. The author is too lazy to add multiple languages, sorry. International users can use screen translation features.
