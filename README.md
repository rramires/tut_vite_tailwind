# Tutorial Tailwind CSS

Tutorial to configure:  
Tailwind CSS + Automatic Class Sorting

- IMPORTANTE !

    Esse tutorial é uma continuação da configuração do front-end usando React com TypeScript usando o Vite.  
     Antes deve ser concluído esse outro tutorial, para instalando e configurando o Vite, Prettier, etc:  
     [Tutorial React + Code Format](https://github.com/rramires/fe1_react_code-format/blob/master/README.md)

    Seguido do tutorial para instalação do React Router DOM:  
     [Tutorial React + React Router DOM](https://github.com/rramires/fe2_react-router-dom/blob/master/README.md)

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

1 - Instale o plugin para organizar a ordem das classes no Tailwind:  
[Automatic Class Sorting](https://tailwindcss.com/blog/automatic-class-sorting-with-prettier)

```sh
pnpm add -D prettier-plugin-tailwindcss
```

2 - Adicione no arquivo de configuração do Prettier, **prettierrc.json**:

```js
// depois de
/* "arrowParens": "always" */,
"plugins": ["prettier-plugin-tailwindcss"]
```

3 - Para testar, adicione alguns estilos na nossa página Dashboard em **dashboard.tsx**:

```js
<>
	<Helmet title='Dashboard' />
	<div className='text-center'>
		<h2 className='text-2xl font-bold'>Dashboard Page!</h2>
	</div>
</>
```

- Perceba o autocomplete funcionando dentro do className, graças a extensão instalada no passo 3.

- Veja tamtém a ordem classificação das classes, invertendo a ordem
  **'font-bold text-2xl'** e vendo que volta para **'text-2xl font-bold'** quando salva, graças ao prettier-plugin-tailwindcss.

4 - Adicione também na página SignIn:

```js
<>
	<Helmet title='SignIn' />
	<div className='text-center'>
		<h2 className='text-2xl font-bold'>SignIn Page!</h2>
	</div>
</>
```

4 - Rode para verificar:

```sh
pnpm dev
```

- Veja o conteúdo das páginas Dashboard e SignIn, centralizados e com os h2 formatados.

5 - Vamos adicionar alguma formatação nas páginas de erro, **e404.tsx** e **error.tsx**, que ficarão assim, respectivamente:

```js
<>
	<Helmet title='Not Found' />
	<div className='flex h-screen flex-col items-center justify-center'>
		<h1 className='text-3xl font-bold'>404 - Página não encontrada</h1>
		<h3 className='font-bold'>
			Voltar para a
			<a
				className='ml-1 text-blue-600 hover:text-blue-800 hover:underline'
				href='/'
			>
				página inicial
			</a>
		</h3>
	</div>
</>
```

```js
<>
	<Helmet title='Error' />
	<div
		id='error-page'
		className='flex h-screen flex-col items-center justify-center'
	>
		<h1 className='text-3xl font-bold'>Oops!</h1>
		<p>Desculpe, ocorreu um erro.</p>
		<p>
			<i className='font-bold text-red-600'>
				{error.statusText || error.message}
			</i>
		</p>
	</div>
</>
```

- Lembrando que para testar essas páginas de erro devemos:  
  Usar uma rota inexistente **http://localhost:3001/other** para **e404.tsx**  
  Provocar um erro em alguma página: **throw new Error('Simulação de erro no Dashboard')**, por exemplo, para **error.tsx**.
