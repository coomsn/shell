```
#!/system/bin/sh

# 删除日志
find . -size +1M -name "*.log" -exec rm -rf {} \;

# 清除并重启 sing-box 进程
if pgrep sing-box > /dev/null; then
  kill -9 $(pidof sing-box)
#  rm -rf /data/Box/src/*.db
  echo -e "\033[1;32mSB进程已清理并重启！\033[0m"
  /data/Box/sing-box run -c ./box.json -D /data/Box/
else
#  rm -rf /data/Box/src/*.db
  echo -e "\033[1;32mSB进程未启动，启动进程！\033[0m"
  /data/Box/sing-box run -c ./box.json -D /data/Box/
fi

# 01start.sh
```
