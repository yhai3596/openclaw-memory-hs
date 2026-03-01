# BACKUP.md - 备份与恢复策略

## 备份架构

```
本地Git仓库 → GitHub: https://github.com/yhai3596/openclaw-memory-hs.git
              ↓
          自动/手动备份
```

## 重要文件清单

### 核心文件（必须备份）
- `MEMORY.md` - 长期记忆，核心知识
- `IDENTITY.md` - 助手身份定义
- `USER.md` - 用户信息
- `tasks.md` - 任务追踪
- `SOUL.md` - 安全规则

### 持续更新文件（频繁备份）
- `memory/YYYY-MM-DD.md` - 每日对话记录
- `profile/*.md` - 画像和分析文件

### 历史归档（定期清理）
- 旧的 `memory/` 文件（可归档到 `archive/`）

## 备份频率

- **自动备份**: 每10次会话或每天（待配置cron）
- **手动备份**: 重要会议/决策后立即备份
- **完整备份**: 每周一次完整同步到远程仓库

## 恢复流程

### 场景1: 服务器迁移/恢复
```bash
# 1. 拉取完整仓库
git clone <远程仓库> /root/.openclaw/workspace
cd /root/.openclaw/workspace

# 2. 读取关键文件确认
cat MEMORY.md
cat tasks.md

# 3. 继续工作
```

### 场景2: 部分文件丢失
```bash
# 从git历史恢复
git checkout HEAD -- <文件路径>
```

## 当前状态

- [x] 本地git初始化
- [x] 配置远程仓库 (GitHub)
- [x] 完成首次推送（使用Fine-grained PAT）
- [ ] 设置自动备份 (cron)
- [ ] 测试恢复流程

## 远程仓库

- **平台**: GitHub
- **地址**: https://github.com/yhai3596/openclaw-memory-hs.git
- **分支**: main

## 待确认

- 是否需要加密敏感信息
- 自动备份触发条件（建议：每天/每10次heartbeat）
- 整理频率（建议：每10次heartbeat整理MEMORY.md）
