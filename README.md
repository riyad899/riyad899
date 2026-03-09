<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Riyadus Salehin - GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600;700&family=JetBrains+Mono:wght@300;400;700&display=swap" rel="stylesheet">
<style>
:root {
  --neon-cyan: #00f5ff;
  --neon-purple: #bf00ff;
  --neon-green: #39ff14;
  --neon-orange: #ff6b00;
  --dark-bg: #020408;
  --panel-bg: rgba(0, 245, 255, 0.03);
  --border-glow: rgba(0, 245, 255, 0.3);
  --text-primary: #e0f7ff;
  --text-dim: #5a8a99;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: var(--dark-bg);
  font-family: 'Rajdhani', sans-serif;
  color: var(--text-primary);
  overflow-x: hidden;
  min-height: 100vh;
}

/* ===== ANIMATED GRID BACKGROUND ===== */
.grid-bg {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background-image: 
    linear-gradient(rgba(0,245,255,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,245,255,0.04) 1px, transparent 1px);
  background-size: 60px 60px;
  animation: gridMove 20s linear infinite;
  z-index: 0;
}

@keyframes gridMove {
  0% { transform: translateY(0); }
  100% { transform: translateY(60px); }
}

/* ===== FLOATING PARTICLES ===== */
.particles {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0;
  pointer-events: none;
}

.particle {
  position: absolute;
  width: 2px; height: 2px;
  border-radius: 50%;
  animation: floatParticle linear infinite;
}

@keyframes floatParticle {
  0% { transform: translateY(100vh) scale(0); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(-10vh) scale(1); opacity: 0; }
}

/* ===== SCANLINE EFFECT ===== */
.scanline {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 4px;
  background: linear-gradient(90deg, transparent, var(--neon-cyan), transparent);
  animation: scanDown 4s linear infinite;
  z-index: 1000;
  opacity: 0.4;
  pointer-events: none;
}

@keyframes scanDown {
  0% { top: -4px; }
  100% { top: 100vh; }
}

/* ===== MAIN CONTAINER ===== */
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 40px 20px;
  position: relative;
  z-index: 10;
}

/* ===== HERO SECTION ===== */
.hero {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 40px;
  align-items: center;
  margin-bottom: 60px;
  padding: 50px;
  background: var(--panel-bg);
  border: 1px solid var(--border-glow);
  border-radius: 4px;
  position: relative;
  overflow: hidden;
  animation: fadeSlideIn 1s ease forwards;
}

@keyframes fadeSlideIn {
  from { opacity: 0; transform: translateY(-30px); }
  to { opacity: 1; transform: translateY(0); }
}

.hero::before {
  content: '';
  position: absolute;
  top: -2px; left: -2px; right: -2px; bottom: -2px;
  background: linear-gradient(45deg, var(--neon-cyan), var(--neon-purple), var(--neon-green), var(--neon-orange), var(--neon-cyan));
  background-size: 400%;
  border-radius: 4px;
  z-index: -1;
  animation: borderRotate 6s linear infinite;
}

@keyframes borderRotate {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.hero::after {
  content: '';
  position: absolute;
  inset: 2px;
  background: #030a0e;
  border-radius: 2px;
  z-index: -1;
}

/* ===== GLITCH TEXT ===== */
.glitch-container {
  position: relative;
  margin-bottom: 10px;
}

.glitch {
  font-family: 'Orbitron', sans-serif;
  font-size: clamp(28px, 4vw, 48px);
  font-weight: 900;
  color: var(--neon-cyan);
  text-shadow: 0 0 10px var(--neon-cyan), 0 0 30px var(--neon-cyan), 0 0 60px rgba(0,245,255,0.3);
  position: relative;
  animation: glitchMain 5s infinite;
  letter-spacing: 2px;
}

.glitch::before, .glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
}

.glitch::before {
  color: var(--neon-purple);
  animation: glitchTop 5s infinite;
  clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
  text-shadow: 0 0 10px var(--neon-purple);
}

.glitch::after {
  color: var(--neon-green);
  animation: glitchBottom 5s infinite;
  clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
  text-shadow: 0 0 10px var(--neon-green);
}

@keyframes glitchMain {
  0%, 90%, 100% { transform: translate(0); filter: none; }
  92% { transform: translate(-2px, 0); filter: hue-rotate(90deg); }
  94% { transform: translate(2px, 0); filter: hue-rotate(-90deg); }
  96% { transform: translate(0, 2px); }
  98% { transform: translate(0, -2px); }
}

@keyframes glitchTop {
  0%, 90%, 100% { transform: translate(0); }
  92% { transform: translate(-4px, 0); }
  94% { transform: translate(4px, 0); }
  96% { transform: translate(-2px, 0); }
  98% { transform: translate(2px, 0); }
}

@keyframes glitchBottom {
  0%, 90%, 100% { transform: translate(0); }
  92% { transform: translate(4px, 0); }
  94% { transform: translate(-4px, 0); }
  96% { transform: translate(2px, 0); }
  98% { transform: translate(-2px, 0); }
}

/* ===== TYPING EFFECT ===== */
.role-text {
  font-family: 'JetBrains Mono', monospace;
  font-size: 18px;
  color: var(--neon-green);
  margin-bottom: 20px;
  position: relative;
}

.role-text::after {
  content: '|';
  animation: blink 0.8s step-end infinite;
  color: var(--neon-green);
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.typing-text {
  display: inline;
  overflow: hidden;
  white-space: nowrap;
  border-right: none;
  animation: typing 3s steps(40) 0.5s both;
}

@keyframes typing {
  from { width: 0; }
  to { width: 100%; }
}

/* ===== AVATAR ===== */
.avatar-wrapper {
  position: relative;
  width: 160px;
  height: 160px;
  flex-shrink: 0;
}

.avatar-ring {
  position: absolute;
  inset: -15px;
  border-radius: 50%;
  border: 2px solid transparent;
  background: linear-gradient(45deg, var(--neon-cyan), var(--neon-purple)) border-box;
  animation: spin 8s linear infinite;
}

.avatar-ring-2 {
  position: absolute;
  inset: -25px;
  border-radius: 50%;
  border: 1px dashed var(--neon-purple);
  opacity: 0.5;
  animation: spin 12s linear infinite reverse;
}

.avatar-ring-3 {
  position: absolute;
  inset: -40px;
  border-radius: 50%;
  border: 1px solid rgba(0,245,255,0.2);
  animation: spin 20s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.avatar-img {
  width: 160px;
  height: 160px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid var(--neon-cyan);
  box-shadow: 0 0 30px rgba(0,245,255,0.5), 0 0 60px rgba(0,245,255,0.2), inset 0 0 30px rgba(0,245,255,0.1);
  animation: avatarPulse 3s ease-in-out infinite;
  background: linear-gradient(135deg, #0a1a2a, #0f3460);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 60px;
  text-align: center;
  line-height: 160px;
}

@keyframes avatarPulse {
  0%, 100% { box-shadow: 0 0 30px rgba(0,245,255,0.5), 0 0 60px rgba(0,245,255,0.2); }
  50% { box-shadow: 0 0 50px rgba(0,245,255,0.8), 0 0 100px rgba(0,245,255,0.4), 0 0 150px rgba(191,0,255,0.2); }
}

/* ===== STATUS BADGES ===== */
.status-row {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 20px;
}

.badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 6px 14px;
  background: rgba(0,245,255,0.05);
  border: 1px solid rgba(0,245,255,0.2);
  border-radius: 2px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  color: var(--neon-cyan);
  transition: all 0.3s;
  cursor: default;
}

.badge:hover {
  background: rgba(0,245,255,0.15);
  border-color: var(--neon-cyan);
  box-shadow: 0 0 20px rgba(0,245,255,0.3);
  transform: translateY(-2px);
}

.badge-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--neon-green);
  animation: dotPulse 1.5s ease-in-out infinite;
}

@keyframes dotPulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.5); opacity: 0.7; }
}

/* ===== SECTION HEADERS ===== */
.section-header {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 30px;
  font-family: 'Orbitron', sans-serif;
  font-size: 14px;
  font-weight: 700;
  letter-spacing: 4px;
  color: var(--neon-cyan);
  text-transform: uppercase;
}

.section-header::before {
  content: '';
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--neon-cyan));
  opacity: 0.4;
}

.section-header::after {
  content: '';
  flex: 1;
  height: 1px;
  background: linear-gradient(to left, transparent, var(--neon-cyan));
  opacity: 0.4;
}

.section-icon {
  font-size: 20px;
}

/* ===== INFO GRID ===== */
.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 16px;
  margin-bottom: 50px;
}

.info-card {
  padding: 20px 24px;
  background: var(--panel-bg);
  border: 1px solid var(--border-glow);
  border-radius: 3px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
  animation: cardSlideIn 0.6s ease backwards;
}

.info-card:nth-child(1) { animation-delay: 0.1s; }
.info-card:nth-child(2) { animation-delay: 0.2s; }
.info-card:nth-child(3) { animation-delay: 0.3s; }
.info-card:nth-child(4) { animation-delay: 0.4s; }
.info-card:nth-child(5) { animation-delay: 0.5s; }
.info-card:nth-child(6) { animation-delay: 0.6s; }

@keyframes cardSlideIn {
  from { opacity: 0; transform: translateX(-20px); }
  to { opacity: 1; transform: translateX(0); }
}

.info-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0;
  width: 3px; height: 100%;
  background: linear-gradient(to bottom, var(--neon-cyan), var(--neon-purple));
}

.info-card::after {
  content: '';
  position: absolute;
  top: 0; left: -100%; right: 0; bottom: 0;
  background: linear-gradient(90deg, transparent, rgba(0,245,255,0.05), transparent);
  transition: left 0.5s;
}

.info-card:hover::after { left: 100%; }

.info-card:hover {
  border-color: var(--neon-cyan);
  box-shadow: 0 0 25px rgba(0,245,255,0.15), inset 0 0 25px rgba(0,245,255,0.03);
  transform: translateX(5px);
}

.info-icon {
  font-size: 24px;
  flex-shrink: 0;
  filter: drop-shadow(0 0 8px currentColor);
}

.info-content label {
  display: block;
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  color: var(--text-dim);
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 4px;
}

.info-content span, .info-content a {
  font-size: 15px;
  font-weight: 600;
  color: var(--text-primary);
  text-decoration: none;
  transition: color 0.3s;
}

.info-content a:hover { color: var(--neon-cyan); }

/* ===== SKILLS SECTION ===== */
.skills-section {
  margin-bottom: 50px;
}

.tech-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: center;
}

.tech-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  padding: 16px 20px;
  background: var(--panel-bg);
  border: 1px solid var(--border-glow);
  border-radius: 3px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 11px;
  color: var(--text-dim);
  transition: all 0.3s;
  cursor: default;
  min-width: 80px;
  text-align: center;
  position: relative;
  overflow: hidden;
  animation: techFadeIn 0.5s ease backwards;
}

.tech-item:nth-child(n) { animation-delay: calc(n * 0.05s); }

@keyframes techFadeIn {
  from { opacity: 0; transform: scale(0.8); }
  to { opacity: 1; transform: scale(1); }
}

.tech-item::before {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 100%; height: 2px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
  transform: scaleX(0);
  transition: transform 0.3s;
}

.tech-item:hover::before { transform: scaleX(1); }

.tech-item:hover {
  color: var(--neon-cyan);
  border-color: var(--neon-cyan);
  box-shadow: 0 0 20px rgba(0,245,255,0.2), 0 -10px 30px rgba(0,245,255,0.1);
  transform: translateY(-6px);
}

.tech-item img {
  width: 40px;
  height: 40px;
  object-fit: contain;
  filter: brightness(0.8) saturate(0.7);
  transition: filter 0.3s;
}

.tech-item:hover img {
  filter: brightness(1.2) saturate(1.2) drop-shadow(0 0 8px var(--neon-cyan));
}

/* ===== STAT BARS ===== */
.stats-section {
  margin-bottom: 50px;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}

.stat-card {
  padding: 24px;
  background: var(--panel-bg);
  border: 1px solid var(--border-glow);
  border-radius: 3px;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
  animation: statPopIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) backwards;
}

.stat-card:nth-child(1) { animation-delay: 0.1s; }
.stat-card:nth-child(2) { animation-delay: 0.2s; }
.stat-card:nth-child(3) { animation-delay: 0.3s; }
.stat-card:nth-child(4) { animation-delay: 0.4s; }

@keyframes statPopIn {
  from { opacity: 0; transform: scale(0.5); }
  to { opacity: 1; transform: scale(1); }
}

.stat-card:hover {
  border-color: var(--neon-purple);
  box-shadow: 0 0 30px rgba(191,0,255,0.2);
  transform: scale(1.05);
}

.stat-number {
  font-family: 'Orbitron', sans-serif;
  font-size: 40px;
  font-weight: 900;
  color: var(--neon-cyan);
  text-shadow: 0 0 20px var(--neon-cyan);
  line-height: 1;
  margin-bottom: 8px;
  animation: countUp 2s ease forwards;
}

.stat-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 11px;
  color: var(--text-dim);
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* ===== SKILL BARS ===== */
.skill-bars {
  margin-bottom: 50px;
}

.skill-bar-item {
  margin-bottom: 20px;
  animation: slideRight 0.8s ease backwards;
}

.skill-bar-item:nth-child(1) { animation-delay: 0.1s; }
.skill-bar-item:nth-child(2) { animation-delay: 0.2s; }
.skill-bar-item:nth-child(3) { animation-delay: 0.3s; }
.skill-bar-item:nth-child(4) { animation-delay: 0.4s; }
.skill-bar-item:nth-child(5) { animation-delay: 0.5s; }
.skill-bar-item:nth-child(6) { animation-delay: 0.6s; }

@keyframes slideRight {
  from { opacity: 0; transform: translateX(-30px); }
  to { opacity: 1; transform: translateX(0); }
}

.skill-bar-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 8px;
}

.skill-name {
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  color: var(--text-primary);
  display: flex;
  align-items: center;
  gap: 8px;
}

.skill-pct {
  font-family: 'Orbitron', sans-serif;
  font-size: 12px;
  color: var(--neon-cyan);
}

.skill-track {
  width: 100%;
  height: 6px;
  background: rgba(255,255,255,0.05);
  border-radius: 3px;
  overflow: hidden;
  position: relative;
}

.skill-fill {
  height: 100%;
  border-radius: 3px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
  box-shadow: 0 0 10px var(--neon-cyan);
  position: relative;
  animation: fillBar 2s cubic-bezier(0.4, 0, 0.2, 1) backwards;
}

.skill-fill::after {
  content: '';
  position: absolute;
  top: 0; right: 0;
  width: 20px; height: 100%;
  background: rgba(255,255,255,0.4);
  filter: blur(6px);
  animation: shimmer 2s ease-in-out infinite;
}

@keyframes fillBar {
  from { width: 0 !important; }
}

@keyframes shimmer {
  0%, 100% { opacity: 0; }
  50% { opacity: 1; }
}

/* ===== SOCIAL LINKS ===== */
.social-section {
  margin-bottom: 50px;
}

.social-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  justify-content: center;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px 24px;
  text-decoration: none;
  border: 1px solid;
  border-radius: 2px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 1px;
  transition: all 0.3s;
  position: relative;
  overflow: hidden;
}

.social-link::before {
  content: '';
  position: absolute;
  top: 0; left: -100%;
  width: 100%; height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
  transition: left 0.4s;
}

.social-link:hover::before { left: 100%; }

.social-link:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
}

.social-link.twitter { border-color: #1da1f2; color: #1da1f2; }
.social-link.twitter:hover { background: rgba(29,161,242,0.1); box-shadow: 0 10px 30px rgba(29,161,242,0.3); }
.social-link.linkedin { border-color: #0077b5; color: #0077b5; }
.social-link.linkedin:hover { background: rgba(0,119,181,0.1); box-shadow: 0 10px 30px rgba(0,119,181,0.3); }
.social-link.github { border-color: #fff; color: #fff; }
.social-link.github:hover { background: rgba(255,255,255,0.1); box-shadow: 0 10px 30px rgba(255,255,255,0.2); }
.social-link.leetcode { border-color: #ffa116; color: #ffa116; }
.social-link.leetcode:hover { background: rgba(255,161,22,0.1); box-shadow: 0 10px 30px rgba(255,161,22,0.3); }
.social-link.youtube { border-color: #ff0000; color: #ff0000; }
.social-link.youtube:hover { background: rgba(255,0,0,0.1); box-shadow: 0 10px 30px rgba(255,0,0,0.3); }
.social-link.discord { border-color: #5865f2; color: #5865f2; }
.social-link.discord:hover { background: rgba(88,101,242,0.1); box-shadow: 0 10px 30px rgba(88,101,242,0.3); }
.social-link.facebook { border-color: #1877f2; color: #1877f2; }
.social-link.facebook:hover { background: rgba(24,119,242,0.1); box-shadow: 0 10px 30px rgba(24,119,242,0.3); }

/* ===== PROJECTS ===== */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  margin-bottom: 50px;
}

.project-card {
  padding: 28px;
  background: var(--panel-bg);
  border: 1px solid var(--border-glow);
  border-radius: 3px;
  position: relative;
  overflow: hidden;
  transition: all 0.4s;
  animation: projectFade 0.7s ease backwards;
}

.project-card:nth-child(1) { animation-delay: 0.1s; }
.project-card:nth-child(2) { animation-delay: 0.2s; }
.project-card:nth-child(3) { animation-delay: 0.3s; }

@keyframes projectFade {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.project-card:hover {
  border-color: var(--neon-cyan);
  box-shadow: 0 0 40px rgba(0,245,255,0.15), 0 20px 60px rgba(0,0,0,0.5);
  transform: translateY(-8px);
}

.project-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 2px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple), var(--neon-green));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s;
}

.project-card:hover::before { transform: scaleX(1); }

.project-emoji { font-size: 36px; margin-bottom: 12px; display: block; }

.project-name {
  font-family: 'Orbitron', sans-serif;
  font-size: 16px;
  font-weight: 700;
  color: var(--neon-cyan);
  margin-bottom: 10px;
  text-decoration: none;
  display: block;
  transition: text-shadow 0.3s;
}

.project-name:hover {
  text-shadow: 0 0 15px var(--neon-cyan);
}

.project-desc {
  font-size: 14px;
  color: var(--text-dim);
  line-height: 1.6;
  margin-bottom: 16px;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.project-tag {
  padding: 3px 10px;
  background: rgba(0,245,255,0.08);
  border: 1px solid rgba(0,245,255,0.15);
  border-radius: 2px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  color: var(--neon-cyan);
  letter-spacing: 1px;
}

/* ===== FUN FACT BOX ===== */
.fun-fact {
  padding: 30px;
  background: linear-gradient(135deg, rgba(191,0,255,0.05), rgba(0,245,255,0.05));
  border: 1px solid rgba(191,0,255,0.3);
  border-radius: 3px;
  margin-bottom: 50px;
  position: relative;
  overflow: hidden;
  animation: funFactIn 1s ease 0.8s backwards;
}

@keyframes funFactIn {
  from { opacity: 0; transform: scale(0.95); }
  to { opacity: 1; transform: scale(1); }
}

.fun-fact::before {
  content: '⚡';
  position: absolute;
  top: -20px; right: -20px;
  font-size: 80px;
  opacity: 0.1;
  animation: spin 10s linear infinite;
}

.fun-fact-label {
  font-family: 'Orbitron', sans-serif;
  font-size: 11px;
  letter-spacing: 4px;
  color: var(--neon-purple);
  margin-bottom: 12px;
  text-transform: uppercase;
}

.fun-fact-text {
  font-size: 16px;
  line-height: 1.7;
  color: var(--text-primary);
}

/* ===== GIF SHOWCASE ===== */
.gif-showcase {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 50px;
}

.gif-item {
  border-radius: 3px;
  overflow: hidden;
  border: 1px solid var(--border-glow);
  position: relative;
  aspect-ratio: 16/9;
  transition: all 0.3s;
}

.gif-item:hover {
  border-color: var(--neon-cyan);
  box-shadow: 0 0 30px rgba(0,245,255,0.3);
  transform: scale(1.03);
}

.gif-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* ===== GITHUB STATS ===== */
.github-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 50px;
}

.stats-img-wrapper {
  border: 1px solid var(--border-glow);
  border-radius: 3px;
  overflow: hidden;
  transition: all 0.3s;
  background: var(--panel-bg);
  padding: 15px;
}

.stats-img-wrapper:hover {
  border-color: var(--neon-cyan);
  box-shadow: 0 0 30px rgba(0,245,255,0.2);
}

.stats-img-wrapper img {
  width: 100%;
  display: block;
}

/* ===== FOOTER ===== */
.footer {
  text-align: center;
  padding: 40px;
  border-top: 1px solid rgba(0,245,255,0.1);
  position: relative;
}

.footer-text {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  color: var(--text-dim);
  letter-spacing: 2px;
}

.footer-glow {
  font-family: 'Orbitron', sans-serif;
  font-size: 20px;
  color: var(--neon-cyan);
  text-shadow: 0 0 20px var(--neon-cyan);
  margin-bottom: 10px;
  animation: pulseFade 3s ease-in-out infinite;
}

@keyframes pulseFade {
  0%, 100% { opacity: 0.7; }
  50% { opacity: 1; }
}

/* ===== CORNER DECORATIONS ===== */
.corner-tl, .corner-tr, .corner-bl, .corner-br {
  position: absolute;
  width: 20px; height: 20px;
  border-color: var(--neon-cyan);
  border-style: solid;
  opacity: 0.6;
}
.corner-tl { top: 10px; left: 10px; border-width: 2px 0 0 2px; }
.corner-tr { top: 10px; right: 10px; border-width: 2px 2px 0 0; }
.corner-bl { bottom: 10px; left: 10px; border-width: 0 0 2px 2px; }
.corner-br { bottom: 10px; right: 10px; border-width: 0 2px 2px 0; }

/* ===== VIEW COUNTER BADGE ===== */
.view-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: rgba(0,245,255,0.05);
  border: 1px solid rgba(0,245,255,0.2);
  border-radius: 2px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  color: var(--text-dim);
  animation: fadeIn 1s ease 1.5s backwards;
  margin-bottom: 30px;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.view-count {
  font-family: 'Orbitron', sans-serif;
  font-size: 14px;
  color: var(--neon-cyan);
  font-weight: 700;
}

/* LOADING BAR */
.loader-bar {
  position: fixed;
  top: 0; left: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
  animation: loadBar 2s ease forwards;
  z-index: 9999;
  box-shadow: 0 0 15px var(--neon-cyan);
}

@keyframes loadBar {
  from { width: 0; }
  to { width: 100%; }
}

/* CURSOR TRAIL handled in JS */
.cursor-dot {
  position: fixed;
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--neon-cyan);
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%, -50%);
  transition: all 0.05s;
  box-shadow: 0 0 10px var(--neon-cyan);
}

@media (max-width: 768px) {
  .hero { grid-template-columns: 1fr; text-align: center; padding: 30px 20px; }
  .avatar-wrapper { margin: 0 auto 20px; }
  .github-stats { grid-template-columns: 1fr; }
  .gif-showcase { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<div class="loader-bar"></div>
<div class="scanline"></div>
<div class="grid-bg"></div>
<div class="particles" id="particles"></div>
<div class="cursor-dot" id="cursorDot"></div>

<div class="container">

  <!-- HERO -->
  <section class="hero">
    <div class="corner-tl"></div><div class="corner-tr"></div>
    <div class="corner-bl"></div><div class="corner-br"></div>

    <div class="hero-content">
      <div style="margin-bottom: 6px;">
        <span style="font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--text-dim);letter-spacing:3px;">// INITIALIZED</span>
      </div>
      <div class="glitch-container">
        <h1 class="glitch" data-text="Riyadus Salehin">Riyadus Salehin</h1>
      </div>
      <div class="role-text">
        <span class="typing-text" id="typingText">Full Stack Developer 🇧🇩</span>
      </div>
      <p style="font-size:15px;color:var(--text-dim);line-height:1.7;max-width:500px;margin-bottom:20px;">
        Crafting digital experiences from <span style="color:var(--neon-cyan)">Bangladesh</span> 🌏 — 
        Passionate about building scalable, beautiful full-stack applications with 
        React, Next.js, and Django.
      </p>

      <div class="view-badge">
        <div class="badge-dot"></div>
        <span>PROFILE VIEWS</span>
        <span class="view-count" id="viewCounter">0</span>
      </div>

      <div class="status-row">
        <div class="badge"><div class="badge-dot"></div> AVAILABLE FOR COLLAB</div>
        <div class="badge">📍 DHAKA, BD</div>
        <div class="badge">🎓 FULL STACK DEV</div>
        <div class="badge">☕ COFFEE FUELED</div>
      </div>
    </div>

    <div class="avatar-wrapper">
      <div class="avatar-ring-3"></div>
      <div class="avatar-ring-2"></div>
      <div class="avatar-ring"></div>
    </div>
  </section>

  <!-- CODED GIF SHOWCASE -->
  <section class="gif-showcase">
    <div class="gif-item">
      <img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" alt="Coding" />
    </div>
    <div class="gif-item">
      <img src="https://media.giphy.com/media/L1R1tvI9svkIWwpVYr/giphy.gif" alt="Dev" />
    </div>
    <div class="gif-item">
      <img src="https://media.giphy.com/media/ZVik7pIGkcAYoAwhfx/giphy.gif" alt="Matrix" />
    </div>
  </section>

  <!-- INFO CARDS -->
  <div class="section-header">
    <span class="section-icon">🛰️</span>
    SYSTEM.INFO
    <span class="section-icon">🛰️</span>
  </div>
  <div class="info-grid">
    <div class="info-card">
      <span class="info-icon">🔭</span>
      <div class="info-content">
        <label>Currently Building</label>
        <a href="https://courageous-sawine-39b32c.netlify.app/" target="_blank">Rootsy Project →</a>
      </div>
    </div>
    <div class="info-card">
      <span class="info-icon">🌱</span>
      <div class="info-content">
        <label>Currently Learning</label>
        <span>Python Django · Next.js</span>
      </div>
    </div>
    <div class="info-card">
      <span class="info-icon">👯</span>
      <div class="info-content">
        <label>Looking to Collaborate</label>
        <a href="https://github.com/CodeConnect" target="_blank">CodeConnect →</a>
      </div>
    </div>
    <div class="info-card">
      <span class="info-icon">🤝</span>
      <div class="info-content">
        <label>Seeking Help With</label>
        <span>MoneyMaster App</span>
      </div>
    </div>
    <div class="info-card">
      <span class="info-icon">💬</span>
      <div class="info-content">
        <label>Ask Me About</label>
        <span>React · Next.js · Full Stack</span>
      </div>
    </div>
    <div class="info-card">
      <span class="info-icon">📧</span>
      <div class="info-content">
        <label>Reach Me At</label>
        <a href="mailto:raditkhan42@gmail.com">raditkhan42@gmail.com</a>
      </div>
    </div>
  </div>

  <!-- SKILL BARS -->
  <div class="section-header">
    <span class="section-icon">📊</span>
    SKILL.MATRIX
    <span class="section-icon">📊</span>
  </div>
  <div class="skill-bars" style="margin-bottom:50px;">
    <div class="skill-bar-item">
      <div class="skill-bar-header">
        <span class="skill-name">⚛️ React / Next.js</span>
        <span class="skill-pct">92%</span>
      </div>
      <div class="skill-track"><div class="skill-fill" style="width:92%;animation-delay:0.1s"></div></div>
    </div>
    <div class="skill-bar-item">
      <div class="skill-bar-header">
        <span class="skill-name">🎨 HTML / CSS / Tailwind</span>
        <span class="skill-pct">95%</span>
      </div>
      <div class="skill-track"><div class="skill-fill" style="width:95%;animation-delay:0.2s;background:linear-gradient(90deg,#39ff14,#00f5ff);box-shadow:0 0 10px #39ff14"></div></div>
    </div>
    <div class="skill-bar-item">
      <div class="skill-bar-header">
        <span class="skill-name">🐍 Python / Django</span>
        <span class="skill-pct">75%</span>
      </div>
      <div class="skill-track"><div class="skill-fill" style="width:75%;animation-delay:0.3s;background:linear-gradient(90deg,#bf00ff,#00f5ff)"></div></div>
    </div>
    <div class="skill-bar-item">
      <div class="skill-bar-header">
        <span class="skill-name">🍃 MongoDB / MySQL</span>
        <span class="skill-pct">80%</span>
      </div>
      <div class="skill-track"><div class="skill-fill" style="width:80%;animation-delay:0.4s;background:linear-gradient(90deg,#ff6b00,#ff0080)"></div></div>
    </div>
    <div class="skill-bar-item">
      <div class="skill-bar-header">
        <span class="skill-name">☁️ AWS / GCP</span>
        <span class="skill-pct">65%</span>
      </div>
      <div class="skill-track"><div class="skill-fill" style="width:65%;animation-delay:0.5s;background:linear-gradient(90deg,#ff9900,#ffcc00)"></div></div>
    </div>
    <div class="skill-bar-item">
      <div class="skill-bar-header">
        <span class="skill-name">🎮 Vue.js / Angular</span>
        <span class="skill-pct">70%</span>
      </div>
      <div class="skill-track"><div class="skill-fill" style="width:70%;animation-delay:0.6s;background:linear-gradient(90deg,#42b883,#00f5ff)"></div></div>
    </div>
  </div>

  <!-- STATS CARDS -->
  <div class="section-header">
    <span class="section-icon">📡</span>
    GITHUB.STATS
    <span class="section-icon">📡</span>
  </div>
  <div class="stats-grid" style="margin-bottom:40px;">
    <div class="stat-card">
      <div class="stat-number" data-target="50">0</div>
      <div class="stat-label">Repositories</div>
    </div>
    <div class="stat-card">
      <div class="stat-number" data-target="1200">0</div>
      <div class="stat-label">Contributions</div>
    </div>
    <div class="stat-card">
      <div class="stat-number" data-target="340">0</div>
      <div class="stat-label">Profile Views</div>
    </div>
    <div class="stat-card">
      <div class="stat-number" data-target="3">0</div>
      <div class="stat-label">Years Active</div>
    </div>
  </div>

  <!-- GITHUB STATS IMAGES -->
  <div class="github-stats">
    <div class="stats-img-wrapper">
      <img src="https://github-readme-stats.vercel.app/api?username=riyad899&show_icons=true&theme=chartreuse-dark&bg_color=020408&border_color=00f5ff&title_color=00f5ff&text_color=a0d8ef&icon_color=bf00ff" alt="GitHub Stats" />
    </div>
    <div class="stats-img-wrapper">
      <img src="https://github-readme-stats.vercel.app/api/top-langs?username=riyad899&layout=compact&theme=chartreuse-dark&bg_color=020408&border_color=00f5ff&title_color=00f5ff&text_color=a0d8ef" alt="Top Languages" />
    </div>
  </div>
  <div style="margin-bottom:50px;">
    <div class="stats-img-wrapper" style="padding:15px;">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=riyad899&theme=matrix&background=020408&border=00f5ff&ring=bf00ff&fire=00f5ff&currStreakLabel=00f5ff" alt="Streak Stats" style="width:100%" />
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section-header">
    <span class="section-icon">⚙️</span>
    TECH.STACK
    <span class="section-icon">⚙️</span>
  </div>
  <div class="tech-grid" style="margin-bottom:50px;">
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="React"><span>React</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nextjs/nextjs-original.svg" alt="Next.js" style="background:white;border-radius:50%;padding:4px"><span>Next.js</span></div>
    <div class="tech-item"><img src="https://cdn.worldvectorlogo.com/logos/django.svg" alt="Django"><span>Django</span></div>
    <div class="tech-item"><img src="https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg" alt="Tailwind"><span>Tailwind</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" alt="MongoDB"><span>MongoDB</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="MySQL"><span>MySQL</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="AWS"><span>AWS</span></div>
    <div class="tech-item"><img src="https://www.vectorlogo.zone/logos/google_cloud/google_cloud-icon.svg" alt="GCP"><span>GCP</span></div>
    <div class="tech-item"><img src="https://www.vectorlogo.zone/logos/figma/figma-icon.svg" alt="Figma"><span>Figma</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vuejs/vuejs-original-wordmark.svg" alt="Vue"><span>Vue.js</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/angularjs/angularjs-original-wordmark.svg" alt="Angular"><span>Angular</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/sass/sass-original.svg" alt="Sass"><span>Sass</span></div>
    <div class="tech-item"><img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="Git"><span>Git</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="Java"><span>Java</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="Linux"><span>Linux</span></div>
    <div class="tech-item"><img src="https://www.vectorlogo.zone/logos/getpostman/getpostman-icon.svg" alt="Postman"><span>Postman</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/d3js/d3js-original.svg" alt="D3.js"><span>D3.js</span></div>
    <div class="tech-item"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="HTML5"><span>HTML5</span></div>
  </div>

  <!-- PROJECTS -->
  <div class="section-header">
    <span class="section-icon">🚀</span>
    FEATURED.PROJECTS
    <span class="section-icon">🚀</span>
  </div>
  <div class="projects-grid">
    <div class="project-card">
      <span class="project-emoji">🌿</span>
      <a class="project-name" href="https://courageous-sawine-39b32c.netlify.app/" target="_blank">Rootsy</a>
      <p class="project-desc">A modern plant care platform with real-time plant tracking, care reminders, and community sharing features.</p>
      <div class="project-tags">
        <span class="project-tag">REACT</span>
        <span class="project-tag">NODE.JS</span>
        <span class="project-tag">MONGODB</span>
        <span class="project-tag">LIVE</span>
      </div>
    </div>
    <div class="project-card">
      <span class="project-emoji">🔗</span>
      <a class="project-name" href="https://github.com/CodeConnect" target="_blank">CodeConnect</a>
      <p class="project-desc">A developer collaboration platform designed to connect programmers worldwide for open-source and private projects.</p>
      <div class="project-tags">
        <span class="project-tag">NEXT.JS</span>
        <span class="project-tag">COLLAB</span>
        <span class="project-tag">OPEN SOURCE</span>
      </div>
    </div>
    <div class="project-card">
      <span class="project-emoji">💰</span>
      <a class="project-name" href="#" target="_blank">MoneyMaster</a>
      <p class="project-desc">An intelligent personal finance tracker with AI-powered insights, budgeting tools, and expense visualization.</p>
      <div class="project-tags">
        <span class="project-tag">REACT</span>
        <span class="project-tag">DJANGO</span>
        <span class="project-tag">FINANCE</span>
        <span class="project-tag">IN DEV</span>
      </div>
    </div>
  </div>

  <!-- SOCIAL LINKS -->
  <div class="section-header">
    <span class="section-icon">🌐</span>
    CONNECT.NETWORK
    <span class="section-icon">🌐</span>
  </div>
  <div class="social-grid" style="margin-bottom:50px;">
    <a href="https://twitter.com/raditkhanyt" class="social-link twitter" target="_blank">🐦 Twitter</a>
    <a href="https://www.linkedin.com/in/riyadus-salehin-50b749243/" class="social-link linkedin" target="_blank">💼 LinkedIn</a>
    <a href="https://portfolioriyadus.netlify.app/" class="social-link github" target="_blank">🌐 Portfolio</a>
    <a href="https://leetcode.com/u/radit90070/" class="social-link leetcode" target="_blank">⚔️ LeetCode</a>
    <a href="https://www.youtube.com/channel/ucudx01xh6zxjw-06m5wab7q" class="social-link youtube" target="_blank">▶️ YouTube</a>
    <a href="https://discord.gg/riyadkhan0340" class="social-link discord" target="_blank">💬 Discord</a>
    <a href="https://fb.com/riyad.khan.384" class="social-link facebook" target="_blank">📘 Facebook</a>
  </div>

  <!-- FUN FACT -->
  <div class="fun-fact">
    <div class="fun-fact-label">// SYSTEM.FUN_FACT</div>
    <div class="fun-fact-text">
      ⚡ Did you know? The shortest war in history was between Britain and Zanzibar in 1896. 
      It lasted only <span style="color:var(--neon-cyan);font-weight:700">38 minutes</span>! 
      Zanzibar surrendered after a British warship bombarded the island's palace. 
      They didn't even have time to pop popcorn! 🍿
    </div>
  </div>

  <!-- SECOND GIF ROW -->
  <div class="gif-showcase" style="grid-template-columns:1fr 1fr;gap:16px;margin-bottom:50px">
    <div class="gif-item" style="aspect-ratio:unset;height:200px">
      <img src="https://media.giphy.com/media/RbDKaczqWovIugyJmW/giphy.gif" alt="Code" style="width:100%;height:100%;object-fit:cover" />
    </div>
    <div class="gif-item" style="aspect-ratio:unset;height:200px">
      <img src="https://media.giphy.com/media/SWoSkN6DxTszqIKEqv/giphy.gif" alt="Dev" style="width:100%;height:100%;object-fit:cover" />
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-glow">RIYADUS SALEHIN</div>
    <div class="footer-text">FULL STACK DEVELOPER · BANGLADESH · 2024</div>
    <div style="margin-top:15px;font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--text-dim)">
      <span style="color:var(--neon-cyan)">const</span> passion = <span style="color:var(--neon-green)">"Building the future, one commit at a time"</span>;
    </div>
  </div>

</div>

<script>
// ===== CURSOR TRAIL =====
const cursorDot = document.getElementById('cursorDot');
document.addEventListener('mousemove', e => {
  cursorDot.style.left = e.clientX + 'px';
  cursorDot.style.top = e.clientY + 'px';
});

// ===== PARTICLES =====
const particleContainer = document.getElementById('particles');
const colors = ['#00f5ff', '#bf00ff', '#39ff14', '#ff6b00'];
for (let i = 0; i < 60; i++) {
  const p = document.createElement('div');
  p.className = 'particle';
  p.style.cssText = `
    left: ${Math.random() * 100}%;
    background: ${colors[Math.floor(Math.random() * colors.length)]};
    width: ${Math.random() * 3 + 1}px;
    height: ${Math.random() * 3 + 1}px;
    animation-duration: ${Math.random() * 15 + 10}s;
    animation-delay: ${Math.random() * 10}s;
    box-shadow: 0 0 6px currentColor;
  `;
  particleContainer.appendChild(p);
}

// ===== TYPING EFFECT =====
const texts = ['Full Stack Developer 🇧🇩', 'React & Next.js Expert ⚛️', 'Django Backend Dev 🐍', 'UI/UX Enthusiast 🎨'];
let textIdx = 0, charIdx = 0, deleting = false;
const typingEl = document.getElementById('typingText');

function typeLoop() {
  const currentText = texts[textIdx];
  if (!deleting) {
    typingEl.textContent = currentText.slice(0, charIdx + 1);
    charIdx++;
    if (charIdx === currentText.length) { deleting = true; setTimeout(typeLoop, 2000); return; }
  } else {
    typingEl.textContent = currentText.slice(0, charIdx - 1);
    charIdx--;
    if (charIdx === 0) { deleting = false; textIdx = (textIdx + 1) % texts.length; }
  }
  setTimeout(typeLoop, deleting ? 50 : 80);
}
setTimeout(typeLoop, 1500);

// ===== COUNT UP ANIMATION =====
function animateCount(el, target) {
  const duration = 2000;
  const start = Date.now();
  const timer = setInterval(() => {
    const elapsed = Date.now() - start;
    const progress = Math.min(elapsed / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3);
    el.textContent = Math.floor(eased * target).toLocaleString();
    if (progress === 1) clearInterval(timer);
  }, 16);
}

const statNums = document.querySelectorAll('.stat-number');
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const target = parseInt(e.target.dataset.target);
      animateCount(e.target, target);
      observer.unobserve(e.target);
    }
  });
}, { threshold: 0.5 });
statNums.forEach(n => observer.observe(n));

// ===== VIEW COUNTER =====
let views = 342;
const vc = document.getElementById('viewCounter');
let v = 0;
const vcTimer = setInterval(() => {
  v += Math.ceil(views / 80);
  if (v >= views) { v = views; clearInterval(vcTimer); }
  vc.textContent = v.toLocaleString();
}, 25);
</script>
</body>
</html>
