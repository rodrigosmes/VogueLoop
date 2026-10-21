# Como colocar o site da VogueLoop no ar (GitHub + Vercel)

Tempo: uns 10 minutos. Não precisa instalar nada; tudo é feito pelo navegador.

## O que tem nesta pasta

| Arquivo | Vira a página | O que é |
|---|---|---|
| `index.html` | `seusite.vercel.app/` | Explicação interativa do Colab + botão "▶ Apresentação comercial" |
| `apresentacao/index.html` | `seusite.vercel.app/apresentacao` | Só os slides animados (reserva) |
| `vercel.json` | — | Configuração: endereços sem ".html" |
| `TUTORIAL.md` | — | Este passo a passo |

O site é **estático**: não tem build, não tem dependência. Fontes e imagens já estão dentro dos arquivos.

---

## Parte 1 — Subir para o GitHub (pelo navegador)

1. Descompacte o zip. Você vai usar **o conteúdo** da pasta (os arquivos `index.html`, `vercel.json`, a pasta `apresentacao`…), não a pasta de fora.
2. Entre em **https://github.com** e faça login (ou crie uma conta grátis em *Sign up*).
3. No canto superior direito, clique em **+** → **New repository**.
4. Preencha:
   - **Repository name:** `vogueloop` (ou o nome que quiser, sem espaços)
   - **Public** ou **Private** (os dois funcionam com a Vercel)
   - **Não** marque "Add a README".
   - Clique em **Create repository**.
5. Na página do repositório vazio, clique no link **uploading an existing file**.
6. **Arraste para a janela** os arquivos `index.html`, `vercel.json`, `TUTORIAL.md` **e a pasta `apresentacao`** inteira.
   - Confira na lista se apareceu `apresentacao/index.html` (com a pasta na frente).
7. Embaixo, em *Commit changes*, escreva algo como `site vogueloop` e clique em **Commit changes**.
8. Pronto: o repositório deve mostrar `index.html`, `vercel.json`, `TUTORIAL.md` e a pasta `apresentacao`.

> Se a pasta `apresentacao` não subir ao arrastar (alguns navegadores não aceitam pastas): clique em **Add file → Create new file**, digite `apresentacao/index.html` no nome (a barra cria a pasta), cole qualquer texto, salve; depois entre na pasta e use **Add file → Upload files** para enviar o `index.html` dela por cima.

---

## Parte 2 — Publicar na Vercel

1. Entre em **https://vercel.com** e clique em **Sign Up** / **Log in** → **Continue with GitHub** (use a mesma conta do GitHub).
2. No painel, clique em **Add New… → Project**.
3. Na lista *Import Git Repository*, ache o `vogueloop` e clique em **Import**.
   - Se ele não aparecer: clique em **Adjust GitHub App Permissions** e libere o acesso ao repositório.
4. Na tela de configuração:
   - **Framework Preset:** `Other`
   - **Root Directory:** `./` (deixe como está)
   - **Build Command:** deixe vazio (se tiver algo, clique em *Override* e apague)
   - **Output Directory:** deixe vazio / padrão
5. Clique em **Deploy** e espere uns 30 segundos.
6. Quando aparecer a tela de parabéns, clique na imagem do site ou em **Continue to Dashboard → Visit**. O endereço é algo como `https://vogueloop.vercel.app`.

### Conferir

- `https://SEU-SITE.vercel.app/` → abre a explicação do Colab.
- Clique em **▶ Apresentação comercial** → abrem os slides; **Esc** fecha.
- `https://SEU-SITE.vercel.app/apresentacao` → abrem só os slides.
- Um botão **Abrir no Colab ↗** → deve abrir o Colab do grupo na célula certa.

---

## Mudou algo? Como atualizar

1. No GitHub, entre no repositório e clique em **Add file → Upload files**. Envie o arquivo novo com **o mesmo nome** (ex.: `index.html`); ele substitui o antigo. Não use o lápis de edição, porque os arquivos são grandes demais para o editor.
2. **Commit changes**.
3. A Vercel publica sozinha a versão nova em ~30 segundos (não precisa fazer nada lá).

---

## Alternativa: pela linha de comando (sem GitHub)

Se tiver o Node.js instalado:

```bash
cd caminho/da/pasta/descompactada
npx vercel          # faz login e responde as perguntas (aceite os padrões; framework: Other)
npx vercel --prod   # publica a versão final
```

---

## Usando na apresentação

| Tecla | O que faz |
|---|---|
| ← → | Na página: muda de seção. Nos slides: etapa anterior / próxima |
| − / + | Velocidade das animações (0,5× até 4×) |
| A | Slides: liga/desliga o automático |
| N | Slides: mostra as notas de fala |
| E | Troca o estilo visual: **Editorial** (o nosso) ou **Marca** (logo e cores oficiais da VogueLoop) |
| Shift+Enter | Página: executa a célula selecionada e passa para a próxima (como no Colab) |
| Ctrl+F9 | Página: executa todas as células |
| F | Slides: tela cheia |
| Esc | Fecha os slides |

O estilo escolhido fica salvo no navegador e vale para a página e para os slides. Também dá para trocar pelos botões **Editorial / Marca** no menu lateral, pelo botão **Estilo** no celular ou pelo ícone de paleta nos controles dos slides.

Cada célula de código tem o botão **▶** do Colab: ao clicar, ela "executa" e mostra, aos poucos, as saídas reais da execução oficial (logs de treino época a época, tabelas e gráficos). No menu lateral, **▶ Executar tudo** roda o notebook inteiro em sequência e **Limpar saídas** apaga tudo para começar do zero. O código não roda de verdade no navegador (TensorFlow não funciona lá); para rodar de verdade, use o botão **Abrir no Colab ↗** de cada célula.

Dica: no projetor, abra o site em tela cheia do navegador (**F11**) e teste a velocidade antes de começar.
