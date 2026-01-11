# 📝 Notas de Estudo: CSS Layout & SVG Sprites

Este documento resume os principais aprendizados técnicos sobre o desenvolvimento do projeto **Festivite**, focando em arquitetura CSS (Flexbox vs. Grid), posicionamento avançado e otimização de ativos com SVG Sprites.

---

### 1. Flexbox vs. Position Absolute

A escolha entre Flexbox e Posicionamento Absoluto define a estrutura do layout (fluida ou fixa).

- **Flexbox (Layout Fluido):** Os elementos são "conscientes" uns dos outros. Ideal para menus, formulários e alinhamentos gerais. Evita o uso excessivo de coordenadas manuais.
- **Position Absolute (Layout Manual):** O elemento é removido do fluxo normal do documento (vira um "fantasma"). Não respeita propriedades como `gap` ou `justify-content` do pai.
  - **Regra de Ouro:** Para que o `absolute` funcione corretamente, o elemento pai deve ter `position: relative`.
- **Centralização Absoluta Moderna:** .centralizado {
  position: absolute;
  inset: 0;
  margin: auto;
  width: 100px; /_ Tamanho obrigatório _/
  height: 100px;
  }

### 2. O Poder do `inset`

O `inset` é um shorthand (atalho) moderno que substitui as propriedades `top`, `right`, `bottom` e `left`.

- **Eficiência:** Reduz 4 linhas de código para 1.
- **Comportamento:** Se o elemento não tiver `width/height` definido, o `inset: 0` fará o elemento esticar até preencher todo o espaço do pai.

### 3. Flexbox Avançado: Casos Específicos

- **`align-self`:** Permite que um item específico "se rabela" contra a regra `align-items` definida no pai. Atua no Eixo Transversal.
- **`justify-self`:** **Não existe no Flexbox**, apenas no CSS Grid. No Flexbox, para mover apenas um item no eixo principal, utilizamos `margin-left: auto` ou `margin-right: auto`.
- **`align-content`:** Só "acorda" quando existe `flex-wrap: wrap`. Ele controla o alinhamento das **linhas** (o bloco inteiro) e não dos itens individualmente.

### 4. CSS Grid Garden: Resumo de Propriedades

- **`grid-template`:** Atalho mestre para definir linhas e colunas. Ex: `grid-template: 1fr 50px / 20% 1fr;` (Linhas / Colunas).
- **`grid-column`:** Shorthand preferencial sobre `grid-column-start/end`. Permite o uso do `span` para mesclar células (Ex: `grid-column: 1 / span 2`).
- **`grid-area`:** Define as quatro coordenadas de uma vez: `row-start / column-start / row-end / column-end`.

### 5. SVG Sprites: Otimização e Performance

A técnica de Sprites consiste em criar uma "biblioteca" de ícones oculta para manter o HTML limpo e permitir cache eficiente.

**Estrutura do arquivo `icons.svg`:**
<svg xmlns="http://www.w3.org/2000/svg">
<symbol id="calendar" viewBox="0 0 32 32">
<path d="..." fill="currentColor" />
</symbol>
</svg>

**Implementação no HTML:**
<svg class="icon calendar-blue">
<use href="assets/icons.svg#calendar"></use>
</svg>

**Vantagens:**

- **Estilização:** Ao usar `fill="currentColor"` no SVG, o ícone herda a cor definida pela propriedade `color` no CSS.
- **Manutenção:** Alterar um ícone no arquivo centralizado atualiza todas as instâncias no site.
- **Padrão:** Seguir o Style Guide (32x32) garante que os ícones tenham respiros consistentes e não quebrem o layout.

---

> [!NOTE]
> Estas notas são um resumo técnico. O processo detalhado com todos os desafios resolvidos está documentado nos meus arquivos pessoais de estudo.
> [Veja as anotações de estudo deste projeto aqui](https://docs.google.com/document/d/1XexOnZptEOgIy88NBwxHRRvkrMKh_GhXbn4DejDUYII/edit?usp=sharing)
