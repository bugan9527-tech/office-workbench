# 个人办公工作台（在线版）

- `index.html` —— 工作台本体（单文件、无外部依赖、离线可用）。
- 数据表文件 `data/workspace.json` **不放在本仓库**，放在私有仓库 `office-workbench-data` 里，页面通过 GitHub Contents API 读写它。

## 使用步骤

1. 把本地的 `index.html` 上传到本仓库根目录（Add file → Upload files）。
2. 仓库 Settings → Pages → Source 选 `Deploy from a branch`，分支 `main`、目录 `/ (root)` → Save。
   一两分钟后在线地址：`https://bugan9527-tech.github.io/office-workbench/`
3. 生成访问数据用的细粒度 Token：Settings → Developer settings → Fine-grained tokens
   - Repository access：Only select repositories → `office-workbench-data`
   - Permissions → Repository permissions → Contents: Read and write
4. 打开在线页面 → 「数据 → 在线数据表」→ 类型选「GitHub 仓库文件」，填：
   - 仓库：`bugan9527-tech/office-workbench-data`
   - 数据文件路径：`data/workspace.json`
   - 分支：`main`
   - 密钥：第 3 步生成的 Token
   - 保存配置 → 测试连接 → 双向同步（合并两边）→ 打开「改完自动推送 + 打开时自动拉取」
5. 手机上打开同一个网址，重复第 4 步的填写，两端就是同一份数据。

> Token 只保存在各自浏览器的本地存储里，不会写进 HTML 文件。
> 数据放在私有仓库，公开页面看不到你的待办内容。

## 更新页面

本地 `个人办公工作台.html` 有改动时，把新的 `index.html` 重新上传覆盖（Add file → Upload files → 同名文件自动覆盖 → Commit changes），刷新网页即可生效。
