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







