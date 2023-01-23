title: 批量更新 OpenWRT 软件包
date: '2022-12-16 18:38:11'
updated: '2022-12-16 20:01:51'
tags: [openwrt, iStoreOS]
---
## 分开更新

```
# 仅更新LuCI相关软件包
opkg list-upgradable | grep luci- | cut -f 1 -d ' ' | xargs opkg upgrade
# 更新全部可更新软件包，包含OpenWRT内核等
opkg list-upgradable | cut -f 1 -d ' ' | xargs opkg upgrade
```

## 批量更新

```
opkg list-upgradable | grep luci- | cut -f 1 -d ' ' | xargs opkg upgrade
opkg list-upgradable | cut -f 1 -d ' ' | xargs opkg upgrade
```

