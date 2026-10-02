# Editor de e-mails Zeom (drag & drop)

Editor visual em um único arquivo (`index.html`) montado sobre a biblioteca de
blocos do projeto Zeom (127 blocos, 24 categorias — `blocks/` do repositório
`hiagofbranco/zeom`).

## O que o cliente consegue fazer

- **Arrastar blocos** da biblioteca (com miniaturas, busca e filtro por categoria)
  para o e-mail, ou clicar em **+** para inserir abaixo do bloco selecionado.
- **Reordenar** arrastando pela alça ⠿ ou com os botões subir/descer;
  **duplicar** e **excluir** blocos.
- **Editar textos direto no e-mail** (clique e escreva). Negrito, itálico, link,
  limpar estilo e inserção de variáveis (`{{nome}}`, `{{codigo}}`…).
  Colar texto remove a formatação de origem.
- **Botões e links**: trocar o endereço (com sugestões das variáveis
  `{{LINK_*}}` usadas na régua).
- **Imagens**: trocar por URL ou enviar do computador, ajustar a altura à
  proporção, editar o texto alternativo; ícones da biblioteca têm um seletor
  próprio. Imagens de fundo (blocos "Fundos") também são editáveis.
- Pré-visualizar em **Desktop/Celular** e nos temas **Claro/Escuro**.
- **Assunto, pré-header e nome** do e-mail; 4 modelos iniciais.
- **Desfazer/Refazer** (Ctrl+Z / Ctrl+Shift+Z).
- **Salvamento automático** no navegador, rascunhos múltiplos, e
  **Salvar/Abrir projeto (.json)** para compartilhar ou continuar depois.
- **Exportar HTML** (baixar ou copiar) no mesmo formato dos e-mails da régua:
  tabela de 600px, CSS do design system (claro/escuro + mobile), pré-header oculto
  e condicional MSO para Outlook.

## Publicar para o cliente

O arquivo é autocontido: basta hospedá-lo. Para ficar junto do projeto, copie
`email-builder/index.html` para o repositório `zeom` (ex.: `editor-emails.html`)
e adicione um card em `index-projeto.html`:

```html
<a class="card" href="editor-emails.html">
<div class="n">Editor</div>
<div class="t">Montar e-mails</div>
<div class="d">Arraste blocos da biblioteca, edite textos, imagens e links e exporte o HTML pronto para disparo.</div>
</a>
```

As imagens apontam para `https://hiagofbranco.github.io/zeom/assets/…`, então
funcionam em qualquer hospedagem (e no HTML exportado).

## Atualizar quando a biblioteca mudar

```bash
git clone https://github.com/hiagofbranco/zeom ../zeom
python3 email-builder/build.py ../zeom
```

O script lê `blocks/_index.json` e cada bloco, extrai as linhas da tabela
`.container`, separa o CSS próprio de cada bloco (isolando classes como `.col`,
`.gut`, `.g-t` para não colidirem) e gera `index.html` a partir de
`editor.template.html`.
