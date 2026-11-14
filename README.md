# O Claude vira seu estÃºdio de vÃ­deo: 7 repositÃ³rios grÃ¡tis

VÃ­deo do INEMA.CLUB, com avatar e voz do Nei Maldaner, sobre sete repositÃ³rios gratuitos do GitHub que mostram como fazer
vÃ­deo pedindo para o Claude escrever o vÃ­deo como cÃ³digo: motion graphics, desenho animado, explicativos e clipes de mÃºsica.

**Assistir:** https://inematds.github.io/claude-estudio-video/videos/ (16:9 e 9:16) Â· YouTube: [16:9](https://www.youtube.com/watch?v=xkAzBrdUVhA) Â· [9:16](https://www.youtube.com/watch?v=c4xoc26xFEU)

## Como funciona

O Claude nÃ£o gera arquivo de vÃ­deo. Ele escreve uma **pÃ¡gina web que desenha cada quadro**; o **Chrome** tira uma foto de
cada quadro e o **FFmpeg** junta tudo num MP4. Como cada quadro Ã© desenhado por cÃ³digo, o texto sai nÃ­tido e qualquer coisa
muda sÃ³ pedindo.

```
seu prompt â†’ Claude Code â†’ pÃ¡gina web (HTML + JS) â†’ Chrome (quadro a quadro) â†’ FFmpeg â†’ MP4
```

VocÃª precisa de Node, Chrome e FFmpeg (grÃ¡tis) e do Claude Code (plano pago do Claude). Os repositÃ³rios sÃ£o grÃ¡tis.

## Os 7 repositÃ³rios

Estrelas e licenÃ§a conferidas em 22/10/2026.

| # | RepositÃ³rio | O que tem | â˜… | LicenÃ§a |
|---|---|---|---|---|
| 1 | [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos) | 703 prompts de vÃ­deos reais, cada um com o link do post original (motion graphics, explicativos, 3D, joguinhos) | 9,2 mil | MIT |
| 2 | [joeseesun/opus-video-prompts](https://github.com/joeseesun/opus-video-prompts) | 54 casos e 18 prompts completos; pÃ¡gina em chinÃªs, prompts em inglÃªs. Tem o prompt de uma linha | 690 | nÃ£o informada |
| 3 | [Vincentwei1021/mg-styles-15](https://github.com/Vincentwei1021/mg-styles-15) | 15 estilos de motion graphics: filme de 10 s + prompt + cÃ³digo. Troque sÃ³ o `Creative seed`; revise com `rubric.md` | 1,8 mil | MIT |
| 4 | [lemomo-ai/lemo-opuscar](https://github.com/lemomo-ai/lemo-opuscar) | Skill do Claude Code com 59 estilos de filme (aquarela, nanquim, giz de cera, xilogravuraâ€¦) | 5,5 mil | MIT |
| 5 | [JohnHeibel/ClaudeAnimationBase](https://github.com/JohnHeibel/ClaudeAnimationBase) | Kit de desenho animado com o Clawd e 31 emoÃ§Ãµes, guia de animaÃ§Ã£o para o modelo | 1,6 mil | MIT |
| 6 | [JohnHeibel/PDoomVideo](https://github.com/JohnHeibel/PDoomVideo) + [mexicat/pdoom-video](https://github.com/mexicat/pdoom-video) | Dois clipes para a mesma mÃºsica: pinceladas Ã— karaokÃª neon em 4K 60 fps | 2,5 mil + 3,3 mil | nÃ£o informada + MIT |
| 7 | [athemeroy/awesome-claude-5-5-videos](https://github.com/athemeroy/awesome-claude-5-5-videos) | 424 posts de origem (Opus, Sonnet, Haiku); tabela "sua tarefa â†’ exemplo para copiar" | 721 | CC-BY-4.0 |

## Prompts para comeÃ§ar

- **Uma linha** (repositÃ³rio 2): `make a modern slick and punchy video for a modern startup that works on inference`
  (o criador relata ~1 min e ~US$ 2). Troque pelo seu tema.
- **Instalar o lemo-opuscar** (repositÃ³rio 4):
  ```bash
  claude plugin marketplace add lemomo-ai/lemo-opuscar
  claude plugin install lemo-opuscar@lemolab
  ```
  Depois: *"FaÃ§a um filme de 45 s, em aquarela, sobre a fazenda de cafÃ© da minha famÃ­lia."* Um filme leva de 30 a 60 min
  e gasta bastante token: comece curto.
- **Desenho animado** (repositÃ³rio 5): *"Read ANIMATION_GUIDE.md, then make a 15-second video of Clawd trying to catch a butterfly."*

## Limites

- Ã“timo para motion graphics, desenho animado, explicativos e clipes com letra. **NÃ£o** Ã© para pessoas realistas (aÃ­ entra um
  modelo de vÃ­deo).
- O mesmo prompt gera um filme diferente a cada vez: conte com 2 ou 3 rodadas.
- Custo: um criador relata a mesma cena por US$ 2,19 no Haiku e US$ 3,04 no Opus. Teste antes o modelo mais barato.
- **Por onde comeÃ§ar:** um estilo do lemo-opuscar, menos de 30 s, sobre algo que vocÃª vende ou ensina.

## O processo, do inÃ­cio ao fim

Como este vÃ­deo foi feito (ðŸ§  sessÃ£o com o Nei Â· âš™ï¸ script Â· ðŸ¤– agente):

1. ðŸ§  Pedido do Nei: link de referÃªncia + "crie um repo, 16:9 e 9:16, lives4, INEMA.VIDEOS".
2. âš™ï¸ Legenda da referÃªncia (`yt-dlp --write-auto-subs`) e download (inemavox `baixar_v1.py`).
3. ðŸ§  NÃºmeros conferidos nos repositÃ³rios pela API do GitHub; roteiro em portuguÃªs (`roteiro/pt.json`, 10 cenas).
4. âš™ï¸ Avatar e voz do Nei pelo estÃºdio HeyGen (`explicavideos/engine/heygen-studio.mjs`), 1 bloco.
5. ðŸ¤– Artes de capa e de abertura de cada repositÃ³rio pelo Codex (`image_gen`).
6. ðŸ§  Roteiro visual (`visual/gerar_visual.py`): trechos animados da referÃªncia + diagrama, prints do GitHub, terminal e contadores.
7. âš™ï¸ Render no Explicavideos v2 (HyperFrames: pÃ¡gina â†’ Chrome â†’ FFmpeg, o mesmo caminho do vÃ­deo).
8. âš™ï¸ VersÃ£o 9:16: visual do 16:9 em cima, avatar embaixo.
9. âš™ï¸ `scripts/publica.py`: release com os MP4 e o player em `videos/`.
10. âš™ï¸ YouTube (canal INEMA Tec, via yt-pubx) e Telegram INEMA.VIDEOS.

ConteÃºdo aberto e gratuito do [INEMA.CLUB](https://inema.club).

---

Projeto adaptado da comunidade INEMA TDS - Marca Arckhe