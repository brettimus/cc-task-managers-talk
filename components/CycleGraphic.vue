<script setup>
// Plan → Implement → Review cycle graphic
// Iteration 3: Refined "Constellation Flow" - cleaner, more atmospheric
</script>

<template>
  <div class="cycle-container">
    <svg class="cycle-svg" viewBox="0 0 520 280" fill="none" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <!-- Central radial atmosphere -->
        <radialGradient id="centerGlow" cx="50%" cy="45%" r="55%">
          <stop offset="0%" stop-color="oklch(0.5 0.15 263.9)" stop-opacity="0.08"/>
          <stop offset="50%" stop-color="oklch(0.4 0.1 263.9)" stop-opacity="0.03"/>
          <stop offset="100%" stop-color="oklch(0.2 0.05 263.9)" stop-opacity="0"/>
        </radialGradient>

        <!-- Node auras - more intense -->
        <radialGradient id="planAura" cx="50%" cy="50%" r="70%">
          <stop offset="0%" stop-color="oklch(0.6 0.26 263.9)" stop-opacity="0.35"/>
          <stop offset="50%" stop-color="oklch(0.55 0.22 263.9)" stop-opacity="0.12"/>
          <stop offset="100%" stop-color="oklch(0.5 0.18 263.9)" stop-opacity="0"/>
        </radialGradient>
        <radialGradient id="implementAura" cx="50%" cy="50%" r="70%">
          <stop offset="0%" stop-color="oklch(0.68 0.24 155)" stop-opacity="0.35"/>
          <stop offset="50%" stop-color="oklch(0.62 0.20 155)" stop-opacity="0.12"/>
          <stop offset="100%" stop-color="oklch(0.55 0.16 155)" stop-opacity="0"/>
        </radialGradient>
        <radialGradient id="reviewAura" cx="50%" cy="50%" r="70%">
          <stop offset="0%" stop-color="oklch(0.65 0.26 300)" stop-opacity="0.35"/>
          <stop offset="50%" stop-color="oklch(0.58 0.22 300)" stop-opacity="0.12"/>
          <stop offset="100%" stop-color="oklch(0.52 0.18 300)" stop-opacity="0"/>
        </radialGradient>

        <!-- Filters -->
        <filter id="softGlow" x="-60%" y="-60%" width="220%" height="220%">
          <feGaussianBlur stdDeviation="4" result="blur"/>
          <feMerge>
            <feMergeNode in="blur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <filter id="particleGlow" x="-200%" y="-200%" width="500%" height="500%">
          <feGaussianBlur stdDeviation="3" result="blur"/>
          <feMerge>
            <feMergeNode in="blur"/>
            <feMergeNode in="blur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <filter id="pathGlow" x="-40%" y="-40%" width="180%" height="180%">
          <feGaussianBlur stdDeviation="2.5" result="blur"/>
          <feMerge>
            <feMergeNode in="blur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <filter id="starGlow" x="-100%" y="-100%" width="300%" height="300%">
          <feGaussianBlur stdDeviation="1" result="blur"/>
          <feMerge>
            <feMergeNode in="blur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>

        <!-- Path gradients -->
        <linearGradient id="flowGradient1" gradientUnits="userSpaceOnUse" x1="80" y1="130" x2="260" y2="65">
          <stop offset="0%" stop-color="oklch(0.6 0.26 263.9)"/>
          <stop offset="100%" stop-color="oklch(0.68 0.24 155)"/>
        </linearGradient>
        <linearGradient id="flowGradient2" gradientUnits="userSpaceOnUse" x1="260" y1="65" x2="440" y2="170">
          <stop offset="0%" stop-color="oklch(0.68 0.24 155)"/>
          <stop offset="100%" stop-color="oklch(0.65 0.26 300)"/>
        </linearGradient>
        <linearGradient id="flowGradient3" gradientUnits="userSpaceOnUse" x1="440" y1="170" x2="80" y2="130">
          <stop offset="0%" stop-color="oklch(0.65 0.26 300)"/>
          <stop offset="100%" stop-color="oklch(0.6 0.26 263.9)"/>
        </linearGradient>
      </defs>

      <!-- Background atmosphere -->
      <rect x="0" y="0" width="520" height="280" fill="url(#centerGlow)"/>

      <!-- Scattered stars/particles for depth -->
      <g class="stars">
        <circle cx="45" cy="45" r="1" fill="oklch(0.7 0.15 263.9)" opacity="0.4" class="star s1"/>
        <circle cx="480" cy="60" r="1.2" fill="oklch(0.65 0.12 155)" opacity="0.35" class="star s2"/>
        <circle cx="95" cy="220" r="0.8" fill="oklch(0.6 0.1 300)" opacity="0.3" class="star s3"/>
        <circle cx="420" cy="240" r="1" fill="oklch(0.65 0.15 263.9)" opacity="0.35" class="star s4"/>
        <circle cx="180" cy="35" r="0.7" fill="oklch(0.7 0.12 200)" opacity="0.25" class="star s5"/>
        <circle cx="350" cy="250" r="0.9" fill="oklch(0.6 0.1 263.9)" opacity="0.3" class="star s6"/>
        <circle cx="500" cy="140" r="1.1" fill="oklch(0.55 0.08 300)" opacity="0.25" class="star s7"/>
        <circle cx="25" cy="150" r="0.8" fill="oklch(0.65 0.1 155)" opacity="0.3" class="star s8"/>
      </g>

      <!-- Orbital ellipse -->
      <ellipse
        cx="260" cy="130"
        rx="195" ry="80"
        fill="none"
        stroke="oklch(0.4 0.1 263.9)"
        stroke-width="1"
        stroke-dasharray="4 10"
        opacity="0.5"
        class="orbit-ring"
      />

      <!-- Node auras -->
      <ellipse cx="80" cy="130" rx="75" ry="60" fill="url(#planAura)" class="aura plan-aura"/>
      <ellipse cx="260" cy="65" rx="75" ry="60" fill="url(#implementAura)" class="aura implement-aura"/>
      <ellipse cx="440" cy="170" rx="75" ry="60" fill="url(#reviewAura)" class="aura review-aura"/>

      <!-- Connection paths -->
      <path
        class="flow-path p1"
        d="M 118 110 C 170 50, 215 38, 260 48"
        stroke="url(#flowGradient1)"
        stroke-width="2.5"
        fill="none"
        stroke-linecap="round"
        filter="url(#pathGlow)"
      />
      <path
        class="flow-path p2"
        d="M 298 78 C 365 100, 408 130, 425 155"
        stroke="url(#flowGradient2)"
        stroke-width="2.5"
        fill="none"
        stroke-linecap="round"
        filter="url(#pathGlow)"
      />
      <path
        class="flow-path p3"
        d="M 405 195 C 310 228, 155 205, 90 155"
        stroke="url(#flowGradient3)"
        stroke-width="2.5"
        fill="none"
        stroke-linecap="round"
        filter="url(#pathGlow)"
      />

      <!-- Animated particles -->
      <circle class="particle" r="4.5" fill="oklch(0.78 0.28 263.9)" filter="url(#particleGlow)">
        <animateMotion dur="3s" repeatCount="indefinite" keyPoints="0;1" keyTimes="0;1" calcMode="spline" keySplines="0.25 0.1 0.25 1" path="M 118 110 C 170 50, 215 38, 260 48"/>
      </circle>
      <circle class="particle" r="4.5" fill="oklch(0.75 0.26 155)" filter="url(#particleGlow)">
        <animateMotion dur="2.8s" repeatCount="indefinite" begin="0.6s" keyPoints="0;1" keyTimes="0;1" calcMode="spline" keySplines="0.25 0.1 0.25 1" path="M 298 78 C 365 100, 408 130, 425 155"/>
      </circle>
      <circle class="particle" r="4.5" fill="oklch(0.72 0.28 300)" filter="url(#particleGlow)">
        <animateMotion dur="3.8s" repeatCount="indefinite" begin="0.3s" keyPoints="0;1" keyTimes="0;1" calcMode="spline" keySplines="0.25 0.1 0.25 1" path="M 405 195 C 310 228, 155 205, 90 155"/>
      </circle>

      <!-- Direction indicators -->
      <polygon points="257,48 248,40 250,51" fill="oklch(0.72 0.26 155)" opacity="0.85" class="arrow a1"/>
      <polygon points="427,158 418,147 429,151" fill="oklch(0.68 0.28 300)" opacity="0.85" class="arrow a2"/>
      <polygon points="88,152 96,163 94,150" fill="oklch(0.65 0.26 263.9)" opacity="0.85" class="arrow a3"/>

      <!-- Node: PLAN -->
      <g class="node plan-node">
        <polygon
          points="80,92 120,112 120,148 80,168 40,148 40,112"
          fill="oklch(0.12 0.04 263.9)"
          stroke="oklch(0.6 0.26 263.9)"
          stroke-width="2"
          filter="url(#softGlow)"
          class="hex"
        />
        <polygon
          points="80,100 112,116 112,144 80,160 48,144 48,116"
          fill="none"
          stroke="oklch(0.55 0.22 263.9)"
          stroke-width="0.5"
          stroke-opacity="0.5"
          stroke-dasharray="5 4"
          class="hex-inner"
        />
        <circle cx="120" cy="112" r="5" fill="oklch(0.6 0.26 263.9)" class="conn"/>
        <circle cx="120" cy="112" r="5" fill="oklch(0.6 0.26 263.9)" class="conn-pulse"/>

        <text x="80" y="126" text-anchor="middle" dominant-baseline="middle" class="node-label">PLAN</text>
        <text x="80" y="145" text-anchor="middle" dominant-baseline="middle" class="node-sub plan-sub">strategy</text>
      </g>

      <!-- Node: IMPLEMENT -->
      <g class="node implement-node">
        <polygon
          points="260,27 300,47 300,83 260,103 220,83 220,47"
          fill="oklch(0.12 0.04 155)"
          stroke="oklch(0.68 0.24 155)"
          stroke-width="2"
          filter="url(#softGlow)"
          class="hex"
        />
        <polygon
          points="260,35 292,51 292,79 260,95 228,79 228,51"
          fill="none"
          stroke="oklch(0.62 0.20 155)"
          stroke-width="0.5"
          stroke-opacity="0.5"
          stroke-dasharray="5 4"
          class="hex-inner"
        />
        <circle cx="220" cy="65" r="5" fill="oklch(0.68 0.24 155)" class="conn"/>
        <circle cx="220" cy="65" r="5" fill="oklch(0.68 0.24 155)" class="conn-pulse" style="animation-delay: 0.4s"/>
        <circle cx="300" cy="78" r="5" fill="oklch(0.68 0.24 155)" class="conn"/>
        <circle cx="300" cy="78" r="5" fill="oklch(0.68 0.24 155)" class="conn-pulse" style="animation-delay: 0.8s"/>

        <text x="260" y="62" text-anchor="middle" dominant-baseline="middle" class="node-label">IMPLEMENT</text>
        <text x="260" y="81" text-anchor="middle" dominant-baseline="middle" class="node-sub implement-sub">build</text>
      </g>

      <!-- Node: REVIEW -->
      <g class="node review-node">
        <polygon
          points="440,132 480,152 480,188 440,208 400,188 400,152"
          fill="oklch(0.12 0.04 300)"
          stroke="oklch(0.65 0.26 300)"
          stroke-width="2"
          filter="url(#softGlow)"
          class="hex"
        />
        <polygon
          points="440,140 472,156 472,184 440,200 408,184 408,156"
          fill="none"
          stroke="oklch(0.60 0.22 300)"
          stroke-width="0.5"
          stroke-opacity="0.5"
          stroke-dasharray="5 4"
          class="hex-inner"
        />
        <circle cx="400" cy="152" r="5" fill="oklch(0.65 0.26 300)" class="conn"/>
        <circle cx="400" cy="152" r="5" fill="oklch(0.65 0.26 300)" class="conn-pulse" style="animation-delay: 0.6s"/>

        <text x="440" y="167" text-anchor="middle" dominant-baseline="middle" class="node-label">REVIEW</text>
        <text x="440" y="186" text-anchor="middle" dominant-baseline="middle" class="node-sub review-sub">validate</text>
      </g>

      <!-- Center label -->
      <text x="260" y="252" text-anchor="middle" dominant-baseline="middle" class="center-label">
        <tspan class="the-txt">THE</tspan><tspan dx="6" class="cycle-txt">DEVELOPMENT CYCLE</tspan>
      </text>

      <!-- Corner accents -->
      <path d="M 15 15 L 40 15 L 40 19 L 19 19 L 19 40 L 15 40 Z" fill="oklch(0.5 0.15 263.9)" opacity="0.4" class="corner c1"/>
      <path d="M 505 15 L 480 15 L 480 19 L 501 19 L 501 40 L 505 40 Z" fill="oklch(0.5 0.15 263.9)" opacity="0.4" class="corner c2"/>
      <path d="M 15 265 L 40 265 L 40 261 L 19 261 L 19 240 L 15 240 Z" fill="oklch(0.5 0.15 263.9)" opacity="0.4" class="corner c3"/>
      <path d="M 505 265 L 480 265 L 480 261 L 501 261 L 501 240 L 505 240 Z" fill="oklch(0.5 0.15 263.9)" opacity="0.4" class="corner c4"/>
    </svg>
  </div>
</template>

<style scoped>
.cycle-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.25rem 0;
}

.cycle-svg {
  width: 100%;
  max-width: 640px;
  height: auto;
}

/* Typography */
.node-label {
  font-family: 'Outfit', sans-serif;
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.12em;
  fill: oklch(0.97 0.01 260);
}

.node-sub {
  font-family: 'JetBrains Mono', monospace;
  font-size: 9px;
  letter-spacing: 0.08em;
}

.plan-sub { fill: oklch(0.7 0.22 263.9); }
.implement-sub { fill: oklch(0.72 0.2 155); }
.review-sub { fill: oklch(0.7 0.24 300); }

.center-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.2em;
}

.the-txt { fill: oklch(0.6 0.15 263.9); }
.cycle-txt { fill: oklch(0.45 0.04 260); }

/* Star twinkle - staggered */
.star {
  animation: twinkle 4s ease-in-out infinite;
}
.s1 { animation-delay: 0s; }
.s2 { animation-delay: 0.7s; }
.s3 { animation-delay: 1.4s; }
.s4 { animation-delay: 2.1s; }
.s5 { animation-delay: 0.3s; }
.s6 { animation-delay: 1.8s; }
.s7 { animation-delay: 2.5s; }
.s8 { animation-delay: 1.1s; }

@keyframes twinkle {
  0%, 100% { opacity: 0.15; transform: scale(0.8); }
  50% { opacity: 0.6; transform: scale(1.2); }
}

/* Aura breathing - more dramatic */
.aura {
  animation: breathe 5s ease-in-out infinite;
  transform-origin: center;
}
.plan-aura { animation-delay: 0s; }
.implement-aura { animation-delay: 1.6s; }
.review-aura { animation-delay: 3.2s; }

@keyframes breathe {
  0%, 100% {
    opacity: 0.5;
    transform: scale(0.95);
  }
  50% {
    opacity: 1;
    transform: scale(1.1);
  }
}

/* Orbit ring */
.orbit-ring {
  animation: orbit-flow 70s linear infinite;
  transform-origin: center;
}

@keyframes orbit-flow {
  from { stroke-dashoffset: 0; }
  to { stroke-dashoffset: 200; }
}

/* Hexagon inner ring rotation */
.hex-inner {
  animation: inner-dash 20s linear infinite;
  transform-origin: center;
}

@keyframes inner-dash {
  from { stroke-dashoffset: 0; }
  to { stroke-dashoffset: 36; }
}

/* Connection pulse */
.conn { opacity: 0.9; }

.conn-pulse {
  animation: pulse-out 2.8s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

@keyframes pulse-out {
  0% { opacity: 0.8; r: 5; }
  60% { opacity: 0; r: 16; }
  100% { opacity: 0; r: 16; }
}

/* Flow path dash animation */
.flow-path {
  stroke-dasharray: 12 8;
  animation: path-flow 3s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
.p1 { animation-delay: 0s; }
.p2 { animation-delay: 0.5s; }
.p3 { animation-delay: 1s; }

@keyframes path-flow {
  from { stroke-dashoffset: 40; }
  to { stroke-dashoffset: 0; }
}

/* Particle glow */
.particle {
  animation: glow-pulse 2s ease-in-out infinite alternate;
}

@keyframes glow-pulse {
  from { opacity: 0.75; }
  to { opacity: 1; }
}

/* Arrow pulse */
.arrow {
  animation: arrow-breathe 3.5s ease-in-out infinite;
}
.a1 { animation-delay: 0s; }
.a2 { animation-delay: 0.8s; }
.a3 { animation-delay: 1.6s; }

@keyframes arrow-breathe {
  0%, 100% { opacity: 0.5; }
  50% { opacity: 1; }
}

/* Corner pulse */
.corner {
  animation: corner-fade 6s ease-in-out infinite;
}
.c1 { animation-delay: 0s; }
.c2 { animation-delay: 1.5s; }
.c3 { animation-delay: 3s; }
.c4 { animation-delay: 4.5s; }

@keyframes corner-fade {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 0.6; }
}
</style>
