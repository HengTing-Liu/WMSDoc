# 通用组件对比表：Figma vs 现有代码

## 📊 统计总览

| 来源 | 组件数量 | 状态 |
|------|----------|------|
| Figma 设计 | 48 | - |
| 现有代码 UI Kit | 33 | - |
| 已实现 | 29 | ✅ |
| 缺失 | 19 | ❌ |

---

## ✅ 已实现组件

| Figma 组件 | 现有代码 | 路径 | 状态 |
|-----------|----------|------|------|
| button | ✅ | `@vben/shadcn-ui/button` | ✅ |
| input | ✅ | `@vben/shadcn-ui/input` | ✅ |
| select | ✅ | `@vben/shadcn-ui/select` | ✅ |
| checkbox | ✅ | `@vben/shadcn-ui/checkbox` | ✅ |
| radio-group | ✅ | `@vben/shadcn-ui/radio-group` | ✅ |
| switch | ✅ | `@vben/shadcn-ui/switch` | ✅ |
| textarea | ✅ | `@vben/shadcn-ui/textarea` | ✅ |
| dialog | ✅ | `@vben/modal` | ✅ |
| drawer | ✅ | `@vben/drawer` | ✅ |
| table | ✅ | VxeTable (业务组件) | ✅ |
| form | ✅ | `@vben/form-ui` | ✅ |
| tabs | ✅ | `@vben/tabs-ui` | ✅ |
| pagination | ✅ | `@vben/shadcn-ui/pagination` | ✅ |
| badge | ✅ | `@vben/shadcn-ui/badge` | ✅ |
| avatar | ✅ | `@vben/shadcn-ui/avatar` | ✅ |
| card | ✅ | `@vben/shadcn-ui/card` | ✅ |
| tooltip | ✅ | `@vben/shadcn-ui/tooltip` | ✅ |
| popover | ✅ | `@vben/shadcn-ui/popover` | ✅ |
| dropdown-menu | ✅ | `@vben/shadcn-ui/dropdown-menu` | ✅ |
| separator | ✅ | `@vben/shadcn-ui/separator` | ✅ |
| label | ✅ | `@vben/shadcn-ui/label` | ✅ |
| alert | ✅ | `@vben/alert` | ✅ |
| progress | ✅ | `@vben/shadcn-ui/progress` | ✅ |
| calendar | ✅ | (集成第三方) | ✅ |
| chart | ✅ | (集成ECharts) | ✅ |
| accordion | ✅ | `@vben/shadcn-ui/accordion` | ✅ |
| collapsible | ✅ | `@vben/shadcn-ui/collapsible` | ✅ |
| scroll-area | ✅ | `@vben/shadcn-ui/scroll-area` | ✅ |
| context-menu | ✅ | `@vben/shadcn-ui/context-menu` | ✅ |
| menubar | ✅ | `@vben/shadcn-ui/menubar` | ✅ |

---

## ❌ 缺失组件（需开发）

| Figma 组件 | 类型 | 说明 |
|-----------|------|------|
| alert-dialog | 弹窗 | 带确认/取消的警告弹窗 |
| aspect-ratio | 布局 | 保持元素宽高比 |
| carousel | 轮播 | 图片/内容轮播组件 |
| command | 命令 | 搜索/命令面板（如 Cmd+K） |
| hover-card | 悬浮 | 悬浮预览卡片 |
| input-otp | 输入 | OTP 验证码输入框 |
| navigation-menu | 导航 | 导航菜单组件 |
| resizable | 布局 | 可拖拽调整尺寸 |
| sheet | 侧滑 | 侧边滑出面板 |
| sidebar | 导航 | 侧边导航栏 |
| skeleton | 加载 | 骨架屏加载状态 |
| slider | 输入 | 滑块选择器 |
| sonner | 通知 | 轻量级通知提示（Toast） |
| toggle-group | 输入 | 多选切换组 |
| toggle | 输入 | 单个切换开关 |
| breadcrumb | 导航 | 面包屑导航 |
| skeleton | 加载 | 骨架屏 |
| tree | 数据 | 树形结构展示 |

---

## 🔧 建议优先级

### P0（优先开发）
1. **alert-dialog** - 确认弹窗（业务必备）
2. **tree** - 树形组件（部门/菜单管理）
3. **breadcrumb** - 面包屑（导航必备）
4. **sidebar** - 侧边栏组件（布局必备）

### P1（次优先）
5. **command** - 命令面板（提升体验）
6. **resizable** - 可调整尺寸面板
7. **sheet** - 移动端侧滑面板

### P2（后续优化）
8. carousel、skeleton、sonner 等

---

## 📝 备注

- Vben Admin 框架已封装大量业务组件（VbenModal, VbenForm, VxeTableGrid）
- 建议优先使用框架已有组件，缺失的再补充
- 通用组件开发后需同步到 UI Kit 包中复用

---

*生成时间：2026-03-29*
*来源：TASK-003-FE*