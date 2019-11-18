hugo new site myblog

git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c

本地启动项目：
hugo server -t m10c --buildDrafts

hugo new post/blog.md

刷新public文件夹：
hugo --theme=m10c --baseUrl="https://wengshiquan.github.io/" --buildDrafts

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

