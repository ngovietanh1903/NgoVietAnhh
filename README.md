Nhập Môn Công Nghệ Thông Tin
Bài: Kiểm soát phiên bản với GitHub
GitHub là gì?
GitHub.com là trang web lưu trữ trực tuyến các kho lưu trữ Git.
Nhiều dự án nguồn mở sử dụng nó, chẳng hạn như hạt nhân Linux.
Bạn có thể nhận được không gian miễn phí cho các dự án nguồn mở hoặc bạn có thể trả tiền cho các dự án riêng tư.
Câu hỏi: Tôi có phải sử dụng GitHub để sử dụng Git không?
Trả lời: KHÔNG!
Bạn có thể sử dụng Git hoàn toàn cục bộ cho mục đích của riêng bạn hoặc
Bạn có thể sử dụng dịch vụ khác như GitLab (GitLab.com)
Tài nguyên Git
GitHub.com là trang web lưu trữ trực tuyến các kho lưu trữ Git.
Tại dòng lệnh: (nơi <verb> = config, add, commit, v.v.)
 	$ git help <verb> 
	$ git <verb> --help 
	$ man git-<verb>

Sách trực tuyến miễn phí: https://git-scm.com/book/en/v2
Trang web Git: http://git-scm.com/
Lịch sử Git
Xuất phát từ cộng đồng phát triển Linux
Linus Torvalds, 2005
Mục tiêu ban đầu:
Tốc độ
Hỗ trợ phát triển phi tuyến tính (hàng ngàn nhánh song song)
Phân phối đầy đủ
Có khả năng xử lý các dự án lớn như Linux một cách hiệu quả
Cách sử dụng Git
Máy chủ có thể:
GitHub
GitLab
Qui trình làm việc
Modify files in your working directory.Stage files, adding snapshots of them to your staging area.
Do  a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory (your local copy of the repo).
 Notes:
If a particular version of a file is in the git directory, it’s considered committed. 
If it’s modified but has been added to the staging area, it is staged. 
If it was changed since it was checked out but has not been staged, it is modifie!)
Sẵn sàng sử dụng Git! 
Set the name and email for Git to use when you commit:$ git config --global user.name “Mai Xuan Trang”$ git config --global user.email trangmx@gmail.com
You can call git config --list to verify these are set.
These will be set globally for all Git projects you work with.
You can set variables on a project-only basis by not using the --global flag.
The latest version of Git will also prompt you that push.default is not set, you can make this warning go away with:$ git config --global push.default simple
You can also set the editor used for writing commit messages (default = vim):$ git config --global core.editor emacs
Lệnh Git
Thêm & Commit các tệp tin
The first time we asked a file to be tracked, and everytime before we commit a file we must add it to the staging area. This can be done with the following command
$ git add file1.txt file2.txt
This takes a snapshot of the files and adds it to the staging area. You can still modify files in the working directory, but you will need to add again to have these changes saved in the staging area.
Note: To unstage a change, you can use the following
$ git reset HEAD filename
To move staged changes into the local repository we commit them from the staging area
$ git commit -m “Updated filename”
Note: All of these commands are acting on the local copy of your repository. You will need to push them to remote to see these changes elsewhere.
Trạng thái và sự khác biệt
Để xem trạng thái của các tập tin của bạn trong thư mục làm việc Và khu vực staging:
$ git status		or 
$ git status –s  
 (-S hiển thị phiên bản một dòng ngắn)
Để xem sự khác biệt giữa bạn thư mục làm việc và khu vực staging
$ git diff
Để thấy sự khác biệt giữa khu vực staging và bản sao cục bộ của kho lưu trữ:
$ git diff --cached
Sau khi chỉnh sửa một tập tin
$emacs rea.txt
$git status
# Trên nhánh master
# Changes not staged for commit:
# (sử dụng "git add <tệp>..." để cập nhật những gì sẽ được commit)
# (sử dụng "git checkout -- <file>..." để hủy bỏ các thay đổi trong thư mục làm việc)
#
# modified:   rea.txt
#
no changes added to commit (use "git add" and/or "git commit -a") 
$ git status -s
M rea.txt	 Note: M is in second column = “working  tree”
$ git diff		 Shows modifications that have not been staged.
diff --git a/rea.txt b/rea.txt
Index 66b293d..90b65fd 100644
--- a/rea.txt
+++ b/rea.txt
@@ -1,2 +1,4 @@
Here is rea's file.
+
+One new line added.
$ git diff --cached 	  Shows nothing, no modifications have been staged yet. 
Sau khi đưa một tệp tin vào vùng staging
Xem nhật ký
Để xem nhật ký của tất cả các thay đổi trong kho lưu trữ cục bộ:
	$ git log	hoặc	 
	$ git log –-oneline (để hiển thị phiên bản ngắn hơn)

1677b2d Đã chỉnh sửa dòng đầu tiên của readme
258efa7 Đã thêm dòng vào readme
0e52da7 Cam kết ban đầu
git log -5 (chỉ hiển thị 5 bản cập nhật gần đây nhất, v.v.)  

Lưu ý: các thay đổi sẽ được liệt kê theo commitID #, (SHA-1 hash)
Lưu ý: những thay đổi được thực hiện đối với kho lưu trữ từ xa trước lần cuối bạn sao chép/kéo từ kho lưu trữ đó cũng sẽ được bao gồm ở đây
Kéo và đẩy
Thực hành tốt:
Add và Commit những thay đổi của bạn đối với kho lưu trữ cục bộ của bạn
Pull từ kho lưu trữ từ xa để lấy những thay đổi gần đây nhất (sửa xung đột nếu cần, thêm và cam kết chúng vào kho lưu trữ cục bộ của bạn)
Push những thay đổi của bạn đối với kho lưu trữ từ xa

Để lấy các bản cập nhật mới nhất từ ​​kho lưu trữ từ xa vào kho lưu trữ cục bộ của bạn và đưa chúng vào thư mục làm việc của bạn:
$ git pull origin master
Để đẩy những thay đổi của bạn từ kho lưu trữ cục bộ sang kho lưu trữ từ xa:
$ git push origin master

Ghi chú: origin = một bí danh cho URL bạn đã sao chép từ
 	   master = nhánh từ xa mà bạn đang kéo từ/đẩy tới, (chi nhánh cục bộ mà bạn đang kéo tới/đẩy ra là chi nhánh hiện tại của bạn)
Tránh các vấn đề thường gặp
Không chỉnh sửa kho lưu trữ (thư mục .git) theo cách thủ công. Nó không được thiết kế để con người có thể sửa đổi.
Cố gắng không thực hiện nhiều thay đổi lớn cùng một lúc. Thay vào đó, hãy thực hiện nhiều lần commit, mỗi lần có một mục đích logic duy nhất. Điều này sẽ giảm thiểu xung đột hợp nhất. 
Luôn luôn git pull trước khi chỉnh sửa một tệp. Rất dễ quên điều này. Nếu bạn quên, bạn có thể sẽ chỉnh sửa một phiên bản lỗi thời, điều này có thể gây ra xung đột hợp nhất khó chịu.
Đừng quên git push sau khi bạn đã thực hiện và cam kết thay đổi. Chúng không được sao chép vào kho lưu trữ từ xa cho đến khi bạn thực hiện push. 
Phân nhánh
Để tạo một nhánh có tên là thử nghiệm:
	$ git branch experimental

Để liệt kê tất cả các nhánh: (* hiển thị nhánh bạn hiện đang ở)
	$ git branch

Để chuyển sang nhánh thử nghiệm:
	$ git checkout experimental

Sau đó, những thay đổi giữa hai nhánh sẽ khác nhau để hợp nhất những thay đổi từ nhánh thử nghiệm vào nhánh chính:
	$ git checkout master
	$ git merge experimental

Ghi chú: git log -- graph có thể hữu ích để hiển thị các nhánh.
Lưu ý: Các nhánh này nằm trongkho lưu trữ cục bộ của bạn!
Tom tat
Bạn *sẽ* sử dụng phần mềm kiểm soát phiên bản khi làm việc trên các dự án, cả ở đây và trong ngành
Lời khuyên: chỉ cần thiết lập một kho lưu trữ, ngay cả đối với các dự án nhỏ, nó sẽ giúp bạn tiết kiệm thời gian và công sức
Rather foolish not to





















