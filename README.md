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
discard changes in working directory // loại bỏ các thay đổi trong thư mục làm việc 
ví dụ

$git checkout -- README.md
// tương tự: $ git restore <file>
9. git reset
unstage // bỏ khỏi danh sách add 

$ git reset HEAD README.md
// hoặc dùng: $ git restore --staged <file>

-------------------------
10. git branch
dùng để xem có nhánh nào rồi :D

$ git branch
* master

11. git checkout -b <ten-branch>
khi ta làm 1 project ví dụ là 1 web đi thì nó có nhiều page : about, product ... thì khi viết 1 chức năng nào đó ta thường tạo nhánh mới để ko ảnh hưởng đến nhánh master và khi ta vừa lòng vs các thay đổi ở nhánh thì lúc đó ta sẽ ghép nhánh đó vs nhánh master --> đảm bảo master luôn là bản ngon nhất ko có lỗi gì 
ví dụ: cần thao tác vs chức năng file nào đó ta cần dùng git trên mà file thì là chưa add :D

$ git checkout -b feature/file-test
Switched to a new branch 'feature/file-test'

// câu lệnh trên đồng thời 2 lệnh : tạo nhánh mới và chuyển sang nhánh mới làm việc-checkout

$ git branch
* feature/file-test     // dấu * nè đang ở nhánh feature/file-test
  master

// cái nhánh mới và master đều chỉ đến commit cuối cùng lúc tạo ra
// giờ chuyển sang nhánh master làm việc nào :D
// các thay đổi cần commit mới chuyển nhánh dc

$ git checkout master
Switched to branch 'master'

mọi thay đổi ở file này lúc bên feature sang master đều biến mất
ở nhánh này khi log có thể xem các commit tại nhánh và bên master 
còn bên master chỉ có master thôi --> đảm bảo nhánh con ko ảnh hưởng đên nhánh chính. giờ thì cần hợp nhánh con vs chính nhé

12. git merge
giờ cần hợp B vào A
đầu tiên bạn phải ở A nếu chưa dùng checkout A, của mình đang ở feature thì mới viết đc cái này: 













