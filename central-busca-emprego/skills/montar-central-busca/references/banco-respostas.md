# Banco de respostas: estrutura e perguntas-base

Cada documento em `respostas/<id>` tem:

| Campo | Uso |
|---|---|
| `pergunta` | A pergunta-modelo |
| `tags` | Palavras e expressões que a pergunta costuma ter, em PT, EN e ES; a busca da página usa isso |
| `resposta_pt` / `resposta_en` / `resposta_es` | Resposta em cada idioma |
| `curta` | Versão até 200 caracteres para formulários com limite |
| `revisar` | `true` quando a pessoa precisa conferir antes de usar |
| `usos` | Contador, comece em 0 |

Use os marcadores `{empresa}`, `{cargo}` e `{faixa}`: a página troca pelos dados da vaga escolhida.

## Perguntas-base (escreva com os fatos da pessoa)

1. Fale sobre você e sua trajetória
2. Por que você saiu do último emprego? (revisar: true, salvo se a pessoa contou o motivo)
3. Por que você quer trabalhar na nossa empresa? (revisar: true, usa {empresa} e {cargo})
4. Experiência com ferramentas de IA
5. Experiência com gestão da mudança ou reestruturação
6. Nível de inglês (e de espanhol, se houver)
7. Trabalho remoto e modelo preferido
8. Pretensão salarial: "A combinar conforme o pacote completo. Como referência, para esta posição minha faixa é {faixa}."
9. Disponibilidade para início
10. Projeto ou resultado de que mais se orgulha
11. Uma pergunta técnica central da área da pessoa (ex.: cultura, vendas, dados)
12. Primeiros 90 dias no cargo
13. Como usa dados e indicadores
14. Situação em que discordou de uma liderança: deixe só a estrutura (situação, argumento, proposta, resultado, aprendizado) e `revisar: true`. Nunca invente a história.
15. Como se mantém atualizado(a)

Regras: primeira pessoa, tom de conversa direto, sem travessão, sem bajulação, só fatos confirmados.
