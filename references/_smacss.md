<img src="images/smacss.svg" alt="SMACSS" style="display:block; margin-left:auto; margin-right:auto;"/>

# SMACSS - SCALABLE and MODULAR ARCHITECTURE for CSS

> "O SMACSS é uma maneira de examinar seu processo de design e como uma maneira de adequar essas estruturas rígidas a um processo de pensamento flexível." - Jonathan Snook

Criado dentro do Yahoo! por Jonathan Snook, esse modelo baseia-se na divisão de regras em cinco categorias: Base, Layout, Módulo, Estado e Tema. Essa sugestão de separação de categorias em folhas de estilo distintas visa melhorar a localização de regras e, como consequência, facilitar a manutenção dos projetos.

## Princípios

A metodologia SMACSS divide as regras CSS em cinco categorias:

  1. **Base**
     - São as regras que definirão a base do projeto.
     - São regras do tipo que não utilizam classes ou IDs e se parecem muito com as regras encontradas em um _CSS Reset_ ou _Normalize_.
     - Em resumo, apenas elementos, seletores descendentes, seletores filhos e pseudo-classes entram nessa categoria.
     - É a categoria recomendada para definição de tipografia.

  2. **Layout**
     - Nessa categoria são colocados os estilos de estruturas maiores (wireframe) que não se repetem nas views HTML como: `header`, `footer`, `sidebar`, `main`.
     - Seletores que não representam componentes ou estruturas reutilizáveis também devem se descritos nessa categoria.

  3. **Módulo**
     - Essa categoria engloba regras para componentes atômicos ou moleculares. Os nomes devem fazer referência à função do elemento e não ao seu conteúdo.
     - Módulos são o cerne do desenvolvimento dentro da metodologia SMACSS e serão os componentes mais utilizados.
     - Módulos devem ser independentes: não devem depender de outros módulos para funcionar.
     - Módulos devem ser intercambiáveis: podem ser utilizados em qualquer lugar sem ter sua aparência modificada.
     - Essa categoria é responsável por abrigar os componentes, blocos reutilizáveis como títulos, botões, listas, tabelas, menus, blocos de texto, galerias, slideshows, etc.

  4. **Estado**
     - Essa categoria é uma espécie de modificador de comportamento de classes.
     - Essa categoria cuida de comportamentos como `.is-hidden`, `.is-active`, `.is-current`. É a única categoria que permite o uso de `!important` em suas regras.
     - É comum Javascript fazer uso dessa categoria.

  5. **Tema**
     - Essa categoria tem a finalidade de definir a identidade visual de um projeto.
     - Os estilos de temas podem modificar a aparência de outras regras existentes nas categorias anteriores.

## Benefícios

Os benefícios obtidos com SMACSS são:

  - Ótima organização de código que ataca principalmente a localização de rápida de regras.
  - Pode ser aplicada em conjunto com outras metodologias como BEM e ITCSS.

## Contratempos

  - Se não for bem organizada a categoria Módulo pode crescer desordenadamente e se tornar catastrófica.

## Recomendações

### Regras gerais

  - Os nomes de cada parte são escritos no singular.
  - Base e Layout podem ser escritos em apenas um arquivo.
  - Módulos devem ser escritos dentro de um diretório módulo.
  - É comum utilizar prefixos (namespaces) em nomes de classes para indicar a categoria de cada componente dentro das categorias Layout e Tema. Ex.: `.l-class` (layout), `.t-class` (tema).

### Regras por categoria

  1. **Base**
     - Definir regras mais genericamente possível pois elas são globais e perpetuam por todo o projeto. Devem ser, portanto, minimalistas e consistentes com o projeto.
     - Jamais utilizar classes e IDs nessa categoria.

  2. **Layout**
     - Ao definir wireframe, utilizar seletores únicos como `#header`, `#footer` ou `#sidebar`.
     - Recomenda-se o uso de IDs ou classes com o prefixo `.l-` como seletores.
     - Utilizar essa categoria para mutações específicas de layout (Ex.: `.l-fluid #header` e `.l-fixed #header`).

  3. **Módulo**
     - Utilizar nomes claros para facilitar a leitura do HTML.
     - Evitar escrever seletores de elementos dento de cada módulo.
     - Para garantir uma aparência melhor de código, componentes filhos de módulos são escritos na folha de estilos com indentação, ressaltando a hierarquia dentro dos módulos.
     - O uso de IDs é fortemente combatido.

  4. **Estado**
     - Utilizar verbos como `is` e `had`.
     - Caso o elemento seja manipulado via Javascript é permitido utilizar classes ou atributos `data-state` (Ex.: `class="is-hidden"` ou `data-state="hidden"` são equivalentes nessa metodologia).
     - Nessa categoria é permitido o uso de `!important` para reforçar regras muito específicas.

  5. **Tema**
     - Essa categoria é pouco utilizada e não tem uma documentação bem definida.

## Exemplos

### 1. Base

```css
/**
 * Exemplo de arquivo Base contendo apenas estilos genéricos.
 * Nessa categoria não se usa classes ou IDs.
 */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html, body {
  /* Seletores de elementos */
}

blockquote p {
  /* Seletores descendentes */
}

li > span {
  /* Seletores filhos */
}

:focus {
  /* Pseudo-classes */
}
```

### 2. Layout

```css
/**
 * Exemplo de arquivo Layout contendo apenas estruturas únicas ou não reutilizáveis.
 */
#toolbar {
  /* Regras de objeto de wireframe */
}

  /* Mutações de objetos */
  /* Indentação para melhorar legibilidade */
  .l-fluid #toolbar { }
  .l-fixed #toolbar { }
```

### 3. Módulo

```css
/**
 * Exemplo de arquivo Módulo contendo estilos reutilizáveis e extensíveis.
 */
 /* Objetos atômicos */
.heading { }
.title { }
.subtitle { }

/* Objetos moleculares */
.media { }

  /* Indentação para melhorar legibilidade */
  .media-img { }
  .media-main { }
```

### 4. Estado

```css
/**
 * Exemplo de arquivo Estado contendo estilos de comportamento de objetos.
 */
 /* Classes de estado utilizando verbos */
.is-active { }
.has-child {}

/* O uso é importante é permitido em classes específicas */
.is-hidden { display: none !important; }

/* Classes podem ser substituídas por data-attributes */
[data-state='active'] { }
```

### 5. Tema

```css
/**
 * Exemplo de arquivo Tema.
 */

/**
 * Tema Vermelho
 */
.t-red .heading { /* Regras do tema vermelho */ }

/**
 * Tema Verde
 */
.t-green .heading { /* Regras do tema verde */ }

/**
 * Tema Azul
 */
.t-blue .heading { /* Regras do tema azul */ }

/**
 * NOTE
 * Os temas podem ser separados em arquivos diferentes para facilitar a manutenção.
 * Ex.: theme-red.css, theme-green.css, theme-blue.css
 */
```

## Referências

  - [https://smacss.com/](https://smacss.com/)
  - [https://smacss.com/book/](https://smacss.com/book/)
