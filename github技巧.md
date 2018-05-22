
## 如果有一天，push时提示你ssh上传失败了，

有可能是你的 git 和 TortoiseGit 版本老了，github网站不再支持了。升级版本吧。




git push 时为何要输入密码，明明已经 有私钥了。

	git 可以用 https 方式访问也可以用 ssh 方式访问，其中 https 就是你每次要输入密码那种了，ssh的话可以不用输入密码，但是安全哪里来呢 —— 就是密钥！ 密钥git 密钥使用 ssh-keygen 生成，分为 私钥和公钥，私钥本地保存，公钥放到服务端，github,osc git 等都差不多的设置。2. https 和 ssh 的仓库地址不一样，如 开源中国的仓库 上提供了个按钮让你复制，
	htttps格式：https://git.oschina.net/user_name/project_name.git   
	git 格式： git@git.oschina.net:user_name/project_name.git

	注意到 git地址的格式，前头是 git@ 
	user_name 前面是 :

 

	所以当你有私钥时，push时还要求 你输入 密码时，是因为 这个仓库 使用的上传地址是
	https 格式的。

tortoisegit如何修改仓库上传地址？ 

	右键仓库文件夹，点settings,点击 Remote,点击 origin,然后修改 URL地址就好。
	
	htttps格式：https://git.oschina.net/user_name/project_name.git   
	git 格式： git@git.oschina.net:user_name/project_name.git