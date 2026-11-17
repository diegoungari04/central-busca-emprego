# Usar com outras IAs ou só no navegador

A página `template/central-busca.html` funciona sem o Claude. Fora dele:

- os dados ficam salvos no navegador em que você abriu o arquivo (troque de navegador ou limpe os dados e eles somem);
- os botões "Refinar", "Traduzir" e "Gerar com Claude" não aparecem; mensagens e banco de respostas continuam funcionando;
- não há radar diário automático.

## Passo a passo

1. Baixe `template/central-busca.html`.
2. Abra uma conversa na IA que você usa, anexe o arquivo e o seu CV, e cole o prompt abaixo.
3. Salve o arquivo que a IA devolver e abra no navegador (duplo clique).

### Prompt para personalizar

```
Você vai personalizar uma página HTML de busca de emprego. Edite SOMENTE o objeto CONFIG no início do <script>, sem mexer no resto do código, e me devolva o arquivo completo.

Regras:
- Use apenas fatos do meu CV e do que eu disser. Nunca invente números, empresas, cargos ou formação. Se faltar algo, pergunte antes.
- Textos em primeira pessoa, tom direto, sem travessão e sem linguagem corporativa vazia.
- provas: de 4 a 8 resultados concretos meus, cada um em pt, en e es.
- perfil: um parágrafo factual com experiências, números, formação, idiomas, cidade e modelo de trabalho.
- respostasIniciais: crie respostas para estas perguntas, com os campos pergunta, tags, resposta_pt, resposta_en e resposta_es: fale sobre você; por que saiu do último emprego (marque revisar: true); por que quer trabalhar na empresa (use {empresa} e {cargo}, revisar: true); pretensão salarial (use {faixa}); disponibilidade; nível de idiomas; trabalho remoto; projeto de que mais se orgulha; primeiros 90 dias.
- salarios: se a minha área não for RH no Brasil, pesquise faixas de mercado da minha área e porte de empresa em guias salariais de consultorias de recrutamento e substitua a tabela, no mesmo formato [cargo, porte, CLT mín, CLT máx, nota]. Me diga as fontes.

Meu cargo-alvo: ____
Plano B: ____
Cidade e modelo de trabalho aceito: ____
```

### Prompt para analisar uma vaga

```
Com base no meu perfil (CONFIG.perfil da página) e na tabela de salários dela, analise a vaga abaixo: aderência de 0 a 100, de duas a quatro lacunas reais, faixa de pretensão CLT e PJ (PJ = CLT × 1,35 a 1,45) considerando setor e porte da empresa, e o número único para formulário. Diga as fontes que usou para o porte.

[cole a vaga]
```

### Prompt para responder uma pergunta de seleção

```
Responda esta pergunta de processo seletivo como se fosse eu, em primeira pessoa, só com fatos do meu perfil, sem travessão, em até ___ caracteres e em ___ (idioma). Se a pergunta pedir algo que meu perfil não cobre, escreva o melhor possível e diga na última linha o que eu devo completar.

Pergunta: ____
```

Depois, salve as boas respostas na aba Perguntas da página para não precisar pedir de novo.
