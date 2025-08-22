# TogotherRules

> 基于 KazumiRules 的规则同步仓库，自动同步最新的动漫规则文件

## 🚀 功能特性

- **自动同步**: 每日自动从 [KazumiRules](https://github.com/Predidit/KazumiRules) 同步最新规则
- **智能更新**: 基于版本号和时间戳的智能更新机制
- **多种策略**: 支持完全同步、智能同步、增量同步、选择性同步
- **手动触发**: 支持 GitHub Actions 手动触发同步
- **自动维护**: 自动更新 `index.json` 索引文件

## 📋 同步策略

### 1. 智能同步 (Smart) - 默认
- 比较规则版本号和更新时间
- 只更新有变化的规则文件
- 推荐用于日常自动同步

### 2. 完全同步 (Full)  
- 下载并覆盖所有规则文件
- 确保与源仓库完全一致
- 适用于初始化或重置

### 3. 增量同步 (Incremental)
- 只添加新规则，不覆盖现有规则
- 保留本地修改
- 适用于有自定义规则的场景

### 4. 选择性同步 (Selective)
- 根据配置列表同步指定规则
- 可在 `.github/sync-config.json` 中配置
- 适用于只需要部分规则的场景

## 🔧 使用方法

### 自动同步
系统会在每天凌晨 2 点 (UTC) 自动运行同步任务。

### 手动同步
1. 进入 GitHub 仓库的 Actions 页面
2. 选择 "同步 KazumiRules 规则" 工作流
3. 点击 "Run workflow"
4. 选择同步策略和其他选项
5. 点击 "Run workflow" 开始执行

### 配置选项
- **同步策略**: 选择 `full`、`smart`、`incremental` 或 `selective`
- **选择性规则**: 当策略为 `selective` 时，输入要同步的规则名称（逗号分隔）
- **强制更新**: 忽略版本比较，强制更新所有规则

## 📁 文件结构

```
TogotherRules/
├── .github/
│   ├── workflows/
│   │   ├── update.yml              # 原有的 index.json 更新工作流
│   │   └── sync-kazumi-rules.yml   # 新的 KazumiRules 同步工作流
│   └── sync-config.json            # 同步配置文件
├── rules/                          # 规则文件目录
│   ├── AGE.json
│   ├── libvio.json
│   └── ...
├── index.json                      # 规则索引文件（自动生成）
└── README.md
```

## 📊 同步状态

工作流执行后会显示详细的同步统计信息：
- 总规则数量
- 下载的规则数量  
- 更新的规则数量
- 新增的规则数量
- 跳过的规则数量
- 失败的规则数量

## ⚙️ 高级配置

编辑 `.github/sync-config.json` 文件可以自定义：
- 源仓库信息
- 同步设置
- 选择性规则列表
- 定时任务配置

## 🔄 工作流程

1. **获取源数据**: 从 KazumiRules 仓库获取 `index.json`
2. **版本比较**: 与本地规则进行版本和时间戳比较  
3. **下载规则**: 并发下载需要更新的规则文件
4. **保存文件**: 将规则文件保存到 `rules/` 目录
5. **更新索引**: 自动更新本地 `index.json` 文件
6. **提交变更**: 自动提交并推送变更到仓库

## 🚨 注意事项

- 同步过程中会自动备份现有规则文件
- 失败的下载会自动重试 3 次
- 支持最大 5 个并发下载以提高效率
- 所有操作都有详细的日志记录

togother视频源规则仓库，支持自动化规则同步和索引生成

## 项目结构

```
TogotherRules/
├── rules/              # 规则文件目录
│   ├── xxx.json     # 其他规则
├── index.json         # 规则索引文件（自动生成）
```

## 规则文件格式

每个规则文件都是一个JSON格式的配置文件，包含以下主要字段：

```json
{
    "name": "",
    "displayName": "",
    "version": "",
    "author": "",
    "baseURL": "",
    "searchURL": "",
    "searchList": "",
    "searchName": "",
    "searchResult": "",
    "chapterRoads": "",
    "chapterResult": "",
    "referer": ""
}
```
 
> 兼容kazumi的规则  

## 开发

```bash
# 克隆仓库
git clone https://github.com/pwxiao/TogotherRules.git

# 进入目录
cd TogotherRules

# 同步云端代码
git pull origin main

```

## 贡献

欢迎提交新的规则文件或改进现有规则！