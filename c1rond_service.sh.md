```
#!/system/bin/sh
(
crond() {
  /data/user/0/bin.mt.plus/files/term/usr/bin/applets/crond
}

until [ $(getprop sys.boot_completed) = "1" ]; do
  sleep 5
done
  
until [ $(ps -ef | grep crond | grep -v "grep" | wc -l) = "1" ]; do
  kill -9 $(pidof crond)>/dev/null 2>&1
  sleep 3 && echo "1. 启动crond进程！" && crond && echo "2. 启动成功！"
done
  echo -e "\033[0;31m3. crond已启动！\033[0m"
  echo -e "\033[0;31mpid: $(pidof crond)\033[0m"
)&

# 开机自启crond服务，已测试成功。脚本文件名不能带有crond字符
```
