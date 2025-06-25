# 🔢 Contador Síncrono com Flip-Flops JK  

Este projeto apresenta o desenvolvimento de um contador síncrono utilizando Flip-Flops JK, projetado para percorrer a seguinte sequência de estados:  
000 → 010 → 101 → 110 → 000 → ...

🛑 **Estados inválidos** (001, 011, 100 e 111) são automaticamente redirecionados para o estado inicial **000** no próximo pulso de clock.  

## 🛠️ Tecnologias e Ferramentas  

- ✔️ CircuitVerse – Simulador de circuitos digitais online  
  

## 🚀 Funcionamento  

- ✅ O contador é síncrono, ou seja, todas as transições ocorrem no mesmo pulso de clock.  
- ✅ Flip-Flops JK foram utilizados na implementação.  
- 🔄 Caso o circuito entre em qualquer estado inválido, ele automaticamente volta para **000** no próximo clock.  

## 🖥️ Demonstração  

<img src="https://github.com/GabrielGoulartM/maia_projetos/blob/635f07e938fa5a1d192d48e3eabf76cf428ed2b5/Sistemas%20Digitais/Contador/contador%20anel.gif" width="600"/>  

![Demonstração do circuito](seu-gif-aqui.gif)  

## 🔗 Acesse o circuito no CircuitVerse  

[Clique aqui para abrir no CircuitVerse](https://circuitverse.org/users/309363/projects/contador-dc47540d-4ca7-4b06-9c4a-3b633e0c12fd)  

## 📜 Enunciado do Projeto  

> “Projete um contador síncrono usando FFs JK que tenha a seguinte sequência: 000, 010, 101, 110 e repete.  
> Os estados indesejáveis (não usados) 001, 011, 100 e 111 têm de levar o contador sempre para 000 no próximo pulso de clock.”  


