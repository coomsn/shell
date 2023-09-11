```
#!/system/bin/sh

(
    until [ $(getprop init.svc.bootanim) = "stopped" ]; do
        sleep 10
    done

    if [ -f "/data/Box/01start.sh" ]; then
        chmod 755 /data/Box/*
        /data/Box/01start.sh
    fi
)&

# 01start.sh
```
