<script setup>
// Plan → Execute → Review cycle graphic
</script>

<template>
  <div class="cycle-container">
    <!-- SVG orbital path with animated flow -->
    <svg class="cycle-svg" viewBox="0 0 500 240" fill="none" xmlns="http://www.w3.org/2000/svg">
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
        cx="250" cy="115"
        rx="190" ry="75"
        stroke="oklch(0.25 0.02 263.9)"
        stroke-width="1"
        fill="none"
        stroke-dasharray="4 8"
        class="orbit-ring"
      />

      <!-- Connecting arcs between nodes -->
      <!-- Plan to Execute -->
      <path
        d="M 95 85 Q 160 35, 250 50"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.4"
        filter="url(#glow)"
      />
      <path
        d="M 250 50 L 243 45 M 250 50 L 245 57"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.6"
      />

      <!-- Execute to Review -->
      <path
        d="M 290 60 Q 380 100, 400 140"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.4"
        filter="url(#glow)"
      />
      <path
        d="M 400 140 L 405 132 M 400 140 L 393 135"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.6"
      />

      <!-- Review to Plan -->
      <path
        d="M 380 175 Q 250 210, 95 145"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.4"
        filter="url(#glow)"
      />
      <path
        d="M 95 145 L 103 150 M 95 145 L 100 137"
        stroke="oklch(0.565 0.239 263.9)"
        stroke-width="2"
        fill="none"
        stroke-opacity="0.6"
      />

      <!-- Node: PLAN (left) -->
      <g class="node plan-node">
        <circle
          cx="70" cy="115" r="42"
          fill="oklch(0.15 0.02 263.9)"
          stroke="oklch(0.565 0.239 263.9)"
          stroke-width="2"
          filter="url(#glow)"
        />
        <circle
          cx="70" cy="115" r="42"
          fill="none"
          stroke="oklch(0.565 0.239 263.9)"
          stroke-width="1"
          stroke-opacity="0.3"
          stroke-dasharray="3 3"
          class="inner-ring"
        />
        <text
          x="70" y="111"
          text-anchor="middle"
          dominant-baseline="middle"
          fill="oklch(0.97 0.005 260)"
          class="node-label"
        >PLAN</text>
        <text
          x="70" y="127"
          text-anchor="middle"
          dominant-baseline="middle"
          fill="oklch(0.565 0.239 263.9)"
          class="node-sublabel"
        >strategy</text>
      </g>

      <!-- Node: EXECUTE (top) -->
      <g class="node execute-node">
        <circle
          cx="250" cy="50" r="42"
          fill="oklch(0.15 0.02 263.9)"
          stroke="oklch(0.65 0.20 155)"
          stroke-width="2"
          filter="url(#glow)"
        />
        <circle
          cx="250" cy="50" r="42"
          fill="none"
          stroke="oklch(0.65 0.20 155)"
          stroke-width="1"
          stroke-opacity="0.3"
          stroke-dasharray="3 3"
          class="inner-ring"
        />
        <text
          x="250" y="46"
          text-anchor="middle"
          dominant-baseline="middle"
          fill="oklch(0.97 0.005 260)"
          class="node-label"
        >IMPLEMENT</text>
        <text
          x="250" y="62"
          text-anchor="middle"
          dominant-baseline="middle"
          fill="oklch(0.65 0.20 155)"
          class="node-sublabel"
        >build</text>
      </g>

      <!-- Node: REVIEW (right) -->
      <g class="node review-node">
        <circle
          cx="420" cy="155" r="42"
          fill="oklch(0.15 0.02 263.9)"
          stroke="oklch(0.60 0.22 300)"
          stroke-width="2"
          filter="url(#glow)"
        />
        <circle
          cx="420" cy="155" r="42"
          fill="none"
          stroke="oklch(0.60 0.22 300)"
          stroke-width="1"
          stroke-opacity="0.3"
          stroke-dasharray="3 3"
          class="inner-ring"
        />
        <text
          x="420" y="151"
          text-anchor="middle"
          dominant-baseline="middle"
          fill="oklch(0.97 0.005 260)"
          class="node-label"
        >REVIEW</text>
        <text
          x="420" y="167"
          text-anchor="middle"
          dominant-baseline="middle"
          fill="oklch(0.60 0.22 300)"
          class="node-sublabel"
        >validate</text>
      </g>

      <!-- Center label -->
      <text
        x="250" y="205"
        text-anchor="middle"
        dominant-baseline="middle"
        fill="oklch(0.45 0.01 260)"
        class="center-label"
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
  max-width: 550px;
  height: auto;
}

/* Explicit text styling to prevent Slidev global style interference */
.cycle-svg .node-label {
  font-family: 'Outfit', sans-serif;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 0.05em;
}

.cycle-svg .node-sublabel {
  font-family: 'JetBrains Mono', monospace;
  font-size: 9px;
  opacity: 0.8;
}

.cycle-svg .center-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.1em;
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
