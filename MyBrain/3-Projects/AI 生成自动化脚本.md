# FlowGenius SmartAdapter


A traffic-driven automated API test script generation tool that solves the problem of missing or outdated API documentation. By leveraging multi-dimensional traffic analysis and an intelligent rule engine, it generates high-availability Pytest test scripts with a single click.

## Features

### Dual-Mode Traffic Collection

- **Proxy Mode**: Capture HTTP/HTTPS traffic in real-time using MitmProxy

- **Log Mode**: Extract traffic from Nginx, Apache, or custom application logs

### Intelligent Analysis

- Automatic request-response correlation analysis
	- 分析过程如下：
		- 按请求应答时序依次分析数据关联关系，针对某个请求应答报文对，分析当前请求报文字段，与之前的请求报文对中哪些应答报文字段相等
		- 再基于相等字段的描述进行语义比对，如果相符则标注这两个字段存在“关联关系”
		- 当一个字段和多个请求报文对中的应答字段相符时，以发生时间最接近的标注关联
		- 当一个字段和同一个请求报文对中多个字段相符时，标注“待定关联关系”

- JSONPath and regex-based pattern matching
	- http协议json格式，优先采用jsonpath提取字段值
	- 如果存在xml协议，采用xmlpath提取字段值
	- 如果json，xml不适合的场景，则使用正则表达式

### Smart Assertion Generation

- Health assertions (status code, response time)

- Contract assertions (Swagger/OpenAPI schema validation)

- Semantic assertions (business logic validation)

- Snapshot comparison for regression testing


### Test Generation

- Pytest-compatible test scripts

- API object layer for reusable code

- Data-driven testing support (YAML, JSON, CSV, Excel)

- Allure report integration

  

### LLM Integration

- Intelligent test case generation using Large Language Models

- Support for Zhipu AI (智谱AI), OpenAI, and Anthropic

- Automatic assertion generation with semantic analysis

- Smart correlation detection for request dependencies