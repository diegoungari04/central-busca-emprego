# Central de Busca de Emprego

Uma central pessoal para organizar a busca de emprego em um só lugar: vagas, pretensão salarial, mensagens para recrutadores, respostas para processos seletivos e um radar diário de vagas. Feita para rodar no Claude como plugin, mas também funciona aberta no navegador e pode ser montada com outras IAs.

Criada por [Diego Ungari](https://www.linkedin.com/in/diegoungari), profissional de RH, durante a própria busca de recolocação.

## O que a central faz

| Aba | Para que serve |
|---|---|
| **Painel** | Vagas ativas, aplicações da semana contra a meta, entrevistas, follow-ups pendentes, funil com taxa de retorno e a lista do que fazer hoje |
| **Vagas** | Tracker com status, data de aplicação, pretensão, versão do CV, recrutador, próximo passo, palavras-chave e notas |
| **Radar diário** | Vagas novas encontradas nos dias úteis, com nota de aderência e o motivo; um clique salva no tracker ou descarta |
| **Remuneração** | Faixa CLT e PJ por cargo, porte e setor, número único para formulários e conversor CLT ↔ PJ |
| **Mensagens** | Convite, mensagem pós-candidatura, e-mail, follow-up, agradecimento e pedido de indicação, em português, inglês e espanhol, sem gastar créditos |
| **Perguntas** | Banco de respostas para perguntas de seleção. Busca primeiro no banco (grátis); traduz ou gera com IA só em último caso, e salva o resultado para reaproveitar |
| **Padrões** | Famílias de cargo, setor, porte, modelo, plataformas e palavras-chave mais frequentes, e onde há mais retorno |
| **Contatos** | Recrutadores, gestores e pessoas que podem indicar, com data de follow-up |

## Três formas de usar

### 1. No Claude, com o plugin (recomendado)

O plugin traz duas skills:

- **montar-central-busca**: entrevista você, monta a página com os seus dados, publica com banco de dados privado, preenche o banco de respostas e agenda o radar diário.
- **analisar-vaga**: quando você manda uma vaga, sugere a pretensão em CLT e PJ, mostra aderência e lacunas e registra a vaga na central.

**Instalação**

1. Baixe o arquivo `central-busca-emprego.plugin` na página de [Releases](../../releases) deste repositório (ou gere o seu: compacte em .zip o conteúdo da pasta do plugin e troque a extensão para `.plugin`).
2. No Claude, abra a área de plugins, escolha enviar um plugin e selecione o arquivo.
3. Em uma conversa, peça: **"Monte minha central de busca de emprego"**. Tenha à mão seu CV ou seu LinkedIn.
4. Para analisar uma vaga depois, cole a descrição e peça: **"Analisa essa vaga e registra na central"**.

O radar diário precisa do Claude com acesso ao seu navegador e de uma tarefa agendada; o plugin cria a tarefa se a sua conta tiver esses recursos.

### 2. No Claude, sem instalar nada

Envie o arquivo ([`template/central-busca.html`](template/central-busca.html](https://github.com/diegoungari04/central-busca-emprego/blob/main/central-busca-emprego/template/central-busca.html)) em uma conversa e peça: *"Personalize o CONFIG desta página com os meus dados do CV anexo, usando só fatos verdadeiros, e publique como artifact com banco de dados."*

### 3. Em outras IAs ou só no navegador

A página funciona sozinha: abra `template/central-busca.html` no navegador e os dados ficam salvos nele. Para personalizar com ChatGPT, Gemini ou outra IA, siga ([docs/outras-ias.md](https://github.com/diegoungari04/central-busca-emprego/blob/main/central-busca-emprego/docs/outras-ias.md)).

## Como a pretensão é calculada

Base nos Guias Salariais 2027 da Robert Half e da Michael Page (empresas médias e grandes), com CAGED, Vagas.com e Glassdoor como referência de mercado amplo. A faixa CLT vai do 50º ao 75º percentil; PJ é CLT × 1,35 a 1,45. A tabela que vem no modelo é de **RH no Brasil**: para outras áreas, peça à IA para pesquisar e trocar. Detalhes em [metodologia-salarial.md](skills/montar-central-busca/references/metodologia-salarial.md).

## Privacidade e cuidados

- No Claude, os dados ficam no banco da página e só a pessoa dona lê, mesmo se o link for compartilhado. No navegador, ficam só naquele navegador.
- A IA escreve com base no que você informar. Revise tudo antes de enviar, principalmente as respostas marcadas para revisão.
- O radar lê páginas de vagas pelo seu navegador e não se candidata a nada. Plataformas como o LinkedIn restringem automação nos termos de uso: use com moderação e por sua conta.
- Os valores salariais são referências de mercado, não garantia de oferta.

## Estrutura

```
.claude-plugin/plugin.json        manifesto do plugin
skills/montar-central-busca/      monta e publica a central
  references/central-busca.html   modelo da página
  references/entrevista-perfil.md roteiro para coletar o perfil
  references/banco-respostas.md   estrutura e perguntas-base
  references/radar-prompt.md      texto da tarefa do radar diário
  references/metodologia-salarial.md
skills/analisar-vaga/             pretensão, aderência e registro de vagas
template/central-busca.html       mesma página, para usar fora do plugin
docs/outras-ias.md                guia para ChatGPT, Gemini e navegador
```

## Contribua

Sugestões e melhorias são bem-vindas por issue ou pull request: novas tabelas salariais por área, modelos de mensagem, perguntas-base e traduções.

## Licença

MIT. Use, adapte e compartilhe, mantendo o crédito.
