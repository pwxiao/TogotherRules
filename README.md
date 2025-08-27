# TogotherRules

> 基于 KazumiRules 的规则同步仓库，自动同步最新的动漫规则文件


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