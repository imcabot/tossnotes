- 在项目开发过程中,一般都会添加.gitignore文件,但有的时候规则不生效.
  原因是.gitignore只能忽略那些原来没有被track的文件,如果某些文件已经被纳入了版本管理,这时修改.gitignore是无效的.
  解决方法是清楚本地缓存,然后再提交.
- ```Plain Text
  git rm -r cache .
  git add .
  git commit -m "update .gitignore"
  ```