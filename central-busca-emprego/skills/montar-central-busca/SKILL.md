---
name: montar-central-busca
description: Monta, para a pessoa usuária, uma central pessoal de busca de emprego publicada como página com banco de dados (tracker de vagas, remuneração, gerador de mensagens em português, inglês e espanhol, banco de respostas para perguntas de seleção, padrões, contatos e radar diário de vagas). Use quando a pessoa pedir "montar minha central de busca de emprego", "criar um tracker de vagas", "organizar minha busca de emprego", "página para acompanhar candidaturas" ou "instalar a central de busca".
---

# Montar a Central de Busca de Emprego

Construa a central a partir do modelo em `references/central-busca.html`, personalizada com fatos reais da pessoa. A página roda dentro do Claude com banco de dados próprio e, fora dele, guarda os dados no navegador.

## 1. Coletar o perfil

Antes de tocar no modelo, colete o perfil com o roteiro de `references/entrevista-perfil.md`. Aproveite o que já existe na conversa, na memória ou em um CV anexado; pergunte só o que faltar. Regras:

- Use apenas fatos que a pessoa confirmou. Nunca invente números, empresas, cargos ou formação.
- Quando dois materiais divergirem (CV antigo, perfil do LinkedIn, memória), pergunte qual está certo antes de seguir.
- Escreva as provas e o perfil em primeira pessoa, sem travessão e sem linguagem corporativa vazia.

## 2. Preparar a remuneração

Siga `references/metodologia-salarial.md`. O modelo traz uma tabela de exemplo para RH no Brasil (Robert Half e Michael Page 2027). Para outras áreas ou países, pesquise as faixas antes e substitua `CONFIG.salarios`. Cite as fontes para a pessoa.

## 3. Personalizar e publicar

1. Copie o modelo para a pasta de trabalho e edite apenas o objeto `CONFIG` no início do script: `nome`, `primeiroNome`, `subtitulo`, `foco`, `assinatura`, `cargoAlvo`, `resumo`, `resumoEmail`, `provas` (de 4 a 8, nos três idiomas), `perfil`, `planilhaUrl` (opcional), `salarios`, `setores`, `metas` e `respostasIniciais`.
2. Publique a página como artifact (veja as orientações de páginas da ferramenta de artifacts) e, depois de publicada, declare as capacidades `{"db":{"rules":[{"path":"","read":"admin","write":"admin"}]},"user":{},"sample":{}}`. A regra mantém os dados visíveis só para a dona ou o dono da página, mesmo se o link for compartilhado.
3. Popule o banco depois da publicação, com escrita no banco do artifact:
   - `respostas/<id>`: o banco de respostas de `references/banco-respostas.md`, preenchido com os fatos da pessoa (português obrigatório; inglês e espanhol quando a busca incluir vagas nesses idiomas). Marque `revisar: true` em qualquer resposta que dependa de opinião ou história pessoal que você não tem.
   - `vagas/<id>`: vagas que a pessoa já mencionou, com `status: "A confirmar"` quando não souber o andamento.
   - Não grave seeds dentro do HTML para o modo Claude.
4. Se a ferramenta de artifacts não estiver disponível, entregue o arquivo HTML personalizado: ele funciona aberto no navegador, em modo local.

## 4. Agendar o radar diário

Se a sessão tiver ferramentas de tarefas agendadas e a pessoa quiser o radar, rode primeiro uma busca de teste na conversa (LinkedIn Vagas, publicações do LinkedIn e Remotar, últimos 7 dias), grave as vagas e a lista `vistos` em `config/radar`, e então crie uma tarefa agendada com o texto de `references/radar-prompt.md`, preenchendo perfil, cargos-alvo, localização e o slug da página. Ela precisa do computador da pessoa com o navegador e o LinkedIn logado. Diga em uma frase quando roda e o que exige. O radar só lê: nunca se candidata, envia mensagens ou altera perfis.

## 5. Entregar

Responda com um resumo curto: o que cada aba faz, o que ficou marcado para revisar, quando o radar roda e o que a pessoa deve conferir primeiro. Ofereça registrar a próxima vaga.

## Depois de montada

Quando a pessoa mandar uma descrição de vaga, use a skill `analisar-vaga` para registrar a vaga e sugerir a pretensão.
