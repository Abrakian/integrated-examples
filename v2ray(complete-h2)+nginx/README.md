除v2ray kcp外,所用应用共用443端口。此端口由v2ray监听（即v2ray前置），利用vless tcp回落/分流特性实现，分流出ws，非v2ray的web回落给nginx。

v2ray tcp类应用直连，且以http/1.1或http/2自适应代理科学上网；v2ray ws类应用分流一次。

注意：

1、nginx 支持 h2c server，但不支持http/1.1 server与h2c server共用一个端口或一个进程，故回落端口或进程必须分开。

2、nginx 不支持 h2c proxy，故无法搭建vless\vmess+h2反代应用。

3、nginx 预编译程序包不带支持 PROXY protocol 协议的模块。如要使用此项协议应用，需加http_realip_module与stream_realip_module两模块构建自定义模板，后进行源代码编译和安装。另编译时选取源代码版本建议不要低于1.13.11。

4、配置1：没有启用PROXY protocol，仅端口回落。配置2：启用了PROXY protocol，且端口回落。配置3：启用了PROXY protocol，且进程回落。
