# HowTo - Mock 第三方接口返回

## 场景
依赖外部接口（如支付、短信、物流）的测试，需要稳定可控的响应。

## 方案对比

### 1. WireMock
```java
stubFor(post(urlEqualTo("/api/payment"))
    .willReturn(aResponse()
        .withStatus(200)
        .withBody("{\"success\": true}")));
```
**优点**：独立部署，支持团队共享
**缺点**：需要额外维护服务

### 2. Mock Service Worker (MSW)
```javascript
rest.post('/api/payment', (req, res, ctx) => {
  return res(ctx.status(200), ctx.json({ success: true }));
});
```
**优点**：集成在测试代码中，维护方便
**缺点**：前端/Node.js 场景更适合

### 3. Charles / Fiddler 抓包改包
**优点**：快速验证，无需编码
**缺点**：手工操作，不可重复

## 推荐实践
- 接口自动化：WireMock
- 单元测试：Mockito/Mock.js
- 临时验证：Charles Map Local

---
标签：#testing #mock #api
