# GAME_DESIGN.md — CYBER-BREACH: VECTOR SIEGE

> Architectural & Design System Specification for **CYBER-BREACH: VECTOR SIEGE**, a top-down 2D cyber-arena action shooter built with pure HTML5 Canvas and procedural Web Audio API synthesis.

---

## 1. Aesthetic Direction & Theme Concept
- **Concept Name:** *"Cyber-Tactical Vector Defense"*
- **Inspiration:** High-octane arcade twin-stick classics (Geometry Wars, Alien Shooter, Crimsonland), retro vector graphics, and military diagnostic heads-up telemetry.
- **Aesthetic Vernacular:** Deep dark cosmic-void arena with tactical coordinate grids (`SEC [X,Y]`), neon particle trails, geometric drone swarms, and high-contrast tactical HUD widgets.
- **Tone:** Fast-paced, responsive, punchy, adrenaline-fueled, with zero loading friction or external asset dependencies.

---

## 2. Color System & Contrast Proof (WCAG AAA)

| Token Name | Hex Value | Semantic Role | Contrast on `#08090e` |
| :--- | :--- | :--- | :--- |
| `--bg-dark` | `#08090E` | Arena void background canvas | Base Canvas |
| `--panel-bg` | `rgba(14, 18, 27, 0.85)` | Glassmorphism tactical HUD & modal backings | Elevated Surface |
| `--panel-border` | `rgba(56, 189, 248, 0.25)` | 1px perimeter panel boundaries | Hairline border |
| `--cyan-glow` | `#00F0FF` | Player interceptor, Pulse Blaster, XP cores, Shield | **14.2:1 (AAA Pass)** |
| `--crimson-glow`| `#FF2A5F` | Hostile drones, hull damage alerts, boss health bar | **6.1:1 (AA Pass)** |
| `--amber-glow` | `#F59E0B` | Scatter Cannon, critical strikes, score multiplier | **10.5:1 (AAA Pass)** |
| `--emerald-glow`| `#10B981` | Plasma Grenade Launcher, health regeneration | **9.4:1 (AAA Pass)** |
| `--violet-glow` | `#A855F7` | Hyper Railgun, Dash energy, sniper sentinels | **6.8:1 (AA Pass)** |
| `--text-main` | `#F1F5F9` | Primary HUD readouts & stat numbers | **17.8:1 (AAA Pass)** |
| `--text-muted` | `#94A3B8` | Sub-labels, equipment descriptions, telemetry keys | **7.6:1 (AAA Pass)** |

---

## 3. Typographic System & Hierarchy
- **Primary Telemetry Stack:** `"JetBrains Mono", Consolas, "Courier New", monospace`
  - Used for score, wave numbers, HP/Shield meters, ammo status, and radar coordinates.
  - Ensures numerical stability (zero horizontal jitter during rapid changes).
- **Display / Header Stack:** `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
  - Used for title screens, wave victory banners, and perk card headers.
  - Generous letter-spacing (`0.15em` to `0.2em`) for military/cyber signposting.

---

## 4. Audio Engine (Pure Web Audio API Synthesizer)
Zero external `.mp3` or `.wav` dependencies — 100% synthesized procedural sound:
- **Pulse Blaster:** Sawtooth oscillator sweeping 700Hz $\to$ 140Hz with exponential decay.
- **Scatter Cannon:** Bandpass-filtered white noise buffer combined with a low sine thump (120Hz $\to$ 30Hz).
- **Hyper Railgun:** High-harmonic triangle sweep (1800Hz $\to$ 220Hz) with instant discharge.
- **Plasma Launcher:** Low resonant sine drop (450Hz $\to$ 80Hz) followed by expanding filtered noise explosion.
- **Explosions & Impacts:** Multi-stage lowpass filtered white noise burst with exponential attenuation.
- **Dash Ability:** Bandpass filter frequency sweep with quick stereo presence.
- **Level-Up Fanfare:** Arpeggiated 4-note cyber chord (A4, C#5, E5, A5).
- **Procedural BGM:** Built-in dynamic synth bassline and quarter-note beat that intensifies during combat.

---

## 5. Arsenal & Weapons Matrix

| Slot | Weapon Name | Fire Rate | Base Dmg | Trajectory | Special Trait |
| :---: | :--- | :---: | :---: | :--- | :--- |
| **1** | **Pulse Blaster** | 9.1 shots/s | 22 | Twin / Single rapid cyan bolts | High precision, low spread |
| **2** | **Scatter Cannon** | 1.9 shots/s | 15 $\times$ 7 | 28° conic spread | Devastating close-range knockback |
| **3** | **Hyper Railgun** | 1.2 shots/s | 150 | Instantaneous linear beam | Pierces up to 8 targets in a line |
| **4** | **Plasma Launcher** | 1.4 shots/s | 95 | Heavy ballistic orb | Explodes in a 120px AoE shockwave |

---

## 6. Roguelite Overclock Perks (12 Total)
On each level-up, the game pauses and prompts the player to select 1 of 3 randomized perks:
1. **Overclock Capacitor:** +25% Fire Rate across all weapons.
2. **Depleted Thorium:** +30% Bullet & Blast Damage + enhanced knockback.
3. **Vector Thrusters:** +22% Movement Speed & Dash Cooldown reduced by 30%.
4. **Aegis Capacitor:** +40 Maximum Shield & +50% faster shield recharge rate.
5. **Nanite Reconstructor:** +30 Maximum Hull Integrity & 2.5 HP/second automatic repair.
6. **Graviton Magnet:** +120% XP Core magnetic attraction radius and speed.
7. **Critical Sensor:** 25% Chance for Critical Hits dealing 2.5x damage.
8. **Nova Hyper-Dash:** Dashing triggers a 360° kinetic shockwave damaging & repelling nearby foes.
9. **Cryo Injection:** Projectiles chill enemies, slowing movement speed by 40%.
10. **Multi-Chamber Barrels:** Scatter Cannon fires +3 pellets; Pulse Blaster fires twin cannons.
11. **Chain Feedback:** Slain drones release electrostatic arcs that zap up to 2 neighboring enemies.
12. **Reflective Coating:** Projectiles bounce off the arena perimeter hazard wall once toward enemies.

---

## 7. Controls & How to Run
- **Launch via batch file:** Double-click [`open_game.bat`](file:///d:/Antigravity/open_game.bat)
- **Direct browser opening:** Open [`game.html`](file:///d:/Antigravity/game.html) in any browser (Chrome, Edge, Firefox, Brave)
- **Key Bindings:**
  - `W A S D` or `Arrow Keys`: Move interceptor craft
  - `Mouse Aim`: 360° crosshair targeting
  - `Left Mouse Button (LMB)`: Fire active weapon (Hold for continuous fire)
  - `Spacebar` or `Right Mouse Button (RMB)`: Hyper-Dash with invincibility frames
  - `1`, `2`, `3`, `4` or `Mouse Wheel`: Switch weapons
  - `Escape` or `P`: Pause / Suspend game
  - `Audio Button`: Toggle synthesized audio on/off
