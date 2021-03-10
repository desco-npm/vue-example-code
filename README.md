<div align="right">
  <a href="README.US.md">
    <img alt="Read in American English" src="https://img.shields.io/static/v1?label=&message=🇺🇸 Read in American English&color=red&style=for-the-badge" />
  </a>
</div>

<table>
  <tr>
    <td><img src="https://i.ibb.co/TM21mQP/vue-example-code.png"></td>
    <td>  
      <h1>@desco/vue-example-code</h1>
      Componente VueJS para exemplo de códigos.
      <br /><br />
      <div align="center">
        <img alt="Licença MIT" src="https://img.shields.io/static/v1?label=Licença&message=MIT&color=green&style=for-the-badge">
        <img alt="Versão 1.2.1" src="https://img.shields.io/static/v1?label=Versão&message=1.2.1&color=blue&style=for-the-badge">
      </div>
      <h4 align="center"> 
        🚀 Pronto para uso 🚀
      </h4>
    </td>
  </tr>
</table>

> <a href="https://github.com/desco-npm" target="_blank">Veja outros projetos NPM aqui.</a>

> <a href="https://github.com/descoifica" target="_blank">Veja outros projetos aqui.</a>

---

## 📋 Tabela de conteúdos

* [🛠️ Tecnologias](#Tecnologias)
* [⚙️ Instalação](#Instalação)
* [📦 Importação](#Importação)
* [📚 Como Usar](#Como-Usar)

---

## 🛠️ Tecnologias

As seguintes tecnologias são utilizadas:

* [VueJs](https://vuejs.org/)
* [PUG/JADE](https://pugjs.org)
* [SCSS/SASS](https://sass-lang.com)

---

<a name="Instalação"></a>

## ⚙️ Instalação

```bash
npm install --save @desco/vue-example-code
```

> Note que será necessário ter o **NPM** instalado para o comando funcionar.

---

<a name="Importação"></a>

## 📦 Importação

```js
import exampleCode from '@desco/vue-example-code'
```

---

<a name="Como-Usar"></a>

## 📚 Como Usar

```html
<template>
  <exampleCode :code="code">
</template>
```

```js
export default {
  components: exampleCode,
  data () {
    return {
      code: {
        title: 'Título;
        description: 'Minha Descrição';
        example: [
          {
            lang: 'html',
            name: 'Exemplo de HTML',
            icon: 'fab.fa-html5',
            content: `
<template lang="pug">
div(@click="onClick") Meu exemplo em HTML aqui
</template>
            `,
          },
          {
            lang: 'javascript',
            name: 'Exemplo de JS',
            icon: 'fab.fa-js',
            content: `
export default {
    methods: {
        onClick () {
            alert('Exemplo de JS!')
        }
    }
}
            `,
          },
        ]
      }
    }
  }
}
```

### Parâmetros

| Nome | Tipo | Obrigatório | Padrão | Descrição |
|---|---|---|---|---|
| title | String | Não | - | O título do exemplo |
| description | String | Não | - | A descrição do exemplo |
| example | JSON/Array | Sim | - | JSON ou Array de JSONs contendo informações dos códigos que aparecerão em cada aba. |
| example.lang | String | Não | - | Linguagem do código. Essa informação será usada na sintaxe do código assim como no ícone e título da aba (Caso não informado) |
example.name | String | Não | A linguagem do código | Nome a ser exibido na aba do código |
example.icon | String | Sim | Ícone da linguagem | Ícone a ser exbido na aba do código |
example.content | String | Não | - | Código do exemplo |

---

## Autor

<table>
  <tr>
    <td width="150px">
      <img src="https://scontent.fsdu1-1.fna.fbcdn.net/v/t1.0-9/539886_235546170253505_5977326689811409130_n.jpg?_nc_cat=106&ccb=3&_nc_sid=174925&_nc_eui2=AeGgFWn_fWInwRkTo3mHSP993TbQ0TzG0Y3dNtDRPMbRjS-eZL1tr4I5maqz6O-jva9qWnIxKOsD3UtSm9CTeCys&_nc_ohc=Qw6NaDGrtIgAX9uFF2c&_nc_ht=scontent.fsdu1-1.fna&oh=5ebac9874d7a24e157c8c99fd965c2a4&oe=606539CE" width="100px;" alt=""/>
      <b>Rafael A. R. Dias</b>
    </td>
    <td>  
      <a href="mailto:eu@diasrafael.com.br" target="_blank" >
        <img alt="Email eu@diasrafael.com.br" src="https://img.shields.io/static/v1?label=Email&message=eu@diasrafael.com.br&color=red&logo=gmail&style=for-the-badge">
      </a>
      <a href="https://www.linkedin.com/in/diasrafael/" target="_blank">
        <img alt="Linkedin @diasrafael" src="https://img.shields.io/static/v1?label=Linkedin&message=@diasrafael&color=blue&logo=linkedin&style=for-the-badge">
      </a>
      <a href="https://www.facebook.com/eudiasrafael" target="_blank">
        <img alt="Facebook @eudiasrafael" src="https://img.shields.io/static/v1?label=Facebook&message=@eudiasrafael&color=blue&logo=facebook&style=for-the-badge">
      </a>
      <a href="https://github.com/descodifica" target="_blank">
        <img alt="GitHub Geral @descodifica" src="https://img.shields.io/static/v1?label=GitHub Geral&message=@descodifica&color=black&logo=github&style=for-the-badge">
      </a>
      <a href="https://github.com/desco-npm" target="_blank">
        <img alt="GitHub NPM @desco-npm" src="https://img.shields.io/static/v1?label=GitHub NPM&message=@desco-npm&color=black&logo=github&style=for-the-badge">
      </a>
      <a href="https://www.npmjs.com/org/desco" target="_blank">
        <img alt="NPM @desco" src="https://img.shields.io/static/v1?label=NPM&message=@desco&color=red&logo=npm&style=for-the-badge">
      </a>
    </td>
  </tr>
</table>