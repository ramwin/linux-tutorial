**Linux 知识快速查询**  
*这个是我平时遇到各种问题的时候记录下来的笔记.*

# 页面导航
* [command 常用口令](#常用口令)
* [software 软件](#软件)
* [regular expression 正则表达式学习](#正则表达式)
* [system 系统](./linux/system.md)
* [user & group 用户和组](./linux/user_group.md)
* [file 文本处理](./text.md)
* [markdown](./markdown.md)
* [bash, shell编程](./shellprogramming/README.md)

# 常用口令
* exit # 退出
* fdisk # 对磁盘进行分区
* find
    * `find . -path "*/migrations/*.py"` *查找文件*
    * `find ./ -type f -name "*.py" | xargs grep "verify_ssl"`
* notify-send
    * `notify-send 保护视力，休息一会`
* rename
    * `rename 's/group_public/group-public/g' *` *把当前目录下所有文件的group_public变成group-public*
* zentify
    * `zenity --info --text '保护视力，休息一会'

# 常用组合命令
* [批量修改文件名](https://stackoverflow.com/questions/6840332/rename-multiple-files-by-replacing-a-particular-pattern-in-the-filenames-using-a)
```shell
for f in *.png; do mv "$f" "`echo $f | sed s/file/ffff/`"; done
```

# 软件
* [database数据库](./database/README.md)
    * [mongodb](./mongodb.md)
    * [mysql](./mysql.md)
* [chromium]
    ```
    chromium-browser --proxy-server="socks5://127.0.0.1:1080" --host-resolver-rules="MAP * 0.0.0.0 , EXCLUDE localhost" &
    ```
* except  # 自动输入账号密码的工具，用来自动化脚本里面避免卡住
* [git](./git/README.md)
* [gpg](https://statistics.berkeley.edu/computing/encrypt)
    * 创建密钥 gpg --full-gen-key
    * 加密文件 gpg -e -r USERNAME <file>
    * 解密文件 gpg -d -o <target> <file>
* [MySQL](./database/README.md)
    * [Grant权限控制](./database/mysql_grant.md)
* [nginx](./nginx.md)
* [redis](./redis/README.md)
* [阮一峰的oauth讲解](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)
* [screen](./screen.md) *用来开启后台shell*
    ```
    screen -list
    screen -S sjtupt    # 创建新的screen
    ctrl + A + D    # 关闭当前screen
    screen -r sjtupt    # 还原之前的screen
    ```
* smtp邮件服务器
    * [digitalocean.com教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04)
    ```
    sudo apt install mailutils
    sudo apt install postfix
    修改 inet_interfaces = loopback-only 或者 localhost
    service postfix restart
    ```
    * [配置文档](http://blog.csdn.net/reage11/article/details/9295005)
* [vim](./vim.md) [tutorial教程](http://www.openvim.com/)

# 正则表达式
* [在线学习](https://regexone.com)
* [在线测试](https://regex101.com/#python)
* 规则:
    1. 基础 abc
    2. 数字 \d
    3. 通配符 .
    4. 任意选择 [abc] 匹配中间任何一个 [^abc] 反向匹配，不要出现abc任何一个
    5. [a-z] 匹配 a 到 z的小写字母
    6. 指定数量 \d{1,3}
    7. 至少有数字 \d+
    8. 可有可无一个 \d?
    9. \s 空白符(space)
    10. ^开头
    11. $结尾
    12. ()当作一个group ^(.*).pdf$ 所有的pdf文件的文件名
    13. | 代表或者 (cats|dogs)
    14. \w 数字或者字母
    15. \D \S \W 代表反过来
