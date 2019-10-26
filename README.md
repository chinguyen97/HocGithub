# Git for Windows

[I. Giới thiệu về Git](#gioithieuvegit)

[1. Khái niệm](#khainiem)

[2. Tại sao nên dùng Git](#taisaonendunggit)

[3. Flow cơ bản của Git](#flowcobancuacuagit)

[II. Hệ thống câu lệnh trong Git](#hethongcaulenhtronggit)

[2.1. Git status, git init](#gitstatus,gitinit)

[2.2. Git add](#gitadd)

[2.3. Git commit](#gitcommit)

[2.4. Git push](#gitpush)

[2.5. Git clone](#gitclone)

[2.6. Git branch](#gitbranch)

[2.7. Git stash](#gitstash)

[2.8. Git fetch](#gitfetch)

[2.9. Git pull](#gitpull)

[2.10. Git diff](#gitdiff)

[2.11. Một số câu lệnh khác](#motsocaulenhkhac)

[III. Kết luận](#ketluan)
***************

<a name="gioithieuvegit"></a>
## I. Giới thiệu về Git
<a name="khainiem"></a>
### 1.1. Khái niệm 
**Git** là 1 trong những Hệ thống quản lý phiên bản phân tán (Distributed Version Control System – DVCS)
 phổ biến nhất hiện nay, giúp mỗi máy tính có thể lưu trữ nhiều phiên bản 
 khác nhau của một mã nguồn được clone từ repository 
 chứa mã nguồn, mỗi thay đổi vào mã nguồn trên máy tính sẽ có thể 
 commit rồi đưa lên máy chủ nơi đặt kho chứa chính. 
 Người dùng khác cũng có thể clone lại mã nguồn từ kho chứa 
 hoặc clone lại một tập hợp các thay đổi mới nhất trên máy tính kia.  
 
 Git hỗ trợ trên nhiều Hệ điều hành Windows, Macs, Linux.
 
 Bài viết này mình sẽ tìm hiểu trên hệ điều hành Windows
 
<a name="taisaonendunggit"></a>
### 1.2. Tại sao nên dùng Git?
- Việc tách nhập các nhánh trong SVN là rất khó khăn do xung đột 
trong quá trình tách nhập, với Git thì việc này trở nên thật dễ dàng.
- Tốc độ thực hiện nhanh hơn.
- Dễ sử dụng, an toàn, thuận tiện.
- Size của local repository nhỏ.
- ....

<a name="flowcobancuagit"></a>
### 1.3.  Flow cơ bản của Git
Để hiểu được flow của Git cần nắm rõ 1 số khái niệm.
- **Repository**: Là nơi chứa source code, lịch sử thay đổi, nội dung thay đổi 
của từng cá nhân tác động vào project.
	- Dữ liệu trong Repo chứa trong 1 folder ẩn có tên .git
	- Repo chia thành 2 loại Local Repository và Remote Repository
		- Local Repository : Là kho chứa trên máy tính cá nhân 
		- Remote Repository : Là kho chứa một máy chủ từ xa
- **Remote**: Server online.
- **Local**: server local trên máy 
- **Working copy**: Nơi làm việc trực tiếp trên máy local

**Sau đây là flow cơ bản của Git**
- Clone project từ server về local
- Bạn sẽ sửa đổi tại Working Space 
- Add: Xác nhận sợ thay đổi và đưa lên Staging Are 
- Commit: Lưu các thay đổi từ thư mục đang làm việc (working coppy) 
vào server local (local repo)

Nếu bạn muốn cập nhật sự thay đổi này lên server thì dùng lệnh push

<a name="hethongcaulenhtronggit"></a>
## II. Hệ thống câu lệnh trong Git

Cần phân biệt rõ Git là công cụ để quản lý source code, Github là nơi để chứa code.

Trước tiên bạn cần đăng ký 1 tài khoản Github trên https://github.com/ .

Cần ghi nhớ 2 thông tin: **username, email, pasword**.

Tạo 1 Repo trên Github 

Tiếp theo download Git https://git-scm.com/downloads. Băt đầu cài đăt Git.

Để kiểm tra Git đã cài đặt thành công chưa bạn dùng câu lệnh `git --version`

![version](https://github.com/chinguyen97/HocGithub/blob/master/images/version.png)

Hiện mình cài version 2.19.2

**Cấu hình đồng bộ git và github**

Git hỗ trợ 3 tuỳ chọn là –global, –system, –local. 
Tuy nhiên, thường chọn –global.
```
git config --global user.name = "username"

git config --global user.email = "email"
```

Vậy là Git đã được cài đặt thành công và đồng bộ với Github của bạn.

<a name="gitstatus,gitinit"></a>
### 2.1 Git status, git init
Bạn hãy tạo một thư mục mới để git làm việc với thư mục này.

Để check status của project sử dụng câu lệnh 

```
git status
```

Tạo một folder ẩn có tên `.git` vào thư mục đã tạo, đó là những repo cần thiết 

``` 
git int
```
<a name="gitadd"></a>
### 2.2. Git add
Sau khi thực hiện thay đỏi source code. Bạn cần phải cập nhật nó lên Staging Area.

Cập nhật tất cả các file trong floder.

```
git add .
```

Hoặc 
```
git add *
```

Cập nhật 1 file mà bạn muốn.

```
git add "name file"
```
<a name="gitcommit"></a>
### 2.3. Git commit
Sau lệnh `git add`, bạn cần sử dụng lệnh commint để đẩy thông tin thay đổi lên Local Repo.
```
git commit --m "message"
```
Hai lệnh `git add` và `git commit` có thể gộp thành lênh:
```git commit -a --m "message"```
<a name="gitpush"></a>
### 2.4 Git push 
Sau lệnh commit, thông tin đang ở Local Repo, muốn cập nhật lên sever 
thì bạn phải dùng câu lệnh push:
```
git remote add <tên project cần push><url>

git push <tên project cần push>

git push --set -upstream Gitproject master 
```

<a name="gitclone"></a>
### 2.5. Git clone
Câu lệnh Git này dùng để copy 1 project từ Local Respository đến một thư mục khác, 
hoặc từ server về máy tính của bạn.

Để clone một project từ Local Respository trên máy:
```
git clone/path/to/repository
```
Để clone một project trên server, bạn có thể sử dụng https hoặc ssh:
```
git clone "url"
```

<a name="gitbranch"></a>
### 2.6. Git branch 
Trong 1 dự án có nhiều người cùng làm, mỗi người đảm nhiệm 1 công việc khác nhau,
Khi đó bạn có thể tạo nhiều nhánh khác nhau mỗi người làm 1 nhánh của mình.
Mặc định ban đầu bạn ở nhánh master. 

- Để kiểm tra nhánh hiện tại dùng lệnh

``` 
git branch
```

- Để tạo một nhánh mới:
```
git branch <name_branch>
```
- Để chuyển và tạo mới 
```
git branch -b <name_branch>
```

<a name="gitfetch"></a>
### 2.7. Git fetch
Câu lệnh này dùng để lấy source code từ server về Local Repo
``` 
git fetch <name_branch>
```
<a name="gitpull"></a>
### 2.8. Git full
Câu lệnh này dùng dể lất source code từ server về Working Space 

<a name="gitdiff"></a>
### 2.9. Git diff

- Xem những thay đổi khi chưa add
```
git diff
```
- Xem thay đổi khi đã add, chưa commit
```
git diff --cached
```
- Xem thay đổi giữa 2 lần commit
```
git diff commit1_ID commit2_ID
```

<a name="motsocaulenhkhac"></a>
### 2.10. Một số câu lệnh khác

- Câu lệnh trợ giúp
```
git config --help
```

hoặc
```git help config```

- Xem lịch sử commit 
```
git log
```
- Xem commit history cho hai commits gần nhất

```
git log -2
```
- Xem commit history cho hai commits gần nhất, bao gồm cả thay đổi

```git log -p -2```

- Xem thông tin cụ thể của một lần commit

```
git show commit_ID
```

- Liệt kê các settings đang sử dụng:

```
git config --list
```

- Đổi message của commit cuối

```
git commit --amend -m "New commit massage"
```
- Revert một commit rồi push

```
git revert commit_ID

git push origin master
```

<a name="ketluan"></a>
## III. Kết luận
Git là một công cụ tuyệt vời cho tất cả mọi người, đặc biệt làm việc 
với sourcecode, làm việc nhóm,...Lợi ích mà Git đem lại vô cùng to lớn. 

Trên đây là kiến thức mình tìm hiểu được về Git. Mong nhận được sự góp ý của cộng đồng.


***Tài liệu tham thảo***
[1]: https://github.com/hocchudong/git-github-for-sysadmin

[2]: http://rogerdudler.github.io/git-guide/index.vi.html

