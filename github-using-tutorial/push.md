1. 检查是否已安装git并初始化git仓库：
	1. 检查是否安装git
	2. 初始化本地Git仓库
		1. 切换目录至要推送的项目
		2. 初始化
		    `git init`
2. 在GitHub创建一个新的仓库
     + 
3. 将项目链接到仓库
	1. 设置与本地文件对应的远程仓库
		`git remote add origin url-of-your-repo`
	2. 添加文件到git并提交更改
		+ 将文件添加到Git暂存区
		`git add`
		+ 确认这些更改
		`git commit -m "description-of-change"`
	3. 使用SSH鉴权替代用户名密码登录
		1. 生成SSH密钥
			  If you do not have a SSH key, follow the steps below: 
			 1. Generate SSH key pair
				+ Generate new SSH key
				`ssh-keygen -t rsa -b 4096 -C "youremail.example.com"`
				+ The youremail.example.com refer to your GitHub email address
			 2. 保存密钥：
				+ 当提示你输入文件路径时，按回车键（Enter）使用默认路径 ~/.ssh/id_rsa。
				+ 你也可以选择设置一个 passphrase（密码短语）来保护你的密钥，或者直接按回车键跳过。
			 3. 添加密钥到SSH-agent: 
			    + 启动SSH-agent:
			    `eval "$(ssh-agent -s)"`
			    + 将你的SSH私钥添加到SSH-agent: 
			    `ssh-add ~/.ssh/id_rsa`
		2. 复制公钥
		    + 生成并复制SSH公钥内容:
		    `pbcopy < ~/.ssh/id_rsa.pub`
		3. 添加SSH密钥到GitHub
		    1. 填写SSH Key信息: 
		        + 在 GitHub 的 “Add new SSH Key” 页面上，将 Title 字段填写为一个描述性名称（例如 “My Mac SSH Key”）
		        + 在 Key 字段中，粘贴刚刚复制的公钥内容
		    2. 保存SSH Key:
		        + 点击绿色的 Add SSH key 按钮，保存该密钥
		4. 测试SSH连接
		    在终端中，运行以下命令来测试是否成功连接到 GitHub:
		    `ssh -T git@github.com`
		    如果设置正确，你应该会看到类似如下的输出:
		    `Hi Songheng-HE! You've successfully authenticated, but GitHub does not provide shell access.`
	4. 配置Git使用SSH
		    执行以下命令，将远程仓库的 URL 更改为 SSH 格式:
		    `git remote set-url origin git@github.com:username/repo-name.git`
		    这样在推送时使用SSH连接，不用验证用户名密码
	5. 推送项目到GitHub远程仓库
	    如果是第一次推送，使用以下指令:
	    `git push -u origin main`

