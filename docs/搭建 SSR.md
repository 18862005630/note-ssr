# 搭建 SSR

## 安装流程

1. 连接上 VPS 后依次执行以下三条命令：
  
    ```
    wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
    chmod +x shadowsocks-all.sh
    ./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
    ```
    
    > 如果运行上面第一条命令时，出现找不到 `wegt` 之类的提示，则表明系统没有预装 `wegt`，先运行以下命令完成 `wegt` 的安装。
    
    ```
    CentOS：
    yum -y install wget
    Ubuntu/Debian：
    apt-get -y install wget
    ```

2. 接下来会有几个参数需要选择，依次为：
  
    1. 提示安装哪个版本，我们输入 `2` 后按回车，即选择 SSR 安装。

    ![image](https://user-images.githubusercontent.com/32833804/60750564-a61c3a00-9fdc-11e9-92d8-1d06f595c407.png)

    2. 然后会提示设置 SSR 密码，输入自定义密码后按回车，建议不要使用默认密码。

    ![image](https://user-images.githubusercontent.com/32833804/60750572-d06df780-9fdc-11e9-9d07-92e9d28329f2.png)

    3. 接下来选择 SSR 要使用的服务器端口，最好是五位数的端口。

    ![image](https://user-images.githubusercontent.com/32833804/60750599-38bcd900-9fdd-11e9-8274-79c9d48f3f57.png)

    4. 然后选择加密方式，如果选择 `aes-256-cfb` 的话，就输入对应序号 `2`，按回车继续。

    ![image](https://user-images.githubusercontent.com/32833804/60750603-44a89b00-9fdd-11e9-92a1-3cfc2518fe5e.png)

    5. 接下来选择协议，建议选择自 `auth_aes128_md5` 开始以下的几种，输入对应序号按回车。

    ![image](https://user-images.githubusercontent.com/32833804/60750613-51c58a00-9fdd-11e9-98bd-a7ab9a7b45b9.png)

    6. 选择混淆方式, 选择 `http_simple` 即可，选择好后按回车继续。

    ![image](https://user-images.githubusercontent.com/32833804/60750618-643fc380-9fdd-11e9-97ff-308076a50c42.png)

    7. 以上参数设置完成后，按任意键开始安装。

    ![image](https://user-images.githubusercontent.com/32833804/60750619-69047780-9fdd-11e9-9450-0d5aaf12b9b4.png)

    8. 安装完成后，会有如下图安装成功的提示，记住刚才设置的各项参数，在客户端连接时需要用到。

    ![image](https://user-images.githubusercontent.com/32833804/60750620-6dc92b80-9fdd-11e9-80b5-a6193e3c8463.png)

    9. 经过以上几个简单的参数选择后，SSR服务器端已经自动安装成功了。保险起见，输入reboot重启VPS服务器，SSR会自动随系统重启。
    
## SSR 常用命令

```
启动SSR：
/etc/init.d/shadowsocks-r start
退出SSR：
/etc/init.d/shadowsocks-r stop
重启SSR：
/etc/init.d/shadowsocks-r restart
SSR状态：
/etc/init.d/shadowsocks-r status
卸载SSR：
./shadowsocks-all.sh uninstall
```

> 另外如果需要更改SSR的相关配置参数，配置文件位置在：/etc/shadowsocks-r/config.json