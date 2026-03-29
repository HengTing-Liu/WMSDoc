# WMS 基础设置模块接口文档

## 1. 概述

### 1.1 模块说明
基础设置模块包含系统运行所需的核心配置数据，为其他业务模块提供基础数据支撑。

### 1.2 包含功能
- 用户管理 (User)
- 角色管理 (Role)
- 菜单管理 (Menu)
- 部门管理 (Dept)
- 字典管理 (Dict)
- 岗位管理 (Post)
- 系统配置 (Config)

---

## 2. 接口规范

### 2.1 统一返回格式

#### 成功响应
```json
{
  "code": 0,
  "msg": "success",
  "data": {...}
}
```

#### 失败响应
```json
{
  "code": 1,
  "msg": "错误信息",
  "data": null
}
```

#### 分页响应
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 100,
    "rows": [...]
  }
}
```

### 2.2 公共请求头
```
Content-Type: application/json
Authorization: Bearer {token}
```

### 2.3 权限说明
接口使用 `@RequiresPermissions` 注解控制权限，格式：`模块:资源:操作`
例如：`system:user:list` 表示用户模块的列表权限

---

## 3. 用户管理 (User)

### 3.1 查询用户列表
- **URL**: `GET /api/user/list`
- **权限**: `system:user:list`
- **描述**: 分页查询用户列表

**Request Parameters:**
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| pageNum | int | 否 | 页码，默认1 |
| pageSize | int | 否 | 每页数量，默认10 |
| userName | string | 否 | 用户名 |
| phonenumber | string | 否 | 手机号 |
| status | string | 否 | 状态(0正常/1停用) |
| deptId | long | 否 | 部门ID |

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 50,
    "rows": [
      {
        "userId": 1,
        "deptId": 100,
        "userName": "admin",
        "nickName": "管理员",
        "email": "admin@example.com",
        "phonenumber": "15888888888",
        "sex": "0",
        "avatar": "/profile/avatar.jpg",
        "status": "0",
        "delFlag": "0",
        "loginIp": "127.0.0.1",
        "loginDate": "2026-03-29 10:00:00",
        "createBy": "admin",
        "createTime": "2026-01-01 08:00:00",
        "updateBy": null,
        "updateTime": null,
        "remark": "系统管理员"
      }
    ]
  }
}
```

### 3.2 查询用户详情
- **URL**: `GET /api/user/{userId}`
- **权限**: `system:user:query`
- **描述**: 根据ID查询用户详情

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "userId": 1,
    "deptId": 100,
    "deptName": "研发部",
    "userName": "admin",
    "nickName": "管理员",
    "email": "admin@example.com",
    "phonenumber": "15888888888",
    "sex": "0",
    "avatar": "/profile/avatar.jpg",
    "status": "0",
    "roles": [
      {
        "roleId": 1,
        "roleName": "超级管理员",
        "roleKey": "admin"
      }
    ]
  }
}
```

### 3.3 新增用户
- **URL**: `POST /api/user`
- **权限**: `system:user:add`
- **描述**: 创建新用户

**Request Body:**
```json
{
  "deptId": 100,
  "userName": "newuser",
  "nickName": "新用户",
  "email": "newuser@example.com",
  "phonenumber": "15888888888",
  "sex": "0",
  "status": "0",
  "password": "123456",
  "roleIds": [1, 2],
  "remark": "新用户备注"
}
```

**Response:**
```json
{
  "code": 0,
  "msg": "新增成功",
  "data": null
}
```

### 3.4 修改用户
- **URL**: `PUT /api/user`
- **权限**: `system:user:edit`
- **描述**: 修改用户信息

**Request Body:**
```json
{
  "userId": 1,
  "deptId": 100,
  "nickName": "管理员V2",
  "email": "admin2@example.com",
  "phonenumber": "15888888889",
  "sex": "1",
  "status": "0",
  "roleIds": [1, 3],
  "remark": "更新备注"
}
```

### 3.5 删除用户
- **URL**: `DELETE /api/user/{userIds}`
- **权限**: `system:user:remove`
- **描述**: 删除用户(批量,逗号分隔)

**Response:**
```json
{
  "code": 0,
  "msg": "删除成功",
  "data": null
}
```

### 3.6 重置密码
- **URL**: `PUT /api/user/resetPwd`
- **权限**: `system:user:resetPwd`
- **描述**: 重置用户密码

**Request Body:**
```json
{
  "userId": 1,
  "password": "123456"
}
```

### 3.7 修改状态
- **URL**: `PUT /api/user/changeStatus`
- **权限**: `system:user:edit`
- **描述**: 修改用户状态

**Request Body:**
```json
{
  "userId": 1,
  "status": "0"
}
```

### 3.8 导出用户
- **URL**: `POST /api/user/export`
- **权限**: `system:user:export`
- **描述**: 导出用户Excel

---

## 4. 角色管理 (Role)

### 4.1 查询角色列表
- **URL**: `GET /api/role/list`
- **权限**: `system:role:list`
- **描述**: 分页查询角色列表

**Request Parameters:**
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| pageNum | int | 否 | 页码，默认1 |
| pageSize | int | 否 | 每页数量，默认10 |
| roleName | string | 否 | 角色名称 |
| roleKey | string | 否 | 角色标识 |
| status | string | 否 | 状态 |

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 10,
    "rows": [
      {
        "roleId": 1,
        "roleName": "超级管理员",
        "roleKey": "admin",
        "roleSort": 1,
        "status": "0",
        "createTime": "2026-01-01 08:00:00",
        "remark": "系统最高权限"
      }
    ]
  }
}
```

### 4.2 查询角色详情
- **URL**: `GET /api/role/{roleId}`
- **权限**: `system:role:query`
- **描述**: 根据ID查询角色详情(含菜单权限)

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "roleId": 1,
    "roleName": "超级管理员",
    "roleKey": "admin",
    "roleSort": 1,
    "status": "0",
    "menuIds": [1, 2, 3, 100, 101],
    "remark": "系统最高权限"
  }
}
```

### 4.3 新增角色
- **URL**: `POST /api/role`
- **权限**: `system:role:add`
- **描述**: 创建新角色

**Request Body:**
```json
{
  "roleName": "业务管理员",
  "roleKey": "business",
  "roleSort": 2,
  "status": "0",
  "menuIds": [1, 2, 10, 11],
  "remark": "业务管理角色"
}
```

### 4.4 修改角色
- **URL**: `PUT /api/role`
- **权限**: `system:role:edit`
- **描述**: 修改角色信息

**Request Body:**
```json
{
  "roleId": 2,
  "roleName": "业务管理员V2",
  "roleKey": "business",
  "roleSort": 2,
  "status": "0",
  "menuIds": [1, 2, 10, 11, 12],
  "remark": "更新备注"
}
```

### 4.5 删除角色
- **URL**: `DELETE /api/role/{roleIds}`
- **权限**: `system:role:remove`
- **描述**: 删除角色

---

## 5. 菜单管理 (Menu)

### 5.1 查询菜单列表
- **URL**: `GET /api/menu/list`
- **权限**: `system:menu:list`
- **描述**: 查询所有菜单(树形结构)

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {
      "menuId": 1,
      "menuName": "系统管理",
      "parentId": 0,
      "orderNum": 1,
      "path": "/system",
      "component": null,
      "menuType": "M",
      "visible": "0",
      "status": "0",
      "perms": null,
      "icon": "system",
      "children": [
        {
          "menuId": 100,
          "menuName": "用户管理",
          "parentId": 1,
          "orderNum": 1,
          "path": "user",
          "component": "system/user/index",
          "menuType": "C",
          "visible": "0",
          "status": "0",
          "perms": "system:user:list"
        }
      ]
    }
  ]
}
```

### 5.2 查询菜单详情
- **URL**: `GET /api/menu/{menuId}`
- **权限**: `system:menu:query`
- **描述**: 根据ID查询菜单详情

### 5.3 新增菜单
- **URL**: `POST /api/menu`
- **权限**: `system:menu:add`
- **描述**: 创建新菜单

**Request Body:**
```json
{
  "menuName": "角色管理",
  "parentId": 1,
  "orderNum": 2,
  "path": "role",
  "component": "system/role/index",
  "menuType": "C",
  "visible": "0",
  "status": "0",
  "perms": "system:role:list",
  "icon": "peoples"
}
```

**菜单类型说明:**
- `M`: 目录
- `C`: 菜单
- `F`: 按钮

### 5.4 修改菜单
- **URL**: `PUT /api/menu`
- **权限**: `system:menu:edit`
- **描述**: 修改菜单信息

### 5.5 删除菜单
- **URL**: `DELETE /api/menu/{menuId}`
- **权限**: `system:menu:remove`
- **描述**: 删除菜单

---

## 6. 部门管理 (Dept)

### 6.1 查询部门列表
- **URL**: `GET /api/dept/list`
- **权限**: `system:dept:list`
- **描述**: 查询所有部门(树形结构)

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {
      "deptId": 100,
      "parentId": 0,
      "deptName": "总公司",
      "orderNum": 1,
      "leader": "张三",
      "phone": "15888888888",
      "email": "zhangsan@example.com",
      "status": "0",
      "children": [
        {
          "deptId": 101,
          "parentId": 100,
          "deptName": "研发部",
          "orderNum": 1,
          "leader": "李四",
          "status": "0"
        }
      ]
    }
  ]
}
```

### 6.2 查询部门详情
- **URL**: `GET /api/dept/{deptId}`
- **权限**: `system:dept:query`
- **描述**: 根据ID查询部门详情

### 6.3 新增部门
- **URL**: `POST /api/dept`
- **权限**: `system:dept:add`
- **描述**: 创建新部门

**Request Body:**
```json
{
  "parentId": 100,
  "deptName": "销售部",
  "orderNum": 3,
  "leader": "王五",
  "phone": "15888888889",
  "email": "wangwu@example.com",
  "status": "0"
}
```

### 6.4 修改部门
- **URL**: `PUT /api/dept`
- **权限**: `system:dept:edit`
- **描述**: 修改部门信息

### 6.5 删除部门
- **URL**: `DELETE /api/dept/{deptId}`
- **权限**: `system:dept:remove`
- **描述**: 删除部门

---

## 7. 字典管理 (Dict)

### 7.1 查询字典类型列表
- **URL**: `GET /api/dict/type/list`
- **权限**: `system:dict:list`
- **描述**: 分页查询字典类型

**Request Parameters:**
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| dictName | string | 否 | 字典名称 |
| dictType | string | 否 | 字典类型 |
| status | string | 否 | 状态 |

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 20,
    "rows": [
      {
        "dictId": 1,
        "dictName": "用户性别",
        "dictType": "sys_user_sex",
        "status": "0",
        "createTime": "2026-01-01 08:00:00"
      }
    ]
  }
}
```

### 7.2 查询字典数据列表
- **URL**: `GET /api/dict/data/list`
- **权限**: `system:dict:list`
- **描述**: 分页查询字典数据

**Request Parameters:**
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| dictType | string | 否 | 字典类型 |
| dictLabel | string | 否 | 字典标签 |
| status | string | 否 | 状态 |

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 5,
    "rows": [
      {
        "dictCode": 1,
        "dictLabel": "男",
        "dictValue": "0",
        "dictType": "sys_user_sex",
        "cssClass": null,
        "listClass": "default",
        "isDefault": "Y",
        "status": "0",
        "orderNum": 1
      },
      {
        "dictCode": 2,
        "dictLabel": "女",
        "dictValue": "1",
        "dictType": "sys_user_sex",
        "cssClass": null,
        "listClass": "default",
        "isDefault": "N",
        "status": "0",
        "orderNum": 2
      }
    ]
  }
}
```

### 7.3 查询字典数据(根据类型)
- **URL**: `GET /api/dict/data/type/{dictType}`
- **权限**: 公开
- **描述**: 根据字典类型获取所有数据(用于下拉选项)

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {"dictLabel": "男", "dictValue": "0"},
    {"dictLabel": "女", "dictValue": "1"}
  ]
}
```

---

## 8. 岗位管理 (Post)

### 8.1 查询岗位列表
- **URL**: `GET /api/post/list`
- **权限**: `system:post:list`
- **描述**: 分页查询岗位列表

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 5,
    "rows": [
      {
        "postId": 1,
        "postCode": "CEO",
        "postName": "首席执行官",
        "postSort": 1,
        "status": "0",
        "createTime": "2026-01-01 08:00:00"
      }
    ]
  }
}
```

### 8.2 新增/修改/删除岗位
- **URL**: `POST/PUT/DELETE /api/post`
- **权限**: `system:post:add/edit/remove`

---

## 9. 系统配置 (Config)

### 9.1 查询配置列表
- **URL**: `GET /api/config/list`
- **权限**: `system:config:list`
- **描述**: 分页查询系统配置

**Request Parameters:**
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| configName | string | 否 | 配置名称 |
| configKey | string | 否 | 配置键名 |
| status | string | 否 | 状态 |

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "total": 10,
    "rows": [
      {
        "configId": 1,
        "configName": "主框架页-默认皮肤",
        "configKey": "sys.index.skinName",
        "configValue": "skin-blue",
        "configType": "Y",
        "status": "0"
      }
    ]
  }
}
```

### 9.2 根据键名查询配置
- **URL**: `GET /api/config/configKey/{configKey}`
- **权限**: 公开
- **描述**: 根据键名获取配置值

**Response:**
```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "configKey": "sys.index.skinName",
    "configValue": "skin-blue"
  }
}
```

---

## 10. 通用数据接口

### 10.1 获取所有部门(下拉树)
- **URL**: `GET /api/dept/treeselect`
- **权限**: `system:dept:query`
- **描述**: 获取部门下拉树结构

### 10.2 获取角色下拉列表
- **URL**: `GET /api/role/optionselect`
- **权限**: 公开
- **描述**: 获取所有角色(简单信息,用于下拉)

### 10.3 获取路由菜单
- **URL**: `GET /api/menu/getRouters`
- **权限**: 登录用户
- **描述**: 获取用户路由菜单(用于前端动态路由)

---

## 11. 错误码说明

| 错误码 | 说明 |
|--------|------|
| 0 | 成功 |
| 1 | 失败 |
| 401 | 未授权 |
| 403 | 无权限 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |

---

## 12. 版本记录

| 版本 | 日期 | 说明 |
|------|------|------|
| 1.0.0 | 2026-03-29 | 初始版本 |