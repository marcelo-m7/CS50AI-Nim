# 🧠 Agente de Q-Learning para o Jogo Nim

O Nim consiste em vários montes, cada um com um número de objetos.
Em cada jogada:

* O jogador escolhe **um único monte**
* Retira **quantos objetos quiser** desse monte

**Perde quem retirar o último objeto.**

Apesar da simplicidade, a combinação de múltiplos montes produz um espaço de estados grande, tornando o problema ideal para técnicas de aprendizagem por reforço.

---

## Arquitetura da Solução

O projeto é composto por dois ficheiros principais:

* **`nim.py`** — implementação do jogo e do agente Q-learning
* **`play.py`** — interface para treino e jogo humano

### Funções-chave implementadas (resumo)

#### `get_q_value(state, action)`

* Retorna o valor Q associado ao par `(estado, ação)`.
* Devolve `0.0` caso ainda não exista Q registado.

#### `update_q_value(state, action, old_q, reward, future_rewards)`

* Aplica a fórmula do Q-learning.
* Atualiza a tabela Q interna (`self.q`).
* Inclui logs úteis para debug.

#### `best_future_reward(state)`

* Calcula o maior Q possível entre todas as ações válidas naquele estado.
* Retorna `0.0` se não existirem valores Q registados.

#### `choose_action(state, epsilon=True)`

* Implementa a política **ε-greedy**:

  * Com probabilidade ε, escolhe ação aleatória.
  * Caso contrário, escolhe a ação com maior valor Q.

---

## Resultados Preliminares do Treino

Treino rápido utilizado:

```bash
python3 -c "from nim import train; train(10)"
```

Observações do log:

* No início, quase todos os `best_future_reward` são `0.0` (tabela Q vazia).
* Com algumas iterações, surgem valores positivos crescentes (`0.25`, `0.5`, `0.75`, `0.875`) — o agente reforça decisões boas.
* Surgem também valores negativos (`-0.5`, `-0.75`, `-0.96875`) — punições propagadas de jogadas que levaram à derrota.
* A tabela Q começa a ganhar forma, distinguindo movimentos vantajosos dos prejudiciais.

## Metodologia (Q-Learning)

O agente segue a atualização:

```
Q(s,a) ← old_q + α * ((reward + future_reward) − old_q)
```

Onde:

* **s** = estado atual
* **a** = ação tomada
* **α** = taxa de aprendizagem
* **reward** = recompensa imediata
* **future_reward** = melhor Q futuro possível

Com repetição suficiente, o agente ajusta os seus Q-values até convergir para uma política estável.

---

## Como Utilizar

### Treino

```bash
python nim.py
```

### Jogo humano vs agente

```bash
python play.py
```

### Treino rápido para inspeção

```bash
python -c "from nim import train; train(10)"
```

### Ambiente virtual (opcional)

```bash
python -m venv venv
```

## 🔗 Referências

- [Nim – CS50's Introduction to AI](https://cs50.harvard.edu/ai/projects/4/nim/)
- [Neural Networks – Lecture 5 (CS50 AI 2020)](https://youtu.be/J1QD9hLDEDY?si=41EOOXi-BaDbVy5E)
