<div align="center">

# 喰 LEBOT — Portfólio temático Tokyo Ghoul

![License: MIT](https://img.shields.io/badge/Licença-MIT-red.svg)
![Three.js](https://img.shields.io/badge/Three.js-r187-black.svg)
![GSAP](https://img.shields.io/badge/GSAP-3.12-green.svg)
![Deploy](https://img.shields.io/badge/Deploy-Vercel-black.svg)

**[▶ Ver no ar: lebot.vercel.app](https://lebot.vercel.app/)**

Portfólio pessoal com a estética de Tokyo Ghoul — cinemática de entrada,
centopeia procedural em WebGL, player de música, flor higanbana interativa
e carrossel de dossiês dos personagens.

</div>

---

## ✨ Mecânicas

| Mecânica | Descrição |
|---|---|
| **1000-7** | Segure/clique no contador do herói: correntes de ferro, glitch, o Kaneki surge na tela e uma **centopeia 3D (WebGL, Three.js)** atravessa a página — com fallback automático para Canvas2D em qualquer dispositivo sem WebGL |
| **Centopeia procedural** | Cinemática própria: mola de espaçamento, onda de dois harmônicos, marcha metacrônica com IK de 2 ossos por perna, timestep fixo de 120 Hz (idêntico em telas de 60/90/120/144 Hz) |
| **Flor higanbana** | Clique troca a frase (fila embaralhada, sem repetição) e a cor da flor muda conforme o personagem — 22 frases de 12 personagens |
| **Player de música** | 3 faixas com capa, visualizador, seek, volume, prev/next, atalhos de teclado (`Space`, `Ctrl+←/→`) e modo recolhido |
| **Dossiês** | Carrossel de 5 personagens com swipe/teclado/scroll horizontal, profundidade circular e pré-decodificação de imagens |
| **Modo de movimento** | Botão no HUD liga/desliga as animações com persistência local (`lebot:motion:v2`) — independente das configurações do dispositivo |

## 🎯 Otimizações

- **3D lazy**: o Three.js (383 KB) só é carregado no primeiro clique do 1000-7 — custo zero no carregamento inicial
- **InstancedMesh**: corpo, pernas e ossos da centopeia em ~7 draw calls
- **Watchdog de FPS**: degrada DPR → 1 e, se necessário, cai pro motor 2D automaticamente
- **Tiers de dispositivo**: full / lite / mini conforme CPU e memória (brasas, parallax e reveals se adaptam)
- **Compositor-only**: animações contínuas usam apenas `transform`/`opacity`; pausa por `IntersectionObserver` e aba oculta
- **Vídeo AV1 1080p** com fallback H.264 para Safari antigo; assets WebP nas imagens
- **Acessibilidade**: alvos de 44px, foco visível, `aria-pressed`, toasts com `role=status`

## 🧱 Stack

HTML/CSS/JS puro (sem build) · GSAP + ScrollTrigger · Lenis · Three.js r187 · Tailwind compilado estaticamente · Vercel

## 📂 Estrutura

```
index.html          — tudo-em-um: marcação, estilos e motores (2D/3D)
tailwind.css        — utilitários Tailwind compilados estaticamente
vendor/             — libs self-hosted e pinadas (GSAP, ScrollTrigger, Lenis, three)
*.mp3 / *.webp / *  — mídia do site (áudio, vídeo, capas, perfis)
LICENSE             — MIT (código) + notas de licenças de terceiros
```

## 🚀 Rodando localmente

É um site estático — qualquer servidor serve:

```bash
npx serve .           # ou
python3 -m http.server
```

> Abrir o `index.html` direto do disco funciona, mas o motor 3D usa módulos ES —
> prefira um servidor local.

## 📄 Licença

Código sob [MIT](LICENSE). Mídias são propriedade do autor.
*Tokyo Ghoul © Sui Ishida / Shueisha — projeto de fã, sem fins comerciais.*
