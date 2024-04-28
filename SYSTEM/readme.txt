# 题目概述
这是一道Windows内核提权题目。
最新版的Windows虚拟机中运行了有漏洞的驱动sioctl.sys，你的任务是找到漏洞并写出利用，完成从低权限（虚拟机中的user权限）提权至nt authority\SYSTEM的过程，然后读取C:\flag.txt文件。

# 题目环境
部署题目使用的虚拟机下载地址为：https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/
你可以选择自己喜欢的虚拟化软件安装对应的虚拟机，加载附件中的sioctl.sys进行本地测试。

远程部署环境中对虚拟机做了以下更改：
1. 为了加载sioctl.sys开启了测试签名选项(TESTSIGNING)，同时为了部署关闭了防火墙
2. 关闭了Windows Defender，选手无需考虑免杀
3. 在C:\flag.txt放置了只有SYSTEM用户可读的flag文件

考虑到部署以及虚拟化软件不同带来的细微差异可能会给漏洞利用带来不确定性，这里给出远程环境的完整服务列表及其状态（services.txt），如果你还需要其他信息，请联系管理员（**请注意，当发生争议时，以远程部署环境为准**）

# 如何验证
远程验证利用的步骤为：
1. 选手连接118.31.189.56的12345端口，通过PoW
2. 选手提供一个下载链接，该下载链接需要包含且只包含一个可执行程序（.exe文件）
3. 远程地址会在验证完成后会返回给选手验证过程的录像下载链接，选手可以查看录像检查利用运行结果

一个示例验证过程如下（>开头的行是选手的输入）：
```
Proof your work, give me the result of the command below:
hashcash -qCmb 26 vMxWoIUq
> 1:26:240321:vMxWoIUq::FAMicl7dum5x0ReJ:00000000EC9d2
PoW pass
give me the download link of your exploit:
valid url format: ^(http|https)://[a-zA-Z0-9/:.%@]+$
> http://example.com:8000/exp.exe
running... this may take a few minutes
You MUST keep this connection during this time
================================
download your result at http://118.31.189.56:50391/tmptx9ke5jn.exe-screen0.webm with the credential ctf:M5B53WT1
this link will expire 120 seconds later
```

# 注意事项
1. **远程资源有限，请尽量在本地测试**
2. 进行一轮验证大概需要3分钟，请合理规划做题时间
3. 其他问题请联系管理员