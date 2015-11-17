# ������� �������� ������ Git

���������� �� ��������� git [������ �� �����](http://habrahabr.ru/post/60347/)


### 1. ������� �������

**`git help commandName`** &ndash; ������� git �������  

**`git status`** &ndash; ������ git [ ������� �������� ]  
**`git status --untracked-files=all`** &ndash; �������� ��� untracked-files  

**`git init`** &ndash; ����� �����������


### 2. �������� ������������

**`git config --list`** &ndash; ������ ���� ��������  

**`git config --global user.name "Vladyslav Krasovsky"`** &ndash; ���������� ��������� ����� ������  
**`git config --global user.email "v.o.krasovsky"`** &ndash; ���������� ��������� email ������  

**`git config --global core.editor "'D:\Soft\Portable\ST3\sublime_text.exe' -multiInst -notabbar -nosession -noPlugin"`** &ndash; ���������� ��������� ��������� ������������  

**`git config --global merge.tool kdiff3`** &ndash; ���������� ��������� ������� ������� �����  
**`git config --global mergetool.kdiff3.cmd '"C:\\Program Files\\KDiff3\\kdiff3" $BASE $LOCAL $REMOTE -o $MERGED'`** &ndash; ���������� ��������� ���� �������  

**`git config --global push.default matching`** &ndash; ���������� ��������� ��� push  

**`git config --system core.autocrlf false`** &ndash; ����������: warning: LF will be replaced by CRLF


### 3. �����

**`git add .`** &ndash; ���������� ���� ������ � ������  
**`git add fileName`** &ndash; ���������� ����� � ������  
**`git add "*.php"`** &ndash; ���������� ���� php ������ � ������  

**`git rm --chached fileName`** &ndash; �������� ����� �� �������  
**`git rm -r --cached folderName`** &ndash; �������� ����� (����������) ����� ������� ���  
**`git rm --cached fileName`** &ndash; �������� ����� �� git-����������� ��� ��� ����������� ��������  


### 4. ���������� �������

**`git commit -a -m"comment"`** &ndash; ������ ���� ������, � ������������  
**`git commit -m"comment"`** &ndash; ������ ������������������ ������ + �������  

**`git reset`** &ndash; ������� � ������������� �������, ����� ���������, �������� ��� �������  
**������:**
```
	1. git commit� � ������������ ������; 
	2. git reset --soft HEAD^ � ��������� � ������ ��� ��� ����������� ��������, �������� ��� ��������� ������� � ������������������ ����� 
	3. edit WRONGFILE 
	4. edit ANOTHERWRONGFILE 
	5. add.
	6. git commit -c ORIG_HEAD � �������� � ���������� �������, ����� ���������� ������������� ��� ���������. ���� ��������� �������� �������, �� ���������� �������� ������� ����� -�:
	7. git commit -C ORIG_HEAD
```


### 5. ������ � �������

**`git checkout -- fileName`** &ndash; ����� untracked �����, �� ��������� �� �����������  
**`git checkout -b new_f`** &ndash; �������� ����� ����� � ������� � ���  
**`git checkout branchName`** &ndash; ������������� �� �����  

**`git branch`** &ndash; �������� �����  
**`git branch new_f2`** &ndash; �������� ����� �����  
**`git branch -v`** &ndash; ��������� �������� �����  

**`git merge branchName`** &ndash; ������� ����� [ ������� ��������� ����� � ������� ]  
**`git mergetool`** &ndash; ����� ������� ������� ����� [ ���� ����-������� �� ���������� ]


### 6. ����

**`git log`** &ndash; ������� �������� [ ����� �� ������� - ������� Q ]  
**`git log --pretty=format:"%h - %an, %ar : %s"`** &ndash; ������� �������� � �������� �������  
**`git log --since=2.weeks`** &ndash; ������� �������� �� 2 ������  
**`git log -p -2`** &ndash; �������� ��������� � 2 ��������


### 7. ��������� �����������

**`git remote -v`** &ndash; ��������� �����������  
**`git remote add origin https://kros16@bitbucket.org/kros16/lider.git`** &ndash; ���������� ������ ����������� [*remote* - ���������; *origin* - ��������]  

**`git push -u origin master`** &ndash; �������� ��� ����������� ��������� � ����������� *origin* ����� *master* [ -u ]  
**`git push -u origin --all`** &ndash; pushes up the repo and its refs for the first time  
**`git push -u origin --tags`** &ndash; pushes up any tags  

**`git fetch`** &ndash; �������� ��������� ��������� �� ����������� (�� ���������)  
**`git pull`** &ndash; �������� ��������� ��������� �� ����������� � ����������

* * *
&copy; <v.o.krasovsky@gmail.com>, 2015 