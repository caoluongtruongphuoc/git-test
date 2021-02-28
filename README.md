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
$ git checkout master  // từ dòng này là đã merge
$ git merge feature/file-test
Updating 60637b5..f5a5c75
Fast-forward
 README.md     | 48 ++++++++++++++++++++++++++++++++++++++++++++++--
 file-test.txt |  1 +
 2 files changed, 47 insertions(+), 2 deletions(-)

// status
commit f5a5c7514448405e1a22b80ada6cc3d51d5ce28f (HEAD -> master, feature/file-test)
Author: caoluongtruongphuoc <caophong8991@gmail.com>
Date:   Sat Feb 27 12:22:08 2021 +0700

    update file readme line:210 ->  219
// cmt hơi sai nhưng ok, giờ master chứa tất cả các commit của bên feature/file-test :D
// giờ hợp nhất rồi thì branch kia có thể thừa nếu bạn ko dùng và muốn xóa đi

13. git branch -D <ten-branch>

// giờ đang có :
$ git branch
  feature/file-test
* master

//sau đó
$ git branch -D feature/file-test
Deleted branch feature/file-test (was f5a5c75).

$ git branch
* master

-------------------------
14. các chi tiết vể git reset
git reset --soft <to_id_commit>
git reset --mixed <to_id_commit>
git reset --hard <to_id_commit>
// mục đích commit nào ko vừa ý thì dùng lệnh quay lại
chẳng hạn bạn vừa commit số 3 
và như ngăn xếp như sau : 3 2 1
bạn muốn hủy commit số 3 vừa xong thì 
$ git reset --soft <id_commit số 2>
còn commit số 1 quay về staging area
$ git reset --mixed <id_commit số 2>
thì commit số 1 quay về working directory
$ git reset --hard <id_commit số 2> 
thì quay về hẳn số 2 luôn, mọi thay đổi về sau biến mất 

--------------------------
15. git revert <commit>
ý nghĩa hoàn lại trạng thái trc đó
chẳng hạn bạn vừa viết dòng ko vừa ý
dùng lệnh xóa dòng đó 
thế khác j reset ??
cái này bạn có thể hoàn nguyên lại cách vài commit trong quá khứ chứ ko phải chỉ commit mới nhất

lệnh này sẽ tạo commit mới và hoàn nguyên code

thế thì tốt nhất là sửa và tạo commit mới là tốt nhất

16. .gitignore

như tên git phớt lờ :D
file này sẽ có trong project của bạn mục đích đặt các file muốn untrack vào
các thay đổi vs git sẽ bỏ qua file nè : git status ko hiện nữa :D
giờ tạo 2 file 
test-gitignore.txt và .gitignore
//
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        test-gitignore.txt

no changes added to commit (use "git add" and/or "git commit -a")

giờ bạn ko muốn test-gitignore.txt trong repo của mình thì vào 
.gitignore và gõ : test-gitignore.txt thế là xong
// đó thấy chưa 
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

no changes added to commit (use "git add" and/or "git commit -a")

// nên ignore khi chưa commit bao giờ ko thì fix mệt 

--------------------------
đó bấy h ta mới thao tác trên local repo 
giờ cần up lên remote repo
$ git remote add origin https://github.com/caoluongtruongphuoc/git-test.git
để kêt nối vs remote repo
// chi tiết ?? 
$ git remote -v
origin  https://github.com/caoluongtruongphuoc/git-test.git (fetch)
origin  https://github.com/caoluongtruongphuoc/git-test.git (push)

// nếu đã từng push rồi thì 
$ git push
nếu mà lần đầu thì có lỗi
$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master

// nếu lần đầu 
$ git push -u origin master
thì 
$ git push -u origin master
Enumerating objects: 38, done.
Counting objects: 100% (38/38), done.
Delta compression using up to 4 threads
Compressing objects: 100% (33/33), done.
Writing objects: 100% (38/38), 6.58 KiB | 374.00 KiB/s, done.
Total 38 (delta 10), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (10/10), done.
To https://github.com/caoluongtruongphuoc/git-test.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
----------------------------------------
// nếu lần đầu tham gia vào dự án bạn cần tải toàn bộ thì dùng
$ git clone 

// nếu bạn đã clone rồi và cần cập nhật dùng 
$ git pull

-----------------------------------------
pull request (pull - kéo | push - đẩy)
qui trình lm vc trong team 
1. git checkout -b <feature_branch> // trc khi vào việc đc giao tạo nhánh mới nhé sau đó hẵng làm gì thì lm
2. git push origin <branch> // lm các kiểu rồi thì branch vẫn chỉ tại local thôi giờ push nó lên github luôn
3. create a  pull request on GitHub
4. review code
5. merge to master
















