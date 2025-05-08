# gulimall-admin-vue
谷粒商城后台管理系统前端vue项目——————>中文版 README.zh.md。
至少每人 2 次提交（含有效 commit message，且每次均具有有效工作量，有效工作量是指贡献的Changes数量不能少于10 lines）
使用文档（对 AI 辅助的工作进行简要的说明）AI 使用过程截图（每人不少于 3 张，展示你们如何提问、生成与比对），截图提交到img-work（命名xxx截图（自己名字））
<!-- by 黎  柚 -->
中文翻译版本 README.zh.md（可借助 AI，但需润色）
任务：中文翻译版本 README.zh.md——>含项目介绍


<!-- by 梁佐妃 -->
中文翻译版本 README.zh.md（可借助 AI，但需润色）
任务：中文翻译版本 README.zh.md——>安装/部署说明
第一次：
安装
Node.js	验证命令(node -v)	Node.js 中文镜像站
npm	验证命令(npm -v)	npm config set registry https://registry.npmmirror.com
Git	git --version-
1. 克隆我自己的仓库
https://github.com/liangzuofei/gulimall-admin-vue.git
fork 潘燕艳的仓库
https://github.com/ppyy112233/gulimall-admin-vue.git
cd D:\英语
2. 安装项目依赖
npm install --registry=https://registry.npmmirror.com --legacy-peer-deps
3. 环境配置
新建 .env 文件并配置后端服务地址：
VUE_APP_API_BASE_URL=http://localhost:8081/api/remote
5. 本地开发运行启动后端服务
# 进入后端项目目录
cd gulimall-parent/gulimall-admin
# 启动 Spring Boot 应用
mvn spring-boot:run
启动前端服务
# 返回前端项目根目录
cd ../../../gulimall-admin-vue
# 开发模式运行
npm run dev  
访问地址：http://localhost:8080
6. Docker 部署
6.1 修改配置文件
编辑 docker-compose.yml：
将 gulimall-admin-vue 服务端口映射改为 8080:80
配置后端服务连接地址（VUE_APP_API_BASE_URL）
6.2 构建镜像并运行
# 构建前端镜像
docker build -t gulimall-admin-vue:latest ./gulimall-admin-vue
# 启动容器组
docker-compose up -d 
访问地址：http://localhost:8080
7. Linux 服务器部署（推荐）
7.1 构建前端项目   
# 生成生产环境静态文件
npm run build
7.2 配置 Nginx
将输出的 dist 目录部署到 Nginx，配置反向代理指向后端服务。

第二次：
1. 基础工具安装
Node.js	Windows/Mac 一键安装包	node -v	下载时选择 cnpm 镜像源
npm	随Node.js自动安装	npm -v	npm config set registry https://registry.npmmirror.com
Git	官方下载 或 腾讯镜像	git --version	
1. 克隆我自己的仓库
https://github.com/liangzuofei/gulimall-admin-vue.git
fork 潘燕艳的仓库
https://github.com/ppyy112233/gulimall-admin-vue.git
cd D:\英语
2. 安装项目依赖（使用淘宝镜像加速，解决依赖冲突）
npm install --registry=https://registry.npmmirror.com --legacy-peer-deps
3. 环境配置
新建 .env 文件并配置后端服务地址：
VUE_APP_API_BASE_URL=http://localhost:8081/api/remote
5. 本地开发运行启动后端服务
# 进入后端项目目录
cd gulimall-parent/gulimall-admin
# 启动 Spring Boot 应用
mvn spring-boot:run
启动前端服务
# 返回前端项目根目录
cd ../../../gulimall-admin-vue
# 开发模式运行
npm run dev  
访问地址：http://localhost:8080
6. Docker 部署
6.1 修改配置文件
编辑 docker-compose.yml：
将 gulimall-admin-vue 服务端口映射改为 8080:80。
设置环境变量 VUE_APP_API_BASE_URL（如 http://backend_service:8081/api/remote）。
6.2 构建与运行
# 构建前端镜像
docker build -t gulimall-admin-vue:latest ./gulimall-admin-vue
# 启动容器组
docker-compose up -d
访问地址：http://localhost:8080
7. Linux 服务器部署（推荐生产环境）
7.1 构建前端静态资源
# 生成生产环境静态文件
npm run build:prod  
7.2 配置 Nginx
部署静态文件：将 dist 目录复制到 Nginx 的 html 目录（如 /var/www/html/gulimall-admin）。
sudo cp -r dist /var/www/html/gulimall-admin
配置 Nginx 虚拟主机：
编辑 /etc/nginx/conf.d/gulimall-admin.conf：     
server {
    listen       80;
    server_name  your_domain.com;  # 替换为域名或IP

    location / {
        root   /var/www/html/gulimall-admin;  # 静态资源路径
        try_files $uri $uri/ /index.html;   # SPA路由重定向
    }

    location /api/ {
        proxy_pass http://127.0.0.1:8081/api/;  # 后端服务地址
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

重启 Nginx：
sudo nginx -t && sudo systemctl restart nginx
    
8. 常见问题排查
前端资源未加载：检查 nginx.conf 中 root 路径是否正确。
API 请求失败：确认后端服务已启动，且 proxy_pass 地址正确。
Docker 端口冲突：检查 docker-compose.yml 中的端口映射配置。
权限问题：确保 Nginx 有权限读取静态资源目录（chmod -R 755 /var/www/html/gulimall-admin）。

<!-- by 李金焕 -->
中文翻译版本 README.zh.md（可借助 AI，但需润色）
任务：中文翻译版本 README.zh.md——>带截图主要功能的使用教程


<!-- by 王  愉 -->
项目术语表（中英文对照，不少于 5 个关键词）
|     英文术语       | 中文翻译  |                             说明                              |
| Repository        | 代码仓库  | 用于存储和管理项目代码的版本控制系统（如Git）中的存储位置。        |
| Commit            | 提交      | 将代码更改永久记录到版本历史中的操作。                           |
| Pull Request (PR) | 拉取请求  | 贡献者请求将代码更改合并到主项目的提议，通常用于代码审查和协作开发。|
| Fork              | 分支/复刻 | 创建项目的独立副本，以便在不影响原项目的情况下进行修改和实验。     |
| Merge             | 合并      | 将不同分支的代码更改整合到一起的操作。                            |
| Open Source       | 开源      | 源代码公开并可自由使用、修改和分发的软件或项目。                   |
| AI Model          | AI模型    | 通过算法训练得到的可用于预测、分类或决策的数据结构。               |
| Debugging         | 调试      | 查找并修复代码中的错误或问题的过程。                              |
| Deployment        | 部署      | 将软件或应用程序发布到生产环境以供用户使用的过程。                 |
| Branch            | 分支      | 在版本控制系统中创建的独立开发线，用于隔离不同功能或修复的开发。     |
| Clone             | 克隆      | 将远程代码仓库完整复制到本地环境的操作。                           |
| Push              | 推送      | 将本地代码更改上传到远程仓库的操作。                               |
| Machine Learning  | 机器学习  | 通过算法让计算机从数据中学习规律，并自动优化预测或决策模型的技术。    |
| Merge Conflict    | 合并冲突  | 当不同分支对同一代码部分进行修改时，版本控制系统无法自动解决的冲突。  |
| Pull              | 拉取      | 将远程仓库的最新更改同步到本地环境的操作。                         |
| Rebase            | 变基      | 将一个分支的修改历史重新应用到另一个分支基部的版本控制操作。         |
| Deep Learning     | 深度学习  | 基于多层神经网络的机器学习方法，擅长处理图像、语音等复杂数据。        |
| Staging Area      | 暂存区    | Git中临时存储已修改文件准备提交的区域。                            |
| Natural Language Processing (NLP)| 自然语言处理 | 让计算机理解、解释和生成人类语言的技术领域。       |

<!-- by 覃卫婷 -->
请使用AI对专业术语进行审核。审核——>中文版 README.zh.md,是否有错别字，如果有请重新提交
