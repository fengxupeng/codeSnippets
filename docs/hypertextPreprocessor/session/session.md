### 一个商品页面10个ajax同时请求(开启了session),一个接口响应时间1s,一共需要多少秒
答案肯定不是1s,因为session是阻塞的,第二个请求必须等第一个请求释放,第二个才开始请求!

* 0ms   --> session_start() --> 创建文件锁 :/var/lib/php/session/sess_唯一标识
* 15ms  --> 业务代码, -->文件仍处于锁定中
* 350ms --> 业务代码结束 --> 文件锁释放,允许下一个请求进来

为什么这么设计呢? 
>是不是有点类似于队列,第一个执行完,第二个才执行.   
假想一个场景,如果两个请求同时进行,同时记录一个数据,$_SESSION["template_id"] = $tid;   
第一个请求设置$tid = 1,然后执行其他业务,耗时2s;   
此时第二个请求设置$tid = 3,没有其他业务代码执行立即保存;   
此时第一个请求2s后结束执行,保存session;   
此时的template_id被第二个同时进行的线程请求覆盖!   
就是为了避免类似的并发场景,如何解决呢?   
可以采用无状态的请求,避免用session来存储数据!


原文参考:https://ma.ttias.be/php-session-locking-prevent-sessions-blocking-in-requests/


### php.ini关于Session的相关设置:
* session.use_cookies：默认的值是“1”，代表SessionID使用Cookie来传递，反之就是使用Query_String来传递；
* session.name：这个就是SessionID储存的变量名称，可能是Cookie，也可能是Query_String来传递，默认值是“PHPSESSID”；
* session.cookie_lifetime：这个代表SessionID在客户端Cookie储存的时间，默认是0，代表浏览器一关闭SessionID就作废……就是因为这个所以Session不能永久使用！
* session.gc_maxlifetime：这个是Session数据在服务器端储存的时间，如果超过这个时间，那么Session数据就自动删除！

