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

(
crond() {
/data/user/0/bin.mt.plus/files/term/usr/bin/applets/crond
}

until [ $(ps -ef | grep sing-box | grep -v "grep" | wc -l) -eq "1" ]; do
    sleep 1
done

while [ $(ps -ef | grep crond | grep -v "grep" | wc -l) -ne "1" ]; do
    kill -9 $(pidof crond)>/dev/null 2>&1
    sleep 3 && echo "1. 启动crond进程！" && crond && echo "2. 启动成功！"
done
    echo -e "3. crond启动完毕！"
    echo -e "pid: $(pidof crond)"
)&

# crond service
```
