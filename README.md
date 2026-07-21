# Realm 一键安装管理脚本（DeepSeek-V4-Pro编写+部分手调）

[Realm](https://github.com/zhboner/realm) 的交互式一键安装/管理脚本，提供菜单化操作，简化 Realm 的安装、配置转发规则、服务启停等全部流程。

## 管理面板预览

```
  ╔══════════════════════════════════════════╗
  ║       Realm 一键安装管理脚本 v2.0         ║
  ║    GitHub: github.com/Max-Hu-CN/realm    ║
  ╚══════════════════════════════════════════╝

  版本: 2.6.2  |  规则: 3 条  |  状态: 运行中

  ── 安装管理 ──────────────────────────
   1. 安装 Realm          2. 更新 Realm          3. 卸载 Realm

  ── 转发规则 ──────────────────────────
   4. 添加转发规则        5. 删除转发规则        6. 查看所有规则

  ── 服务控制 ──────────────────────────
   7. 启动 Realm          8. 停止 Realm          9. 重启 Realm
  10. 查看运行状态

  ── 配置管理 ──────────────────────────
  11. 查看配置文件        12. 修改日志级别       13. 开关 UDP 模式

  ── 系统工具 ──────────────────────────
  14. 查看实时日志        15. 开机自启管理       16. 备份与恢复

   0. 退出
```


## 快速使用

```bash
wget -O realm.sh https://github.com/Max-Hu-CN/realm/releases/download/v1.0.0/realm.sh && bash realm.sh
```

安装后可通过 `realm-manager` 快捷命令随时调用。

## 功能一览

### 安装管理
| 选项 | 功能 |
|------|------|
| 1 | 安装 Realm（自动检测架构、下载最新版、创建 systemd 服务） |
| 2 | 更新 Realm |
| 3 | 卸载 Realm（保留备份到 `/var/backups/realm/`） |

### 转发规则
| 选项 | 功能 |
|------|------|
| 4 | 添加转发规则（支持地址格式校验、重复检测） |
| 5 | 删除转发规则（支持单条删除或清空全部） |
| 6 | 查看所有转发规则及当前监听端口 |

### 服务控制
| 选项 | 功能 |
|------|------|
| 7 | 启动 Realm |
| 8 | 停止 Realm |
| 9 | 重启 Realm |
| 10 | 查看运行状态（版本、PID、内存、运行时间、监听端口等） |

### 配置管理
| 选项 | 功能 |
|------|------|
| 11 | 查看当前配置文件 |
| 12 | 修改日志级别（off/error/warn/info/debug/trace） |
| 13 | 开关 UDP 模式 |

### 系统工具
| 选项 | 功能 |
|------|------|
| 14 | 查看实时日志 |
| 15 | 管理开机自启 |
| 16 | 备份与恢复（备份配置、列表查看、恢复、删除） |

## 文件路径

| 文件 | 路径 |
|------|------|
| 主程序 | `/opt/realm/realm` |
| 配置文件 | `/opt/realm/config.toml` |
| 转发规则 | `/opt/realm/endpoints.dat` |
| 设置文件 | `/opt/realm/settings.conf` |
| 日志文件 | `/opt/realm/realm.log` |
| 备份目录 | `/opt/realm/backups/` |
| systemd 服务 | `/etc/systemd/system/realm.service` |
| 快捷命令 | `/usr/local/bin/realm-manager` |

## 环境要求

- Linux 系统（x86_64、aarch64、armv7）
- root 权限
- curl、tar、systemctl

## 注意事项

- 卸载时需输入大写 `YES` 确认
- 添加转发规则后会自动重启 Realm 使规则生效
- 无转发规则时 Realm 无法启动（新版本Realm的设定）
