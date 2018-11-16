
循环运行的例行性工作排程则是由 cron (crond) 这个系统服务来控制的。

Linux 系统上面原本就有非常多的例行性工作，因此这个系统服务是默认启动的。

另外， 由于使用者自己也可以进行例行性工作排程，所以， Linux 也提供使用者控制例行性工作排程的命令 (crontab)。


## 使用者的配置

为了安全性的问题，我们可以限制使用 crontab 的使用者帐号

- /etc/cron.allow：

将可以使用 crontab 的帐号写入其中，若不在这个文件内的使用者则不可使用 crontab；

- /etc/cron.deny：

将不可以使用 crontab 的帐号写入其中，若未记录到这个文件当中的使用者，就可以使用 crontab 。

## crontab 语法
    crontab [-u username] [-l|-e|-r]
    选项与参数：
    -u  ：只有 root 才能进行这个任务，亦即帮其他使用者创建/移除 crontab 工作排程；
    -e  ：编辑 crontab 的工作内容
    -l  ：查阅 crontab 的工作内容
    -r  ：移除所有的 crontab 的工作内容，若仅要移除一项，请用 -e 去编辑。

    例子
    */1 * * * * bash /home/gaohaipeng/test.sh >> /home/gaohaipeng/test.log
    
代表意义 | 分钟 | 小时 | 日期 | 月份 | 周
---|---
数字范围 | 0-59 | 0-23 | 1-31 |	1-12 |	0-7