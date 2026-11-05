<div align="center">

# 喰 LEBOT — Portfólio temático Tokyo Ghoul

![License: MIT](https://img.shields.io/badge/Licença-MIT-red.svg)
![GSAP](https://img.shields.io/badge/GSAP-3.12-green.svg)
![Deploy](https://img.shields.io/badge/Deploy-Vercel-black.svg)

**[▶ Ver no ar: lebot.vercel.app](https://lebot.vercel.app/)**

Portfólio pessoal com a estética de Tokyo Ghoul — cinemática de entrada,
centopeia procedural em Canvas2D, player de música, flor higanbana interativa
e carrossel de dossiês dos personagens.

</div>

---

## ✨ Mecânicas

| Mecânica | Descrição |
|---|---|
| **1000-7** | Segure/clique no contador do herói: correntes de ferro, glitch, o Kaneki surge na tela e uma **centopeia procedural (Canvas2D)** atravessa a página |
| **Centopeia procedural** | Cinemática própria: mola de espaçamento, onda de dois harmônicos, marcha metacrônica das pernas, timestep fixo de 120 Hz (idêntico em telas de 60/90/120/144 Hz). Visual original do site, preservado |
| **Flor higanbana** | Clique troca a frase (fila embaralhada, sem repetição) e a cor da flor muda conforme o personagem — 22 frases de 12 personagens |
| **Player de música** | 3 faixas com capa, visualizador, seek, volume, prev/next, atalhos de teclado (`Space`, `Ctrl+←/→`) e modo recolhido |
| **Dossiês** | Carrossel de 5 personagens com swipe/teclado/scroll horizontal, profundidade circular e pré-decodificação de imagens |
| **Modo de movimento** | Botão no HUD liga/desliga as animações com persistência local (`lebot:motion:v2`) — independente das configurações do dispositivo |

## 🎯 Otimizações

- **Centopeia com sprites pré-assados**: cada tergito e a cabeça são desenhados 1× em canvas offscreen (MDN: evitar `shadowBlur`/gradientes por frame); o loop por frame vira `clearRect` + ~36 `drawImage` + 1 stroke
- **Sem Three.js**: a versão WebGL foi aposentada — o site não baixa mais ~800 KB de motor 3D
- **Vídeo de fundo pausado durante a cena do 1000-7** (o pico de GPU/CPU) e em aba oculta; governador de FPS degrada vídeo/tier quando a média cai
- **Tiers de dispositivo**: full / lite / mini conforme CPU e memória (brasas, parallax e reveals se adaptam)
- **Compositor-only**: animações contínuas usam apenas `transform`/`opacity`; pausa por `IntersectionObserver` e aba oculta
- **Vídeo AV1 1080p** com fallback H.264 para Safari antigo; assets WebP nas imagens
- **Acessibilidade**: alvos de 44px, foco visível, `aria-pressed`, toasts com `role=status`

## 🧱 Stack

HTML/CSS/JS puro (sem build) · GSAP + ScrollTrigger · Lenis · Tailwind compilado estaticamente · Vercel

## 📂 Estrutura

```
index.html          — tudo-em-um: marcação, estilos e motores de animação
tailwind.css        — utilitários Tailwind compilados estaticamente
vendor/             — libs self-hosted e pinadas (GSAP, ScrollTrigger, Lenis)
*.mp3 / *.webp / *  — mídia do site (áudio, vídeo, capas, perfis)
LICENSE             — MIT (código) + notas de licenças de terceiros
```

## 🚀 Rodando localmente

É um site estático — qualquer servidor serve:

```bash
npx serve .           # ou
python3 -m http.server
```

## 📄 Licença

Código sob [MIT](LICENSE). Mídias são propriedade do autor.
*Tokyo Ghoul © Sui Ishida / Shueisha — projeto de fã, sem fins comerciais.*
