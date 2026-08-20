# Changelog

## [7.0.0] - 2026-08-20

### Added
- 新增 `README.md` 文档
- `.gitignore` 添加更多忽略规则（日志、构建产物、IDE 配置等）

### Changed
- 升级 `typescript` 5.4.5 → 7.0.2（移至 `devDependencies`）
- 升级 `@types/node` 20.12.11 → 26.2.0
- 更新 `peerDependencies` 范围为 `>=5.0.0 <8.0.0`
- `package.json` 添加 `bugs` 字段
- `package.json` 发布标签改为 `v7`
- 重命名 `changlog.md` → `changelog.md`（修正拼写错误）

### Removed
- `base.json`: 移除 `noImplicitAny: false`（遵循 `strict: true`）
- `web/app.json`: 移除 `removeComments`（应用无需移除注释）
- `web/react-lib.json`: 移除 `noEmit: true`（库需要输出文件）

### Fixed
- `base.json`: 修复格式问题（declaration 缩进）
- `base.json`: 添加 `exclude: ["node_modules"]`（避免编译 node_modules）

## [5.0.3] - 2026-XX-XX

### Changed
- 文档和配置优化

## 5.0.2
- 删除 `"allowImportingTsExtensions": true`。在 `module` 为 `node16` 、 `nodenext` 和 `bundler` 时 `rewriteRelativeImportExtensions` 默认为 `true`。`allowImportingTsExtensions` 为 `false`。不应该做限制
- lib 下 `removeComments` 为 `true`
- monorepo 下相互引入需要设置 `"incremental": true`
    > Composite projects may not disable incremental compilation.ts
- node 下默认 tsc 编译，`isolatedModules=false`。react 下默认 vite/webpack 编译，`isolatedModules=true`
- 其他文件单独设置，删除 base 里多余的配置
    - `"lib"`
    - `"moduleResolution": "NodeNext",`
    - `"module": "NodeNext",`
    - `"target": "ES2022",`
- base 里已经设置，删除其他文件重复配置
    - `"skipLibCheck": true`
    - `"strict": true,`
    - `"moduleDetection": "force"`
    - `"declaration": true`
    - `"declarationMap": true`
    - `"esModuleInterop": true`
    - `"noFallthroughCasesInSwitch": true`
    - `"resolveJsonModule": true`
    - `"target": "ES2022"`
    - `"verbatimModuleSyntax": true`
    - `"noUnusedLocals": true`
    - `"noUnusedParameters": true`
