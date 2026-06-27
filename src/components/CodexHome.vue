<template>
  <div class="page">
    <div class="grid-bg" />
    <div class="scan-line" />

    <div class="glow-orb orb1" />
    <div class="glow-orb orb2" />
    <div class="glow-orb orb3" />

    <div class="corner corner-tl" />
    <div class="corner corner-tr" />
    <div class="corner corner-bl" />
    <div class="corner corner-br" />

    <div class="content">
      <div class="badge">
        <span class="dot" />
        v2.4.1 · 正式版
      </div>

      <h1 class="title">你好，<em>Codex</em>！</h1>

      <p class="subtitle">
        下一代开发体验，为创造者而生。<br />
        简洁、快速、无处不在。
      </p>

      <div class="actions">
        <button class="btn-primary" type="button" @click="onStart">开始使用</button>
        <button class="btn-ghost" type="button" @click="onLearnMore">了解更多 →</button>
      </div>

      <div class="stats">
        <div v-for="(stat, index) in stats" :key="stat.label" class="stat-group">
          <div v-if="index > 0" class="divider" />
          <div class="stat">
            <span class="stat-num">{{ stat.value }}</span>
            <span class="stat-label">{{ stat.label }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="ticker">
      <span
        v-for="(_, index) in 3"
        :key="index"
        class="ticker-dot"
        :class="{ active: activeDot === index }"
        @click="activeDot = index"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineOptions({
  name: 'CodexHome',
})

const activeDot = ref(0)

const stats = [
  { value: '12k+', label: '开发者' },
  { value: '99.9%', label: '可用性' },
  { value: '< 50ms', label: '响应时间' },
]

function onStart() {
  console.log('开始使用')
}

function onLearnMore() {
  console.log('了解更多')
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.page {
  align-items: center;
  background: #0a0a0f;
  display: flex;
  flex-direction: column;
  font-family: system-ui, sans-serif;
  justify-content: center;
  min-height: 100vh;
  overflow: hidden;
  position: relative;
}

/* Build the animated grid layer behind the page content. */
.grid-bg {
  animation: gridShift 20s linear infinite;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 48px 48px;
  inset: 0;
  position: absolute;
}

@keyframes gridShift {
  from {
    background-position: 0 0;
  }

  to {
    background-position: 48px 48px;
  }
}

/* Sweep a subtle scan line through the interface. */
.scan-line {
  animation: scan 8s linear infinite;
  background: linear-gradient(90deg, transparent, rgba(127, 119, 221, 0.4), transparent);
  height: 1px;
  left: 0;
  pointer-events: none;
  position: absolute;
  right: 0;
  z-index: 1;
}

@keyframes scan {
  0% {
    opacity: 0;
    top: -2px;
  }

  5% {
    opacity: 1;
  }

  95% {
    opacity: 1;
  }

  100% {
    opacity: 0;
    top: 100%;
  }
}

.glow-orb {
  animation: drift 12s ease-in-out infinite alternate;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.18;
  position: absolute;
}

.orb1 {
  animation-delay: 0s;
  background: #7f77dd;
  height: 360px;
  left: -60px;
  top: -80px;
  width: 360px;
}

.orb2 {
  animation-delay: -5s;
  background: #1d9e75;
  bottom: -60px;
  height: 280px;
  right: -40px;
  width: 280px;
}

.orb3 {
  animation-delay: -9s;
  background: #d85a30;
  height: 200px;
  left: 60%;
  top: 40%;
  width: 200px;
}

@keyframes drift {
  from {
    transform: translate(0, 0) scale(1);
  }

  to {
    transform: translate(30px, 20px) scale(1.08);
  }
}

.corner {
  border-color: rgba(127, 119, 221, 0.3);
  border-style: solid;
  height: 16px;
  position: absolute;
  width: 16px;
}

.corner-tl {
  border-width: 1px 0 0 1px;
  left: 24px;
  top: 24px;
}

.corner-tr {
  border-width: 1px 1px 0 0;
  right: 24px;
  top: 24px;
}

.corner-bl {
  border-width: 0 0 1px 1px;
  bottom: 24px;
  left: 24px;
}

.corner-br {
  border-width: 0 1px 1px 0;
  bottom: 24px;
  right: 24px;
}

.content {
  align-items: center;
  display: flex;
  flex-direction: column;
  gap: 24px;
  position: relative;
  z-index: 2;
}

.badge {
  align-items: center;
  animation: fadeSlideUp 0.6s ease both;
  background: rgba(127, 119, 221, 0.08);
  border: 0.5px solid rgba(127, 119, 221, 0.5);
  border-radius: 999px;
  color: #afa9ec;
  display: inline-flex;
  font-size: 12px;
  gap: 6px;
  letter-spacing: 0.08em;
  padding: 6px 14px;
}

.dot {
  animation: pulse 2s ease-in-out infinite;
  background: #7f77dd;
  border-radius: 50%;
  height: 6px;
  width: 6px;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
    transform: scale(1);
  }

  50% {
    opacity: 0.4;
    transform: scale(0.7);
  }
}

.title {
  animation: fadeSlideUp 0.6s 0.1s ease both;
  color: #f0efe8;
  font-size: clamp(36px, 6vw, 64px);
  font-weight: 500;
  line-height: 1.15;
  text-align: center;
}

.title em {
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background: linear-gradient(135deg, #afa9ec 0%, #7f77dd 50%, #5dcaa5 100%);
  background-clip: text;
  font-style: normal;
  font-weight: 600;
}

.subtitle {
  animation: fadeSlideUp 0.6s 0.2s ease both;
  color: rgba(240, 239, 232, 0.45);
  font-size: 16px;
  line-height: 1.7;
  max-width: 420px;
  text-align: center;
}

.actions {
  animation: fadeSlideUp 0.6s 0.3s ease both;
  display: flex;
  gap: 12px;
  margin-top: 8px;
}

.btn-primary {
  background: #7f77dd;
  border: none;
  border-radius: 8px;
  color: #eeedfe;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  padding: 10px 24px;
  transition:
    transform 0.15s,
    background 0.15s;
}

.btn-primary:hover {
  background: #534ab7;
  transform: translateY(-1px);
}

.btn-ghost {
  background: transparent;
  border: 0.5px solid rgba(240, 239, 232, 0.15);
  border-radius: 8px;
  color: rgba(240, 239, 232, 0.6);
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  padding: 10px 24px;
  transition:
    transform 0.15s,
    border-color 0.15s,
    color 0.15s;
}

.btn-ghost:hover {
  border-color: rgba(240, 239, 232, 0.35);
  color: rgba(240, 239, 232, 0.9);
  transform: translateY(-1px);
}

.stats {
  align-items: center;
  animation: fadeSlideUp 0.6s 0.4s ease both;
  display: flex;
  gap: 0;
  margin-top: 12px;
}

.stat-group {
  align-items: center;
  display: flex;
}

.stat {
  align-items: center;
  display: flex;
  flex-direction: column;
  gap: 2px;
  padding: 0 24px;
}

.stat-num {
  color: #f0efe8;
  font-size: 20px;
  font-weight: 500;
}

.stat-label {
  color: rgba(240, 239, 232, 0.35);
  font-size: 12px;
  letter-spacing: 0.06em;
}

.divider {
  background: rgba(240, 239, 232, 0.1);
  height: 36px;
  width: 0.5px;
}

.ticker {
  animation: fadeSlideUp 0.6s 0.5s ease both;
  bottom: 32px;
  display: flex;
  gap: 8px;
  justify-content: center;
  left: 0;
  position: absolute;
  right: 0;
  z-index: 2;
}

.ticker-dot {
  background: rgba(240, 239, 232, 0.15);
  border-radius: 50%;
  cursor: pointer;
  height: 8px;
  transition: background 0.2s;
  width: 8px;
}

.ticker-dot.active {
  background: #7f77dd;
}

@keyframes fadeSlideUp {
  from {
    opacity: 0;
    transform: translateY(16px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (prefers-reduced-motion: reduce) {
  .grid-bg,
  .scan-line,
  .glow-orb,
  .dot {
    animation: none;
  }

  .badge,
  .title,
  .subtitle,
  .actions,
  .stats,
  .ticker {
    animation: none;
  }
}
</style>
