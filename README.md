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

### merge:

---

## 常用指令：

```bash
# 確認git版本/是否已安裝
$ git --version

# 開始管理此資料夾的專案
$ git init
```
