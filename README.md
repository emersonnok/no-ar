# No Ar — lembrete de estreias de séries

App pessoal (PWA) que mostra quando estreia o próximo episódio das séries que você assiste.
Busca as datas sozinho na base do TVMaze, e cria eventos no Google Agenda para te avisar.

## Arquivos
- `index.html` — o app inteiro (UI + lógica)
- `manifest.webmanifest` — identidade do app (nome, ícones)
- `service-worker.js` — cache offline + habilita instalação
- `icons/` — ícones do app

## Testar no computador
Não basta dar duplo-clique (service worker exige http). Rode um servidor local:

    cd serie-tracker
    python -m http.server 8000

Abra http://localhost:8000

## Publicar de graça (GitHub Pages)
1. Crie um repositório (ex: `no-ar`) e suba estes arquivos na raiz.
2. Settings > Pages > Source: branch `main`, pasta `/root`.
3. Em alguns minutos fica no ar em https://SEU_USUARIO.github.io/no-ar/
   (HTTPS é obrigatório para PWA — o Pages já entrega HTTPS.)

## Gerar o APK (sem Android Studio)
1. Abra https://www.pwabuilder.com
2. Cole a URL do seu GitHub Pages e clique em Start.
3. Aba "Android" > Generate > baixe o pacote.
4. Dentro vem o `.apk` (e instruções). Habilite "instalar de fontes desconhecidas"
   no celular e instale o `.apk`.

## Como as notificações funcionam
- No card de cada série, o botão de calendário abre o Google Agenda já preenchido
  com o episódio. Salve o evento e o Google te notifica no horário — funciona mesmo
  com o app fechado.
- "Jogar todos na Agenda" cria os eventos de todas as séries com data futura.
- O sino (topo) liga notificações locais do navegador, que aparecem quando o app
  está aberto no dia da estreia. Para aviso garantido com o app fechado, use a Agenda.
