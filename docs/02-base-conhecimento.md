# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_cliente.json` | JSON | Identificar margem consignável, renda e perfil do cliente |
| `taxas_bancos.json` | JSON | Listar taxas de juros praticadas por diferentes bancos |
| `simulacoes.csv` | CSV | Registrar simulações anteriores para comparação |
| `regulacoes_inss.json` | JSON | Regras oficiais sobre consignado (margem, teto de juros, prazos permitidos) |

> [!TIP]
> **Quer um dataset mais robusto?** Se quiser enriquecer, pode usar datasets públicos do Hugging Face relacionados a finanças e crédito, adaptando para o contexto de empréstimo consignado.

---

## Adaptações nos Dados


Expansão dos dados mockados para incluir taxas atualizadas de bancos mais relevantes.

Inclusão de campos extras no perfil_cliente.json como idade, benefício líquido e margem disponível.

Normalização dos valores em simulacoes.csv para facilitar cálculos automáticos.

---

## Estratégia de Integração

### Como os dados são carregados?

Os arquivos JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt.

O agente consulta dinamicamente os dados conforme a pergunta do usuário.

As informações relevantes são formatadas em linguagem natural antes de serem apresentadas.

### Como os dados são usados no prompt?
---
System Prompt: inclui regras gerais e limites (ex.: margem consignável máxima).

Dados dinâmicos: taxas de bancos e perfil do cliente são consultados conforme a interação.

Simulações: valores são calculados com base nos dados do cliente e nas taxas disponíveis.


## Exemplo de Contexto Montado

```
Dados do Cliente:
- Nome: João Silva
- Benefício líquido: R$ 3.000
- Margem consignável disponível: R$ 1.050 (35%)

Últimas simulações:
- Empréstimo: R$ 10.000
- Prazo: 60 meses
- Taxa média: 2% ao mês
- Parcela estimada: R$ 270

Taxas de Bancos:
- Banco do Brasil: 1,95% ao mês
- Caixa: 2,10% ao mês
- Bradesco: 2,05% ao mês

...
```
