hugo new site myblog

git clone https://github.com/xiaoheiAh/hugo-theme-pure themes/pure 

本地启动项目：

hugo server -t pure --buildDrafts

新建md文件（当前时间）

hugo new posts/any.md 



刷新public文件夹：
hugo --theme=pure --baseUrl="https://wengshiquan.github.io/" --buildDrafts



cd public

git init

git add .

git commit -m "我的第一次 hugo "

git remote add origin https://github.com/wengshiquan/wengshiquan.github.io.git



第二次提交：

git pull origin master

git add .

git commit -m "我的第二次 hugo "

git push -u origin master

