# xiaoze
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>全能导航｜动态流光渐变版</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: '#165DFF',
            sidebar: '#0F172A',
            card: '#ffffff',
            muted: '#64748b'
          },
          fontFamily: {
            sans: ['Inter', 'system-ui', 'sans-serif'],
          },
        },
      }
    }
  </script>
  <style type="text/tailwindcss">
    @layer utilities {
      .content-auto { content-visibility: auto; }
      .scrollbar-hide::-webkit-scrollbar { display: none; }
      .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }
      .nav-active { @apply bg-primary/10 text-primary border-l-4 border-primary; }
      .card-shadow { box-shadow: 0 2px 12px rgba(22, 93, 255, 0.08); }
      .card-hover { transition: all 0.25s ease; }
      .card-hover:hover { transform: translateY(-4px); box-shadow: 0 8px 24px rgba(22, 93, 255, 0.15); }
    }
    /* 全屏流光渐变动画 */
    .gradient-bg {
      background: linear-gradient(270deg, #e0f7fa, #f5f7fa, #fef3f8, #f0f9ff, #f0fdf4, #fffbeb, #f8fafc, #ecfeff, #fef7ff, #fff7ed);
      background-size: 2000% 2000%;
      animation: gradientFlow 25s ease infinite;
    }
    @keyframes gradientFlow {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
  </style>
</head>
<body class="font-sans text-slate-800 gradient-bg min-h-screen">
  <!-- 移动端汉堡按钮 -->
  <button id="menuBtn" class="fixed top-4 left-4 z-50 lg:hidden w-10 h-10 rounded-lg bg-sidebar text-white flex items-center justify-center">
    <i class="fa fa-bars text-lg"></i>
  </button>

  <!-- 侧边栏遮罩 -->
  <div id="sidebarMask" class="fixed inset-0 bg-black/40 z-40 hidden lg:hidden"></div>

  <!-- 左侧侧边栏 -->
  <aside id="sidebar" class="fixed top-0 left-0 h-screen w-64 bg-sidebar text-slate-200 z-50 transform -translate-x-full lg:translate-x-0 transition-transform duration-300 overflow-y-auto scrollbar-hide">
    <div class="p-5 border-b border-slate-700">
      <div class="flex items-center gap-2">
        <div class="w-9 h-9 rounded-lg bg-primary flex items-center justify-center">
          <i class="fa fa-compass text-white"></i>
        </div>
        <span class="text-lg font-bold text-white">全能快捷导航</span>
      </div>
    </div>
    <nav class="p-3" id="sideNav">
      <a href="#work" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-briefcase mr-2 w-4 text-center"></i>工作办公
      </a>
      <a href="#dev" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-code mr-2 w-4 text-center"></i>开发编程
      </a>
      <a href="#design" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-paint-brush mr-2 w-4 text-center"></i>设计素材
      </a>
      <a href="#media" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-play-circle mr-2 w-4 text-center"></i>影音娱乐
      </a>
      <a href="#study" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-book mr-2 w-4 text-center"></i>学习资源
      </a>
      <a href="#life" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-life-ring mr-2 w-4 text-center"></i>生活实用
      </a>
      <a href="#tool" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-wrench mr-2 w-4 text-center"></i>在线工具
      </a>
      <a href="#ai" class="side-link block px-4 py-3 rounded-lg mb-1 hover:bg-slate-800 transition-colors text-sm">
        <i class="fa fa-robot mr-2 w-4 text-center"></i>AI工具
      </a>
    </nav>
  </aside>

  <!-- 右侧主内容区 -->
  <main class="lg:pl-64 min-h-screen transition-all">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-6 lg:py-8">
      <!-- 搜索区域 -->
      <section class="bg-white/90 backdrop-blur-sm rounded-2xl p-5 mb-8 card-shadow">
        <div class="flex flex-col sm:flex-row gap-3">
          <div class="flex gap-1">
            <button data-engine="baidu" class="search-engine px-4 py-2 rounded-l-lg bg-primary text-white text-sm">百度</button>
            <button data-engine="bing" class="search-engine px-4 py-2 bg-slate-100 text-slate-600 text-sm">必应</button>
            <button data-engine="google" class="search-engine px-4 py-2 rounded-r-lg bg-slate-100 text-slate-600 text-sm">谷歌</button>
          </div>
          <div class="flex-1 flex">
            <input type="text" id="searchInput" placeholder="输入关键词搜索全网..." class="flex-1 border border-slate-200 rounded-l-lg px-4 py-2 outline-none focus:border-primary transition-colors">
            <button id="searchBtn" class="bg-primary text-white px-5 rounded-r-lg">
              <i class="fa fa-search"></i>
            </button>
          </div>
        </div>
      </section>

      <!-- 1. 工作办公 -->
      <section id="work" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">工作办公</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="work-office">办公软件</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="work-cloud">云盘文档</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="work-im">社交办公</button>
        </div>
        <div class="tab-content" id="work-office">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.office.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-orange-100 text-orange-500 flex items-center justify-center"><i class="fa fa-file-text-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Office</div><div class="text-xs text-muted mt-0.5">微软办公套件</div></div>
            </a>
            <a href="https://docs.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-edit"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">腾讯文档</div><div class="text-xs text-muted mt-0.5">在线协作编辑</div></div>
            </a>
            <a href="https://kdocs.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-file"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">金山文档</div><div class="text-xs text-muted mt-0.5">WPS在线文档</div></div>
            </a>
            <a href="https://shimo.im" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-cyan-100 text-cyan-500 flex items-center justify-center"><i class="fa fa-sticky-note"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">石墨文档</div><div class="text-xs text-muted mt-0.5">轻量化协作文档</div></div>
            </a>
            <a href="https://www.notion.so" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-th"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Notion</div><div class="text-xs text-muted mt-0.5">全能笔记工具</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="work-cloud">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://pan.baidu.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-cloud"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">百度网盘</div><div class="text-xs text-muted mt-0.5">大容量云存储</div></div>
            </a>
            <a href="https://pan.quark.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-indigo-100 text-indigo-500 flex items-center justify-center"><i class="fa fa-database"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">夸克网盘</div><div class="text-xs text-muted mt-0.5">高速免费网盘</div></div>
            </a>
            <a href="https://drive.weixin.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-lime-100 text-lime-500 flex items-center justify-center"><i class="fa fa-folder-open"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">微信文件盘</div><div class="text-xs text-muted mt-0.5">微信云端文件</div></div>
            </a>
            <a href="https://www.aliyundrive.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-cloud-upload"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">阿里云盘</div><div class="text-xs text-muted mt-0.5">阿里存储服务</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="work-im">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.feishu.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-comments"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">飞书</div><div class="text-xs text-muted mt-0.5">企业协同办公</div></div>
            </a>
            <a href="https://work.weixin.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-emerald-100 text-emerald-500 flex items-center justify-center"><i class="fa fa-users"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">企业微信</div><div class="text-xs text-muted mt-0.5">企业沟通工具</div></div>
            </a>
            <a href="https://dingtalk.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-sky-100 text-sky-500 flex items-center justify-center"><i class="fa fa-bullhorn"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">钉钉</div><div class="text-xs text-muted mt-0.5">移动办公平台</div></div>
            </a>
            <a href="https://www.weixin.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-wechat"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">微信</div><div class="text-xs text-muted mt-0.5">日常社交沟通</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 2. 开发编程 -->
      <section id="dev" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">开发编程</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="dev-front">前端资源</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="dev-back">后端开发</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="dev-code">代码仓库</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="dev-tool">开发工具</button>
        </div>
        <div class="tab-content" id="dev-front">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://caniuse.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-check-square-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Can I Use</div><div class="text-xs text-muted mt-0.5">CSS兼容性查询</div></div>
            </a>
            <a href="https://vuejs.org" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-emerald-100 text-emerald-500 flex items-center justify-center"><i class="fa fa-leaf"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Vue官网</div><div class="text-xs text-muted mt-0.5">渐进式JS框架</div></div>
            </a>
            <a href="https://react.dev" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-sky-100 text-sky-500 flex items-center justify-center"><i class="fa fa-cog"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">React官网</div><div class="text-xs text-muted mt-0.5">前端主流框架</div></div>
            </a>
            <a href="https://www.tslang.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-code"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">TypeScript</div><div class="text-xs text-muted mt-0.5">JS超集语言</div></div>
            </a>
            <a href="https://tailwindcss.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-cyan-100 text-cyan-500 flex items-center justify-center"><i class="fa fa-wind"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">TailwindCSS</div><div class="text-xs text-muted mt-0.5">原子化CSS框架</div></div>
            </a>
            <a href="https://www.bootcss.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-bootstrap"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Bootstrap</div><div class="text-xs text-muted mt-0.5">前端UI框架</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="dev-back">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://nodejs.org" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-server"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">NodeJS</div><div class="text-xs text-muted mt-0.5">后端运行环境</div></div>
            </a>
            <a href="https://www.python.org" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-yellow-100 text-yellow-500 flex items-center justify-center"><i class="fa fa-snake"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Python</div><div class="text-xs text-muted mt-0.5">全能编程语言</div></div>
            </a>
            <a href="https://spring.io" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-leaf"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">SpringBoot</div><div class="text-xs text-muted mt-0.5">Java后端框架</div></div>
            </a>
            <a href="https://www.php.net" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-code"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">PHP</div><div class="text-xs text-muted mt-0.5">网页开发语言</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="dev-code">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://github.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-slate-100 text-slate-700 flex items-center justify-center"><i class="fa fa-github"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">GitHub</div><div class="text-xs text-muted mt-0.5">全球代码仓库</div></div>
            </a>
            <a href="https://gitee.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-git"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Gitee码云</div><div class="text-xs text-muted mt-0.5">国内开源平台</div></div>
            </a>
            <a href="https://gitcode.net" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-code-fork"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">GitCode</div><div class="text-xs text-muted mt-0.5">CSDN代码平台</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="dev-tool">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.json.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-yellow-100 text-yellow-600 flex items-center justify-center"><i class="fa fa-code"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">JSON格式化</div><div class="text-xs text-muted mt-0.5">在线JSON工具</div></div>
            </a>
            <a href="https://tool.oschina.net" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-orange-100 text-orange-500 flex items-center justify-center"><i class="fa fa-wrench"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">开源工具库</div><div class="text-xs text-muted mt-0.5">各类在线开发工具</div></div>
            </a>
            <a href="https://code.visualstudio.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-edit"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">VS Code</div><div class="text-xs text-muted mt-0.5">全能代码编辑器</div></div>
            </a>
            <a href="https://www.postman.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-orange-100 text-orange-500 flex items-center justify-center"><i class="fa fa-paper-plane"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Postman</div><div class="text-xs text-muted mt-0.5">API接口测试</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 3. 设计素材 -->
      <section id="design" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">设计素材</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="design-pic">免费图库</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="design-icon">图标资源</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="design-ui">UI设计</button>
        </div>
        <div class="tab-content" id="design-pic">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://unsplash.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-rose-100 text-rose-500 flex items-center justify-center"><i class="fa fa-picture-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Unsplash</div><div class="text-xs text-muted mt-0.5">高清无版权图库</div></div>
            </a>
            <a href="https://pixabay.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-teal-100 text-teal-500 flex items-center justify-center"><i class="fa fa-camera"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Pixabay</div><div class="text-xs text-muted mt-0.5">图片视频音频素材</div></div>
            </a>
            <a href="https://www.pexels.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-image"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Pexels</div><div class="text-xs text-muted mt-0.5">免费商用摄影图</div></div>
            </a>
            <a href="https://www.freepik.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-yellow-100 text-yellow-500 flex items-center justify-center"><i class="fa fa-picture-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Freepik</div><div class="text-xs text-muted mt-0.5">矢量图设计素材</div></div>
            </a>
            <a href="https://www.58pic.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-picture-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">千库网</div><div class="text-xs text-muted mt-0.5">国内设计素材库</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="design-icon">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.iconfont.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-indigo-100 text-indigo-500 flex items-center justify-center"><i class="fa fa-flag"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">阿里图标库</div><div class="text-xs text-muted mt-0.5">海量矢量图标</div></div>
            </a>
            <a href="https://fontawesome.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-amber-100 text-amber-500 flex items-center justify-center"><i class="fa fa-star"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">FontAwesome</div><div class="text-xs text-muted mt-0.5">经典字体图标</div></div>
            </a>
            <a href="https://icons8.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-heart"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Icons8</div><div class="text-xs text-muted mt-0.5">全能图标工具</div></div>
            </a>
            <a href="https://www.flaticon.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-thumbs-up"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Flaticon</div><div class="text-xs text-muted mt-0.5">免费矢量图标</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="design-ui">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.zcool.com.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-pink-100 text-pink-500 flex items-center justify-center"><i class="fa fa-paint-brush"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">站酷</div><div class="text-xs text-muted mt-0.5">设计师作品平台</div></div>
            </a>
            <a href="https://dribbble.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-orange-100 text-orange-500 flex items-center justify-center"><i class="fa fa-dribbble"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Dribbble</div><div class="text-xs text-muted mt-0.5">海外UI灵感社区</div></div>
            </a>
            <a href="https://www.behance.net" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-behance"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Behance</div><div class="text-xs text-muted mt-0.5">顶尖设计作品</div></div>
            </a>
            <a href="https://www.figma.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-paint-brush"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Figma</div><div class="text-xs text-muted mt-0.5">在线UI设计工具</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 4. 影音娱乐 -->
      <section id="media" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">影音娱乐</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="media-video">视频平台</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="media-music">音乐网站</button>
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md text-slate-500" data-tab="media-anime">动漫影视</button>
        </div>
        <div class="tab-content" id="media-video">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.bilibili.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-pink-100 text-pink-500 flex items-center justify-center"><i class="fa fa-play"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">哔哩哔哩</div><div class="text-xs text-muted mt-0.5">二次元视频社区</div></div>
            </a>
            <a href="https://www.iqiyi.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-film"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">爱奇艺</div><div class="text-xs text-muted mt-0.5">高清影视追剧</div></div>
            </a>
            <a href="https://v.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-video-camera"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">腾讯视频</div><div class="text-xs text-muted mt-0.5">热门剧集综艺</div></div>
            </a>
            <a href="https://www.youku.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-play-circle"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">优酷</div><div class="text-xs text-muted mt-0.5">经典影视平台</div></div>
            </a>
            <a href="https://www.mgtv.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-yellow-100 text-yellow-500 flex items-center justify-center"><i class="fa fa-play"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">芒果TV</div><div class="text-xs text-muted mt-0.5">综艺剧集平台</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="media-music">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://music.163.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-music"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">网易云音乐</div><div class="text-xs text-muted mt-0.5">听歌社交平台</div></div>
            </a>
            <a href="https://y.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-headphones"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">QQ音乐</div><div class="text-xs text-muted mt-0.5">海量正版曲库</div></div>
            </a>
            <a href="https://music.migu.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-music"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">咪咕音乐</div><div class="text-xs text-muted mt-0.5">免费版权音乐</div></div>
            </a>
            <a href="https://www.kugou.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-music"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">酷狗音乐</div><div class="text-xs text-muted mt-0.5">K歌听歌神器</div></div>
            </a>
          </div>
        </div>
        <div class="tab-content hidden" id="media-anime">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://acfun.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-yellow-100 text-yellow-500 flex items-center justify-center"><i class="fa fa-gamepad"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Acfun</div><div class="text-xs text-muted mt-0.5">老牌动漫社区</div></div>
            </a>
            <a href="https://www.dm530.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-film"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">动漫天堂</div><div class="text-xs text-muted mt-0.5">动漫在线观看</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 5. 学习资源 -->
      <section id="study" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">学习资源</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="study-online">在线课堂</button>
        </div>
        <div class="tab-content" id="study-online">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.icourse163.org" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-graduation-cap"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">中国大学MOOC</div><div class="text-xs text-muted mt-0.5">名校免费公开课</div></div>
            </a>
            <a href="https://ke.qq.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-teal-100 text-teal-500 flex items-center justify-center"><i class="fa fa-book"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">腾讯课堂</div><div class="text-xs text-muted mt-0.5">职业技能学习</div></div>
            </a>
            <a href="https://study.163.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-orange-100 text-orange-500 flex items-center justify-center"><i class="fa fa-lightbulb-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">网易云课堂</div><div class="text-xs text-muted mt-0.5">职场技能教程</div></div>
            </a>
            <a href="https://www.lizhi.io" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-book"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate>荔枝微课</div><div class="text-xs text-muted mt-0.5">知识付费学习</div></div>
            </a>
            <a href="https://www.nowcoder.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-code"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">牛客网</div><div class="text-xs text-muted mt-0.5">求职刷题平台</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 6. 生活实用 -->
      <section id="life" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">生活实用</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="life-tool">便民工具</button>
        </div>
        <div class="tab-content" id="life-tool">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.timeanddate.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-teal-100 text-teal-500 flex items-center justify-center"><i class="fa fa-clock-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">全球时间</div><div class="text-xs text-muted mt-0.5">时区日期查询</div></div>
            </a>
            <a href="https://www.weather.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-sky-100 text-sky-500 flex items-center justify-center"><i class="fa fa-cloud"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">天气查询</div><div class="text-xs text-muted mt-0.5">全球天气预报</div></div>
            </a>
            <a href="https://www.12306.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-train"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">12306</div><div class="text-xs text-muted mt-0.5">铁路购票出行</div></div>
            </a>
            <a href="https://www.baidu.com/map/" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-map-marker"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">百度地图</div><div class="text-xs text-muted mt-0.5">出行导航路线</div></div>
            </a>
            <a href="https://www.amap.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-location-arrow"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">高德地图</div><div class="text-xs text-muted mt-0.5">精准导航工具</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 7. 在线工具 -->
      <section id="tool" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">在线工具</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="tool-all">常用工具</button>
        </div>
        <div class="tab-content" id="tool-all">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://www.pdf24.org" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-rose-100 text-rose-500 flex items-center justify-center"><i class="fa fa-file-pdf-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">PDF工具箱</div><div class="text-xs text-muted mt-0.5">PDF转换编辑</div></div>
            </a>
            <a href="https://www.zhongzhuan.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-amber-100 text-amber-500 flex items-center justify-center"><i class="fa fa-exchange"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">格式转换</div><div class="text-xs text-muted mt-0.5">音视频格式转换</div></div>
            </a>
            <a href="https://www.toutiao.com/tools/qrcode/" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-qrcode"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">二维码生成</div><div class="text-xs text-muted mt-0.5">在线制作二维码</div></div>
            </a>
            <a href="https://www.baidu.com/s?wd=在线压缩" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-compress"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">图片压缩</div><div class="text-xs text-muted mt-0.5">无损图片压缩</div></div>
            </a>
            <a href="https://translate.google.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-language"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">谷歌翻译</div><div class="text-xs text-muted mt-0.5">多语言翻译</div></div>
            </a>
          </div>
        </div>
      </section>

      <!-- 8. AI工具 -->
      <section id="ai" class="mb-12 scroll-mt-20">
        <h2 class="text-xl font-bold mb-4 text-slate-900">AI工具</h2>
        <div class="flex gap-2 mb-5 border-b border-slate-200 pb-2 flex-wrap">
          <button class="tab-btn px-4 py-2 text-sm rounded-t-md tab-active" data-tab="ai-all">AI全能工具</button>
        </div>
        <div class="tab-content" id="ai-all">
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            <a href="https://chat.openai.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-green-100 text-green-500 flex items-center justify-center"><i class="fa fa-robot"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">ChatGPT</div><div class="text-xs text-muted mt-0.5">全球顶级AI助手</div></div>
            </a>
            <a href="https://www.doubao.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-robot"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">豆包AI</div><div class="text-xs text-muted mt-0.5">字节跳动AI</div></div>
            </a>
            <a href="https://xinghuo.xfyun.cn" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-red-100 text-red-500 flex items-center justify-center"><i class="fa fa-robot"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">讯飞星火</div><div class="text-xs text-muted mt-0.5">科大讯飞AI</div></div>
            </a>
            <a href="https://ai.baidu.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-blue-100 text-blue-500 flex items-center justify-center"><i class="fa fa-robot"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">文心一言</div><div class="text-xs text-muted mt-0.5">百度AI大模型</div></div>
            </a>
            <a href="https://www.midjourney.com" target="_blank" class="bg-white p-4 rounded-xl card-shadow card-hover flex items-center gap-3">
              <div class="w-10 h-10 rounded-lg bg-purple-100 text-purple-500 flex items-center justify-center"><i class="fa fa-picture-o"></i></div>
              <div class="flex-1 min-w-0"><div class="font-medium text-sm truncate">Midjourney</div><div class="text-xs text-muted mt-0.5">AI绘画工具</div></div>
            </a>
          </div>
        </div>
      </section>
    </div>
  </main>

  <script>
    // ========== 移动端侧边栏控制 ==========
    const menuBtn = document.getElementById('menuBtn');
    const sidebar = document.getElementById('sidebar');
    const mask = document.getElementById('sidebarMask');
    const sideLinks = document.querySelectorAll('.side-link');

    function openSidebar() {
      sidebar.classList.remove('-translate-x-full');
      mask.classList.remove('hidden');
    }
    function closeSidebar() {
      sidebar.classList.add('-translate-x-full');
      mask.classList.add('hidden');
    }
    menuBtn.addEventListener('click', openSidebar);
    mask.addEventListener('click', closeSidebar);
    sideLinks.forEach(link => {
      link.addEventListener('click', () => window.innerWidth < 1024 && closeSidebar())
    })

    // ========== Tab 二级分类切换（已修复BUG） ==========
    const tabBtns = document.querySelectorAll('.tab-btn');
    tabBtns.forEach(btn => {
      btn.addEventListener('click', (e) => {
        e.preventDefault();
        const tabGroup = btn.closest('section');
        const tabId = btn.dataset.tab;
        
        // 只重置当前分组的按钮
        tabGroup.querySelectorAll('.tab-btn').forEach(b => {
          b.classList.remove('tab-active','text-primary');
          b.classList.add('text-slate-500');
        });
        btn.classList.add('tab-active','text-primary');
        btn.classList.remove('text-slate-500');
        
        // 只重置当前分组的内容
        tabGroup.querySelectorAll('.tab-content').forEach(c => c.classList.add('hidden'));
        document.getElementById(tabId).classList.remove('hidden');
      })
    })

    // ========== 滚动监听 Scroll Spy 侧边栏高亮 ==========
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.side-link');
    window.addEventListener('scroll', () => {
      let current = '';
      sections.forEach(sec => {
        const secTop = sec.offsetTop - 120;
        const secHeight = sec.offsetHeight;
        if(window.scrollY >= secTop) current = sec.getAttribute('id');
      })
      navLinks.forEach(link => {
        link.classList.remove('nav-active');
        if(link.getAttribute('href').slice(1) === current){
          link.classList.add('nav-active');
        }
      })
    })

    // 平滑滚动
    document.documentElement.style.scrollBehavior = 'smooth';

    // ========== 多搜索引擎搜索功能 ==========
    const searchEngines = {
      baidu: 'https://www.baidu.com/s?wd=',
      bing: 'https://cn.bing.com/search?q=',
      google: 'https://www.google.com/search?q='
    };
    let currentEngine = 'baidu';
    const engineBtns = document.querySelectorAll('.search-engine');
    const searchInput = document.getElementById('searchInput');
    const searchBtn = document.getElementById('searchBtn');

    engineBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        engineBtns.forEach(b => {
          b.classList.remove('bg-primary','text-white');
          b.classList.add('bg-slate-100','text-slate-600');
        })
        btn.classList.add('bg-primary','text-white');
        btn.classList.remove('bg-slate-100','text-slate-600');
        currentEngine = btn.dataset.engine;
      })
    })

    function doSearch(){
      const keyword = searchInput.value.trim();
      if(!keyword) return;
      window.open(searchEngines[currentEngine] + encodeURIComponent(keyword), '_blank');
    }
    searchBtn.addEventListener('click', doSearch);
    searchInput.addEventListener('keydown', e=>e.key==='Enter'&&doSearch());
  </script>
</body>
</html>
