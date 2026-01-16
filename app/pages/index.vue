<script setup lang="ts">
definePageMeta({
  layout: 'empty',
})

function nav(url: string) {
  window.location.href = url
}

let dark = $ref(false)

onMounted(() => {
  if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
    dark = true
  } else if (window.matchMedia('(prefers-color-scheme: light)').matches) {
    dark = false
  }
})
</script>
<template>
  <div class="wrapper" id="wrapper" :class="{ dark }">
    <div class="content">
      <h1>Type Words</h1>
      <h2 class="font-normal m-0">学习英语，一次敲击，一点进步，开源单词与文章练习工具</h2>
      <div class="">
        <div class="base-button" @click="nav('/words')">开始单词练习</div>
        <div class="base-button" @click="nav('/articles')">开始文章练习</div>
      </div>

      <div class="container mb-4">
        <div class="card-wrap">
          <div class="card">
            <div class="emoji">📚</div>
            <div class="title">单词练习</div>
            <div class="desc">
              <ul>
                <li>四种模式：跟打/听写/自测/默写</li>
                <li>智能模式：智能规划复习与默写</li>
                <li>自由模式：不受限制，自行规划</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="emoji">✍️</div>
            <div class="title">文章练习</div>
            <div class="desc">
              <ul>
                <li>内置常见书籍，也可自行添加文章</li>
                <li>跟打 + 默写双模式，让背诵更高效</li>
                <li>支持边听边默写，强化记忆</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="emoji">📕</div>
            <div class="title">收藏、错词本、已掌握</div>
            <div class="desc">
              <ul>
                <li>输入错误自动添加到错词本</li>
                <li>主动添加到已掌握，后续自动跳过</li>
                <li>主动添加到收藏中，以便巩固复习</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="emoji">🌐</div>
            <div class="title">海量词库</div>
            <div class="desc">
              内置小学、初中、高中、四六级、考研、雅思、托福、GRE、GMAT、SAT、BEC、专四、专八等词库
            </div>
          </div>
        </div>
        <div class="card-wrap">
          <div class="card">
            <div class="emoji">🆓</div>
            <div class="title">免费开源</div>
            <div class="desc">
              <ul>
                <li>完全开源，可审查、可修改</li>
                <li>免费使用</li>
                <li>私有部署</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="emoji">⚙️</div>
            <div class="title">高度自由</div>
            <div class="desc">
              <ul>
                <li>丰富的键盘音效</li>
                <li>可自定义快捷键</li>
                <li>高度定制化的设置选项</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="emoji">🎨</div>
            <div class="title">简洁高效</div>
            <div class="desc">
              <ul>
                <li>简洁设计，现代化UI</li>
                <li>界面清爽，操作简单</li>
                <li>不强制关注任何平台</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="emoji">🎯</div>
            <div class="title">个性学习</div>
            <div class="desc">
              <ul>
                <li>自由添加词典与文章</li>
                <li>定制个性学习计划</li>
                <li>多种学习复习策略</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div>
      <div class="line"></div>
      <div class="w-full center gap-4 mt-6 mb-12">
        <channel-icons type="horizontal" :share="false" />
        <a href="https://beian.mps.gov.cn/#/query/webSearch?code=51015602001426" target="_blank"
          >川公网安备51015602001426号
        </a>
        <a href="https://beian.miit.gov.cn/" target="_blank">蜀ICP备2025157466号-2</a>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.wrapper {
  --color-bg: #e6e8eb;
  --color-card-bg: rgb(247, 247, 247);
  --color-card-text: #111827;
  --color-line: #cecece;
  --color-h2: rgb(91, 91, 91);
  --accent: #818cf8;
  --accent-2: #60a5fa;
  --shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
}

.wrapper.dark {
  --color-bg: #0e1217;
  --color-card-bg: rgb(30, 31, 34);
  --color-card-text: #c6c6c6;
  --color-line: #333333;
  --color-h2: rgb(151, 151, 151);
  --shadow: 0 10px 30px rgba(0, 0, 0, 0.35);

  :deep(.github) {
    color: white !important;
  }
}

.wrapper {
  background: var(--color-bg);
  font-family:
    ui-sans-serif,
    system-ui,
    -apple-system,
    Segoe UI,
    Roboto,
    Helvetica,
    Arial,
    'Apple Color Emoji',
    'Segoe UI Emoji';
  color: var(--color-card-text);
  @apply flex flex-col justify-between min-h-screen;

  .content {
    @apply mt-22 flex flex-col items-center gap-8;

    .container {
      width: min(1260px, 92%);

      .card-wrap {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
        margin-bottom: 1.2rem;
        gap: 1rem;
      }
    }
  }
}

h1 {
  font-size: 4.8rem !important;
  background: linear-gradient(120deg, #bd34fe 30%, #41d1ff);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  @apply m-0 font-bold color-transparent bg-clip-text;
}

.card {
  @apply w-auto relative rounded-xl p-5 box-border flex flex-col items-start gap-2 mb-0;
  background: var(--color-card-bg);
  color: var(--color-card-text);
  box-shadow: var(--shadow);
  border: 1px solid var(--color-line);
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease;

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.12);
  }

  .title {
    @apply font-bold;
  }

  .emoji {
    @apply inline-block bg-third rounded-lg p-1.5 text-xl;
  }

  ul {
    @apply mt-0 pl-4;
  }
}

.base-button {
  @apply inline-flex items-center justify-center outline-none text-center transition-all duration-200 user-select-none
   vertical-align-middle whitespace-nowrap rounded-lg cp text-white p-x-5 h-11;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  box-shadow: 0 8px 20px rgba(129, 140, 248, 0.25);
}

.base-button + .base-button {
  @apply ml-8;
}

.base-button:hover {
  transform: translateY(-1px);
  opacity: 0.95;
}

.line {
  border-bottom: 1px solid var(--color-line);
}

@media (max-width: 768px) {
  h1 {
    font-size: 3rem !important;
  }

  .content {
    margin-top: 4rem;
    gap: 1.4rem;
  }

  .base-button {
    width: 100%;
    margin: 0.5rem 0;
    height: 2.8rem;
    font-size: 1rem;
  }

  .base-button + .base-button {
    margin-left: 0;
  }
}

@media (max-width: 480px) {
  h1 {
    font-size: 2.4rem !important;
  }

  .content {
    margin-top: 3.2rem;
    gap: 1.2rem;
  }
}
</style>
