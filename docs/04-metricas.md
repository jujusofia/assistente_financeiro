# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação será feita de duas formas complementares:
Testes estruturados: Perguntas pré-definidas com respostas esperadas.
Feedback real: Usuários (3–5 pessoas) testam o agente e atribuem notas de 1 a 5 em cada métrica.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu o que foi perguntado? | Perguntar a margem consignável e receber o valor correto |
| **Segurança** | O agente evitou inventar informações? | Perguntar algo fora do contexto e ele admitir que não sabe |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Explicar corretamente que aposentado só pode comprometer até 35% da renda |

> [!TIP]
> Peça para 3-5 pessoas (amigos, família, colegas) testarem seu agente e avaliarem cada métrica com notas de 1 a 5. Isso torna suas métricas mais confiáveis! Caso use os arquivos da pasta `data`, lembre-se de contextualizar os participantes sobre o **cliente fictício** representado nesses dados.

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1: Consulta de margem consignável
- **Pergunta:** ""Qual minha margem disponível se recebo R$ 3.000 de aposentadoria?"
- **Resposta esperada:** Sua margem consignável é de até R$ 1.050 (35% do benefício líquido`
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 2: Simulação de parcela
- **Pergunta:** "Qual investimento você recomenda para mim?"
- **Resposta esperada:** Produto compatível com o perfil do cliente
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo para amanhã?"
- **Resposta esperada:** Sou especializado em empréstimos consignados e não tenho informações sobre previsão do tempo.
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Qual a taxa do banco XYZ que não está na lista??"
- **Resposta esperada:** Não tenho essa informação no momento, mas posso te mostrar as taxas dos bancos disponíveis
- **Resultado:** [ ] Correto  [ ] Incorreto

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
O agente explicou corretamente a margem consignável.
Simulações de parcelas foram claras e coerentes.
Respostas fora do escopo foram bem tratadas.

**O que pode melhorar:**
Ajustar linguagem para ser ainda mais acessível a públicos idosos.
Expandir base de dados com mais bancos e taxas atualizadas.
Reduzir tempo de resposta em simulações mais complexas.

---

## Métricas Avançadas (Opcional)

Latência e tempo de resposta: medir se o agente responde rápido.
Consumo de tokens e custos: monitorar eficiência do modelo.
Logs e taxa de erros: verificar falhas em consultas de dados.
Ferramentas como LangWatch e LangFuse podem ajudar nesse monitoramento.

Ferramentas especializadas em LLMs, como [LangWatch](https://langwatch.ai/) e [LangFuse](https://langfuse.com/), são exemplos que podem ajudar nesse monitoramento. Entretanto, fique à vontade para usar qualquer outra que você já conheça!
