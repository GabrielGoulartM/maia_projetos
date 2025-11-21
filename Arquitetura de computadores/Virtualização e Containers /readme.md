# 💡 Virtualização e Containers  
---
<!-- Badges -->
![Status](https://img.shields.io/badge/status-Completed-brightgreen)
![Tech](https://img.shields.io/badge/Tecnologias-VMs%20%7C%20Containers-00ffe7)
![License](https://img.shields.io/badge/License-MIT-00ff44)

---

## 🌐 Conclusão de semestre:
Para fechar a nota do grau B desta disciplina, o professor nos deu a opção de escolher um dos conceitos — virtualização ou containers — e nos aprofundar nele. 
Eu e meu grupo decidimos explorar um pouco de ambos e comparar o desempenho de uma aplicação web em Python executada em uma máquina virtual versus em um container usando Docker

---

# 🖥️ Máquinas Virtuais — "O PC dentro do PC"

### ✨ Conceito básico:
VM é basicamente **um computador inteiro rodando dentro do meu computador**.  
Tem seu próprio sistema operacional, seu próprio kernel e tudo mais.

### ⚡ Pontos que mais chamaram minha atenção:
- Rodam qualquer sistema operacional.
- São super isoladas (ótimo pra não quebrar nada).  
- Mas ocupam muita RAM e espaço no disco.  
- Inicialização mais lenta.

### 🔧 Hipervisores que estudei:
- **Tipo 1 (Bare-metal):** KVM + QEMU
- **Tipo 2:** VirtualBox

---

# 📦 Containers — "Leve, rápido e eficiente"

### ✨ Conceito básico:
Containers são  **minis ambientes isolados**, que compartilham o kernel do sistema.  
Muito mais leves e rápidos que VMs.

### 💥 Pontos que mais chamaram minha atenção:
- Compartilham kernel do host → por isso são tão leves.  
- Sobem em **1 segundo** (ou menos).  
- Ideais pra DevOps e microserviços.  
- O isolamento é bom, mas não tão efetivo quanto VMs.

### 🔍 Como o isolamento funciona:
- **Namespaces:** cada container tem seu próprio espaço contido.
- **cgroups:** limitam RAM/CPU para ter um ambiente mais controlado.

---


---

# 🔬 Meu mini estudo de caso 

# 🧪 Código da Aplicação Web Usada no Teste  
*(Simples, mas perfeita pra comparar desempenho entre container e VM)*

```python
from flask import Flask
import time, os

app = Flask(__name__)

@app.route('/')
def hello():
    return {
        'message': 'Hello from Virtualization Demo!',
        'timestamp': time.time(),
        'hostname': os.uname().nodename,
        'platform': os.uname().sysname
    }

@app.route('/load')
def load_test():
    # Simulate CPU load
    start = time.time()
    result = 0
    for i in range(1000000):
        result += i * i
    return {
        'computation_time': time.time() - start,
        'result': result
    }
```


| Métrica | Docker | VM |
|--------|--------|----|
| Build | ~20s | ~30min |
| Start | 1–2s | ~30s |
| Disco | 150MB | 3–10GB |
| RAM (idle) | 20MB | 260–1024MB |
| CPU (idle) | 0.01% | 8.5% |
| Recuperação | ~2s | até 60s |

---


# ⚡ Observação Rápida: O Poder do Docker com Poucos Recursos

Uma coisa que realmente me chamou atenção durante os testes foi como o **Docker consegue fazer muito com quase nada**.

Eu limitei o container para usar **apenas 2 núcleos de CPU e 4 GB de RAM**, e mesmo assim, em ambiente *idle*, o uso de CPU ficou extremamente baixo

Isso ressalta dois pontos:

- Containers são **absurdamente eficientes** na forma como usam o hardware.  
- Mesmo com restrições fortes, eles continuam leves, responsivos e estáveis.  

A VM, por outro lado, consumia recursos mesmo parada — só pra existir.

![teste](https://github.com/user-attachments/assets/a4803454-b388-43a7-b3e0-69c19ea8f080)
