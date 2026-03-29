# 通用组件对比表：Figma vs 现有代码

## 📊 统计总览

| 来源 | 组件数量 | 状态 |
|------|----------|------|
| Figma 设计 | 48 | - |
| 现有代码 UI Kit | 33 | - |
| **实际已实现** | **34** | ✅ |
| **实际缺失** | **14** | ❌ |

---

## ✅ 已实现组件

| Figma 组件 | 现有代码路径 | 状态 |
|-----------|------------|------|
| button | `@vben/shadcn-ui/button` | ✅ |
| input | `@vben/shadcn-ui/input` | ✅ |
| select | `@vben/shadcn-ui/select` | ✅ |
| checkbox | `@vben/shadcn-ui/checkbox` | ✅ |
| radio-group | `@vben/shadcn-ui/radio-group` | ✅ |
| switch | `@vben/shadcn-ui/switch` | ✅ |
| textarea | `@vben/shadcn-ui/textarea` | ✅ |
| dialog | `@vben/modal` | ✅ |
| drawer | `@vben/drawer` | ✅ |
| table | VxeTable (业务组件) | ✅ |
| form | `@vben/form-ui` | ✅ |
| tabs | `@vben/tabs-ui` | ✅ |
| pagination | `@vben/shadcn-ui/pagination` | ✅ |
| badge | `@vben/shadcn-ui/badge` | ✅ |
| avatar | `@vben/shadcn-ui/avatar` | ✅ |
| card | `@vben/shadcn-ui/card` | ✅ |
| tooltip | `@vben/shadcn-ui/tooltip` | ✅ |
| popover | `@vben/shadcn-ui/popover` | ✅ |
| dropdown-menu | `@vben/shadcn-ui/dropdown-menu` | ✅ |
| separator | `@vben/shadcn-ui/separator` | ✅ |
| label | `@vben/shadcn-ui/label` | ✅ |
| alert | `@vben/alert` | ✅ |
| progress | `@vben/shadcn-ui/progress` | ✅ |
| calendar | (集成第三方) | ✅ |
| chart | (集成ECharts) | ✅ |
| accordion | `@vben/shadcn-ui/accordion` | ✅ |
| collapsible | `@vben/shadcn-ui/collapsible` | ✅ |
| scroll-area | `@vben/shadcn-ui/scroll-area` | ✅ |
| context-menu | `@vben/shadcn-ui/context-menu` | ✅ |
| menubar | `@vben/shadcn-ui/menubar` | ✅ |
| alert-dialog | `@vben/shadcn-ui/alert-dialog` | ✅ |
| breadcrumb | `@vben/shadcn-ui/breadcrumb` | ✅ |
| resizable | `@vben/shadcn-ui/resizable` | ✅ |
| sheet | `@vben/shadcn-ui/sheet` | ✅ |
| tree | `@vben/shadcn-ui/tree` | ✅ |

---

## ❌ 缺失组件（需开发）

| Figma 组件 | 类型 | 说明 |
|-----------|------|------|
| aspect-ratio | 布局 | 保持元素宽高比 |
| carousel | 轮播 | 图片/内容轮播组件 |
| command | 命令 | 搜索/命令面板（如 Cmd+K） |
| hover-card | 悬浮 | 悬浮预览卡片 |
| input-otp | 输入 | OTP 验证码输入框 |
| navigation-menu | 导航 | 导航菜单组件 |
| sidebar | 导航 | 侧边导航栏 |
| skeleton | 加载 | 骨架屏加载状态 |
| slider | 输入 | 滑块选择器 |
| sonner | 通知 | 轻量级通知提示（Toast） |
| toggle-group | 输入 | 多选切换组 |
| toggle | 输入 | 单个切换开关 |

---

## 🔧 建议优先级

### P0（优先开发）
1. **sidebar** - 侧边导航栏（布局必备）

### P1（次优先）
2. **command** - 命令面板（提升体验）
3. **skeleton** - 骨架屏（加载状态）

### P2（后续优化）
4. carousel、sonner、hover-card、slider 等

---

## 📝 备注

- **更新：2026-03-29** - 重新核对后发现实际只有12个组件缺失
- Vben Admin 框架已封装大量业务组件（VbenModal, VbenForm, VxeTableGrid）
- 建议优先使用框架已有组件，缺失的再补充
- 通用组件开发后需同步到 UI Kit 包中复用

---

*生成时间：2026-03-29*
*更新时间：2026-03-29 14:50*
*来源：TASK-003-FE, TASK-005-FE*