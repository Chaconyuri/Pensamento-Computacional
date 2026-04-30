# DeliveryZão – Sistema de Entrega de Comida

## O que é esse projeto?

O DeliveryZão é um app simples pra pedir comida delivery. Você escolhe o restaurante, escolhe o que quer comer, faz o pedido e acompanha a entrega. Mais ou menos como aqueles apps de comida que todo mundo usa, mas bem mais simples.

---

## O problema que a gente quer resolver

Todo mundo já passou raiva pedindo comida por telefone, né? 
- O cara não entende o endereço
- Você não sabe se o pedido foi confirmado
- Não sabe quanto tempo demora
- O atendimento é confuso

A gente quer criar um sistema onde:
- O cliente vê o cardápio completo online
- Faz o pedido em poucos cliques
- Acompanha tudo em tempo real
- O restaurante recebe tudo certinho sem erro

---

## Quem usa o sistema?

| Tipo de usuário | O que faz |
|-----------------|-----------|
| **Cliente** | Escolhe comida, faz pedido, acompanha entrega, avalia |
| **Restaurante** | Cadastra cardápio, recebe pedidos, atualiza status |
| **Entregador** | Aceita corrida, pega pedido, entrega, marca como concluído |
| **Admin** | Gerencia tudo, vê relatórios, resolve problemas |

---

## Principais funcionalidades

### Pro cliente:
- Ver cardápio de vários restaurantes
- Filtrar por tipo de comida (pizza, burger, japonês...)
- Fazer pedido com poucos cliques
- Acompanhar o status (recebido → preparando → a caminho → entregue)
- Avaliar o pedido depois

### Pro restaurante:
- Cadastrar e editar cardápio
- Receber pedidos em tempo real
- Mudar status do pedido
- Ver histórico de vendas

### Pro entregador:
- Ver pedidos disponíveis
- Aceitar corrida
- Atualizar localização
- Marcar entrega como feita

---

## Desafios que a gente identificou

### 1. Muita gente pedindo ao mesmo tempo
**Problema:** Em horário de pico, milhares de pessoas podem estar pedindo ao mesmo tempo. O sistema não pode travar.

**Solução:** 
- Servidores que se adaptam sozinhos (auto scaling)
- Banco de dados que aguenta muita consulta
- Cache pro cardápio que não muda tanto

### 2. Localização em tempo real
**Problema:** O cliente quer saber onde está a comida. O entregador precisa mostrar onde está.

**Solução:**
- GPS atualizado a cada poucos segundos
- Mapa mostrando a posição do entregador
- Notificação quando muda de status

### 3. Segurança do pagamento
**Problema:** Muita gente não quer colocar cartão de crédito num app desconhecido.

**Solução:**
- Criptografia forte (aquele cadeado no endereço)
- Não guardar dados do cartão no sistema
- Opção de pagar na entrega

### 4. Integração com restaurantes
**Problema:** Cada restaurante tem um sistema diferente. Como conectar tudo?

**Solução:**
- API padronizada que todo mundo usa
- Adapter pra cada sistema específico

---

## Como o pensamento computacional ajuda

### Decomposição (dividir o problema)
A gente separou o sistema em partes menores:
- Cadastro de usuários
- Cardápio e produtos
- Pedido e pagamento
- Rastreamento
- Avaliações

Cada parte pode ser desenvolvida separada e depois integrada.

### Abstração (ignorar o que não importa)
A gente focou no essencial:
- O cliente só precisa ver o cardápio e fazer pedido
- O restaurante só precisa receber e confirmar
- O entregador só precisa aceitar e entregar

Não precisa de firula. Interface limpa e objetiva.

### Padrões (coisas que se repetem)
- Fluxo de pedido é sempre igual em qualquer restaurante
- Status segue uma sequência lógica
- Avaliação sempre no final

---

## Tecnologias que a gente pretende usar

| Parte | Tecnologia |
|-------|------------|
| Frontend | React ou Vue |
| Backend | Node.js ou Python |
| Banco de dados | PostgreSQL ou MongoDB |
| Cache | Redis |
| Maps | Google Maps API |
| Mensageria | RabbitMQ ou Kafka |

---

## Por que isso é "sistema de larga escala"?

Mesmo sendo mais simples que o original, ainda tem uns desafios de escala:
- Milhares de pedidos por dia
- Centenas de restaurantes simultâneos
- Dezenas de entregadores ativos
- Dados de localização o tempo todo

É um bom exercício pra aprender como lidar com volume grande de gente usando o sistema ao mesmo tempo.

---

## Próximos passos

- [ ] Definir as funcionalidades mínimas (MVP)
- [ ] Desenhar o banco de dados
- [ ] Criar a API
- [ ] Fazer o frontend básico
- [ ] Testar com poucos usuários

---

*Projeto desenvolvido como exercício de pensamento computacional para sistemas de larga escala.*