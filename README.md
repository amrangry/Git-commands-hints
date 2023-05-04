# Git-commands-hints



#### git
```ruby
using to generate .gitignore file 
https://www.gitignore.io/
```

f you committed these files to git even once, it won't help to add gitignore later, you need to untrack those files from git (on any pc that deals with this git)
git rm --cache */UserInterfaceState.xcuserstate
and repeat for all files you wish to ignore (you should never ignore pbxproj though this is critical file)
commit, push and your problem will be solved


```ruby
master git 

1- https://medium.freecodecamp.org/what-is-git-and-how-to-use-it-c341b049ae61

2- https://medium.freecodecamp.org/how-to-become-a-git-expert-e7c38bf54826

Create the branch on your local machine and switch in this branch :
$ git checkout -b [name_of_your_new_branch]

Change working branch :
$ git checkout [name_of_your_new_branch]


Push the branch on github :
$ git push origin [name_of_your_new_branch]


You can see all branches created by using :
$ git branch

Add a new remote for your branch :
The remote branch is automatically created when you push it to the remote server. So when you feel ready for it, you can just do:

git push <remote-name> <branch-name> 

Where <remote-name> is typically origin, the name which git gives to the remote you cloned from. Your colleagues would then just pull that branch, and it's automatically created locally.


After that, you can work locally in your branch, when you are ready to share the branch, push it. The next command push the branch to the remote repository origin and tracks it

git push -u origin your_branch
Teammates can reach your branch, by doing:

git fetch
git checkout origin/your_branch

You can continue working in the branch and pushing whenever you want without passing arguments to git push (argumentless git push will push the master to remote master, your_branch local to remote your_branch, etc...)

git push


Push changes from your commit into your branch :
$ git push [name_of_your_new_remote] [name_of_your_branch]

Update your branch when the original branch from official repository has been updated :
$ git fetch [name_of_your_remote]

Then you need to apply to merge changes, if your branch is derivated from develop you need to do :
$ git merge [name_of_your_remote]/develop

Delete a branch on your local filesystem :
$ git branch -d [name_of_your_new_branch]

To force the deletion of local branch on your filesystem :
$ git branch -D [name_of_your_new_branch]

Delete the branch on github :
$ git push origin :[name_of_your_new_branch]



More Ref
  https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches


Setting your branch to exactly match the remote branch can be done in two steps:

git fetch origin
git reset --hard origin/master


resets to the last committed state. In this case HEAD refers to the HEAD of your branch.
git reset --hard HEAD 



refresh new .git file for new user 

rm -rf .git

or 

git init for fresh one 

merg commit from terminal 
Simply doing the vim "save and quit" command :wq should do the trick.



Create a new repository
git clone https://Amr.Elghadban@git.itworx.com/mobility/PeopleSearch.git
cd PeopleSearch
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

Existing folder
cd existing_folder
git init
git remote add origin https://Amr.Elghadban@git.itworx.com/mobility/PeopleSearch.git
git add .
git commit -m "Initial commit"
git push -u origin master

Existing Git repository
cd existing_repo
git remote add origin https://Amr.Elghadban@git.itworx.com/mobility/PeopleSearch.git
git push -u origin --all
git push -u origin --tags
```
#### How to get specific pod repo 
```ruby

   To use a different url of the repo:
   pod 'Alamofire', :git => 'https://github.com/Alamofire/Alamofire.git'

    To use a different branch of the repo:
    pod 'Alamofire', :git => 'https://github.com/Alamofire/Alamofire.git', :branch => 'dev'

    To use a tag of the repo:
    pod 'Alamofire', :git => 'https://github.com/Alamofire/Alamofire.git', :tag => '3.1.1'

    Or specify a commit:
    pod 'Alamofire', :git => 'https://github.com/Alamofire/Alamofire.git', :commit => '0f506b1c45'
   
```

#### The Gitflow Workflow
##### The Gitflow Workflow defines a strict branching model designed around the project release. 
###### made popular by Vincent Driessen at nvie. https://nvie.com/posts/a-successful-git-branching-model/
###### tutorials https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
```ruby

The installation process
$ brew install git-flow

Starter the project 
$ git flow init

Create New Feature / Branch 
$ git flow feature start feature_branch

Close and merge Feature / Branch
$ git flow feature finish feature_branch

Create Release Candidate 
$ git flow release start 0.1.0
Switched to a new branch 'release/0.1.0'

Close Release 
git flow release finish '0.1.0'
```


#fast-forward merge

يشير المصطلح "fast-forward merge" إلى نوع من الدمج في Git يتم فيه دمج فرع (branch) إلى الفرع الرئيسي في حالة عدم وجود تغييرات في ال main. وبمعنى آخر يتم دمج التغييرات في الفرع الفرعي مباشرةً مع الفرع الرئيسي دون إنشاء نقطة تفرع جديدة. يتم استخدام هذا النوع من الدمج عندما يتم العمل على فرع فرعي بشكل منفرد وبدون أي تداخلات مع الفرع الرئيسي.

#the 3-way merge

هو نوع آخر من دمج الفروع في Git، ويتم استخدامه في حالة وجود تغييرات في ال main. في هذه الحالة يقوم Git بإنشاء نقطة تفرع جديدة (merge commit) ويحاول دمج التغييرات من الفرعين

#Squash Merge

يُعد Squash Merge أحد الطرق التي يتم بها دمج الفروع في Git. يُستخدم هذا الأسلوب عندما تريد دمج التعديلات التي تم إجراؤها في فرع معين إلى فرع آخر.

يُعد Squash Merge طريقة جيدة لتقليل عدد الالتزامات (commits) الزائدة في تاريخ (History) مشروع Git، وللمحافظة على التاريخ (History) الخاص بالمشروع أنيقًا ومنظمًا. ومن المهم ملاحظة أنه إذا كنت تستخدم Squash Merge في Git فيجب عليك التأكد من الحفاظ على تاريخ المشروع مرتبًا ومنظمًا، وذلك باستخدام رسائل الالتزامات الصحيحة ووصف دقيق للتعديلات المدمجة


