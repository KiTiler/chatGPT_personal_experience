# ChatGPT 个人使用经验

## 直接使用openai官方网页(方法麻烦且较为敏感,不推荐)

- 由于中国的网络环境,会无法访问ChatGPT的网页端,想要访问首先需要配置代理(VPN),并且很多操作需要使用到VPN,下面介绍一下我使用的方法
  1. 首先需要在一些服务提供商处购买代理服务,价格一般为10元左右一个月,它会提供一些节点(不过很多代理提供商的网站也需要配置好后才能访问,比较尴尬).也可在一些地方找到免费的节点,例如<https://github.com/freefq/free>
  2. 安装和配置连接软件.如果是购买的服务,一般它会提供教程,可以按照它的教程来使用.如果是使用免费节点,可以先下载clash,它可在下面链接中找到下载地址,不过可能会比较慢<https://github.com/Kr328/ClashForAndroid/releases><https://github.com/Dreamacro/clash/releases>
  3. 在下载好clash软件后,在配置中复制获取的url,点击下载
   ![clash](/img/clash1.png)
   再在设置中选择要访问的结点,再试着用google搜索,如果能搜索到,即配置成功
   ![clash2](/img/clash2.png)
- 在配置好网络环境后,可访问chatGPT的网页端,网址为<https://chat.openai.com/>在此可进行试用,如果遇到了拦截或者无法访问的情况,需根据具体问题进行解决,比较麻烦,主要是ip地址被拒绝或者使用的代理结点被标记为异常结点,如果找不到解决办法可使用下一种方法.
  
## 使用国内镜像

- 现在国内有很多能够直接使用的镜像网站,有些能直接使用,有些需要提供自己的api key,可以在下面的网页进行查找和使用
<https://github.com/lzwme/chatgpt-sites>
  
## 自建国内镜像网站(推荐方法)

- 首先给出最终的自建ChatGPT镜像网站结果,访问<littlehx.cn>输入密码**30409**(并不需要配置VPN),即可便利快速的访问ChatGPT
- 以下给出自建所需的方法
  1. 申请或者购买一个ChatGPT账号.国内环境申请账号比较麻烦,而且成本跟购买差不了太多,在这里不做介绍.而以购买的方式,则需要找一些账号提供商,列举一个我购买过的地方(有些也需要使用VPN才能访问)
  - <http://xzhiku.com>
  - <http://xzhiku.com>
  不过这些网站的账号安全性不能完全保证,也可到telegram上找更多售卖的地方,一般带5美元额度的账号在几块到几十块都有左右,120美元额度的价格一般为一百多,如果是有GPT4的API的账号,现阶段很贵,一般为几千元.
/img  2. 在拥有一个账号之后可登录openai的官网,登录自己的账号,查看自己账号的信息,主要是要获取账号的key,这是完成下面步骤的关键.
  3. 访问<https://github.com/Yidadaa/ChatGPT-Next-Web>
   ![访问页面](/img/chatGPT_next_web.png)
   点击Deploy按钮,会进入Vercel的界面
   ![vercel](/img/2.png)
   点击GitHub按钮,这会创建一个GitHub仓库
   ![vercel部署](/img/3.png)
   点击create之后,会让你配置两个环境变量,第一个是我们在上面获取的key,另一个为访问的密码,密码可以随意设置
   ![环境变量配置](/img/4.png)
   点击Deploy之后就算部署好了,它会提供一个域名,但这个域名只有配置VPN才能访问,解决办法就是配置域名解析,将国内能访问的域名解析到部署好的此项目.首先需要获取一个域名,可以在阿里云,腾讯云等服务提供商处购买,在此不赘述.获取域名之后,进入刚部署后的页面,点击进入settings
   ![设置页面](/img/settings.png)
    再点击Domains区域,在这里即可进行域名解析的配置,即将自己的域名输入,然后点击add按钮,按照它的指示进行操作
  ![域名解析](/img/域名解析.png)
  最后看到这个页面,即为成功
  ![解析结果](/img/解析结果.png)
  现在已经能不挂VPN,直接访问刚配置好的域名,即可访问该页面了

## 使用chatGPT的api进行

- chatGPT开放了api,只需要简单的调用接口,即可用代码来访问chatGPT并完成很多操作,下面是以python为例的使用过程.
- 访问chatGPT的api需要一个良好的网络环境,在国内的电脑上直接运行是不行的,而配置代理来运行也常常出错,于是我选则了在ip地址为国外(推荐在美国地区)的服务器上运行
  1. 购买服务器.在很多服务器提供商处可以购买服务器(腾讯云,阿里云等),一般选则2核4g的轻型应用服务器就够了,ip地址需为非亚洲地区.
  2. 在购买好服务器后,会获得一个IP地址和root用户的密码,然后可以在自己的电脑上下载这些软件
   ![软件图](/img/软件.png)
   其中,xftp可以对服务器上的文件金星上传和下载等操作,xshell可以远程登录到服务器上,用命令行的形式对服务器进行操作,而vscode是一个轻量级但功能强大的编辑器,支持多种插件,其中便有远程登录的插件,可以直接在服务器上编写和运行代码.
   其中,xshell下载并打开,右击左侧会话管理器,选择新建会话
   ![xshell](/img/xshell.png)
   需要在主机出填入服务器的ip地址,点击确定,并根据提示输入用户名的密码,即可登录到主机上,可进行环境配置等操作.为了接下来的操作,可以在这一步完成python的安装,python版本需要在3.7以上.
   ![xshell2](/img/xshell2.png)
   并且在配置好xshell之后,点击上面菜单栏的xftp按钮,即可直接使用xftp进行文件的传输
   ![xshell3](/img/xshell3.png)
   vscode的使用也很简单,只需在下载好后点击左侧Extensions,并搜索ssh,下载第一个插件
   ![xshell3](/img/vscode.png)
   在配置好ip地址,输入用户名和密码,即可登录到远程服务器上,进行代码编写操作.
  3. 调用ChatGPT的接口非常简单,详细内容可参考官方网站<https://platform.openai.com/docs/introduction>
  - 下面进行简单的介绍.首先利用安装好python所需的包`pip install openai`,再在代码中导入openai
  
  ```python
  import openai
  from openai.error import *
  ```

  然后需要配置openai的参数,这里参数为你账号的api_key

  ```python
  openai.api_key = "your_key"
  ```

  然后便可以撰写一个函数来访问chatGPT,它的返回值即为chatGPT回答的结果,也可对它可能产生的错误进行处理

  ```python
  # 直接对chatGPT进行提问
  # data : 提问的信息
  # prefix : 对话的前缀,可为空
  def query_AI(data, prefix=[]):
      try:
          prefix.append({"role": "user", "content": str(data)})
          message = prefix
          completion = openai.ChatCompletion.create(
              model="gpt-3.5-turbo",  # 模型使用gpt3.5
              messages=message,
              max_tokens=100,  # 限制GPT回复的长度
              # temperature=1.5, # 值越大越随机
              # prompt=prompt,  # 提示
          )
          result = completion["choices"][0]["message"]["content"]
          return str(result)
      except Exception as e:
        return ""
  ```

  另外,我利用了python中的pandas库来读取excel文件,并进行批量处理,再将处理后的数据写回到excel中.其中query_AI_attitude()是我自己写好的调用GPT的函数,parallel_apply()是一个多线程库,可以加快一些访问速度.其实这种低运算高IO的操作更适合用协程来实现,但是与pandas库一起使用时出现了bug未解决,就没有实现.

  ```python
  import pandas as pd
  from pandarallel import pandarallel  # 导入pandaralle
  test_data = pd.read_excel("data_input/data_processed.xlsx")
  test_data['GPT判读态度'] = test_data["内容"].parallel_apply(
        lambda x: query_AI_attitude(x))
  test_data.to_excel("data_output/数据测试7_4_normal.xlsx")
  ```

  如果顺利.这样即可实现批量访问chatGPT.


