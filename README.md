# Linux_learn_grep
grep 搜尋檔案內容
1. 基本使用
@ : grep 關鍵字 檔案1 檔案2 ...
2. grep 亦可搭配萬⽤字元（ * ）同時搜尋多個檔案，
例如在 /etc/ ⽬錄之下所有 *.conf 檔案中，尋找 network 這個字眼
@ : grep network /etc/*.conf

常用 參數
---
grep -i 不區分大小寫

grep -v 排除條件顯示

grep -l 顯示符合的檔名

grep -n 顯示條件在第幾行

grep -q 顯示 0 , 1 ( 檢查 $? , 0 is successful ) 

grep -a 查看 binary 檔 (轉文字模式)

找出字詞是 1 byte 以上 ( 中文 , 日文 ... 等 )
---

```Bash
grep -P -aobn '[^\x00-\x7F]'
```
![image](https://user-images.githubusercontent.com/96226780/201519901-86548d2a-21d3-4f4a-b5e2-d4f831904b97.png)

找出 ORACLE tnsnames.ora 對應 HOST 資訊
---

```Bash
grep -A 10 "topprd" $ORACLE_HOME/network/admin/tnsnames.ora | 
sed -n '/ADDRESS/, /ADDRESS/p' | grep HOST | 
awk -F 'HOST =' '{print $2}' | awk -F ')' '{print $1}' | 
sed -n '1,1p'
```

ls -ltr `grep -l -i 123 *`
