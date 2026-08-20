# @uxndigital/tsconfig

共享的 TypeScript 配置预设，适用于不同的项目类型。

## 安装

```bash
pnpm add -D @uxndigital/tsconfig typescript
```

## 使用

在项目的 `tsconfig.json` 中引用对应的配置：

### Web 应用（React + Vite/Webpack）

```json
{
  "extends": "@uxndigital/tsconfig/web/app.json",
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  },
  "include": ["src"]
}
```

### Web 库（React 组件库）

```json
{
  "extends": "@uxndigital/tsconfig/web/react-lib.json",
  "compilerOptions": {
    "outDir": "dist",
    "rootDir": "src"
  },
  "include": ["src"]
}
```

### Node.js 应用

```json
{
  "extends": "@uxndigital/tsconfig/server/node.json",
  "compilerOptions": {
    "outDir": "dist",
    "rootDir": "src"
  },
  "include": ["src"]
}
```

### Node.js 库

```json
{
  "extends": "@uxndigital/tsconfig/server/lib.json",
  "compilerOptions": {
    "outDir": "dist",
    "rootDir": "src"
  },
  "include": ["src"]
}
```

## 配置说明

### `base.json`

所有配置的基础，包含严格模式和通用编译选项。不建议直接使用。

### `web/app.json`

- 适用于 React 应用（Vite、Webpack、Next.js 等）
- 启用 JSX 支持（`"jsx": "react-jsx"`）
- 启用 `isolatedModules`（适配打包工具）
- DOM 类型支持

### `web/react-lib.json`

- 适用于 React 组件库
- 基于 `web/app.json`
- 启用 `composite` 和 `declaration` 用于 monorepo
- 移除注释以减小产物体积

### `server/node.json`

- 适用于 Node.js 应用
- ESM 模块系统（`"module": "NodeNext"`）
- Node.js 类型支持
- 不启用 `isolatedModules`（使用 tsc 直接编译）

### `server/lib.json`

- 适用于 Node.js 库
- 基于 `server/node.json`
- 启用 `composite` 和 `declaration`
- 移除注释

## 兼容性

- TypeScript: `>=5.0.0 <8.0.0`
- Node.js: `>=18.0.0`

## 更新日志

查看 [changelog.md](./changelog.md)

## 许可证

MIT
