注：

1、nginx为v2ray、naiveproxy(caddy2)、trojan(trojan-go)进行sni分流（四层转发），实现共用443端口。

2、v2ray tcp类应用直连，v2ray ws类应用分流一次。

3、naiveproxy直连。v2ray h2类应用分流（反代）一次。

3、trojan(trojan-go)直连。

4、naiveproxy(caddy2) 使用本github文件，才可以同时支持naiveproxy及v2ray h2反向代理。
