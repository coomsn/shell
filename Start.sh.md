```
#!/system/bin/sh

path=/data/box_kernel/
kernel_bin=/data/box_kernel/sing-box
config_file=/data/box_kernel/box.json
log_file=/data/box_kernel/src/log/box.log

# 删除日志
find ${path}* -size +1M -name "*.log" -exec rm -rf {} \;

# 杀掉并重启sing-box进程
if pgrep sing-box>/dev/null 2>&1; then
  kill -9 $(pidof sing-box)
  echo -e "\033[1;32m1.杀掉并重启sing-box进程！\033[0m"
  (${kernel_bin} run -c ${config_file} -D ${path}>/dev/null 2>&1)&
  echo -e "\033[0;31mpid: $(pidof sing-box)\033[0m"
  echo -e "\033[0;31m启动完毕！\033[0m"
else
  echo -e "\033[1;32m2.启动sing-box进程！\033[0m"
  (${kernel_bin} run -c ${config_file} -D ${path}>/dev/null 2>&1)&
  echo -e "\033[0;31mpid: $(pidof sing-box)\033[0m"
  echo -e "\033[0;31m启动完毕！\033[0m"
fi

# Start.sh
```
