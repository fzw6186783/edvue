<template>
  <div style="margin-top: 40px">
    <!--<el-button @click="addArticle()">添加文章</el-button>-->
    <div class="articles-area">
      <el-card style="text-align: left">
        <div v-for="article in articles" :key="article.id">
          <div style="float:left;width:85%;height: 150px;">
            <router-link class="article-link" :to="{path:'jotter/article',query:{id: article.id}}"><span style="font-size: 20px"><strong>{{article.articleTitle}}</strong></span></router-link>
            <el-divider content-position="left">{{article.articleDate}}</el-divider>
            <router-link class="article-link" :to="{path:'jotter/article',query:{id: article.id}}"><p>{{article.articleAbstract}}</p></router-link>
          </div>
          <el-image
            style="margin:18px 0 0 30px;width:100px;height: 100px"
            :src="article.articleCover"
            fit="cover"></el-image>
          <el-divider></el-divider>
        </div>
      </el-card>
    </div>
    <el-pagination
      background
      layout="total, prev, pager, next, jumper"
      @current-change="handleCurrentChange"
      :page-size="pageSize"
      :total="total">
    </el-pagination>
  </div>
</template>

<script>

  export default {
    name: 'Articles',
    data () {
      return {
        articles: [],
        pageSize: 4,
        total: ''
      }
    },
    mounted () {
      this.loadArticles()
    },
    methods: {
      loadArticles () {
        var _this = this
var data={"pageNum":1,"pageSize":4,"size":3,"orderBy":null,"startRow":1,"endRow":3,"total":3,"pages":1,"list":[{"id":1,"articleTitle":"凉风有兴23","articleContentHtml":"<p>凉风有兴，秋月无边，而我思乡的情绪好比度日如年。虽然我风流倜傥玉树临风，但我还是有聪明的头脑和强健的臂腕。2323</p>\n","articleContentMd":"凉风有兴，秋月无边，而我思乡的情绪好比度日如年。虽然我风流倜傥玉树临风，但我还是有聪明的头脑和强健的臂腕。2323","articleAbstract":"凉风有兴，秋月无边，而我思乡的情绪好比度日如年。","articleCover":"https://i.loli.net/2020/01/16/d2ZlKI1WRE4p7XB.png","articleDate":"2020-01-13"},{"id":2,"articleTitle":"爱你一万年","articleContentHtml":"曾经有份真挚的爱情摆在我的面前，我没有珍惜，等到失去的时候才后悔莫急，人世间最痛苦的事莫过余此，如果上天在给我一次机会，我会对那个女孩说我爱你，如果要在这份爱上加个期限，我希望是一万年","articleContentMd":"曾经有份真挚的爱情摆在我的面前，我没有珍惜，等到失去的时候才后悔莫急，人世间最痛苦的事莫过余此，如果上天在给我一次机会，我会对那个女孩说我爱你，如果要在这份爱上加个期限，我希望是一万年","articleAbstract":"曾经有份真挚的爱情摆在我的面前，我没有珍惜，等到失去的时候才后悔莫及，人世间最痛苦的事莫过于此。","articleCover":"https://i.loli.net/2020/01/16/DdGBk1R3mj5er6v.png","articleDate":"2020-01-16"},{"id":3,"articleTitle":"《白卷》项目简介","articleContentHtml":"<p><img src=\"https://i.loli.net/2019/12/15/sYnuTIrDUwAfGgo.png\" alt=\"wjlogo.png\" /></p>\n<hr />\n<p><img src=\"https://img.shields.io/github/license/Antabot/White-Jotter\" alt=\"lisense\" /><br />\n<img src=\"https://img.shields.io/github/v/release/Antabot/White-Jotter\" alt=\"release\" /></p>\n<p>这是一个简单的前后端分离项目，主要采用 Vue.js + SpringBoot 技术栈开发。</p>\n<p>除了用作入门练习，我还希望该项目可以作为一些常见 Web 项目的脚手架，帮助大家简化搭建网站的流程。之所以叫白卷，是因为它从 0 开始，会随着时间的推移逐渐完善。</p>\n<p>欢迎加入微信圈子 【开发者】 分享、讨论学习经验：</p>\n<p><img src=\"https://i.loli.net/2020/01/17/HySWdM7wDfF8EKC.png\" alt=\"圈子\" /></p>\n<h1><a id=\"_17\"></a>整体效果</h1>\n<h2><a id=\"1_19\"></a>1.首页</h2>\n<p>作为展示页面，包括开发这个项目的主要参考资料、近期更新和 Slogan</p>\n<p><img src=\"https://img-blog.csdnimg.cn/20190403215932913.png\" alt=\"首页\" /></p>\n<h2><a id=\"2_25\"></a>2.图书馆</h2>\n<p>提供图书信息展示功能</p>\n<p><img src=\"https://i.loli.net/2019/12/03/AGLbIupct68ThBD.png\" alt=\"图书馆\" /></p>\n<h2><a id=\"3_31\"></a>3.登录页面</h2>\n<p><img src=\"https://i.loli.net/2019/04/14/5cb2fd5b78ae7.png\" alt=\"登录页面\" /></p>\n<h2><a id=\"4_35\"></a>4.后台管理</h2>\n<p>包含 dashboard、内容管理、用户及权限管理等</p>\n<p><img src=\"https://img-blog.csdnimg.cn/20191202200516251.png\" alt=\"后台\" /></p>\n<h1><a id=\"_41\"></a>技术栈</h1>\n<h2><a id=\"1_43\"></a>1.前端技术栈</h2>\n<p>1.Vue<br />\n2.ElementUI<br />\n3.axios</p>\n<h2><a id=\"2_49\"></a>2.后端技术栈</h2>\n<p>1.Spring Boot<br />\n2.Spring Data + JPA<br />\n3.MySQL<br />\n4.Shiro</p>\n<h1><a id=\"_56\"></a>部署方法</h1>\n<p>1.clone 项目到本地</p>\n<p><code>git clone https://github.com/Antabot/White-Jotter</code></p>\n<p>2.数据库脚本放在 <code>wj</code> 项目的根目录下，在MySQL中执行数据库脚本</p>\n<p>3.数据库配置在 <code>wj</code> 项目的 <code>src\\main\\resources</code> 目录下的<code>application.properties</code> 文件中，mysql 版本为 8.0.15</p>\n<p>4.在IntelliJ IDEA中运行 <code>wj</code> 项目，为了保证项目成功运行，可以右键点击 <code>pom.xml</code> 选择 maven -&gt; reimport ，并重启项目</p>\n<p>至此，服务端就启动成功了，同时，运行 <code>wj-vue</code> 项目，访问 <code>http://localhost:8080</code> ，即可进入登录页面，默认账号是 <code>admin</code>，密码是 <code>123</code></p>\n<p>如果要做二次开发，请继续看第五、六步。</p>\n<p>5.进入到 <code>wj-vue</code> 目录中，在命令行依次输入如下命令：</p>\n<pre><code class=\"lang-\"># 安装依赖\nnpm install\n\n# 在 localhost:8080 启动项目\nnpm run dev\n\n</code></pre>\n<p>由于在 <code>wj-vue</code> 项目中已经配置了端口转发，将数据转发到SpringBoot上，因此项目启动之后，在浏览器中输入 <code>http://localhost:8080</code> 就可以访问我们的前端项目了，所有的请求通过端口转发将数据传到 SpringBoot 中（注意此时不要关闭 SpringBoot 项目）。</p>\n<p>6.最后可以用 <code>WebStorm</code> 等工具打开 <code>wj-vue</code>项目，继续开发，开发完成后，当项目要上线时，依然进入到 <code>wj-vue</code> 目录，然后执行如下命令：</p>\n<pre><code class=\"lang-\">npm run build\n</code></pre>\n<p>该命令执行成功之后， <code>wj-vue</code> 目录下生成一个 <code>dist</code> 文件夹，可以将该文件夹中的两个文件 <code>static</code> 和 <code>index.html</code> 拷贝到 <code>wj</code> 项目中 <code>resources/static/</code> 目录下，然后直接运行 <code>wj</code> 项目，访问 <code>http://localhost:8443</code> ，实际上是把前端打包后作为静态文件，但不推荐使用这种方式。</p>\n<h1><a id=\"_93\"></a>教程</h1>\n<p>我在 CSDN 上分享了开发这个项目的教程，有兴趣的小伙伴可以点击下面的链接查看。</p>\n<p>1.<a href=\"https://blog.csdn.net/Neuf_Soleil/article/details/88925013\" target=\"_blank\">项目简介</a></p>\n<p>2.<a href=\"https://blog.csdn.net/Neuf_Soleil/article/details/88926242\" target=\"_blank\">使用 CLI 搭建 Vue.js 项目</a></p>\n<p>3.<a href=\"https://blog.csdn.net/Neuf_Soleil/article/details/88955387\" target=\"_blank\">前后端结合测试（登录页面开发）</a></p>\n<p>4.<a href=\"https://blog.csdn.net/Neuf_Soleil/article/details/89294300\" target=\"_blank\">数据库的引入</a></p>\n<p>5.<a href=\"https://blog.csdn.net/Neuf_Soleil/article/details/89298717\" target=\"_blank\">使用 Element 辅助前端开发</a></p>\n<p>6.<a href=\"https://learner.blog.csdn.net/article/details/89422585\" target=\"_blank\">前端路由与登录拦截器</a></p>\n<p>7.<a href=\"https://learner.blog.csdn.net/article/details/89853305\" target=\"_blank\">导航栏与图书页面设计</a></p>\n<p>8.<a href=\"https://learner.blog.csdn.net/article/details/92413933\" target=\"_blank\">数据库设计与增删改查</a></p>\n<p>9.<a href=\"https://learner.blog.csdn.net/article/details/95310666\" target=\"_blank\">核心功能的前端实现</a></p>\n<p>10.<a href=\"https://learner.blog.csdn.net/article/details/97619312\" target=\"_blank\">图片上传与项目的打包部署</a></p>\n<p>11.<a href=\"https://learner.blog.csdn.net/article/details/100849732\" target=\"_blank\">用户角色权限管理模块设计</a></p>\n<p>12.<a href=\"https://learner.blog.csdn.net/article/details/101121899\" target=\"_blank\">访问控制及其实现思路</a></p>\n<p>13.<a href=\"https://learner.blog.csdn.net/article/details/102690035\" target=\"_blank\">使用 Shiro 实现用户信息加密与登录认证</a></p>\n<p>14.<a href=\"https://learner.blog.csdn.net/article/details/102788866\" target=\"_blank\">用户认证方案与完善的访问拦截</a></p>\n<p>15.<a href=\"https://learner.blog.csdn.net/article/details/103114893\" target=\"_blank\">动态加载后台菜单</a></p>\n<p>16.<a href=\"https://learner.blog.csdn.net/article/details/103250775\" target=\"_blank\">功能级访问控制的实现</a></p>\n<p>(持续更新中)</p>\n<h1><a id=\"_131\"></a>近期更新</h1>\n<p>12-01 实现功能级权限控制<br />\n11-30 利用 vue-elment-admin 项目完善后台界面设计<br />\n11-17 重构项目，完成搭建后台基础界面，实现按角色加载菜单，取消前台访问限制<br />\n04-27 使用前端拦截器，数据库迁移至 mysql 8.0.15，后台管理页面初始化<br />\n04-13 完成图片的上传功能<br />\n04-11 完成图书分类功能<br />\n04-08 完成图书分页功能<br />\n04-06 完成图书查询功能<br />\n04-05 完成图书修改功能<br />\n04-04 完成图书删除功能<br />\n04-03 完成图书新增功能</p>\n","articleContentMd":"![wjlogo.png](https://i.loli.net/2019/12/15/sYnuTIrDUwAfGgo.png)\n\n---\n\n![lisense](https://img.shields.io/github/license/Antabot/White-Jotter)\n![release](https://img.shields.io/github/v/release/Antabot/White-Jotter)\n\n\n这是一个简单的前后端分离项目，主要采用 Vue.js + SpringBoot 技术栈开发。\n\n除了用作入门练习，我还希望该项目可以作为一些常见 Web 项目的脚手架，帮助大家简化搭建网站的流程。之所以叫白卷，是因为它从 0 开始，会随着时间的推移逐渐完善。\n\n欢迎加入微信圈子 【开发者】 分享、讨论学习经验：\n\n![圈子](https://i.loli.net/2020/01/17/HySWdM7wDfF8EKC.png)\n\n\n# 整体效果\n\n## 1.首页\n\n作为展示页面，包括开发这个项目的主要参考资料、近期更新和 Slogan\n\n![首页](https://img-blog.csdnimg.cn/20190403215932913.png)\n\n## 2.图书馆\n\n提供图书信息展示功能\n\n![图书馆](https://i.loli.net/2019/12/03/AGLbIupct68ThBD.png)\n\n## 3.登录页面\n\n![登录页面](https://i.loli.net/2019/04/14/5cb2fd5b78ae7.png)\n\n## 4.后台管理\n\n包含 dashboard、内容管理、用户及权限管理等\n\n![后台](https://img-blog.csdnimg.cn/20191202200516251.png)\n\n# 技术栈\n\n## 1.前端技术栈\n\n1.Vue  \n2.ElementUI  \n3.axios   \n\n## 2.后端技术栈\n\n1.Spring Boot  \n2.Spring Data + JPA \n3.MySQL  \n4.Shiro\n\n# 部署方法\n\n1.clone 项目到本地\n\n`git clone https://github.com/Antabot/White-Jotter`\n\n2.数据库脚本放在 `wj` 项目的根目录下，在MySQL中执行数据库脚本  \n\n3.数据库配置在 `wj` 项目的 `src\\main\\resources` 目录下的`application.properties` 文件中，mysql 版本为 8.0.15   \n\n4.在IntelliJ IDEA中运行 `wj` 项目，为了保证项目成功运行，可以右键点击 `pom.xml` 选择 maven -> reimport ，并重启项目\n\n至此，服务端就启动成功了，同时，运行 `wj-vue` 项目，访问 `http://localhost:8080` ，即可进入登录页面，默认账号是 `admin`，密码是 `123`\n\n如果要做二次开发，请继续看第五、六步。\n\n5.进入到 `wj-vue` 目录中，在命令行依次输入如下命令：  \n\n```\n# 安装依赖\nnpm install\n\n# 在 localhost:8080 启动项目\nnpm run dev\n\n```  \n\n由于在 `wj-vue` 项目中已经配置了端口转发，将数据转发到SpringBoot上，因此项目启动之后，在浏览器中输入 `http://localhost:8080` 就可以访问我们的前端项目了，所有的请求通过端口转发将数据传到 SpringBoot 中（注意此时不要关闭 SpringBoot 项目）。\n\n6.最后可以用 `WebStorm` 等工具打开 `wj-vue`项目，继续开发，开发完成后，当项目要上线时，依然进入到 `wj-vue` 目录，然后执行如下命令：  \n\n```\nnpm run build\n```  \n\n该命令执行成功之后， `wj-vue` 目录下生成一个 `dist` 文件夹，可以将该文件夹中的两个文件 `static` 和 `index.html` 拷贝到 `wj` 项目中 `resources/static/` 目录下，然后直接运行 `wj` 项目，访问 `http://localhost:8443` ，实际上是把前端打包后作为静态文件，但不推荐使用这种方式。\n\n# 教程\n\n我在 CSDN 上分享了开发这个项目的教程，有兴趣的小伙伴可以点击下面的链接查看。  \n\n1.[项目简介](https://blog.csdn.net/Neuf_Soleil/article/details/88925013)\n\n2.[使用 CLI 搭建 Vue.js 项目](https://blog.csdn.net/Neuf_Soleil/article/details/88926242)\n\n3.[前后端结合测试（登录页面开发）](https://blog.csdn.net/Neuf_Soleil/article/details/88955387)\n\n4.[数据库的引入](https://blog.csdn.net/Neuf_Soleil/article/details/89294300)\n\n5.[使用 Element 辅助前端开发](https://blog.csdn.net/Neuf_Soleil/article/details/89298717)\n\n6.[前端路由与登录拦截器](https://learner.blog.csdn.net/article/details/89422585)\n\n7.[导航栏与图书页面设计](https://learner.blog.csdn.net/article/details/89853305)\n\n8.[数据库设计与增删改查](https://learner.blog.csdn.net/article/details/92413933)\n\n9.[核心功能的前端实现](https://learner.blog.csdn.net/article/details/95310666)\n\n10.[图片上传与项目的打包部署](https://learner.blog.csdn.net/article/details/97619312)\n\n11.[用户角色权限管理模块设计](https://learner.blog.csdn.net/article/details/100849732)\n\n12.[访问控制及其实现思路](https://learner.blog.csdn.net/article/details/101121899)\n\n13.[使用 Shiro 实现用户信息加密与登录认证](https://learner.blog.csdn.net/article/details/102690035)\n\n14.[用户认证方案与完善的访问拦截](https://learner.blog.csdn.net/article/details/102788866)\n\n15.[动态加载后台菜单](https://learner.blog.csdn.net/article/details/103114893)\n\n16.[功能级访问控制的实现](https://learner.blog.csdn.net/article/details/103250775)\n\n(持续更新中)\n\n# 近期更新\n \n12-01 实现功能级权限控制  \n11-30 利用 vue-elment-admin 项目完善后台界面设计  \n11-17 重构项目，完成搭建后台基础界面，实现按角色加载菜单，取消前台访问限制  \n04-27 使用前端拦截器，数据库迁移至 mysql 8.0.15，后台管理页面初始化  \n04-13 完成图片的上传功能  \n04-11 完成图书分类功能  \n04-08 完成图书分页功能  \n04-06 完成图书查询功能  \n04-05 完成图书修改功能  \n04-04 完成图书删除功能  \n04-03 完成图书新增功能\n","articleAbstract":"白卷是一个简单的前后端分离项目，主要采用 Vue.js + SpringBoot 技术栈开发。","articleCover":"https://i.loli.net/2020/01/19/egDEfu5jXlJ6r3a.png","articleDate":"2020-01-19"}],"firstPage":1,"prePage":0,"nextPage":0,"lastPage":1,"isFirstPage":true,"isLastPage":true,"hasPreviousPage":false,"hasNextPage":false,"navigatePages":8,"navigatepageNums":[1]}
            _this.articles = data.list
            _this.total = data.total


      },

    }
  }
</script>

<style scoped>
  .articles-area {
    width: 990px;
    height: 750px;
    margin-left: auto;
    margin-right: auto;
  }

  .article-link {
    text-decoration: none;
    color: #606266;
  }

  .article-link:hover {
    color: #409EFF;
  }
</style>
