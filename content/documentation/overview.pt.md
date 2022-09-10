---
name: Visão de conjunto
icon: "images/overview.svg"
seoDescription: Visão de conjunto da abstração Buffalo
seoKeywords: ["buffalo", "framework", "overview", "go", "golang", "mux", "bootstrap", "jquery"]
aliases:
  - /docs/overview
  - /pt/docs/overview
---

# Visão de conjunto

Bem-vindo a bordo

Embora a Buffalo possa ser considerada como uma abstração, é na maior parte das vezes um ecossistema de Go e bibliotecas de JavaScript curadas para se ajustarem juntas. A maioria destes componentes podem ser trocadas por um outro, mas só iremos fornecer suporte para esta mistura padrão.

Neste capítulo, faremos uma excursão dos tijolos padrão entregados com a tua aplicação Buffalo.

## Bibliotecas de backend

### buffalo

A Buffalo é a "cola" entre todos os componentes fornecidos. Ela envolve as bibliotecas e administra o fluxo de trabalho.

### gorilla/mux

O [gorilla/mux](http://www.gorillatoolkit.org/pkg/mux) é um dos roteadores mais utilizados no Go. Enquanto alguns roteadores são mais rápido (como o [httprouter](https://github.com/julienschmidt/httprouter)), `gorilla/mux` é aquele fornecendo a maioria das funcionalidades enquanto sendo rápido o suficiente.

### pop

O [pop](https://github.com/gobuffalo/pop) é o modelo relacional de objeto (ORM, sigla em Inglês). Ele fornece a caixa de ferramenta `soda` para ajudar-te com as tuas necessidades de base de dado e suporta várias bases de dados, tais como PostgreSQL, MySQL e SQLite. 

### plush

O [plush](https://github.com/gobuffalo/plush) é o gerador de modelos de marcação padrão para a Buffalo. Sua sintaxe é próxima aos modelos de marcação de ERB (no Ruby).


## Bibliotecas frontend

### Bootstrap

A [Bootstrap](https://getbootstrap.com/) é uma das bibliotecas de frontend mais famosas. Ela ajuda a construir interfaces que se adaptam ao tamanho e resolução da tela dos dispositivos utilizando componentes comuns como tabelas, carroceis ou esquemas de grade.

### jQuery

A [jQuery](https://jquery.com/) é uma biblioteca rica com o objetivo de tornar a manipulação do modelo de objeto do documento (DOM, sigla em Inglês) e consultas puras de AJAX. Embora seja menos utilizada agora, muitos projetos ainda a têm como uma companheira para ajudar a suportar todos os navegadores.

### Webpack

O [Webpack](https://webpack.js.org/) é um empacotador de recursos de JavaScript bem conhecido. Ele cuidará dos teus ficheiros de recursos estáticos de JavaScript, CSS, imagens.

O Webpack está configurado por padrão para embaralhar e tornar os teus recursos menores em questão de peso de ficheiro.

## Próximos passos

* [Instalação](/en/docs/getting-started/installation) - Instalar a Buffalo!
