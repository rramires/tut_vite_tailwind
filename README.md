# Tutorial Vite + Tailwind CSS

Tutorial to configure:  
Vite + Tailwind CSS

- IMPORTANTE !

    Esse tutorial é uma continuação da configuração do front-end usando React com TypeScript usando o Vite.  
     Antes deve ser concluído esse outro tutorial, para instalando e configurando o Vite, Prettier, etc:  
     [Tutorial Vite + Code Format](https://github.com/rramires/tut_vite_code-format/blob/master/README.md)

    Seguido do tutorial para instalação do React Router DOM:  
     [Tutorial Vite + React Router DOM](https://github.com/rramires/tut_vite_react_router_dom/blob/master/README.md)

---

1 - Instale o Tailwind CSS:  
[Tailwind CSS Using Vite](https://tailwindcss.com/docs/installation/using-vite)

```sh
pnpm add tailwindcss @tailwindcss/vite
```

2 - Caso não tenha ainda, instale a extensão do Tailwind no VSCode:  
[Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)

3 - Atualize o **vite.config.ts**, adicionando:

```js
// adicione
import tailwindcss from '@tailwindcss/vite'

// em plugins adicione
/* plugins: [react()*/ , tailwindcss() /*],*/
```

4 - Crie um arquivo **global.css** dentro de **src** e adicione:

```css
@import 'tailwindcss';
```

5 - Importe **global.css** no **main.tsx**:

```js
// adicione
import './global.css'
```

6 - Rode a aplicação:

```sh
pnpm dev
```

- Acessando via http://localhost:3001 perceba que a formatação padrão do html sumiu, deixando as fontes pequenas.

---
