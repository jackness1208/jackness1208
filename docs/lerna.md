# lerna 常用操作
假设 项目目录如下:
```bash
|- packages
|  |- pkg01
|  |  `- package.json - pkg.name: @yy/pkg01
|  `- pkg02
|     `- package.json - pkg.name: @yy/pkg02
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
## 常用指令
#### 运行 pkg02 下 npm script prettier
```bash
lerna run prettier --scope @yy/pkg02
```

#### 将 pkg02 作为依赖安装到 pkg01
```bash
lerna add @yy/pkg02 --scope @yy/pkg01
```

#### 将汇总到跟目录下的 node_modules 分别在 packages 子组件下创建软连
```bash
lerna link
```

#### 提交代码配置
配置各个子 组件下的 `package.json` 文件, 新增 `maintainers` 字段，补充体积者信息

```json
{
  "maintainers": [
    {
      "name": "jackness1208",
      "emial": "jackness1208@qq.com"
    }
  ]
}
```

然后就可以通过 `lerna publish` 正常发布了
