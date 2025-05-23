---
title: 安全编码规范
---

本文是一个检查列表，当您编写代码时，您需要检查新增代码是否违反了以下列表：

1. 禁止存在无法修改的认证凭据（如：进程二进制中硬编码口令）。
2. 如果采用解释性语言（如 Shell/Python/Perl 脚本、JSP、HTML等）实现，对于不满足未公开接口并需要清理的功能，必须彻底删除，严禁使用注释行等形式仅使功能失效。
3. 禁止使用私有密码算法实现加解密，包括：
    - 未经过专业机构评估的、自行设计的密码算法；
    - 自行定义的通过变形/字符移位/替换等方式执行的数据转换算法；
    - 用编码的方式（如 Base64 编码）实现数据加密的目的的伪加密实现。
    说明：在非加解密场景，出于正常业务目的使用 Base64 等编码方式或变形/移位/替换等算法不违反此条。
4. 密码算法中使用到的随机数必须是密码学意义上的安全随机数。
5. 禁止在系统中存储的日志、调试信息、错误提示中明文打印认证凭据（口令/私钥/预共享密钥）。
