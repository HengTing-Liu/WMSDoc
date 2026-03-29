# WMS 后端接口规范

**调研时间**: 2026-03-29  
**调研人**: BE  
**任务ID**: TASK-002-BE-1

---

## 统一返回格式 (R.java)

```json
{
  "code": 0,        // 0=成功, 1=失败
  "msg": "success", // 消息
  "data": {...}     // 数据
}
```

## 常用方法

| 方法 | 说明 |
|------|------|
| R.ok() | 成功无数据 |
| R.ok(data) | 成功带数据 |

---

## 备注

详细规范需进一步补充完整。

## 角色管理接口 (2026-03-29 更新)

**基础路径**: `/api/system/role`

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | /api/system/role/list | 角色列表 |
| GET | /api/system/role/{id} | 角色详情 |
| POST | /api/system/role | 新增角色 |

**注意**: 旧文档路径 `/api/role/list` 已废弃，请使用 `/api/system/role/list`