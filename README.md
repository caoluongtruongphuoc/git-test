1. git init:

$ git init // tại thư mục project mới

2. git status
xem trạng thái của project, ví dụ: 

$ git status
On branch master // trên nhánh master

No commits yet // chưa commit nào

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md 	// file này chưa đc add
 
nothing added to commit but untracked files present (use "git add" to track)

3. git add
dùng để add các file vào tracked để commit : từ work dir -> staging area 

$ git add . // add tất
// dùng git status kiểm tra lại xem ok chưa nhé

$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md 	// đã add đc rồi nè

4. git commit
dùng để cho các file từ staging area -> committed đại khái chỉ commit rồi mới push lên github đc :D

$ git commit -m 'git-test hướng dẫn các kiểu cho newbie'
// bash: $'\302\226\302\226git': command not found // thấy bảo do copy giờ gõ lại trên window
và kết quả : // shift + insert

$ git commit -m 'git-test hướng dẫn các kiểu cho newbie'
[master (root-commit) 26e1ec8] git-test hướng dẫn các kiểu cho newbie
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md

// đã thêm thành công rồi, giờ kiểm tra
$ git status
On branch master
nothing to commit, working tree clean

// giờ làm thế nào biết mình đã commit cái gì ?? bên dưới nà

5. git log
xem lịch sử commit

$ git log
commit 26e1ec8c7e5e5f9ab596023bb933b0ac659f6e87 (HEAD -> master)  
Author: caoluongtruongphuoc <caophong8991@gmail.com>
Date:   Fri Feb 26 13:49:03 2021 +0700

    git-test hướng dẫn các kiểu cho newbie

// cái cuối cùng commit thì ở head kiểu ngăn xếp, cái chuỗi  sau chữ commit kiểu id xác định commit nào

6. git show
dùng id commit trên để xem chi tiết commit cái gì 

$ git show 26e1ec8c7e5e5f9ab596023bb933b0ac659f6e87
commit 26e1ec8c7e5e5f9ab596023bb933b0ac659f6e87 (HEAD -> master)
Author: caoluongtruongphuoc <caophong8991@gmail.com>
Date:   Fri Feb 26 13:49:03 2021 +0700

    git-test hướng dẫn các kiểu cho newbie

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..e69de29

// đó là tạo file 
----------------------------------------------------------
giờ sửa file này :D mình nhập đến đây chưa Ctrl + S nên file chưa cập nhật
giờ cập nhật rồi sau đó status nhé 

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

// đó modified màu đỏ kìa giờ ta cần xem có thay đổi gì thì dùng git diff

7. git diff

$ git diff
diff --git a/README.md b/README.md
index e69de29..bdf5b31 100644
--- a/README.md
diff --git a/README.md b/README.md
index e69de29..bdf5b31 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1,89 @@
+1. git init:
+
+$ git init // tại thư mục project mới
+
+2. git status
+xem trạng thái của project, ví dụ:
+
+$ git status
+On branch master // trên nhánh master
+
+No commits yet // chưa commit nào
+
+Untracked files:
+  (use "git add <file>..." to include in what will be committed)
+        README.md      // file này chưa đc add
+
+nothing added to commit but untracked files present (use "git add" to track)
+
:
// vân vân....... nhấn Q để thoát
// giờ vì file có thay đổi á nên cần add lại lần nữa
// dùng git add . cho nhanh rồi dùng status kiểm tra

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
// chữ modified màu lục rồi nhé là ok rồi  giờ commit nũa
 
$ git commit -m 'update readme'
[master 561fc3f] update readme
 1 file changed, 89 insertions(+)

// rồi đó giờ xem log nhé
$ git log
commit 561fc3f706904bf5be68852e0222873f1295ab48 (HEAD -> master)
Author: caoluongtruongphuoc <caophong8991@gmail.com>
Date:   Fri Feb 26 14:07:42 2021 +0700

    update readme

commit 26e1ec8c7e5e5f9ab596023bb933b0ac659f6e87
Author: caoluongtruongphuoc <caophong8991@gmail.com>
Date:   Fri Feb 26 13:49:03 2021 +0700

    git-test hướng dẫn các kiểu cho newbie

// giờ tạo file test mới trong thư mục rồi -->add --> commit nhé
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
        new file:   file-test.txt

$ git commit -m 'add file-test.txt and update readme'
[master fbc0a8d] add file-test.txt and update readme
 2 files changed, 57 insertions(+)
 create mode 100644 file-test.txt

$ git status
On branch master
nothing to commit, working tree clean

8. git checkout
dùng để làm bỏ phần vừa thay đổi mà chưa commit
ví dụ

$git checkout -- README.md

9. git reset








