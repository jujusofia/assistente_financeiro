# Código da Aplicação

Esta pasta contém o código do seu agente financeiro.

## Estrutura Sugerida

```
src/
├── app.py              # Aplicação principal (Streamlit/Gradio)
├── agente.py           # Lógica do agente
├── config.py           # Configurações (API keys, etc.)
└── requirements.txt    # Dependências
```

## Exemplo de requirements.txt

```
streamlit
openai
python-dotenv
```

## Como Rodar

```bash
# Instalar dependências
!pip install -q openai-whisper gTTS requests matplotlib openai
!apt-get update -qq && apt-get install -y ffmpeg

!pip install openai-whisper

import os
import re
import whisper
import requests
import matplotlib.pyplot as plt

from gtts import gTTS
from base64 import b64decode
from IPython.display import Audio, display, Javascript
from google.colab import output

# Rodar a aplicação
Google Colab
```
