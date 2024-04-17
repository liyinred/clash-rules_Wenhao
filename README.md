# 自用clash规则,cn域名和特定网站直连(黑名单模式)
**目前 Clash 支持的规则类型如下：**

- DOMAIN-SUFFIX：域名后缀匹配
- DOMAIN：域名匹配
- DOMAIN-KEYWORD：域名关键字匹配
- IP-CIDR：IP 段匹配
- SRC-IP-CIDR：源 IP 段匹配
- GEOIP：GEOIP 数据库（国家代码）匹配
- DST-PORT：目标端口匹配
- SRC-PORT：源端口匹配
- PROCESS-NAME：源进程名匹配
- RULE-SET：Rule Provider 规则匹配
- MATCH：全匹配

```yaml
- DOMAIN-KEYWORD,dwai,🎯 全球直连
- DOMAIN-KEYWORD,cn,🎯 全球直连
```

# 正则与关键词匹配

## 正则表达式

### 定义

- 文本模式，包含普通字符和特殊字符（元字符）
- 用于字符串搜索、替换和匹配

### 原理

- **普通字符匹配：**直接匹配相应字符
- **元字符使用：**具有特殊意义，指定更复杂的匹配模式
- **模式组合：**创建复杂匹配模式

### 匹配 URL 的正则表达式原理

- **起始和结束：**^ 和 $，确保整个字符串匹配 URL 格式
- **协议：**(https?|ftp)，匹配 http 或 https
- **域名：**[a-zA-Z0-9.-]，匹配合法字符
- **端口：**(:\d{1,5})?，匹配可选端口号
- **路径、查询和片段：**(/[\w/:%#\{{input}}\?\(\)~\.=\+\-]*)?，匹配路径、查询参数和片段

## 关键词匹配原理

- 搜索指定的单词或短语
- **完全匹配：**单词必须与搜索词完全一致
- **大小写敏感：**取决于搜索工具设置

## 区别

- **复杂度：**正则表达式更复杂
- **灵活性：**正则表达式更灵活
- **性能：**正则表达式匹配更耗时
- **使用场景：**
    - **正则表达式：**复杂模式识别（验证输入、数据提取）
    - **关键词匹配：**简单文本查找（搜索）
