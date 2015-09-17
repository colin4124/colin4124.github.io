# 在 Windows 下使用 GitHub的配置

- date: 2013-05-01 08:03
- tags: 技术, Git, GitHub

---------------------

## 通过 Cygwin 安装 git

至于怎么安装和使用 Cygwin 参考 [Cygwin:在window下用linux的方式工作](/2013-04-28-a-bref-usage-of-cygwin.html) 

打开```setup.exe```, 安装 ```openssh git git-completion```

![搜索 openssh](/media/2013-05-01-use-github-in-windows/github-1.png)

![搜索git git-completion](/media/2013-05-01-use-github-in-windows/github-2.png)

### 申请GitHub帐号

打开 [GitHub](https://github.com/) 注册一个帐号

### 设置 git

**1. 设置你的名字， 每次用git 提交时才知道是谁修改的。输入以下命令， 把引号里的Your Name Here 换成是你想起的名字**

	git config --global user.name "Your Name Here"

**2. 设置你的Email， 这得和你在GitHub 申请时用的邮箱一致。把引号里的your_email@example.com 换成你的邮箱地址**

	git config --global user.email "your_email@example.com"
    
###通过SSH来访问 GitHub

**1.生成 SSH 密钥**

	ssh-keygen -t rsa -C "your_email@example.com"

**2. 然后你会看到下面的提示，直接按回车**

	Generating public/private rsa key pair.
	# Enter file in which to save the key (/c/Users/you/.ssh/id_rsa):

**3. 看到下面这个提示，意思是每次用git 访问 GitHub时，输入的验证短语，可以不写，直接回车**

	Enter passphrase (empty for no passphrase): [Type a passphrase]
	# Enter same passphrase again: [Type passphrase again]

**4. 然后输入下面的命令，把SSH key 复制到剪贴板。**
	clip < ~/.ssh/id_rsa.pub

**5. 去你GitHub的设置页面(右上角) 添加 这个 SSH key**

![GitHub的设置](/media/2013-05-01-use-github-in-windows/github-3.png)

**6. 在设置页面左边那一栏找到 SSH Keys**

![在设置页面左边那一栏找到 SSH Keys](/media/2013-05-01-use-github-in-windows/github-4.png)

**7. 点击"Add SSH key"**

![点击"Add SSH key"](/media/2013-05-01-use-github-in-windows/github-6.png)

**8. 在 key 那一栏粘贴 SSH key, 确保第4步的命令你已经输入了. Title就是为这个SSH key 做个标记，知道这个SSH key是来自哪里的，比如我的是win7, 就知道是我笔记本上win7的系统**

![粘贴 SSH key](/media/2013-05-01-use-github-in-windows/github-7.png)

**9. 输入以下命令测试是否可以连接上GitHub**

    ssh -T git@github.com

 **你会看到一个警告，输入 yes**

    The authenticity of host 'github.com (207.97.227.239)' can't be established.
	# RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
	# Are you sure you want to continue connecting (yes/no)?

**然后输入你第3步设置的验证短语，没有设置的直接回车**

![输入你第3步设置的验证短语](/media/2013-05-01-use-github-in-windows/github-8.png)

####10. 如果看到下面的提示，恭喜你，成功了

	Hi username! You've successfully authenticated, but GitHub does not
	# provide shell access.


	