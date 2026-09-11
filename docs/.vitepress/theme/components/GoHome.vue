<script setup lang="ts">
import { ArrowRight, Braces, House, Server, Sparkles, Terminal, Workflow } from '@lucide/vue'
import { withBase } from 'vitepress'

const topics = [
  { number: '01', icon: Braces, title: '打好 Go 语言基础', en: 'FOUNDATION', description: '从类型、函数到接口，理解 Go 的设计，写出清晰易读的代码。', tags: ['类型系统', '接口', '标准库'], color: 'cyan' },
  { number: '02', icon: Workflow, title: '理解并发编程', en: 'CONCURRENCY', description: '掌握 goroutine 与 channel，让并发任务有序协作。', tags: ['Goroutine', 'Channel', 'Context'], color: 'blue' },
  { number: '03', icon: Server, title: '走向工程实践', en: 'ENGINEERING', description: '串联服务开发、测试与性能分析，构建可靠的后端应用。', tags: ['HTTP 服务', '单元测试', 'pprof'], color: 'teal' },
]

const nodes = [
  { icon: Braces, title: '语言基础', detail: 'Types · Interfaces', position: 'markup' },
  { icon: Workflow, title: '并发协作', detail: 'Goroutine · Channel', position: 'styles' },
  { icon: Server, title: '服务开发', detail: 'HTTP · API', position: 'logic' },
  { icon: Terminal, title: '工程工具', detail: 'Modules · Test', position: 'frameworks' },
]

const flowPaths = [
  'M110 96 H174 Q198 96 198 120 V161 Q198 175 218 175 H250',
  'M110 256 H174 Q198 256 198 232 V203 Q198 189 218 189 H250',
  'M310 175 H345 Q370 175 370 151 V120 Q370 96 394 96 H450',
  'M310 189 H345 Q370 189 370 213 V232 Q370 256 394 256 H450',
]
</script>

<template>
  <div class="web-home">
    <section class="web-hero" aria-labelledby="web-title">
      <div class="web-intro">
        <p class="web-eyebrow"><i /> 在这里，用简洁代码构建可靠服务</p>
        <h1 id="web-title">走进 Go 语言的世界<br><span>简洁表达，高效并发。</span></h1>
        <p class="web-description">从第一句 Hello, World，到并发服务。<br>系统学习 Go 的语言基础、并发模型与工程实践。</p>
        <div class="web-actions">
          <a class="web-secondary" :href="withBase('/')"><House :size="17" />首页</a>
          <a class="web-primary" :href="withBase('/guide/')">开启学习之旅<ArrowRight :size="17" /></a>
        </div>
        <div class="web-notes"><span>体系清晰</span><span>简洁务实</span><span>持续实践</span></div>
      </div>

      <div class="web-visual" role="img" aria-label="Go 知识体系：以 Go 语言为核心，连接语言基础、并发协作、服务开发与工程工具。">
        <div class="visual-label"><span><i /> THE GO JOURNEY</span><span>从基础到服务</span></div>
        <div class="web-orbit orbit-one" /><div class="web-orbit orbit-two" />
        <svg class="web-connectors" viewBox="0 0 560 350" fill="none" aria-hidden="true">
          <g v-for="(path, index) in flowPaths" :key="path">
            <path :d="path" />
            <path class="web-flow" :d="path" pathLength="100" :style="{ animationDelay: `${index * -0.8}s` }" />
          </g>
        </svg>
        <div v-for="node in nodes" :key="node.position" class="web-node" :class="node.position">
          <component :is="node.icon" :size="24" :stroke-width="1.6" />
          <strong>{{ node.title }}</strong><small>{{ node.detail }}</small>
        </div>
        <div class="web-core"><img :src="withBase('/logo.svg')" alt="" width="64" height="40"><strong>GO</strong><small>简洁 · 并发 · 高效</small></div>
        <div class="visual-caption"><Sparkles :size="14" /> 以简洁应对复杂，让并发井然有序</div>
      </div>
    </section>

    <div class="web-stack"><span>构建你的技术视野</span><div><b>Go</b><i /><b>Goroutine</b><i /><b>Channel</b><i /><b>net/http</b><i /><b>Modules</b></div><span>简洁设计 · 高效协作</span></div>

    <section class="web-learning" aria-labelledby="learning-title">
      <div class="learning-heading"><div><p>LEARN · BUILD · GO</p><h2 id="learning-title">每一步积累，都让下一次构建更从容</h2></div><span>循序渐进，构建你的 Go 知识体系</span></div>
      <div class="web-topics">
        <article v-for="topic in topics" :key="topic.number" class="web-topic" :class="topic.color">
          <div class="topic-top"><div class="topic-icon"><component :is="topic.icon" :size="23" :stroke-width="1.7" /></div><span>{{ topic.number }} / {{ topic.en }}</span></div>
          <h3>{{ topic.title }}</h3><p>{{ topic.description }}</p><div class="topic-tags"><span v-for="tag in topic.tags" :key="tag">{{ tag }}</span></div>
        </article>
      </div>
    </section>
    <p class="web-closing"><span />保持好奇，把每一行 Go 写得更清晰<span /></p>
  </div>
</template>

<style scoped>
.web-home { --web-text: #183641; --web-muted: #526e79; --web-accent: var(--web-primary); --web-line: #cee5eb; --web-surface: rgb(255 255 255 / 78%); max-width: 1200px; margin: 0 auto; padding: clamp(24px, 4vh, 40px) 32px 16px; color: var(--web-text); line-height: 1.5; }
.web-hero { display: grid; grid-template-columns: 1fr 1fr; align-items: center; gap: 48px; padding: 8px 0 clamp(20px, 3vh, 28px); }
.web-eyebrow { display: flex; align-items: center; gap: 10px; margin: 0 0 10px; color: var(--web-accent); font-size: 12px; letter-spacing: 2px; }
.web-eyebrow i, .visual-label i { display: inline-block; width: 6px; height: 6px; border-radius: 50%; background: var(--web-primary); box-shadow: 0 0 0 4px rgb(0 125 156 / 11%); }
.web-intro h1 { margin: 0; padding: 0; text-align: left; font-size: clamp(30px, 3vw, 40px); line-height: 1.3; letter-spacing: 0; font-weight: 750; }
.web-intro h1::after { display: none; }
.web-intro h1 span { color: var(--web-accent); background: linear-gradient(105deg, #007d9c, #009fbd 56%, #168b8b); background-clip: text; -webkit-text-fill-color: transparent; }
.web-description { margin: 10px 0 14px; color: var(--web-muted); font-size: 15px; line-height: 1.6; }
.web-actions { display: flex; flex-wrap: wrap; gap: 12px; }
.web-actions a { display: inline-flex; align-items: center; justify-content: center; gap: 14px; padding: 10px 18px; border-radius: 8px; font-size: 13px; line-height: 24px; font-weight: 600; transition: transform .2s, box-shadow .2s; }
.web-actions a:hover { transform: translateY(-2px); box-shadow: 0 6px 16px rgb(0 125 156 / 18%); }
.web-actions a:focus-visible { outline: 3px solid var(--web-accent); outline-offset: 4px; }
.web-primary { background: linear-gradient(110deg, #007d9c, #009fbd); color: #fff; }
.web-secondary { border: 1px solid #a4d5df; background: rgb(0 125 156 / 6%); color: var(--web-accent); }
.web-notes { display: flex; gap: 22px; margin-top: 12px; color: var(--web-muted); font-size: 11px; }
.web-notes span::before { content: '•'; margin-right: 7px; color: #65b7c9; }
.web-visual { position: relative; width: 100%; aspect-ratio: 560 / 350; background-image: radial-gradient(rgb(0 125 156 / 16%) .8px, transparent .8px); background-size: 18px 18px; }
.visual-label { position: absolute; inset: 0 0 auto; display: flex; justify-content: space-between; color: var(--web-muted); font-size: 9px; letter-spacing: 1.8px; }
.visual-label i { margin-right: 9px; }.visual-label > span:last-child { letter-spacing: 0; }
.web-connectors { position: absolute; inset: 0; width: 100%; height: 100%; stroke: #98cbd7; stroke-width: 1.2; }
.web-orbit { position: absolute; top: 52%; left: 50%; aspect-ratio: 1; transform: translate(-50%, -50%); border: 1px solid rgb(0 125 156 / 10%); border-radius: 50%; }
.orbit-one { width: 44%; }.orbit-two { width: 60%; }
.web-node { position: absolute; display: flex; width: 23%; height: 25%; flex-direction: column; align-items: center; justify-content: center; gap: 6px; border: 1px solid #b2dae4; border-radius: 8px; background: var(--web-surface); color: #007d9c; }
.web-node strong { color: var(--web-text); font-size: 12px; }.web-node small { color: var(--web-muted); font-size: 9px; }
.markup { left: 2%; top: 15%; }.styles { left: 2%; bottom: 14%; border-color: #a8dcd5; color: #087f80; }.logic { right: 2%; top: 15%; border-color: #b0cfe9; color: #2879b0; }.frameworks { right: 2%; bottom: 14%; border-color: #a8dcd5; color: #087f80; }
.web-core { position: absolute; top: 52%; left: 50%; display: flex; width: 24%; height: 37%; transform: translate(-50%, -50%); flex-direction: column; align-items: center; justify-content: center; gap: 10px; border: 1px solid #8acbd9; border-radius: 8px; background: linear-gradient(140deg, #e6f8fc, #e5f6f3); box-shadow: 0 0 0 7px rgb(255 255 255 / 42%), 0 12px 35px rgb(0 125 156 / 11%); color: #007d9c; }
.web-core img { object-fit: contain; }
.web-core strong { font-size: 20px; letter-spacing: 4px; font-weight: 500; }.web-core small { font-size: 9px; letter-spacing: 1px; }
.visual-caption { position: absolute; bottom: 0; display: flex; width: 100%; align-items: center; justify-content: center; gap: 7px; color: var(--web-muted); font-size: 10px; }
.web-stack { display: flex; align-items: center; justify-content: space-between; gap: 20px; padding: 12px 0; border-block: 1px solid var(--web-line); color: var(--web-muted); font-size: 11px; }
.web-stack > div { display: flex; align-items: center; gap: 25px; }.web-stack b { font-size: 16px; font-weight: 600; line-height: 24px; letter-spacing: 0; }.web-stack i { width: 3px; height: 3px; border-radius: 50%; background: #98cbd7; }
.web-learning { padding-top: clamp(20px, 3vh, 28px); }.learning-heading { display: flex; align-items: flex-end; justify-content: space-between; gap: 16px; margin-bottom: 18px; }.learning-heading p { margin: 0 0 8px; color: var(--web-accent); font-size: 9px; letter-spacing: 2px; }.learning-heading h2 { margin: 0; padding: 0; border: 0; font-size: 20px; font-weight: 650; line-height: 1.5; letter-spacing: 0; }.learning-heading > span { color: var(--web-muted); font-size: 11px; }
.web-topics { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }.web-topic { --topic-color: #007d9c; --topic-border: #b2dae4; --topic-tint: rgb(0 125 156 / 7%); position: relative; overflow: hidden; padding: 20px; border: 1px solid var(--topic-border); border-radius: 8px; background: var(--web-surface); }.web-topic::before { position: absolute; top: 0; right: 18px; left: 18px; height: 2px; content: ''; background: linear-gradient(90deg, var(--topic-color), transparent); opacity: .65; }
.blue { --topic-color: #2879b0; --topic-border: #b0cfe9; --topic-tint: rgb(40 121 176 / 7%); }.teal { --topic-color: #087f80; --topic-border: #a8dcd5; --topic-tint: rgb(8 127 128 / 8%); }
.topic-top { display: flex; align-items: center; gap: 12px; color: var(--topic-color); }.topic-top > span { font-size: 9px; line-height: 24px; letter-spacing: 1px; }.topic-icon { padding: 7px; border-radius: 8px; background: var(--topic-tint); }.web-topic h3 { margin: 8px 0 5px; font-size: 17px; font-weight: 650; }.web-topic p { margin: 0; color: var(--web-muted); font-size: 11px; line-height: 1.7; white-space: normal; }.topic-tags { display: flex; flex-wrap: wrap; gap: 7px; margin-top: 10px; }.topic-tags span { padding: 2px 8px; border-radius: 4px; background: var(--topic-tint); color: var(--topic-color); font-size: 10px; line-height: 16px; }
.web-closing { display: flex; align-items: center; justify-content: center; gap: 14px; margin: clamp(18px, 2.5vh, 24px) 0 0; color: var(--web-muted); font-size: 11px; }.web-closing span { width: 24px; height: 1px; background: var(--web-line); }
.web-flow { stroke: var(--web-accent); stroke-width: 2; stroke-linecap: round; stroke-dasharray: 5 95; animation: web-flow 4s linear infinite; }
.web-core::before { position: absolute; inset: -8px; content: ''; border: 1px solid rgb(0 125 156 / 32%); border-radius: 12px; animation: web-pulse 4s ease-out infinite; pointer-events: none; }
.web-core > img { animation: web-float 5s ease-in-out infinite; }.visual-label i { animation: web-beacon 3s ease-in-out infinite; }
@keyframes web-flow { to { stroke-dashoffset: -100; } } @keyframes web-pulse { 0% { transform: scale(1); opacity: .65; } 85%, 100% { transform: scale(1.25); opacity: 0; } } @keyframes web-float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-4px); } } @keyframes web-beacon { 0%, 100% { opacity: 1; } 50% { opacity: .4; } }
:global(.is-home-page .Layout:has(.web-home)) { background-image: radial-gradient(ellipse at 72% 18%, rgb(153 224 240 / 24%), transparent 46%), linear-gradient(150deg, rgb(222 246 251 / 70%), transparent 58%), linear-gradient(215deg, rgb(216 244 237 / 42%), transparent 58%); background-size: auto; }
:global(.VPHome:has(.web-home)) { margin-bottom: 0; }:global(.Layout:has(.web-home) .VPFooter) { padding: 16px 24px; }
:global(.dark .web-home) { --web-text: #e0f3f7; --web-muted: #abc8d1; --web-accent: #5ccfe6; --web-line: #294a57; --web-surface: rgb(20 39 48 / 84%); }
:global(.dark .is-home-page .Layout:has(.web-home)), :global(.dark.is-home-page .Layout:has(.web-home)) { background-image: radial-gradient(ellipse at 70% 18%, rgb(0 125 156 / 22%), transparent 50%), linear-gradient(145deg, rgb(15 90 105 / 28%), transparent 65%); }
:global(.dark .web-home .web-core) { border-color: #337688; background: linear-gradient(140deg, #173e4c, #17494c); box-shadow: 0 0 0 7px rgb(92 207 230 / 8%); color: #80deed; }
:global(.dark .web-home .web-topic) { --topic-border: #315f70; --topic-color: #79d4e8; }:global(.dark .web-home .blue) { --topic-border: #355b7c; --topic-color: #94c9f4; }:global(.dark .web-home .teal) { --topic-border: #326865; --topic-color: #7bd9cd; }
@media (max-width: 960px) { .web-hero { gap: 24px; }.web-stack > span:last-child, .learning-heading > span { display: none; }.web-stack > div { gap: 18px; }.web-core { gap: 5px; }.web-core img { width: 32px; } }
@media (max-width: 700px) { .web-home { padding: 32px 24px 20px; }.web-hero { grid-template-columns: 1fr; gap: 36px; padding-bottom: 30px; }.web-intro { text-align: center; }.web-eyebrow, .web-actions, .web-notes { justify-content: center; }.web-intro h1 { text-align: center; font-size: clamp(27px, 6vw, 38px); line-height: 1.4; }.web-description { font-size: 13px; line-height: 1.8; }.web-visual { max-width: 520px; margin: auto; }.web-stack { flex-direction: column; gap: 12px; }.web-stack > div { gap: 12px; }.web-stack b { font-size: 12px; }.web-learning { padding-top: 30px; }.learning-heading h2 { font-size: 18px; }.web-topics { grid-template-columns: 1fr; gap: 14px; }.web-topic { padding: 20px; }.web-topic h3 { font-size: 15px; line-height: 22px; }.web-topic p { line-height: 1.6; }.web-closing { gap: 8px; font-size: 10px; }.web-closing span { width: 12px; }.web-node { gap: 4px; }.web-node > svg { width: 19px; height: 19px; flex-shrink: 0; }.web-node strong { font-size: 10px; line-height: 1.4; }.web-node small { font-size: 7px; line-height: 1.4; white-space: nowrap; }.web-core { gap: 4px; }.web-core > img { width: 28px; height: 28px; }.web-core strong { font-size: 16px; letter-spacing: 2px; }.web-core small { font-size: 7px; letter-spacing: 0; } }
@media (min-width: 961px) and (max-height: 900px) { .web-home { padding-top: 16px; padding-bottom: 12px; }.web-hero { padding-bottom: 16px; }.web-visual { max-width: 408px; justify-self: end; }.web-intro h1 { font-size: 32px; }.web-eyebrow { margin-bottom: 8px; }.web-description { margin: 12px 0; line-height: 1.7; }.web-actions a { padding: 10px 16px; }.web-notes { margin-top: 8px; }.web-learning { padding-top: 16px; }.learning-heading { margin-bottom: 12px; }.learning-heading h2 { font-size: 18px; }.learning-heading p { margin-bottom: 5px; }.web-topic { padding: 16px; }.web-topic h3 { margin-top: 10px; margin-bottom: 6px; }.web-topic p { margin-bottom: 10px; }.web-closing { margin-top: 18px; }:global(.Layout:has(.web-home) .VPFooter) { padding: 12px 24px; } }
@media (prefers-reduced-motion: reduce) { .web-flow, .web-core::before, .web-core > img, .visual-label i { animation: none; }.web-flow, .web-core::before { opacity: 0; }.web-actions a { transition: none; }.web-actions a:hover { transform: none; } }
@media (max-width: 700px) { .web-topic p { white-space: normal; } }
</style>
