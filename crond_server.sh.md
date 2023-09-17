```
#!/system/bin/sh

(
crond(){
/data/user/0/bin.mt.plus/files/term/usr/bin/applets/crond
}
until [ $(getprop sys.boot_completed) = "1" ]; do
sleep 5
done

COUNT=$(ps -ef | grep crond | grep -v "grep" | wc -l)  
# 如果检测到COUNT=0，说明crond没有启动。
if [ ${COUNT} -eq 0 ]>/dev/null 2>&1 ; then

echo "1.启动crond进程！"
crond
else
kill -9 $(pidof crond)
echo "2.杀掉并重启crond进程！"
crond
fi
)&

# 开机自启crond服务
```
