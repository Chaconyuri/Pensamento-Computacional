# Atividade Individual – Pensamento Computacional

---

## Parte 1: Reflexão sobre Pensamento Computacional

### 1. Definição de Pensamento Computacional

**Pensamento Computacional** nada mais é do que uma forma de pensar organizada para resolver problemas. É tipo quando você quebra uma tarefa grande em partes menores, ou quando percebe que algo que você faz sempre se repete e pode ser automatizado.

Basicamente, são 4 jeitos de olhar para um problema:
- **Decomposição** = dividir para conquistar
- **Reconhecimento de padrões** = perceber o que se repete
- **Abstração** = focar no que importa e ignorar o resto
- **Algoritmo** = criar uma receita passo a passo

**Por que isso é útil no dia a dia?**
- Quando você precisa resolver algo complexo, consegue pensar de forma mais clara
- Ajuda a tomar decisões melhores porque você analisa o problema todo
- Você consegue ver soluções que talvez não visse de outra forma
- Serve para qualquer coisa, não só para computador

---

### 2. Exemplo real de Pensamento Computacional

**Situação:** Montar um lanche para vender na cantina da escola.

**Como organizei meu raciocínio:**

1. **Decomposição:** Pensei em cada etapa separada:
   - O que preciso comprar?
   - Como preparar cada coisa?
   - Quanto tempo leva?
   - Como organizar a venda?

2. **Reconhecimento de padrões:** Percebi que todo dia era a mesma coisa:
   - Sempre vendia mais no intervalo da manhã
   - Os alunos queriam algo rápido
   - Sanduíche natural era o mais pedido

3. **Abstração:** Deixei de lado detalhes que não importavam:
   - Não precisei pensar na cor da toalha da mesa
   - Ignorei se o fornecedor era bonito ou não
   - Só me importei com preço, qualidade e prazo de entrega

4. **Algoritmo:** Criei um passo a passo:
   - Verificar o que tenho em estoque
   - Fazer lista de compras
   - Preparar os sanduíches de manhã
   - Colocar à venda no horário do intervalo
   - Guardar o que sobrou na geladeira

---

## Parte 2: Resolução de Problema

### Cenário: Sistema de organização do refeitório escolar

---

### 1. Decomposição: Principais problemas a resolver

Quando a gente olha para o problema do refeitório, consegue identificar várias coisas que estão erradas. Vou listar as principais:

| # | Problema | O que acontece |
|---|----------|----------------|
| 1 | **Muita gente ao mesmo tempo** | Na hora do recreio, todo mundo quer ir comer junto. Fila enorme, gente sem lugar para sentar |
| 2 | **Comida que sobra e é jogada fora** | Como não sabe quantos vão comer, a escola faz comida demais e joga o que não usa no lixo |
| 3 | **Ninguém controla quem entra** | O aluno entra quando quer, na hora que quer. Não tem regra |
| 4 | **Demora demais** | Por causa da fila, o aluno passa o tempo todo esperando e pouco tempo comendo |
| 5 | **Não consegue planejar** | Sem saber quantos vêm por dia, não tem como melhorar o sistema |

---

### 2. Reconhecimento de padrões

**Isso acontece em outros lugares?**

Sim! Esse problema de fila e organização aparece em vários lugares do dia a dia:

| Onde | Como resolvem | O que a gente aprende |
|------|---------------|----------------------|
| **Restaurante self-service** | Tem faixa de horário, às vezes precisa esperar senha | Controlar o fluxo de pessoas por tempo |
| **Banco** | Senha virtual, chamam por número | Não precisa ficar na fila física |
| **Supermercado** | Caixa rápido para quem tem pouca coisa | Quem tem menos necessidade vai mais rápido |
| **Parque de diversões** | Comprar ingresso com horário marcado | Limita a quantidade de pessoas por vez |
| **Metrô** | Catraca que só deixa passar de um em um | Controla acesso por capacidade |

**O que dessas ideias pode funcionar na escola?**
- Usar senha ou senha virtual (como no banco)
- Dividir os alunos por horário (como no restaurante)
- Colocar um sistema que mostre quantas pessoas podem entrar ao mesmo tempo

---

### 3. Abstração: Simplificando o problema

Para resolver, a gente precisa saber o que é importante e o que pode ignorar.

**O que importa:**
- Quantos alunos cabem no refeitório de uma vez
- Quais são os horários de aula (para saber quando podem ir)
- Quanto tempo o aluno fica comendo em média
- Quantas séries/anos tem na escola

**O que não importa:**
- Se o aluno gosta de arroz ou feijão
- Se a mesa é de madeira ou plástico
- Como o aluno se chama (só precisa saber qual turno ele é)
- Se o refeitório tem decoration bonita ou não

**Resumindo o problema:**
```
Entrada: Aluno quer entrar
Processo: Verificar se tem vaga e se é a hora certa
Saída: Deixa entrar ou diz para voltar no horário certo
```

---

### 4. Algoritmo: Passo a passo da solução

Vou explicar como o sistema funcionaria na prática:

```
PASSO A PASSO:

1. DIVIDIR EM TURNOS
   - Separar os alunos em grupos (A, B, C, D)
   - Cada grupo tem um horário certo para ir

2. CADASTRAR TODO MUNDO
   - Anotar qual turno cada série/turma pertence
   - Pode usar cartão, pulseira ou até celular

3. NO DIA A DIA
   - O aluno chega no refeitório
   - Bater o cartão ou mostrar o código
   - O sistema olha:
     → "Esse aluno é do turno A?"
     → "Agora é hora do turno A?"
     → "Ainda tem vaga?"
   - Se tudo SIM → entra e o sistema anota
   - Se algo NÃO → mostra mensagem e diz o que fazer

4. CONTROLE DE VAGA
   - Mostra na tela quantos entraram e quantos podem entrar
   - Quando encher, fecha a porta até alguém sair

5. FIM DO DIA
   - Mostra quantos comeram
   - Ajuda a planejar o próximo dia
```

**Como funciona na prática:**
- O aluno chega no refeitório
- Passa o cartão ou mostra o código no celular
- O sistema verifica se é a hora certa e se tem vaga
- Se tudo ok, ele entra e o sistema conta mais um
- Se não for a hora, mostra na tela qual é o horário certo

---

## Parte 3: Reflexão Final
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  Aluno      │───>│  Leitor     │───>│  Sistema    │
│  apresenta  │    │  QR Code    │    │  verifica   │
│  cartão     │    │             │    │  turno/vaga │
└─────────────┘    └─────────────┘    └─────────────┘
                                              │
                    ┌───────────┐             │
                    │  LIBERAR  │<────────────┤
                    │  ACESSO   │             │
                    └───────────┘             ▼
                                         ┌─────────────┐
                                         │  REGISTRAR  │
                                         │  ENTRADA    │
                                         └─────────────┘
```

---

## Parte 3: Reflexão Final

### 1. Como o Pensamento Computacional ajudou a estruturar a solução

Usar o Pensamento Computacional facilitou muito porque:

- **Decomposição**: Consegui olhar cada problema separado. A fila é um problema, o desperdício é outro, a falta de controle é mais um. Assim fica mais fácil resolver cada um
- **Reconhecimento de padrões**: Pude ver que outros lugares já tiveram esse problema e resolveram. Não preciso inventar do zero
- **Abstração**: Deixei o problema mais simples. Ignorei o que não importa e foquei no que realmente precisa ser resolvido
- **Algoritmo**: Criei um passo a passo que qualquer um consegue seguir

**No fim:** Uma solução que faz sentido, que pode ser explicada para qualquer pessoa e que realmente resolve o problema.

---

### 2. Parte mais desafiadora e melhorias

**O que foi mais difícil:**
- **Abstração**: É difícil saber o que pode ignorar e o que não pode. Se você tira demais, a solução não funciona. Se deixa demais, complica demais
- **Equilíbrio**: Achar o meio termo entre algo simples de implementar e algo que resolva tudo

**O que daria para melhorar:**
- Usar um aplicativo no celular dos alunos
- Colocar uma tela mostrando quanto tempo de fila falta
- Estudar os dados para prever quantos vão venir em cada dia
- Pensar em alunos que têm necessidades especiais

---

### 3. Onde mais isso pode ser usado?

Esse jeito de pensar serve para muita coisa no dia a dia:

| Situação | Como aplicar |
|----------|--------------|
| **Fazer uma receita** | Dividir em etapas (decomposição), perceber que sempre segue o mesmo passo (padrão), focar no essencial (abstração), seguir o passo a passo (algoritmo) |
| **Organizar as finanças** | Ver onde gastou (padrão), separar gastos fixos dos variáveis (decomposição), focar no que dá para controlar (abstração) |
| **Estudar para prova** | Dividir o conteúdo em partes (decomposição), ver o que mais cai (padrão), focar no mais importante (abstração), fazer um plano de estudos (algoritmo) |
| **Planejar uma viagem** | Listar o que precisa (decomposição), ver melhores preços (padrão), definir o orçamento (abstração), organizar o itinerary (algoritmo) |
| **Organizar o quarto** | Separar por tipo de coisa (decomposição), perceber que sempre guarda no mesmo lugar (padrão), decidir o que doar (abstração), criar rotina de organização (algoritmo) |
| **Fazer compras do mês** | Listar o que precisa (decomposição), comparar preços (padrão), definir quanto pode gastar (abstração), fazer a lista em ordem de prioridade (algoritmo) |

---

## Conclusão

Pensamento Computacional não é coisa de nerd ou de quem programa computador. É um jeito de pensar que ajuda a resolver qualquer problema, desde organizar uma festa até resolver um problema no trabalho.

Quando você aprende a dividir, perceber padrões, simplificar e criar passos, qualquer coisa fica mais fácil de resolver.

---

*Atividade desenvolvida como parte do curso de Pensamento Computacional*
*Centro Universitário do Distrito Federal - UDF*