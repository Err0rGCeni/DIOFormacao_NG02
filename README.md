# Single Page Application com Angular

Relembrando:

- Iniciando: `ng new 01_diretivas`
  - `cd 01_diretivas`
- Criando componente card: `ng g c card`
- Rodando servidor: `ng serve`

## Single Page

Diretivas são a maneira como o angular manipula e altera a DOM dinâmicamente.

- **Estruturais**: Moldam ou remodelam a estrutura da DOM, adicionando ou removendo elementos na tela.
- **De Atributo**: Alteram a aparência ou comportamento de um elemento, componente ou outra diretiva.

### Diretivas Estruturais

A diretiva estrutural **ngIf** permite mostrar ou ocultar um elemento de acordo com uma expressão booleana.

```html
<!--Simple form with shorthand syntax:--->
<div *ngIf="condition">Content to render when condition is true.</div>

<!--Simple form with expanded syntax:--->
<ng-template [ngIf]="condition"
  ><div>Content to render when condition is true.</div></ng-template
>

<!--Form with an "else" block:--->
<div *ngIf="condition; else elseBlock">
  Content to render when condition is true.
</div>
<ng-template #elseBlock>Content to render when condition is false.</ng-template>

<!--Shorthand form with "then" and "else" blocks:--->
<div *ngIf="condition; then thenBlock else elseBlock"></div>
<ng-template #thenBlock>Content to render when condition is true.</ng-template>
<ng-template #elseBlock>Content to render when condition is false.</ng-template>

<!--Form with storing the value locally:--->
<div *ngIf="condition as value; else elseBlock">{{value}}</div>
<ng-template #elseBlock>Content to render when value is null.</ng-template>
```

A diretiva **ngFor** é uma diretiva estrutural Angular que permite repetir um elemento HTML para cada item em uma lista ou array.

```html
<div *ngFor="let user of users">
  <h3>{{ user.name }}</h3>
</div>
```

Forma mais robusta:

```html
<ul>
  <li *ngFor="let item of items; index as i; trackBy: trackByFn">
    {{ item.name }} - {{ item.description }} - Index: {{ i }}
  </li>
</ul>
```

- Iteração com `ngFor`: A diretiva `ngFor` é responsável pela iteração sobre a lista de itens, replicando o template especificado dentro da diretiva para cada item da lista.
- Acesso ao item atual com `let item of`: A variável `item` é criada dentro do contexto da iteração, fornecendo acesso ao item atual da lista em cada iteração.
- Acesso ao índice do item com `index as i`: A variável `i` é criada opcionalmente para fornecer acesso ao índice do item atual da lista em cada iteração.
- Rastreamento de itens com `trackBy: trackByFn`: A função trackByFn é fornecida opcionalmente para otimizar o desempenho de identificação e atualização de itens na lista, especialmente quando a lista é grande e há alterações frequentes.

A diretiva `ngSwitch` é uma diretiva **atributiva**, usada em combinação com as diretivas **estruturais** `ngSwitchCase` e `ngSwitchDefault` Angular que permite alternar o conteúdo de um elemento HTML com base em uma expressão booleana ou um valor literal.

```html
<div [ngSwitch]="user.status">
  <h1 *ngSwitchCase="'active'">Usuário ativo</h1>
  <h1 *ngSwitchCase="'inactive'">Usuário inativo</h1>
  <h1 *ngSwitchDefault>Usuário desconhecido</h1>
</div>
```

### Diretivas de Atributo

A diretiva `ngClass` é usada para adicionar ou remover classes CSS de um elemento HTML com base em uma condição ou expressão.

```html
<div [ngClass]="expression">...</div>
```

A diretiva `ngStyle` é usada para aplicar estilos CSS a um elemento HTML com base em uma condição ou expressão.

```html
<div [ngStyle]="expression">...</div>
```

A diretiva `ngModel` é usada para vincular um elemento HTML a uma propriedade de um componente. Por se tratar de uma comunicação bilateral (HTML-JS), usa notação de `[()]`. É necessário fazer o `import { FormsModule } from '@angular/forms';` em `app.module.ts`.

```html
<input type="text" [(ngModel)]="name" />
```

A diretiva `ngTemplate` é usada para incluir um template Angular em um elemento HTML,sendo renderizado quando instruído a isso. Geralmente utilizado em conjunto com diretivas estruturais.

```html
<ng-template [ngIf]="isEnableBlock">
  <a href="#">Finalizar</a>
</ng-template>
```

```html
<div *ngIf="hero" class="name">{{hero.name}}</div>
```

Sendo equivalente a:

```html
<ng-template [ngIf]="hero">
  <div class="name">{{hero.name}}</div>
</ng-template>
```

A diretiva `ngContent` é uma diretiva estrutural que permite projetar componentes Angular de forma reutilizável e adaptável. Ela é usada para projetar o conteúdo de um componente Angular a partir de outros componentes ou templates.

## Módulos Angular

Em Angular, um módulo é uma unidade de organização que agrupa componentes, diretivas, pipes e serviços. Os módulos são usados para organizar o código Angular e facilitar a reutilização de código.

- **declarations**: Uma lista de componentes, diretivas e pipes que serão incluídos no módulo.
- **imports**: Uma lista de módulos que serão importados pelo módulo.
- **exports**: O subconjunto de declarações que devem ser visíveis e utilizáveis ​​nos modelos de componentes de outros módulos.
- **providers**: Uma lista de serviços que serão fornecidos pelo módulo.
- **bootstrap**: A visualização principal do aplicativo, root-component, que hospeda todas as outras visualizações do aplicativo.

Geralmente utiliza-se módulos para pages, shareds, etc.

## Projetos

- [Criando um Blog com Angular](https://github.com/Err0rGCeni/DIOProject_angular-blog)
