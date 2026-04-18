# Código da Aplicação


```

# ==============================
# PERFIL DO CLIENTE
# ==============================
perfil = {
    "nome": None,
    "margem": 1050
}

# ==============================
# TAXAS DE BANCOS
# ==============================
taxas_bancos = [
    {"banco": "Banco do Brasil", "taxa": 1.95},
    {"banco": "Caixa Econômica Federal", "taxa": 2.10},
    {"banco": "Bradesco", "taxa": 2.05},
    {"banco": "Santander", "taxa": 2.00}
]

# ==============================
# UTILITÁRIOS FINANCEIROS
# ==============================
def calcular_parcela(valor, prazo, taxa):
    i = taxa / 100
    return valor * i / (1 - (1 + i) ** -prazo)


def media_taxa():
    return sum(b["taxa"] for b in taxas_bancos) / len(taxas_bancos)


def melhor_taxa():
    banco = min(taxas_bancos, key=lambda x: x["taxa"])
    return banco["taxa"], banco["banco"]


def comparar_bancos(valor, prazo):
    linhas = []
    for b in taxas_bancos:
        p = calcular_parcela(valor, prazo, b["taxa"])
        linhas.append(f"{b['banco']}: R$ {p:.2f}")
    return "\n".join(linhas)

# ==============================
# NLP FINANCEIRO INTELIGENTE
# ==============================
def interpretar_nlp(texto):
    t = texto.lower()

    # valores numéricos
    nums = re.findall(r'\d+(?:[\.,]\d+)?', t.replace(",", "."))
    valor = float(nums[0]) if len(nums) > 0 else None
    prazo = int(nums[1]) if len(nums) > 1 else None

    # parcela máxima
    parcela_max = None
    match = re.search(r'(até|ate|máximo|maximo|não passar de|nao passar de)\s*(\d+)', t)
    if match:
        parcela_max = float(match.group(2))

    # intenção
    intent = "simulacao" if any(x in t for x in ["simular", "emprestimo", "credito", "consignado"]) else "outro"

    return {
        "intent": intent,
        "valor": valor,
        "prazo": prazo,
        "parcela_max": parcela_max
    }

# ==============================
# CHAT SIMULYN AI
# ==============================
def chat(user_input, history):
    if history is None:
        history = []

    dados = interpretar_nlp(user_input)

    nome = perfil["nome"]
    prefixo = f"Sr(a). {nome}, " if nome else ""

    # ======================
    # REGISTRO DE NOME
    # ======================
    if "meu nome e" in user_input.lower():
        perfil["nome"] = user_input.split()[-1].title()
        return history + [
            (user_input, "Identificação registrada no sistema financeiro.")
        ]

    # ======================
    # SIMULAÇÃO INTELIGENTE
    # ======================
    if dados["intent"] == "simulacao":

        valor = dados["valor"] or 1000
        prazo = dados["prazo"] or 12
        parcela_max = dados["parcela_max"]

        taxa, banco = melhor_taxa()
        parcela = calcular_parcela(valor, prazo, taxa)

        media = media_taxa()

        # decisão de crédito
        status = "APROVADO"

        if parcela_max:
            if parcela > parcela_max:
                status = "NEGADO (excede limite de parcela informado)"
        elif parcela > perfil["margem"]:
            status = "NEGADO (excede margem consignável)"

        resposta = f"""
🏦 SIMULAÇÃO DE CRÉDITO - SIMULYN AI
💰 Valor solicitado: R$ {valor:.2f}
📆 Prazo: {prazo} meses

📉 Taxa aplicada: {taxa:.2f}% a.m.
📊 Média de mercado: {media:.2f}% a.m.
🏦 Banco referência: {banco}

💳 Parcela estimada: R$ {parcela:.2f}
📊 Parcela máxima informada: {parcela_max if parcela_max else 'não informada'}

🧠 Análise de crédito: {status}
────────────────────────────
🏦 Comparação entre bancos:
{comparar_bancos(valor, prazo)}
"""

        return history + [(user_input, resposta)]

    # ======================
    # LIMITE DE CRÉDITO
    # ======================
    if "quanto posso" in user_input.lower() or "limite" in user_input.lower():
        estimativa = perfil["margem"] * 12

        return history + [
            (user_input, f"{prefixo}Limite estimado de crédito consignado: R$ {estimativa:.2f}")
        ]

    # ======================
    # FALLBACK BANCÁRIO
    # ======================
    return history + [
        (user_input,
         "Solicitação não reconhecida pelo sistema financeiro.\n\n"
         "Exemplos válidos:\n"
         "- simular 5000 24\n"
         "- quero pagar até 300 por mês\n"
         "- simular crédito 10000 em 36 meses")
    ]

# ==============================
# INTERFACE GRADIO
# ==============================
with gr.Blocks(theme=gr.themes.Soft()) as app:

    gr.Markdown("#SimuLyn AI Chat")
    gr.Markdown("### Simulador inteligente de crédito pessoal e consignado")

    chatbot = gr.Chatbot(height=520)

    msg = gr.Textbox(
        placeholder="Ex: quero pagar até 300 por mês ou simular 5000 24"
    )

    msg.submit(chat, inputs=[msg, chatbot], outputs=chatbot)

app.launch()

```


## Requerimentos

```
import gradio as gr
import re
```

## Como Rodar

```bash
# Instalar dependências
pip install gradio transformers accelerate

import gradio as gr
import time

# Rodar a aplicação
Google Colab
```
