```
#!/system/bin/sh

(
path=/data/box_kernel/
# path=/data/box_kernel/ or /data/clash_kernel/
    until [ $(getprop init.svc.bootanim) = "stopped" ]; do
        sleep 5
    done
    
    if [ -f "${path}Start.sh" ]; then
        chmod -R 755 ${path}*
        chown -R root:root ${path}*
        ${path}Start.sh
    fi
)&

# proxy service
# /data/adb/service.d/proxy_service.sh
```

# 查询内存里面的开机动画函数
getprop init.svc.bootanim

# -f 
文件参数，例如：-f "/dab/box_kernel/01start.sh"。
查询文件是否存在。
