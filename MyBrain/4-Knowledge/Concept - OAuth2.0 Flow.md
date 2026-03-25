# Concept - OAuth2.0 授权流程

## 核心角色
| 角色 | 说明 |
|------|------|
| Resource Owner | 资源拥有者（用户） |
| Client | 第三方应用 |
| Authorization Server | 授权服务器 |
| Resource Server | 资源服务器 |

## 四种授权模式

### 1. Authorization Code（授权码模式）- 最安全
```
用户 → Client → Authorization Server
            ↓ (授权码)
         Client (换取 token)
            ↓
       Resource Server
```
**适用**：有后端服务的 Web 应用

### 2. Implicit（简化模式）
直接返回 token，无需授权码交换
**适用**：纯前端应用（已不推荐）

### 3. Password（密码模式）
用户直接把账号密码给 Client
**适用**：官方应用，高信任场景

### 4. Client Credentials（客户端凭证模式）
Client 直接用自己凭证获取 token
**适用**：服务器间调用，无用户参与

## 测试要点
- 授权码有效期验证
- Token 刷新机制
- 重定向 URL 白名单校验
- CSRF 防护（state 参数）

---
标签：#auth #security #oauth
