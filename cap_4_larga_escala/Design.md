# Design – DeliveryZão

## Visão Geral

Aqui a gente explica como o sistema foi pensado usando pensamento computacional. Vou explicar de um jeito simples como a gente dividiu o problema, o que a gente ignorou (abstração) e que padrões se repetem.

---

## 1. Decomposição – Dividir pra Conquistar

O sistema grande foi dividido em partes menores que dá pra lidar:

### 1.1 Módulos Principais

| Módulo | O que faz | Quem usa |
|--------|-----------|----------|
| **Cadastro** | Cria conta de cliente, restaurante, entregador | Todos |
| **Cardápio** | Mostra as comidas, preços, fotos | Cliente |
| **Pedido** | Faz o pedido, calcula total, envia pro restaurante | Cliente |
| **Cozinha** | Recebe pedido, marca como preparando, pronto | Restaurante |
| **Entrega** | Entregador aceita, rastreia, entrega | Entregador |
| **Pagamento** | Processa pagamento, confirma | Cliente |
| **Avaliação** | Cliente dá nota e comentário | Cliente |

### 1.2细分 (submódulos)

**Cadastro:**
- Login/Senha
- Dados pessoais (nome, telefone, endereço)
- Tipo de usuário (cliente, restaurante, entregador)

**Cardápio:**
- Lista de produtos
- Preços
- Fotos
- Categorias (pizza, burger, japonês...)

**Pedido:**
- Escolher produtos
- Definir quantidade
- Calcular total
- Escolher endereço
- Confirmar

---

## 2. Abstração – O Essencial

A gente pensou no que realmente importa e ignorou o resto:

### 2.1 O que o cliente precisa ver

```
┌─────────────────┐
│  Cardápio       │  ← Só mostra o que dá pra pedir
│  - Pratos       │
│  - Preços       │
│  - Fotos        │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Carrinho       │  ← Mostra o que escolheu
│  - Items        │
│  - Total        │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Confirmar      │  ← Pedido pronto
│  - Endereço     │
│  - Pagamento    │
└─────────────────┘
```

### 2.2 Camadas do sistema

1. **Interface (o que o usuário vê)**
   - App mobile ou site
   - Botões, listas, mapas

2. **Regras do negócio (lógica)**
   - Calcular preço
   - Validar pedido
   - Atualizar status

3. **Dados (onde salva)**
   - Banco de dados
   - Cache

---

## 3. Padrões – Coisas que Sempre Se Repetem

### 3.1 Fluxo de pedido

Todo pedido segue o mesmo caminho:

```
Cliente faz pedido → Restaurante recebe → Preparando → Pronto →
Entregador pega → A caminho → Entregue → Cliente avalia
```

Isso é um padrão! A gente pode criar um código que serve pra qualquer restaurante.

### 3.2 Status do pedido

| Status | Significa |
|--------|-----------|
| PENDENTE | Acabou de fazer |
| CONFIRMADO | Restaurante viu |
| PREPARANDO | Está fazendo |
| PRONTO | Já pode buscar |
| EM_ROTA | Entregador a caminho |
| ENTREGUE | Chegou no cliente |
| CANCELADO | Algo deu errado |

### 3.3 Padrão de avaliação

Sempre depois de entregue, o cliente pode avaliar:
- Nota de 1 a 5
- Comentário opcional

---

## 4. Modelo de Dados Simplificado

```
┌──────────────┐       ┌──────────────┐
│   Cliente    │       │ Restaurante  │
├──────────────┤       ├──────────────┤
│ - id         │       │ - id         │
│ - nome       │       │ - nome       │
│ - telefone   │       │ - endereço   │
│ - endereço   │       │ - cardápio   │
└──────┬───────┘       └──────────────┘
       │                      │
       │ 1:N                  │ 1:N
       ▼                      ▼
┌──────────────┐       ┌──────────────┐
│   Pedido     │       │  Produto    │
├──────────────┤       ├──────────────┤
│ - id         │       │ - id         │
│ - cliente_id │       │ - nome       │
│ - status    │       │ - preço      │
│ - total      │       │ - foto       │
│ - created_at│       └──────────────┘
└──────────────┘
       │
       │ N:N
       ▼
┌──────────────┐       ┌──────────────┐
│ItemPedido    │       │  Entregador │
├──────────────┤       ├──────────────┤
│ - produto_id │       │ - id         │
│ - quantidade │       │ - nome       │
│ - preco      │       │ - telefone   │
└──────────────┘       │ - status    │
                       └──────────────┘
```

---

## 5. Tecnologias

A gente ainda não definiu tudo, mas a ideia é:

- **Frontend:** React ou Vue (mais rápido de fazer)
- **Backend:** Node.js (mesma linguagem do front)
- **Banco:** PostgreSQL (dados confiáveis)
- **Cache:** Redis (pra não sobrecarregar)
- **Maps:** Google Maps (ou OpenStreetMap)

---

*Seção de design do projeto DeliveryZão*

| Padrão | Aplicação | Benefício |
|--------|-----------|-----------|
| **MVC** | Separação UI/Controller/Model | Manutenibilidade |
| **Repository** | Abstração de acesso a dados | Flexibilidade |
| **Factory** | Criação de objetos complexos | Baixo acoplamento |
| **Observer** | Notificações em tempo real | Atualização reativa |

### 3.2 Padrões de Interface

- **Login:** Padrão similar a sistemas bancários com validação em tempo real
- **Notas:** Estrutura inspirada em LMS (Blackboard, Moodle)
- **Dashboard:** Layout padrão de painéis analíticos

### 3.3 Padrões de Segurança

- Criptografia de senhas (bcrypt)
- Tokens JWT para autenticação
- Rate limiting em APIs
- Sanitização de inputs

---

## 4. Algoritmos Principais

### 4.1 Cálculo de Médias

```
Função calcularMedia(notas):
    soma = 0
    pesoTotal = 0
    
    Para cada nota em notas:
        soma += nota.valor * nota.peso
        pesoTotal += nota.peso
    
    Se pesoTotal > 0:
        Retornar soma / pesoTotal
    Senão:
        Retornar 0
```

### 4.2 Sistema de Recomendação

```
Função recomendarDisciplinas(aluno, historico):
    disciplinasSugeridas = []
    
    Para cada disciplina em disciplinasDisponiveis:
        pontuacao = 0
        
        // Baseado em área de interesse
        Se disciplina.area IN aluno.areasInteresse:
            pontuacao += 30
        
        // Baseado em desempenho em disciplinas relacionadas
        Se disciplina.preRequisitos IN historico.aprovadas:
            pontuacao += 40
        
        // Baseado em carga horária disponível
        Se aluno.cargaHorariaDisponivel >= disciplina.carga:
            pontuacao += 20
        
        Se pontuacao >= 50:
            adicionar(disciplinasSugeridas, disciplina)
    
    Ordenar(disciplinasSugeridas, por pontuacao decrescente)
    Retornar top 5 de disciplinasSugeridas
```

---

## 5. Decisões de Design

### 5.1 Tecnologias Selecionadas

- **Frontend:** React.js
- **Backend:** Node.js com Express
- **Banco de Dados:** PostgreSQL
- **Cache:** Redis
- **Mensageria:** RabbitMQ

### 5.2 Justificativas

| Tecnologia | Razão da Escolha |
|------------|------------------|
| React.js | Componentização, reatividade, comunidade ativa |
| Node.js | JavaScript full-stack, I/O não-bloqueante |
| PostgreSQL | Dados relacionais, ACID, escalabilidade |
| Redis | Cache de alta performance, sessões |
| RabbitMQ | Filas assíncronas, desacoplamento |

---

## 6. Considerações de Escalabilidade

### 6.1 Estratégias

- **Horizontal Scaling:** Load balancer para distribuir requisições
- **Database Sharding:** Particionamento de dados por tenant
- **Caching:** Redis para dados frequentemente acessados
- **CDN:** Entrega de assets estáticos

### 6.2 Métricas Alvo

| Métrica | Meta |
|---------|------|
| Tempo de resposta | < 200ms |
| Uptime | 99.9% |
| Usuários simultâneos | 10.000+ |
| Requisições/dia | 1M+ |

---

> **Nota:** Este documento deve ser atualizado conforme o projeto evolui.