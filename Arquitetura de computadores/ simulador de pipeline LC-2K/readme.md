# 🚀 Análise Comparativa de Técnicas de Contorno de Hazards de Dados em um Pipeline MIPS
![Language](https://img.shields.io/badge/language-Assembly-blue)
![Status](https://img.shields.io/badge/status-Completed-brightgreen)
![License](https://img.shields.io/badge/license-MIT-yellow)
![Architecture](https://img.shields.io/badge/architecture-MIPS-orange)


## 🧠 Sobre o Projeto
Essa pasta apresenta uma comparação prática entre três formas de lidar com **hazards de dados** em um pipeline MIPS de 5 estágios.  
As técnicas avaliadas foram:

- **NOOPs** – pausas manuais inseridas no código  
- **Stalls automáticos** – o simulador insere bolhas quando detecta hazards  
- **Forwarding** – encaminhamento direto dos resultados para evitar pausas

O objetivo é medir qual abordagem gera o **menor número de ciclos de clock** executando o mesmo programa.

---

## 🛠 Ferramentas Utilizadas

### 🔧 Simulador  
Utilizei o simulador online **LC-2K**, da Universidade de Michigan, que permite ativar/desativar técnicas de contorno e visualizar o pipeline em tempo real.

### 📄 Programa utilizado (Assembly)
O código usado nas simulações foi o exemplo **Countdown**, que naturalmente cria dependências entre instruções — ideal para observar hazards de dados.

```assembly
lw 0 1 neg1 
lw 0 2 ten 
lw 0 3 one 
loop add 2 1 2 
beq 2 0 done 
beq 0 0 loop 
done halt 
neg1 .fill -1 
ten .fill 10 
one .fill 1
```
### 🧪 Cenários Avaliados
<img width="516" height="133" alt="1759194861215" src="https://github.com/user-attachments/assets/8291528f-f7d5-404f-b32e-65d5dfd22501" />


### 🏁 Conclusão

NOOPs → Simples, porém adicionam pausas desnecessárias.

Stalls → Automáticos, mas igualmente custosos.

Forwarding → A melhor opção: mantém o pipeline ativo e reduz ciclos.

No geral, forwarding oferece o melhor desempenho com o menor impacto no fluxo de execução.
