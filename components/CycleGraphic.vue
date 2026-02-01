<script setup>
// Plan → Execute → Review cycle graphic
</script>

<template>
  <div class="cycle-container">
    <!-- SVG orbital path with animated flow -->
    <svg class="cycle-svg" viewBox="0 0 400 220" fill="none" xmlns="http://www.w3.org/2000/svg">
      <!-- Outer glow filter -->
      <defs>
        <filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
          <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
          <feMerge>
            <feMergeNode in="coloredBlur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <filter id="softGlow" x="-50%" y="-50%" width="200%" height="200%">
          <feGaussianBlur stdDeviation="8" result="coloredBlur"/>
          <feMerge>
            <feMergeNode in="coloredBlur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <!-- Gradient for animated path -->
        <linearGradient id="pathGradient" gradientUnits="userSpaceOnUse">
          <stop offset="0%" stop-color="oklch(0.565 0.239 263.9)" stop-opacity="0.1"/>
          <stop offset="50%" stop-color="oklch(0.65 0.28 263.9)" stop-opacity="0.6"/>
          <stop offset="100%" stop-color="oklch(0.565 0.239 263.9)" stop-opacity="0.1"/>
        </linearGradient>
      </defs>

      <!-- Background orbital ring - subtle -->
      <ellipse
        cx="200" cy="110"
        rx="160" ry="70"
        stroke="oklch(0.25 0.02 263.9)"
        stroke-width="1"
        fill="none"
        stroke-dasharray="4 8"
        class="orbit-ring"
      />

      <!-- Connecting arcs between nodes -->
      <!-- Plan to Execute -->
      <path
        d="M 85 85 Q 140 40, 200 55"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.4"
        filter="url(#glow)"
      />
      <path
        d="M 200 55 L 193 50 M 200 55 L 195 62"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.6"
      />

      <!-- Execute to Review -->
      <path
        d="M 235 70 Q 310 100, 315 135"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.4"
        filter="url(#glow)"
      />
      <path
        d="M 315 135 L 320 127 M 315 135 L 308 130"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.6"
      />

      <!-- Review to Plan -->
      <path
        d="M 285 165 Q 200 200, 85 140"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.4"
        filter="url(#glow)"
      />
      <path
        d="M 85 140 L 93 145 M 85 140 L 90 132"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.6"
      />

      <!-- Node: PLAN (left) -->
      <g class="node plan-node">
        <circle
          cx="60" cy="110" r="42"
          fill="oklch(0.15 0.02 263.9)"
          stroke="oklch(0.565 0.239 263.9)"
          stroke-width="2"
          filter="url(#glow)"
        />
        <circle
          cx="60" cy="110" r="42"
          fill="none"
          stroke="oklch(0.565 0.239 263.9)"
          stroke-width="1"
          stroke-opacity="0.3"
          stroke-dasharray="3 3"
          class="inner-ring"
        />
        <text
          x="60" y="106"
          text-anchor="middle"
          fill="oklch(0.97 0.005 260)"
          font-family="Outfit, sans-serif"
          font-size="14"
          font-weight="600"
          letter-spacing="0.05em"
        >PLAN</text>
        <text
          x="60" y="122"
          text-anchor="middle"
          fill="oklch(0.565 0.239 263.9)"
          font-family="JetBrains Mono, monospace"
          font-size="9"
          opacity="0.8"
        >strategy</text>
      </g>

      <!-- Node: EXECUTE (top) -->
      <g class="node execute-node">
        <circle
          cx="200" cy="55" r="42"
          fill="oklch(0.15 0.02 263.9)"
          stroke="oklch(0.65 0.20 155)"
          stroke-width="2"
          filter="url(#glow)"
        />
        <circle
          cx="200" cy="55" r="42"
          fill="none"
          stroke="oklch(0.65 0.20 155)"
          stroke-width="1"
          stroke-opacity="0.3"
          stroke-dasharray="3 3"
          class="inner-ring"
        />
        <text
          x="200" y="51"
          text-anchor="middle"
          fill="oklch(0.97 0.005 260)"
          font-family="Outfit, sans-serif"
          font-size="14"
          font-weight="600"
          letter-spacing="0.05em"
        >EXECUTE</text>
        <text
          x="200" y="67"
          text-anchor="middle"
          fill="oklch(0.65 0.20 155)"
          font-family="JetBrains Mono, monospace"
          font-size="9"
          opacity="0.8"
        >implement</text>
      </g>

      <!-- Node: REVIEW (right) -->
      <g class="node review-node">
        <circle
          cx="320" cy="145" r="42"
          fill="oklch(0.15 0.02 263.9)"
          stroke="oklch(0.60 0.22 300)"
          stroke-width="2"
          filter="url(#glow)"
        />
        <circle
          cx="320" cy="145" r="42"
          fill="none"
          stroke="oklch(0.60 0.22 300)"
          stroke-width="1"
          stroke-opacity="0.3"
          stroke-dasharray="3 3"
          class="inner-ring"
        />
        <text
          x="320" y="141"
          text-anchor="middle"
          fill="oklch(0.97 0.005 260)"
          font-family="Outfit, sans-serif"
          font-size="14"
          font-weight="600"
          letter-spacing="0.05em"
        >REVIEW</text>
        <text
          x="320" y="157"
          text-anchor="middle"
          fill="oklch(0.60 0.22 300)"
          font-family="JetBrains Mono, monospace"
          font-size="9"
          opacity="0.8"
        >validate</text>
      </g>

      <!-- Center label -->
      <text
        x="200" y="175"
        text-anchor="middle"
        fill="oklch(0.45 0.01 260)"
        font-family="JetBrains Mono, monospace"
        font-size="10"
        letter-spacing="0.1em"
      >THE DEVELOPMENT CYCLE</text>
    </svg>
  </div>
</template>

<style scoped>
.cycle-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem 0;
}

.cycle-svg {
  width: 100%;
  max-width: 480px;
  height: auto;
}

.orbit-ring {
  animation: orbit-rotate 60s linear infinite;
  transform-origin: center;
}

.inner-ring {
  animation: dash-rotate 20s linear infinite;
  transform-origin: center;
}

.node {
  transition: transform 0.3s ease;
}

@keyframes orbit-rotate {
  from {
    stroke-dashoffset: 0;
  }
  to {
    stroke-dashoffset: 100;
  }
}

@keyframes dash-rotate {
  from {
    stroke-dashoffset: 0;
  }
  to {
    stroke-dashoffset: 50;
  }
}
</style>
