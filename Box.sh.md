```
#!/system/bin/sh

(
    until [ $(getprop init.svc.bootanim) = "stopped" ]; do
        sleep 10
    done

    if [ -f "/data/Box/01start.sh" ]; then
        chmod -R 755 /data/Box/*
        chown -R root:root /data/Box/*
        /data/Box/01start.sh
    fi
)&

# sing-box service
```

# 查询内存里面的开机动画函数
getprop init.svc.bootanim

# -f 
文件参数，例如：-f "/dab/BOX/01start.sh"。
查询文件是否存在。
