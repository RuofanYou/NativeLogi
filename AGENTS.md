# NativeLogi 工作约定

- 默认用简体中文沟通。
- 绝对不要执行 `rm` 删除文件；需要清理时只能移动到废纸篓。
- 这是基于 OpenLogi 的正式二开项目，核心目标是替代臃肿的 Logi Options+，优先支持 Logitech 鼠标在 macOS 上的原生控制。
- 保持 KISS、SSOT、DRY、SOLID：先复用 OpenLogi 既有结构，不为单个功能引入过度抽象。
- 改动要可独立验收、可独立回滚；不要把品牌重命名、权限修复、设备协议改动、UI 调整混成一个不可拆的提交。
- 公开发行时避免使用 Logitech 官方 logo、图标和产品图；可以在 README 中明确写兼容 Logitech / Logi Options+，并声明非官方项目。
