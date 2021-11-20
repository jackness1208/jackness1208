# lerna 常用操作
假设 项目目录如下:
```bash
|- packages
|  |- pkg01
|  |  `- package.json // pkg.name: @yy/pkg01
|  `- pkg02
|     `- package.json // pkg.name: @yy/pkg02
|- lerna.json
|- package.json
```
## 初始化配置
经过以下初始化后，项目的 `node_modules` 将统一到根目录
1. 修改 lerna.json
```json
{
  "packages": [
    "packages/*"
  ],
  "version": "0.30.0",
  "useWorkspaces": true,
  "npmClient": "yarn"
}

```
2. 修改 package.json
```json
{
  "workspaces": [
    "packages/*"
  ]
}
```
