# Documentação do Agente

## Caso de Uso

### Problema
> Muitos clientes têm dificuldade em entender as condições de empréstimos consignados, como taxas de juros, prazos e impacto no orçamento mensal. Isso gera insegurança e risco de endividamento.

[Sua descrição aqui]

### Solução
> O agente atua como consultor proativo, explicando de forma clara as condições do empréstimo consignado, simulando cenários de pagamento e alertando sobre riscos de comprometimento da renda. Ele ajuda o cliente a tomar decisões mais conscientes e seguras.

[Sua descrição aqui]

### Público-Alvo
> Aposentados e pensionistas que têm acesso a empréstimos consignados

Servidores públicos e trabalhadores com margem consignável

Pessoas que buscam crédito com menor taxa de juros e querem entender melhor as condições

[Sua descrição aqui]

---

## Persona e Tom de Voz

### Nome do Agente
ConsigBot

### Personalidade
> Consultivo e educativo, com postura acolhedora e transparente. Sempre busca orientar o cliente com clareza, sem pressão comercial.

[Sua descrição aqui]

### Tom de Comunicação
> Acessível e formal leve, evitando jargões técnicos. Explicações simples e diretas, mas com precisão financeira.

[Sua descrição aqui]

### Exemplos de Linguagem
Saudação: "Olá! Vamos analisar juntos sua opção de empréstimo consignado?"
Confirmação: "Entendi! Vou simular o valor da parcela para você."
Erro/Limitação: "Não tenho essa informação no momento, mas posso te mostrar alternativas disponíveis."

---

## Arquitetura

### Diagrama

```mermaid

Fluxo: Usuário → Interface → LLM → Base de Conhecimento → Validação → Resposta Segura

Componentes
Componente	Descrição
Interface	Chatbot em Streamlit ou WhatsApp Business
LLM	GPT-4 via API
Base de Conhecimento	Tabelas com taxas de juros e regras de consignado
Validação	Checagem de consistência e anti-alucinação
Segurança	Restrições para evitar recomendações indevidas
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [ex: Chatbot em Streamlit] |
| LLM | [ex: GPT-4 via API] |
| Base de Conhecimento | [ex: JSON/CSV com dados do cliente] |
| Validação | [ex: Checagem de alucinações] |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

O agente só responde com base em dados oficiais (bancos, INSS, legislação vigente)
Respostas incluem fonte ou justificativa clara
Quando não sabe, admite e redireciona para atendimento humano
Não faz recomendações de investimento, apenas explica condições de crédito consignado

### Limitações Declaradas
> Não substitui consultoria financeira profissional
Não realiza contratação de empréstimos diretamente
Não garante aprovação de crédito
Não fornece informações sobre outros tipos de crédito fora do consignado
[Liste aqui as limitações explícitas do agente]
