# Especificação de Layout Exaustiva: Aprendendo a Linguagem do Meu Filho

Este documento define **cada detalhe em nível de pixel** para a construção da página de vendas. Siga as instruções estritamente para garantir a fidelidade da implementação e das micro-interações.

**Variáveis Globais (Definidas no CSS)**
- `--color-primary`: #EA5E6A (Rosa/Vermelho)
- `--color-secondary`: #6CC8E9 (Azul Claro)
- `--color-accent`: #FECE17 (Amarelo)
- `--color-bg`: #F3FBFD (Fundo soft azul)
- `--color-text`: #2D3E4E (Texto escuro/Navy)
- `--color-white`: #FFFFFF
- `--font-main`: 'Outfit', sans-serif
- `--font-playful`: 'Fredoka', sans-serif

---

## Seção 1: Hero (Previamente Implementado)

### Arquétipo e Constraints
- **Arquétipo:** Overlapping Grid / Floating Elements
- **Constraints:** Float Loop, Absolute Positioning
- **Justificativa:** Estabelece imediatamente o tom lúdico, orgânico e acolhedor do universo infantil sem perder o peso de um programa estruturado.

### Conteúdo
- **Pre-Hero:** PARA CRIANÇAS DE 0 A 3 ANOS | PROGRAMA DE ESTÍMULO À COMUNICAÇÃO E LINGUAGEM
- **Headline:** Aprendendo a Linguagem do Meu Filho
- **Subheadline:** Entenda os sinais do seu filho e aprenda a estimular a fala através da rotina e do brincar, garantindo que ele alcance cada marco do desenvolvimento no tempo certo.
- **CTA:** QUERO COMEÇAR O PROGRAMA AGORA

### Notas de Implementação
A seção hero já está estruturada no arquivo `index.html` e `style.css`. Mantém-se o grid de 1.1fr e 0.9fr, as formas orgânicas no background, as animações de flutuação e a transição por SVG *Wave* para a próxima seção.

---

## Seção 2: Missão e Luz

### Arquétipo e Constraints
- **Arquétipo:** Storytelling / Layered
- **Constraints:** Scroll Progress (View Timeline), Light Leak, Ambient Motion
- **Justificativa:** O texto fala da "luz" que a criança traz e que não pode ser apagada. Um efeito de luz interligado ao scroll torna a metáfora tangível e imersiva.

### Conteúdo
- **Título:** Toda criança nasce com uma luz radiante. Nossa missão é não deixar que ela se apague.
- **Texto:** Junto com um novo bebê, nasce uma luz. Uma energia que precisa ser alimentada por um ambiente que nutra seu corpo, mente e emoções. Porém, com as novas experiências fora da barriga, a falta de estímulos nutritivos pode gerar frustrações na comunicação e, aos poucos, ir apagando a autoconfiança do pequeno falante.
- **Ênfase:** Nós vemos isso diariamente. E entendemos que para manter essa luz acesa, a criança precisa do estímulo mais poderoso de todos: o estímulo da sua família.
- **Fechamento:** Vocês, familiares, são os guardiões de um tesouro. Por isso, o programa Aprendendo a Linguagem do Meu Filho foi estruturado para entregar a vocês as ferramentas para proteger, amar e estimular essa criança. O objetivo é garantir que ela cresça falante, confiante e cheia de luz para espalhar pelo mundo.

### Layout
- **Container:** `max-width: 1200px`, `margin: 0 auto`, `padding: 100px 20px`.
- **Estrutura:** Grid assimétrico com `grid-template-columns: 1.2fr 0.8fr`, `gap: 80px`. O texto fica na esquerda e a composição visual na direita.
- **Background:** `#FFFFFF` contínuo puxando da wave do Hero.

### Tipografia
- **Título principal:** `clamp(2rem, 4vw, 3rem)`, font `Outfit`, peso 700, line-height 1.2, cor `#2D3E4E`. "luz radiante" usa fonte `Fredoka` e cor `#EA5E6A`.
- **Parágrafos padrão:** `Outfit`, 1.15rem, line-height 1.6, cor `#4A5568`. Margin-bottom de 20px.
- **Box de Ênfase:** `Outfit`, 1.25rem. Negrito em peso 700.

### Cores
- **Box de ênfase (background):** `rgba(108, 200, 233, 0.1)`.
- **Box de ênfase (border-left):** 6px solid `#6CC8E9`.
- **Fechamento (texto):** Cor `#EA5E6A`, peso 600.

### Interatividade e Animações (REQUISITO EXCLUSIVO)
- **A Luz Guia (Efeito Topo Direita):** Um elemento absoluto posicionado no topo-direito do viewport (ou sticky top: 0, right: 0 no container pai).
  - Usar CSS `animation-timeline: view();` atrelado ao scroll da página.
  - Conforme o usuário faz o scroll para baixo, a luz (um gradiente radial `radial-gradient(circle, rgba(254, 206, 23, 0.8) 0%, transparent 60%)` com `filter: blur(80px)`) varia de `opacity: 0.2` a `opacity: 1`, e `transform: scale(0.5)` para `scale(1.5)`. 
- **Entrada de Textos:** Animação `fade-up` via AOS, duração 800ms. O Box de ênfase entra com delay de 200ms.
- **Orbe Secundária:** No bloco visual à direita, manter uma orbe pulsante com `breathe` infinito (scale 1 para 1.2, opacity 0.8 para 0.5 em 4s).

### Responsividade
- **Em < 992px:** Layout colapsa para `grid-template-columns: 1fr`. Foco apenas na cópia textual. A orbe passa para baixo do texto (ou vira background sutil) para não bloquear a leitura.

---

## Seção 3: O Quebra-cabeça

### Arquétipo e Constraints
- **Arquétipo:** Parallax Layers
- **Constraints:** Parallax Elements, Free Drag, Hover Scale
- **Justificativa:** O pedido explicita peças flutuando com parallax em resposta à metáfora do quebra-cabeças no texto. Promerove forte imersão lúdica.

### Conteúdo
- **Título:** Montando o quebra-cabeça da comunicação: A família como peça principal.
- **Analogia:** Já tentou montar um quebra-cabeça? Primeiro, encontramos as peças das laterais para criar a base, certo? Pois bem, a família são as peças laterais.
- **Objetivo:** O objetivo deste programa é orientar você para que forme essa base sólida. É essa estrutura que permite que o desenho principal — a criança se expressando por gestos, palavras e expressões — apareça de forma natural e confiante.

### Layout
- **Padding:** `120px 0`.
- **Estrutura:** `.container` estreito `max-width: 800px`, texto totalmente centralizado. Foco absoluto na mensagem.
- **Posicionamento:** Elementos decorativos (peças) inseridas como `position: absolute` distribuídas ao redor do container de texto dentro de seu wrapper parent com `position: relative` e `overflow: hidden`.

### Tipografia
- **Título:** `Fredoka`, `clamp(2.5rem, 5vw, 3.5rem)`, texto `#2D3E4E`.
- **Corpo:** `Outfit`, 1.25rem, cor `#4A5568`, line-height 1.7.

### Cores
- **Fundo da Seção:** `#F3FBFD`.
- **Peças SVG:** Variadas entre os brand colors `#EA5E6A`, `#6CC8E9`, `#FECE17`, com `opacity: 0.9` e sutil drop-shadow `0 10px 30px rgba(0,0,0,0.1)`. Algumas brancas `#FFF`.

### Elementos Visuais e Animações (REQUISITO EXCLUSIVO)
- **Peças Flutuantes:** Desenhos de peças de puzzle estilo *soft/puffy* espalhados.
- **Parallax CSS Nativo / Mouse:**
  - Implementar CSS animado vinculado a custom properties calculadas via JS *ou* View Timeline CSS para rolagem. Ex: `.piece-front { transform: translateY(calc(var(--scroll) * -0.2px)); }`.
  - Ter no mínimo 3 níveis de profundidade: Background (pequenas e com blur, andam devagar), Midground (peso base) e Foreground (grandes e focadas, andam mais de pressa).
- **Float Infinito:** Somado ao parallax, as peças devem ter um `animation: gentleFloat X.Xs ease-in-out infinite alternate` aleatório para parecer que estão em suspensão.

### Interatividade
- **Hover na Peça:** Ao passar o mouse, a peça dá um ligeiro "salto" vindo ao usuário: `transform: scale(1.15) rotate(10deg)`, cursor passa para pointer, sutil sensação lúdica.

---

## Seção 4: O Caminho Estruturado

### Arquétipo e Constraints
- **Arquétipo:** Scroll Storytelling / Responsive Columns
- **Constraints:** Sticky Element, Draw SVG, Reveal on Demand
- **Justificativa:** Apresenta passos progressivos. Usar uma estrutura onde o título/resumo acompanha no lado enquanto os passos rolam do outro, com uma linha se conectando, traduz perfeitamente um "Caminho".

### Conteúdo
- **Introdução:** Neste programa, você aprende a montar cada parte desse quebra-cabeça através de um caminho estruturado:
- **Passo 1:** **A Base** - Entendendo como o sono, a respiração e a alimentação sustentam a fala.
- **Passo 2:** **O Preparo** - Valorizando a atenção e a imitação como os primeiros encaixes da linguagem.
- **Passo 3:** **A Intenção** - Aprendendo a ler cada gesto e comportamento do seu filho.
- **Passo 4:** **O Diálogo** - Praticando a espera e o estímulo correto para cada idade.
- **Conclusão:** Você assume o seu lugar como a peça principal no desenvolvimento do seu filho, com a segurança de saber exatamente como guiar esse processo.

### Layout
- **Padding:** `120px 0`.
- **Estrutura (Desktop):** Split Assymétrico com `grid-template-columns: 350px 1fr`; `gap: 60px`.
- Coluna Esquerda: Um `.sticky-nav` container (`position: sticky; top: 15vh;`). Ele contém a **Introdução** e a **Conclusão**.
- Coluna Direita: O "Caminho". Uma timeline contendo os 4 passos, empilhados com `gap: 40px`.

### Linha do Caminho (Draw SVG)
- Uma linha SVG conectando rigidamente os itens, cor `#6CC8E9`. Através de `stroke-dasharray` ou vinculando a altura ao scroll progressivo, a linha "pinta" (fica primary `#EA5E6A`) de acordo com o progresso pelo conteúdo.

### Divisão Interna dos Passos
- Cada passo é um "Card". `padding: 40px`, fundo `#FFFFFF`, borda redonda pesada `border-radius: 20px`, sombra suave `box-shadow: 0 10px 40px rgba(0,0,0,0.03)`.
- **Número do Passo:** Absoluto, enorme e translucido atrás do card (e.g., `font-size: 8rem`, `opacity: 0.05`, `font-family: Fredoka`).

### Tipografia e Cores
- **Intro Sticky:** `Outfit`, 1.5rem, `#2D3E4E` peso 700.
- **Títulos dos Passos:** `Fredoka`, 1.8rem, `#EA5E6A`.
- **Texto dos Passos:** `Outfit`, 1.15rem, `#4A5568`.

### Animações
- Revelação gradual com fade-up/stagger de 150ms de diferença por card.
- Scale-in do número no fundo de cada Card no hover.

### Responsividade
- **Mobile (< 992px):** `grid-template-columns: 1fr`. O Sticky deixa de ser sticky e vai para o topo absoluto do fluxo. Timeline se ajusta ao centro com design stack vertical simples.

---

## Seção 5: Para Quem É

### Arquétipo e Constraints
- **Arquétipo:** Bento Box
- **Constraints:** Hover Lift, Glassmorphism, Asymmetric Padding
- **Justificativa:** Apresentação clara de perfis diferentes usando blocos de informação (bento) com visuais modernos, garantindo foco simultâneo mas fragmentado.

### Conteúdo
- **Perfil 1:** Pais de 0 a 3 anos - Que desejam acompanhar de perto cada marco do desenvolvimento.
- **Perfil 2:** Preocupados com o silêncio - Se você sente que seu filho "entende tudo", mas as palavras ainda não saem.
- **Perfil 3:** Rotina corrida - Que buscam transformar momentos comuns em oportunidades reais de estímulo.

### Layout
- **Grid do BentoBox:** `.bento-grid { display: grid; gap: 20px; grid-template-columns: repeat(3, 1fr); grid-auto-rows: minmax(280px, auto); }`
  - Perfil 1: `grid-column: span 1;`
  - Perfil 2: `grid-column: span 2;` (destaque para a maior dor: o silêncio).
  - Perfil 3: `grid-column: span 3;` na segunda linha.
- **Células (Bento Items):**
  - Fundo translúcido (Glassmorphism): `background: rgba(255, 255, 255, 0.6); backdrop-filter: blur(20px); border: 2px solid rgba(255, 255, 255, 0.4);`
  - Borda arredondada premium `border-radius: 32px;`
  - `padding: 40px` assimétrico para alinhar os textos no canto inferior esquerdo.

### Tipografia e Cores
- **Title (Quem é...):** Text-align central (`Outfit`), `clamp(2rem, 4vw, 3rem)`.
- **Textos nos Bentos:** `Fredoka` 1.8rem para o título (Ex: "Pais de 0 a 3 anos"), `#2D3E4E`. E `Outfit` 1.1rem para a descrição, `#5A7184`.
- **Gradiente Dinâmico Global no Container:** Um background que se movimenta lentamente (um radial gradiente pegando secondary e primary).

### Animacoes e Interatividade
- **Hover no Bento:** Escala suave `transform: translateY(-8px) scale(1.02)`, aumenta opacidade da borda e uma sombra dramoca e difusa: `box-shadow: 0 30px 60px rgba(234, 94, 106, 0.15)`. Transição usando `cubic-bezier(0.16, 1, 0.3, 1)`.

### Responsividade
- `< 992px:` Bento grids passam para span 1 inteiro (listagem normal), grid 1 column. Gap 15px.

---

## Seção 6: Quiz/Checklist

### Arquétipo e Constraints
- **Arquétipo:** Gamified / Reactive
- **Constraints:** Click Ripple, Confetti (simulado visualmente com svg animado na conclusão), Hover Fill
- **Justificativa:** Interação tátil melhora o engajamento através da sensação de checklist real de prancheta, promovendo autoidentificação fortíssima.

### Conteúdo
- **Título:** Como saber se essa mentoria é para mim?
- **Subtítulo:** Marque as situações que você vive hoje:
- **Opções:**
  - 1: Tenho um filho(a) entre 0 e 3 anos.
  - 2: Sinto que ele entende tudo, mas não fala.
  - 3: Minha rotina é corrida e não tenho horas livres.
  - 4: Fico ansiosa comparando o desenvolvimento dele.

### Layout
- **Padding:** `100px 0`.
- **Wrapper interativo:** Container central largo (max-width: 900px), alinhado ao centro (títulos) e a lista justificada com grande espaçamento. Fundo `#FFFFFF`, sombra pesada para dar contraste.

### UX Reativa (Form Elements)
- Botões / Checkboxes *enormes* transformados em "Cards interativos".
- Design base: Fundo cinza ultraclaro `#F8FAFC`, borda `2px solid #E2E8F0`, `border-radius: 16px`, `padding: 24px`. Elemento flexível com SVG circular falso de checkbox à esquerda.

### Tipografia
- **Títulos:** `Fredoka`, 2.5rem brilhante, cor sólida `#2D3E4E`.
- **Opções (Label):** `Outfit`, 1.3rem, fontWeight 500.

### Interatividade & Cores de Reação
- **Hover Options:** Troca borda para `#6CC8E9`, preenchimento cinza sutil vai para branco.
- **Click / Checked State:** 
  - Fundo preenche de cor branda `rgba(234, 94, 106, 0.1)`.
  - Borda troca para principal do projeto `--primary` (`#EA5E6A`).
  - Icone anima para marcado (`scale` animado com mola - bouncing anim).
  - Texto risca elegantemente ou só fica na cor primary forte.
- **Gamified:** Um script que, se marcar 2 ou mais, abre um Toast "Esse programa é exato para o que você vive agora!" usando animação `fade-up` elástica da base.

---

## Seção 7: Módulos do Programa

### Arquétipo e Constraints
- **Arquétipo:** Split Horizontal Expansível com Accordion Interativo
- **Constraints:** Reveal on Demand, High Contrast (no ativo)
- **Justificativa:** Organiza muita informação densa mantendo escopo visual limpo. Foca o usuário no módulo selecionado que se expande empurrando a interface verticalmente de forma suave.

### Conteúdo
- **Chamada:** Um programa completo para te dar segurança e ferramentas práticas.
- **Módulos [1 ao 5]** (Conteúdo exato detalhado no copy).

### Layout
- **Container Master:** `max-width: 1000px`, margin automática.
- Divisão inicial: Header com a chamada em um grid header/content.
- **Accordion Wrapper:** Stack vertical, `.module-item` (display flex col, borda esticada separando), sem bordas laterais.

### Design de Cada Módulo (Estilos)
- **Normal:** 
  - Linha do título: `padding: 30px 0`, border-bottom 1px solid `#E2E8F0`. Flex space-between.
  - Título do Módulo: `Outfit`, peso 700, 1.4rem, `#2D3E4E`. Ao lado um icone "Plus" (+).
- **Expandido (Ativo):**
  - Título muda cor para `#EA5E6A`.
  - Icone vira "Menos" (-).
  - O texto explicativo (corpo) é revelado logo abaixo: Cor `#5A7184`, 1.15rem, line-height 1.6, espaçamento de baixo antes da borda ganha padding.

### Animações (CSS Puro ou Lib Suave)
- `grid-template-rows` transitando de `0fr` para `1fr` no box do conteúdo escondido, garantindo slide elástico sem JS intrusivo.
- Icone Rotação `180deg` via css puro ao ativar com atraso de 300ms.

---

## Seção 8: Especialistas

### Arquétipo e Constraints
- **Arquétipo:** Split Assymétrico com Overlap
- **Constraints:** Mask Reveal, Duotone sutil e Layered Image
- **Justificativa:** Dá um tratamento premium aos autores do método.

### Conteúdo
- **Título:** Quem vai guiar você nesta jornada
- **Guia 1:** Deborah Zarth Demenech - Fonoaudióloga...
- **Guia 2:** Karen Barros - Fonoaudióloga...

### Layout
- Section background `linear-gradient(to right, var(--color-bg) 50%, #fff 50%)`.
- Grid para dois perfis de forma diagonal. Profile 1 (`max-width: 50%`) lado esquerdo mas sobrepondo para direita. Profile 2 na base direita sobrepondo à esquerda. (Composição Z-puzzle).
- Card de Perfil contém a Imagem da pessoa e um box com os textos.

### Tratamento Imagem
- Imagens inseridas em máscaras curvilíneas (`mask-image: url(blob.svg);` ou CSS clip-path orgânico).
- Saturação elevada e alta nitidez para destacar o rosto.

### Tipografia e Cores
- **Nomes:** `Fredoka`, 2rem, `#EA5E6A`.
- **Textos Profissionais:** `Outfit`, 1.1rem, bold nas titulações base. Cor: `#2D3E4E`

### Animações
- Revelação com Parallax reverso. No hover da imagem, ela dá zoom in (`scale(1.05)` dentro da máscara delimitada), promovendo efeito "Peek" profissional.

---

## Seção 9: O Que Você Garante

### Arquétipo e Constraints
- **Arquétipo:** Grid Simétrico (2x2) Limpo
- **Constraints:** Floating Accent Icons, Scale In stagger
- **Justificativa:** Em entregáveis (deliverables), Clareza é lei. Grid simétrico permite scannability rápido, os acentos flutuantes mantêm o link com a brand visual.

### Conteúdo
- **Título:** Ao se inscrever, você garante seu lugar no nosso time...
- **Item 1:** Programa Completo.
- **Item 2:** Materiais PDF.
- **Item 3:** Suporte 1 ano.
- **Item 4:** Acesso imediato.

### Layout
- **Padding:** `100px 0`.
- Title com max-width centralizado e bottom margin agressivo.
- **Grid:** `grid-template-columns: repeat(2, 1fr)`. Gab 30px.
- **Card Styling:** `border: 1px solid #E2EFF2; background #FFFFFF; border-radius: 20px; padding: 40px`.

### Tipografia
- Título do box: `Fredoka` 1.5rem, `#2D3E4E`. Texto: `Outfit` 1rem, `#5A7184`.

### Ícones Decorativos (Accent)
- Usando o amarelo da paleta `--color-accent` (#FECE17) como background brando (opacity 0.2) e ícone SVG monocromático da marca em laranja-rose. Tamanho: `64x64px`, borderRadius `border-radius: 20px` girado levemente, para contrapor aos cantos dos quadros.

### Hover Interatividade
- Glow hover: `box-shadow: 0 10px 30px rgba(234, 94, 106, 0.1)` com o SVG do icone girando ao seu ângulo 0 inicial de volta perfeitamente paralelo.

---

## Seção 10: Oferta e Preço (Spotlight)

### Arquétipo e Constraints
- **Arquétipo:** Focused Center / Spotlight
- **Constraints:** Glow Animation, Negative Margin overlap, Zoom Focus no CTA
- **Justificativa:** É a área da conversão, requer isolamento absoluto de poluição, foco central, contrastes extremos apontando para ação.

### Conteúdo
- **Títulos:** Pronto para... Quanto vale...
- **Preços:** De 197 por 12x 9,97 ou 97 à vista.
- CTA: COMPRAR...

### Layout
- Background da Seção: Cor forte! Usa um bloco azul marinho rico (Ex: `#1A2A3A` não brand core mas escurecendo text) ou usa a cor `var(--color-bg)` em tom invertido, mas vamos manter na marca: 
- Card Primário Gigante: `.pricing-card`. Cerca de 800px max, centrado massivamente. Box Shadow intenso de 100px blur brand-colored para dar glow radioativo. Fundo branco puro ou com sutileza.
- Top center absolute tag "Oferta de Acesso" amarelo `--color-accent`.

### Tipografia
- Todos os textos focados centralizados.
- **Valores (o core visual):** "12x" pequeno, "R$ 9,97" gigantesco (`clamp(3.5rem, 8vw, 6rem)` em `Fredoka`). Cor principal `#EA5E6A`.
- **Preço à vista:** Menor, font weight 600, cinza com underline `#5A7184`.

### CTA
- Design Ultra: Botão com padding extra-large. Background `--color-accent` ou `--color-primary`. Sombra pulse (uma animação com CSS `box-shadow` pulsando radialmente a cada 2 segundos via keyframe pra atrair a vista imperativamente).

---

## Seção 11: Garantia

### Arquétipo e Constraints
- **Arquétipo:** Minimal / Badge Centric
- **Constraints:** Single Focus, Float Loop
- **Justificativa:** Desarmar objeção através da simplicidade extrema. Um selo isolado passa transparência.

### Conteúdo
- **Título & Texto:** 7 Dias de Garantia Incondicional, risco zero.

### Layout e Visual
- Simples e limpo em texto sem padding exagerado.
- À esquerda (ou acima em mobile), um distintivo vetorial de "7 Dias Garantia". O distintivo flutua sutilmente.
- O texto corre simples, sem jargão confuso, `Outfit`, 1.25rem, `#4A5568`.

---

## Seção 12: FAQ

### Arquétipo e Constraints
- **Arquétipo:** Dense / Accordion Standard Limpo
- **Constraints:** Fade down
- **Justificativa:** Padrão clássico comprovado. Sem surpresa aqui, facilitar leitura ao máximo.

### Layout e Tipografia
- Container fininho `max-width: 750px` (linha de texto ideal de 60-70 caracteres).
- Respostas em `Outfit` tamanho 1.1rem super legível, line-height 1.8.
- Hover no bloco todo muda bg para rgba blue clarinho, não apenas título.

---

## Seção 13: Dados Científicos (Fechamento)

### Arquétipo e Constraints
- **Arquétipo:** Split Assimetrico (Imagem / Texto)
- **Constraints:** Draw SVG, Text Reveal, Gradient Background
- **Justificativa:** O último apelo é técnico/biológico mas emocional (Janela de Ouro). Argumento inegável amparado por gráfico orgânico.

### Conteúdo & Design
- **Título:** Por que agora? A Janela de Ouro.
- Lado Visual: Um gráfico vetorial (linhas curvas) mostrando as conexões sinápticas (idade 0-3 altíssima).
- **Tratamento:** Esse caminho da curva vai ser desenhado enquanto passa de 0 a 3, a linha principal na cor `--color-primary`, pintando (draw SVG com `stroke-dashoffset`) conforme scorlla o meio da tela.
- Atrás do gráfico, mancha orgânica blur em `opacity:0.2` (amarelo e rosa).
- CTA replicado em modo fantasma ou cor forte para decisão derradeira e imediata.

---

## Seção 14: Rodapé

### Minimalismo Extremo
- Apenas logo ou cor neutra.
- Fundo do footer: `#1A2A3A` (escurecido extremo). Letras Brancas. 
- Links burocráticos (Privacy, Terms - invisível se indisponível, text-only minimalista).
