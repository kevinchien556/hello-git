# Git 練習專案

`此為 III MFEE20 的 git 上課筆記`

---

## 1.設定環境變數(使用者姓名與信箱)

```bash
$ git config --global user.name "輸入姓名"

$ git config --global user.email "輸入email"

# 確認設定內容
$ git config --list
```

設定檔路徑:~/.gitconfig

---

## 2.建立 repository/repo(存儲庫)

在想要被管理專案的資料夾路徑輸入指令:

```bash
$ git init
```

輸入完成後，資料夾內會多出 .git 檔案夾，存放 git 管理的資訊。

如果不想再被 git 管理，則刪除此檔案夾即可。

```bash
$ rm -r .git
```

![](https://i.imgur.com/iYbhwu4.png)

流程:檔案內容更動(工作目錄)後，用 add 加入暫存區域，再用 commit 加入儲存庫。

---

## 3.在 repo 中新增、修改、刪除檔案

```bash
# 查看git狀態(在哪個工作區域)
$ git status

# 檢視這次修改的差異(與repo內比較)
$ git diff

# 反悔修改(輸入後檔案回到上次repo版本)
$ git restore test.txt

# 將檔案(test.txt)加入/反悔加入暫存區域(要先新增或修改)
$ git add test.txt
$ git restore --stage test.txt


# 提交這次的修改(暫存區域內的檔案會被新增到repo)
$ git commit -m "填寫這次commit的資訊"

# 若檔案已經加入過，可以直接用以下指令(add+commit)
$ git commit -am "此次commit資訊"

# 讓檔案回復成特定版本
$ git checkout <commit> test.txt

# 檔案回復到前兩個版本
$ git checkout HEAD~2 test.txt

# 回到現在版本
$ git checkout HEAD test.txt

# 在 git中刪除檔案
$ git rm <file>

# 在硬碟中刪除檔案想反悔
$ git restore <file>

```

`git log` 相關指令:

```bash
# 查看提交紀錄
$ git log

# 查看特定檔案提交紀錄
$ git log <file>

# 查看檔案修改細節(每個版本的詳細刪減內容)
$ git log -p <file>

# 搜尋關鍵字
$ git log --grep="關鍵字"

#查看內容編寫者(顯示每行內文與其修改者)
$ git blame <file>

```

---

## 4.建立分支與合併

git 預設分支為 master，將更改其為 main:

```bash
$ nano ~/.gitconfig
```

```
[init]
        defaultBranch = main
```

已經是 master 的主分支可以執行以下指令改名其為 main:

```bash
$ git branch -m master main
```

分支指令:

```bash
# 檢視分支(* 是標註所在分支)
$ git branch

# 建立分支
$ git branch <分支名>

# 切換分支
$ git switch <分支名>
```

### merge

用法:在別的分支開發完功能並 commit 後，切換回主分支，merge 副分支。

`1.此時主分支會新增副分支內新增的內容，但副分支的內容不會更動。`

`2.若合併完出現視窗請你輸入原因並被鎖住，可以直接輸入 ":wq" 後按enter強制寫入。`

`3.若出現衝突要手動解掉，pull request時出現衝突的話先回副分支merge主分支後再push一次。`

```bash
$ git switch main

$ git merge <副分支>
```

---

## 5.在 github 上建立 repo

```bash
$ git remote add origin
$ git遠端repo的網址
```

- remote: 遠端
- add: 增加
- origin:遠端的名字(不建議修改)

```bash
$ git push -u origin main
```

推送程式碼到遠端，推到`origin`這個遠端，要推的分支是`main`。

---

## 6.Node.js

### 安裝 nodejs:

- Current: 最新的、目前的
- LTS: long-term support 長期維護版
  - Active LTS: 正在積極維護跟升級中的版本
  - Maintenance LTS: 維護中的 LTS 直到生命週期結尾
- EOL: end of life

```bash
# 列出可以安裝的版本
$ nvm ls-remote 14

# windows版本
$ nvm list available

# 安裝最新的 LTS(long-term support 長期維護版)
$ nvm install 14.17.6

# 切換版本
$ nvm use 14.17.6

# 確認目前 node 的版本
$ node -v

# 列出你電腦裡 node 的版本
$ nvm ls
# windows 用 list
$ nvm list

# 設定預設版本
$ nvm alias default 14.17.6
```

---

## 7.寫第一個 nodejs 程式

1.在 github 上建立專案(ex:hello-node)

2.找到這個專案的 url，在 home 目錄下 clone 這個專案

```bash
$ cd ~
$ git clone <url>
```

3.用 vs code 開啟專案資料夾，建立 practice 資料夾

4.在 practice 內建立 sum.js

5.測試結果

```bash
$ cd practice
$ node sum.js

# 不切換資料夾
$ node practice/sum.js
```

## 補充

### 參考資料

- [Git 10 週年，Linux 之父談他是怎麼在 10 天內開發完成](https://buzzorange.com/techorange/2015/04/09/linus-torvalds-talked-about-git/)
- [22 歲開發出 Linux 的 FullStack 天才：Linus Torvalds 的故事](https://www.techapple.com/archives/19224)

- [Git 與 Github 版本控制基本指令與操作入門教學](https://blog.techbridge.cc/2018/01/17/learning-programming-and-coding-with-python-git-and-github-tutorial/)

---

## 常用指令：

```bash
# 切換目錄
$ cd 資料夾名

# 顯示目前路徑
$ pwd

# 列出目前資料夾內檔案
$ ls

# 列出目前資料夾內檔案(包含隱藏的/完整格式/綜合)
$ ls -a
$ ls -l
$ ls -al

# 建立新資料夾
$ mkdir 新資料夾

# 建立新檔案
$ touch new.txt

# 複製/移動/刪除檔案
$ copy/mv/rm

# 清除畫面
$ clear

#印出檔案內容/編輯文字檔
$ cat/nano test.txt

```
