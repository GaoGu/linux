# 循环运行的例行性工作排程

循环运行的例行性工作排程则是由 cron (crond) 这个系统服务来控制的。

Linux 系统上面原本就有非常多的例行性工作，因此这个系统服务是默认启动的。

另外， 由于使用者自己也可以进行例行性工作排程，所以， Linux 也提供使用者控制例行性工作排程的命令 (crontab)。


# 使用者的配置

为了安全性的问题，我们可以限制使用 crontab 的使用者帐号

- /etc/cron.allow：

将可以使用 crontab 的帐号写入其中，若不在这个文件内的使用者则不可使用 crontab；

- /etc/cron.deny：

将不可以使用 crontab 的帐号写入其中，若未记录到这个文件当中的使用者，就可以使用 crontab 。

优先顺序来说， /etc/cron.allow 比 /etc/cron.deny 要优先， 而判断上面，这两个文件只选择一个来限制而已，因此，建议你只要保留一个即可， 免得影响自己在配置上面的判断！一般来说，系统默认是保留 /etc/cron.deny ， 你可以将不想让他运行 crontab 的那个使用者写入 /etc/cron.deny 当中，一个帐号一行！

当使用者使用 crontab 这个命令来创建工作排程之后，该项工作就会被纪录到 /var/spool/cron/ 里面去了，而且是以帐号来作为判别的喔！举例来说， dmtsai 使用 crontab 后， 他的工作会被纪录到 /var/spool/cron/dmtsai 里头去！但请注意，不要使用 vi 直接编辑该文件， 因为可能由於输入语法错误，会导致无法运行 cron 喔！另外， cron 运行的每一项工作都会被纪录到 /var/log/cron 这个登录档中，所以罗，如果你的 Linux 不知道有否被植入木马时，也可以搜寻一下 /var/log/cron 这个登录档呢！