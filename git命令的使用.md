- git简介
    - git是一个分布式的代码版本控制工具，GitHub则是一个代码托管平台。
    - git可以理解为一个小型的数据库。可以本地使用，也可互联网使用。
    - git不但可以用于是代码，还可用于其他文件。意味着不要以为只有代码才可以使用git做版本控制。word、图片等都可以，虽然它们是二进制的。

- git存储阶段
    - git数据库分为3个存储阶段区域，利用这3各阶段可以实现代码修改的还原、回滚、保存。
        >  ||阶段名(US)|阶段名(ZN)|功能|
        >  |--|--|--|--|
        >  |阶段1|untrack|未追踪|只有加入追踪的文件，才可使用git还原等高级操作，初始建立的git仓库需追踪一下|
        >  |阶段2|stage|暂存态|准备进入阶段3提交阶段的文件，可使用此状态中的文件完成恢复，此状态的文件是可以随时改动的，以为着可以把喜欢的修改作为下次还原的基础|
        >  |阶段3|commit|提交态|在此阶段的代码可以用它还原，但是不能随时改动了，代码值得发布的状态就是一次commit|      
    - git状态转化
        - untrack --（git add）-> statge --（git commit）-> commit
        - untrack <--（git checkout）- statge <--（git reset)- commit


- git的命令行使用方法
    - 
    ```shell
    # 初始化个人信息以及配置
    $ git config [--global] 
    $ git config --global core.editor vim
    $ git config --global user.name liangsm
    $ git config --global user.mail 5XXXXXX@qq.com
    $ git config --global --list（查看）


    # 初始化建立git仓库
    $ cd MyNotes
    $ git init (建立git源信息隐藏目录和文件，来记录你的修改历史)

    # 查看此时git repository的状态
    $ git status

    # 使用git追踪当前的目录下的文件
    $ git add -A (或者 git add .)

    # 不追踪当前的目录下的文件（可先建立.gitignore后add）
    $ git rm --cached . -r(不追踪所有文件，可替换为某个文件)
    $ git

    # 从阶段2恢复文件
    $ git checkout -- sogou小鹤.ini

    # 使用git提交当前的目录下的文件
    $ git commit -m "2018-1-3 22:43:22，i think all is perfect" 

    # 使用commit完全、直接再现恢复目录下的文件，略过statge
    $ git reset --hard 节点号 （git reflog）

    # 使用commit完全再现某个文件，恢复到了stage区
    $ git reset 56e6b80953 sogou小鹤.ini
    $ git checkout -- sogou小鹤.ini 


    # 查看提交log
    $ git reflog (最详细的修改操作记录)
    $ git log --pretty=short
    $ git log --pretty=fuller (最详细的日志记录)
    $ git log --pretty=oneline
    

    # 如果你的仓库有东西并且和你要上传的本地git仓库不一致，会提示先pull再push
    $ git pull [远程仓库名] [本地仓库名]
    PS：当你的仓库唯一的时候默认可以直接git pull。仓库唯一的意思是git remote show唯一,一般把远程起名叫做 origin 

    # 上传本地分支到远程分支
    $ git push -u  [远程仓库名] [本地仓库名]

    # 查看所拥有的远程仓库
    $ git remote -v

    $ git pull origin master --allow-unrelated-histories
     ```