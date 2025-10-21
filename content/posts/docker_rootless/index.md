```plaintext
To run Docker as a non-privileged user, consider setting up the
Docker daemon in rootless mode for your user:

    dockerd-rootless-setuptool.sh install

Visit https://docs.docker.com/go/rootless/ to learn about rootless mode.


To run the Docker daemon as a fully privileged service, but granting non-root
users access, refer to https://docs.docker.com/go/daemon-access/

WARNING: Access to the remote API on a privileged Docker daemon is equivalent
         to root access on the host. Refer to the 'Docker daemon attack surface'
         documentation for details: https://docs.docker.com/go/attack-surface/
```

[优化Docker权限管理：配置Docker用户组 - 知乎](https://zhuanlan.zhihu.com/p/654107590)

[bitwarden本地搭建(无需购买SSL证书) - THATO - 博客园](https://www.cnblogs.com/Thato/p/18311581)
