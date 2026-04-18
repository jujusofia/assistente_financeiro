# SimuLyn AI Chat - Simulador Inteligente de Crédito Pessoal e Consignado

## 📌 Visão Geral

O SimuLyn AI Chat é um agente financeiro inteligente para simulação de crédito pessoal e consignado baseado em IA Generativa e dados do usuário.

---

## 🎯 Objetivo

- Simular crédito pessoal e consignado com base em dados reais
- Personalizar recomendações conforme perfil financeiro
- Garantir segurança nas sugestões financeiras
- Evitar alucinações com regras determinísticas

---

## 👤 Persona

Consultor financeiro digital sênior com comunicação:
- Clara
- Objetiva
- Educativa
- Baseada em dados

---

## 🧠 Arquitetura

Usuário → Interface (Streamlit/Gradio)  
→ Parser de intenção  
→ Base de dados do cliente  
→ Motor de regras financeiras  
→ LLM (geração de linguagem)  
→ Resposta final  

---

## 📊 Base de Conhecimento

- transacoes.csv → histórico financeiro  
- historico_atendimento.csv → interações anteriores  
- perfil_investidor.json → perfil do cliente  
- produtos_financeiros.json → produtos e taxas  

---

## 🔐 Regras de Segurança

- Proibido gerar valores sem dados reais  
- Simulações apenas via regras determinísticas  
- Limite de comprometimento: 30% a 35% da renda  
- Solicitar dados quando necessário  
- Respostas sempre baseadas em contexto válido  

---

## 🧠 System Prompt

Você é o SimuLyn AI Chat, um consultor financeiro especializado em simulação de crédito pessoal e consignado.

Regras:
- Não inventar valores financeiros
- Não simular crédito sem dados suficientes
- Usar apenas dados fornecidos pelo sistema
- Priorizar segurança financeira do usuário
- Explicar resultados de forma clara e objetiva

---

## 💬 Exemplo de Interação

Usuário:
“Posso pegar um empréstimo de R$ 10.000?”

Resposta:
- Valor recomendado: R$ 6.000  
- Parcela estimada: R$ 420  
- Comprometimento: 28% da renda  

---

## ⚠️ Edge Cases

Sem dados suficientes:
- Solicitar informações adicionais

Valor acima do limite:
- Sugerir redução de valor ou aumento de prazo

Dados inconsistentes:
- Solicitar atualização do perfil financeiro

---

## 💻 Aplicação

Stack:
- Python  
- Streamlit ou Gradio  
- API de LLM (OpenAI, Claude ou similar)

---

## 🧪 Exemplo (Streamlit)

```python
import streamlit as st

st.title("SimuLyn AI Chat")

user_input = st.text_input("Digite sua solicitação:")

if user_input:
    st.write("Processando simulação...")

    resultado = {
        "valor_recomendado": 6000,
        "parcela": 420,
        "comprometimento": "28%"
    }

    st.json(resultado)
