# 📌 React Router
## ✅ Oque é React Router?
- React Router é um dos pacotes mais utilizados para criar uma estrutura de rotas em aplicações de React;
- Ou seja, permite que nossas SPAs tenham múltiplas páginas;
- Precisamos instalar no nosso projeto;
- A configuração e utilização é simples;
- Também temos outras funções como: Redirect, Nested Routes, Not Found Routes e outros;

<br>

## ✅ Configurando o React Router
- Para configurar o React Router vamos ter que importar três elementos de react-router-dom;
- BrowserRouter: Define onde a área do nosso app que vai trocar as páginas;
- Routes: Define as rotas;
- Route: um elemento deste para cada rota, configurar com path e componente da rota;

Comando do terminal para instalar o react router:
```
npm i react-router-dom
```

Sintaxe de criação das rotas:
```
import './App.css';

//1- config react router
import { BrowserRouter, Routes, Route } from 'react-router-dom';

// pages
import Home from './pages/Home/Home';
import About from './pages/About/About';

function App() {
  return (
    <div className="App">
      <h1>React Router</h1>
      <BrowserRouter>
        <Routes>
          <Route path='/' element={<Home />} />
          <Route path='/About' element={<About />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
};

export default App;
```

<br>

## ✅ Navegação entre páginas
- Para criar links para as páginas vamos precisar utilizar o Link do React Router;
- No Link configuramos os parâmetros to, que recebe a URL/path que será redirecionado quem clicar no link;
- Vamos criar um componente de Navbar para isso;

Sintaxe da tag Link no arquivo Navbar.js:
```
import './Navbar.css';
import { Link } from 'react-router-dom';

const Navbar = () => {
  return (
  <nav>
    <Link to="/">Home</Link>
    <Link to="/about">Sobre</Link>
  </nav>
  );
};

export default Navbar;
```

Chamando Navbar em App.js
```
// components
import Navbar from './components/Navbar';

function App() {
  return (
    <div className="App">
      <h1>React Router</h1>
      <BrowserRouter>
        <Navbar />
        <Routes>
          <Route path='/' element={<Home />} />
          <Route path='/About' element={<About />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
};

export default App;
```

<br>

## ✅ Carregando dados
- Vamos exercitar novamente o carregamento de dados com nosso hook useFetch;
- Depois poderemos utilizá-los para o carregamento de dados individuais;
- Utilizaremos o hook igual ao da última seção e vamos imprimir os produtos na Home da mesma forma;

<br>

## ✅ Rotas dinâmicas
- Para criar uma rota dinâmica vamos precisar definir uma nova Route em App.js;
- Que deve ter o padrão de: /products/:id
- Onde :id é o dado dinâmico, ou seja, podemos ter qualquer valor;
- Na página podemos utilizar o hook useParams para resgatar esta informação;


<br>

## ✅ Carregamento dinâmico de dados
- Graças ao passo dado na aula passada o carregamento individual de um produto será fácil;
- Vamos utilizar o id recebido para formar a nova URL;
- E por fim podemos utilizar o hook useFetch para trazer o item;
- Por fim faremos a validação e impressão do mesmo no JSX;


<br>

## ✅ Nested routes
- As nested routes indicam URLs mais complexas, como: /products/:id/something;
- Neste caso vamos precisar criar um componente que corresponde com o padrão indicado e também a URL em App.js;
- Na nested route teremos o acesso ao parâmetro da URL também;

<br>

## ✅ Página 404
- Podemos criar uma página 404 facilmente com o React Router;
- Basta criarmos o componente da página;
- E no App.js definir um path como *;
- Desta maneira, qualquer rota que não exista cairá neste componente;

<br>

## ✅ Link ativo
- Para ter fácil acesso a uma modificação para os links ativos vamos trocar o Link pelo NavLink;
- Neste elemento temos acesso a um valor chamado isActive;
- Ou seja, podemos ativar uma classe se a rota atual for a que está no atributo to;

<br>

## ✅ Search Params
- Search Params é um recurso que permite obter o que vem na URL em forma de parâmetro, ex: produtos?q=camisa
- Utilizamos o hook useSearchParams para obtê-los;
- Com este recurso fica simples fazer uma funcionalidade de busca no sistema;

<br>

## ✅ Redirecionamento de URL
- Podemos precisar de um redirecionamento de páginas eventualmente;
- Exemplo: uma página antiga do sistema responde agora a uma nova URL;
- Para isso vamos criar a rota com Route normalmente;
- Mas em element vamos utilizar o componente Navigate com um to que vai para a rota correta;