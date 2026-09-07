# 🐗 | FlappyBara (Backup)

> "Nas margens do Rio Capibaribe, uma lenda ganha vida..."

Assuma o controle da **Capivara Voadora**, a heroína mais improvável do ecossistema, em uma jornada desafiadora pelos céus. Desvie de canos, colete iguarias locais (mangas, aguapés e folhas) e utilize power-ups para sobreviver o máximo possível.

O projeto foi desenvolvido em **Python** utilizando a biblioteca **Pygame**, focando em mecânicas de física, geração procedural de obstáculos e um sistema de progressão de dificuldade.

---

## 👨‍💻 | Integrantes
- Heitor Souza de Lima &lt;hsl2&gt;
- Kayque Tavares Marcelino da Costa  &lt;ktmc&gt;
- Gabriel Coelho Crispim  &lt;gcc3&gt;
- Paulo Silva Barroso 
- Roberto Augusto  &lt;ranm&gt;

---
## 📸 | Screenshots

<img width="1591" height="894" alt="image" src="https://github.com/user-attachments/assets/8f97a929-dcc1-4c02-9d88-b9b50b5caa97" />
<img width="1597" height="890" alt="image" src="https://github.com/user-attachments/assets/121a7b5a-dd51-4efd-8483-6c7e93e7141d" />
<img width="1601" height="897" alt="image" src="https://github.com/user-attachments/assets/740208ea-d025-4dee-a7cd-63a7c9edd90f" />

---

## 🎮 | Mecânicas do Jogo

O jogo é um *Endless Runner* (corrida infinita) onde o objetivo é obter a maior pontuação possível.

### 🌟 Funcionalidades Principais:
- **Física de Voo:** Mecânica de pulo (`Espaço` ou `Clique`) e mergulho (`Seta Baixo`) para desviar de obstáculos.
- **Ciclo Dia/Noite:** O céu muda de cor dinamicamente conforme o tempo de jogo avança (Dia -> Entardecer -> Noite).
- **Parallax Background:** Montanhas e nuvens se movem em velocidades diferentes para criar sensação de profundidade.
- **Sistema de Coleta:**
  - 🍃 **Folha:** Pontuação comum.
  - 🔵 **Aguapé:** Pontuação média.
  - 🥭 **Manga:** Pontuação alta (item raro).
- **Power-ups:**
  - 🛡️ **Escudo:** Protege contra uma colisão.
  - ⏳ **Slow Motion:** Desacelera o tempo para facilitar manobras.
- **Ranking Local:** Sistema de High Score que salva as 10 melhores pontuações em arquivo (`scores.txt`).

  ---
  
  
  
### 🏔️ Efeito Parallax (Profundidade Visual)
Para superar a limitação bidimensional e conferir imersão ao cenário, implementamos um sistema de **scrolling diferencial**. Diferentes camadas de renderização se movem a velocidades distintas, criando uma ilusão de ótica de profundidade e distância:

- **Chão e Obstáculos:** Movem-se a 100% da velocidade do jogo (Referencial do Jogador).
- **Montanhas Próximas:** Movem-se a **15%** da velocidade (`scroll_factor = 0.15`).
- **Montanhas Distantes:** Movem-se a apenas **5%** da velocidade (`scroll_factor = 0.05`).

### 🛡️ Sistema de Áudio "Fail-Safe"
Visando a robustez da aplicação, implementamos o padrão de projeto **Dummy Object** para o gerenciamento de som.
1. O jogo tenta carregar os arquivos de áudio da pasta `Soundtrack/`.
2. Caso ocorra um erro (`FileNotFoundError` ou arquivo corrompido), o sistema captura a exceção via `try/except`.
3. São instanciados objetos de som "falsos" (Dummies) que possuem os métodos necessários (como `.play()`), mas não executam nenhuma ação.

> **Resultado:** Isso impede que o jogo sofra um *crash* fatal caso o usuário esqueça de baixar os sons, garantindo a jogabilidade mesmo em silêncio.

## 🛠️ | Tecnologias e Bibliotecas

O projeto foi construído utilizando:

- **Linguagem:** Python 3.x
- **Engine Gráfica:** [Pygame](https://www.pygame.org/) (`pip install pygame`)
- **Módulos Nativos:** `sys`, `random`, `math`, `os`

---

## 📂 | Organização do Código

O código foi estruturado seguindo o paradigma de **Orientação a Objetos** para facilitar a manutenção e escalabilidade:

1.  **Classe `Game`:** Gerencia o loop principal, estados do jogo (Start, Playing, GameOver), inputs e renderização.
2.  **Classe `Capivara`:** Controla a física, colisão, animação de sprites e estados de power-up do jogador.
3.  **Classe `Pipe`:** Responsável pela geração procedural dos canos, movimentação e spawn de itens/power-ups entre as brechas.
4.  **Classes de Ambiente:** `Mountain`, `Cloud`, `Bird` e `Particle` gerenciam os elementos visuais e atmosféricos do jogo.
5.  **Gerenciamento de Assets:** Sistema robusto para carregar sons e imagens, com tratamento de erros (try/except) para evitar falhas caso arquivos estejam faltando.

---

## 🛠️ | Conceitos e Tecnologias Utilizadas

O projeto foi construído em **Python** utilizando a biblioteca **Pygame**. Durante o desenvolvimento, aplicamos diversos conceitos fundamentais da disciplina:

- **Programação Orientada a Objetos (POO):** O jogo é estruturado em classes (`Capivara`, `Pipe`, `Game`, `Cloud`), permitindo encapsulamento e melhor organização do código.
- **Estruturas de Dados:** Uso extensivo de **Listas** para gerenciar as entidades do jogo (nuvens, partículas, canos) e **Dicionários** para armazenar contadores de itens coletados.
- **Laços de Repetição e Condicionais:** Essenciais para o *Game Loop*, detecção de colisões e lógica de *spawn* de inimigos.
- **Tratamento de Exceções (`try/except`):** Implementado no carregamento de assets (sons e imagens) para garantir que o jogo não feche abruptamente caso um arquivo esteja faltando.
- **Manipulação de Arquivos:** Leitura e escrita do arquivo `scores.txt` para persistência do *High Score*.
- **Funções e Modularização:** Separação de responsabilidades (ex: função de desenhar tela, função de atualizar física, função de gerar obstáculos).

## 🚀 | Como Executar o Jogo

Siga o passo a passo abaixo para baixar, configurar e jogar em sua máquina.

### 1. Pré-requisitos
Certifique-se de ter o **Python 3.x** instalado. Se não tiver, baixe no site oficial: [python.org](https://www.python.org/downloads/).

### 2. Baixando o Código
Você pode baixar o projeto de duas formas:

**Opção A: Usando Git (Recomendado)**
Abra seu terminal e execute:
```bash
# Clona o repositório para sua máquina
git clone https://github.com/GabrielCCrispim/Projeto-IP.git or 
          https://github.com/KayqueT/FlappyBara.git

# Entra na pasta do projeto
cd Projeto-IP








