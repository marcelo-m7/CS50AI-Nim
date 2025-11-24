# Agente de Q-Learning para o Jogo Nim

Aluno: **Marcelo Santos (a79433)**

Este trabalho, desenvolvido no âmbito da unidade curricular **Inteligência Artificial**, do curso **Engenharia de Sistemas e Tecnologias Informáticas (1.º ciclo) – Universidade do Algarve**, tem como objetivo implementar um agente inteligente capaz de aprender autonomamente a jogar o clássico jogo **Nim**.

---

## Objetivo Geral

Criar uma inteligência artificial baseada em **aprendizagem por reforço** (*Reinforcement Learning*), utilizando a técnica de **Q-learning**, para que o agente aprenda estratégias vencedoras no jogo Nim jogando repetidamente contra si mesmo.

---

## O Problema: O Jogo Nim

Nim é um jogo de estratégia composto por vários montes contendo um determinado número de objetos. Dois jogadores retiram, alternadamente, um número à sua escolha de objetos de **um único monte**.

**Regra essencial:** quem retirar o **último objeto perde**.

Apesar de simples, o jogo envolve decisão estratégica, especialmente quando vários montes estão presentes e as possíveis combinações crescem rapidamente.

---

## Solução Proposta

O projeto propõe implementar um agente que:

- **Aprende através da experiência**, analisando resultados de milhares de jogos simulados.
- Atualiza continuamente as suas decisões com base no **algoritmo Q-learning**.
- Utiliza uma política de exploração **ε-greedy**, equilibrando exploração e exploração.
- Armazena valores Q para cada par *(estado, ação)*, permitindo prever quais jogadas são mais vantajosas.

---

## Principais Componentes Implementados

### **1. Representação do Jogo (classe Nim)**

- Mantém o estado dos montes.
- Lista ações possíveis.
- Processa jogadas e alterna turnos.

### **2. Agente Inteligente (classe NimAI)**

Responsável por:

- Obter valores Q (função `get_q_value`)
- Atualizar valores Q (função `update_q_value`)
- Estimar recompensas futuras (função `best_future_reward`)
- Escolher ações (função `choose_action`)

### **3. Treino e Simulação**

- O agente joga contra si mesmo repetidamente.
- Aprende gradualmente estratégias vencedoras.
- Após o treino, pode jogar contra um humano.

---

## Metodologia: Q-Learning

O Q-learning segue a fórmula:

```bash
Q(s, a) ← old_q + α * ((reward + future_reward) − old_q)
```

Onde:

- **s** = estado atual do jogo
- **a** = ação tomada
- **α** = taxa de aprendizagem
- **reward** = recompensa imediata
- **future_reward** = melhor estimativa de recompensa futura

Com tempo e repetição, o agente converte experiência em estratégia.

---

## Como usar

- Treinar o agente: execute `python nim.py` (ou o script de treino existente).
- Jogar contra o agente: execute `python play.py` (se disponível) para uma partida humana vs agente.

### Execução local (exemplo)

1. Criar e ativar um ambiente virtual (opcional):

```bash
python -m venv venv
```

2. Treinar (exemplo):

```bash
python nim.py
```

---

## Técnicas e Ferramentas

- **Python 3.12**
- **Q-Learning** e **ε-greedy**
- Testes automáticos com `check50`, `style50`, `submit50`
- Organização em branches Git e documentação (`README.md` e features opcionais)

---

## Conclusão

Este projeto demonstra como técnicas de Inteligência Artificial permitem que máquinas aprendam comportamento estratégico complexo **sem supervisão direta**, apenas através de tentativa, erro e reforço.

A solução desenvolvida mostra a aplicação prática de conceitos fundamentais de RL, Q-learning e tomada de decisão probabilística num problema clássico e matematicamente rico como o Nim.

---

## Referências

- [Nim – CS50's Introduction to AI](https://cs50.harvard.edu/ai/projects/4/nim/)
- [Neural Networks – Lecture 5 (CS50 AI 2020)](https://youtu.be/J1QD9hLDEDY?si=41EOOXi-BaDbVy5E)

---

*Universidade do Algarve – Departamento de Engenharia Eletrotécnica e Informática*

---
