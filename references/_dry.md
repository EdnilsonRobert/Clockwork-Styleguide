<img src="images/dry.svg" alt="DRY" style="display:block; margin-left:auto; margin-right:auto;"/>

# DRY - Don't Repeat Yourself

Acrônimo de _Don't Repeat Yourself_ (não repita a si mesmo), DRY CSS tem como princípio a não repetição de propriedades com mesmos valores dentro do código. A documentação é pobre e se não for bem implementado o resultado pode ser pior que a situação inicial. Conforme novos elementos vão surgindo, o número de classes pode subir consideravelmente e documentos CSS que deveriam ser organizados tendem a caminhar para o caos.

## Princípios

O criador da metodologia, Jeremy Clarke, oferece dois princípios para escrever bom CSS:

  1. **Manter o estilo separado do conteúdo**
     - HTML deve ser estrutural.
     - Tags, classes e IDs devem se referir ao conteúdo em si, e não à aparência.

  2. **Evitar a especificidade aproveitando a cascata**
     - Seletores e definições devem ser tão globais quanto possível para consistência de projeto e para evitar colisões de especificidade.

Os princípios soam familiares pois, essencialmente, são os mesmos encontrados nas metodologias OOCSS e SMACSS.

## Como DRY CSS funciona?

Resumidamente, cada grupo deve ser definido para compartilhar propriedades. Um grupo deve descrever propriedades distintas que serão utilizadas durante o desenvolvimento enquanto outro grupo descreve outro conjunto consistente de características.

DRY CSS se resume a três coisas:

  1. **Agrupar propriedades CSS reutilizáveis juntas.**
     - Nunca repetir definições de estilos e propriedades se é possível evitar;
     - Agrupar seletores com propriedades compartilhadas é melhor que definí-las separadamente.

```css
{
  border-color: Gray;
  background-color: WhiteSmoke;
}
{
  border-color: MediumSeaGreen;
  background-color: WhiteSmoke;
}
```

  2. **Nomear esses grupos logicamente.**
     - Nomear os grupos com base em seu papel no design;
     - Usar um nome em forma de ID no topo da lista e as classes abaixo.

```css
#MEDIUM-WHITE-BACKGROUND,
.medium-white-background
{
  border-color: Gray;
  background-color: WhiteSmoke;
}
#GREEN-WHITE-BACKGROUND,
.green-white-background
{
  border-color: MediumSeaGreen;
  background-color: WhiteSmoke;
}
/* Os IDs em maiúsculas ajudam a localizar mais facilmente
o código com as Developer Tools do navegador */
```

  3. **Adicionar os seletores ao vários grupos CSS.**
     - A ideia geral é pensar em termos de padrões de estilo e agrupar as regras necessárias para criá-lo.
     - Em seguida basta adicionar os seletores CSS que utilizarão o padrão criado.
     - Quando um elemento precisa mudar seu estilo, a alteração é feita removendo sua classe correspondente de um grupo e movendo para outro.
     - HTML não deveria ser modificado.

```css
#MEDIUM-WHITE-BACKGROUND,
.sidebar-widget,
.form-contact,
.button,
.medium-white-background
{
  border-color: Gray;
  background-color: WhiteSmoke;
}
#GREEN-WHITE-BACKGROUND,
.form-field:focus,
.button:active,
.green-white-background
{
  border-color: MediumSeaGreen;
  background-color: WhiteSmoke;
}
```

## Benefícios

Praticar DRY CSS significa fazer uso de algumas boas práticas de desenvolvimento.

  - DRY CSS estimula pensar em termos de padrões de estilo;
  - nomear grupos encoraja a organização racional de padrões;
  - DRY CSS estimula a otimização e generalização de seletores CSS;
  - Tirar vantagem do inspetor das ferramentas de desenvolvedor dos navegadores;
  - Fácil integração com outras metodologias (OOCSS ou SMACSS).

Em adição, com DRY CSS não é necessário fazer alterações no HTML - apenas atribuir classes aos elementos. E, se bem executado, não deve haver qualquer problema de desempenho.

## Contratempos

  - A busca por seletores em um longo arquivo pode incomodar inicialmente.
  - Em projetos maiores a folha de estilos pode se tornar tão extensa a ponto da metodologia não fazer sentido.

## Recomendações

  - Utilizar seletores individuais apenas em exceções.
  - Sempre se perguntar: "Por que isso não é parte um grupo?".
  - Recomendação para separação de grupos:
    - Estruturas
    - Módulos
    - Formas
    - Texto
    - Cores

## Exemplos

```css
/* RUIM */
.button-red {
  display: inline-block;
  min-width: 9rem;
  height: 3.2rem;
  background-color: Crimson;
  color: WhiteSmoke;
}
.button-green {
  display: inline-block;
  min-width: 9rem;
  height: 3.2rem;
  background-color: MediumSeaGreen;
  color: WhiteSmoke;
}
.button-blue {
  display: inline-block;
  min-width: 9rem;
  height: 3.2rem;
  background-color: RoyalBlue;
  color: WhiteSmoke;
}

/* BOM */
#BUTTON-DEFAULT,
.button-default {
  display: inline-block;
  min-width: 9rem;
  height: 3.2rem;
  color: WhiteSmoke;
}
#STYLE-RED,
.button-red {
  background-color: Crimson;
}
#STYLE-GREEN,
.button-green {
  background-color: MediumSeaGreen;
}
#STYLE-BLUE
.button-blue {
  background-color: RoyalBlue;
}
```

## Referências

 - [DRY CSS | Jeremy Clarke (Slideshare)](https://pt.slideshare.net/jeremyclarke/dry-css-a-dontrepeatyourself-methodology-for-creating-efficient-unified-and-scalable-stylesheets)
 - [https://vanseodesign.com/css/dry-principles/](https://vanseodesign.com/css/dry-principles/)
