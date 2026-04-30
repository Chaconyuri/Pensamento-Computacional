# Desafios – DeliveryZão

Aqui a gente lista os principais problemas que vamos enfrentar e como a gente pensa em resolver cada um. Tudo em linguagem simples!

---

## 1. Muita gente usando ao mesmo tempo

### O problema

Imagina numa sexta-feira à noite. Todo mundo pedindo pizza, hamburger, japonês... Miles de pedidos ao mesmo tempo. Se o sistema não aguentar, vai travar e todo mundo fica sem comida.

### Como resolver

| Estratégia | O que é | Pra que serve |
|------------|---------|---------------|
| **Load Balancer** | Distribui as requisições entre vários servidores | Nenhum servidor sobrecarrega |
| **Auto Scaling** | Cria mais servidores quando precisa | Cresce junto com a demanda |
| **Cache** | Salva dados que não mudam muito | Não precisa consultar o banco o tempo todo |
| **Conexão Pool** | Conexões de banco pré-abertas | Acelera consulta ao banco |

**Como fica:
```
Usuário → Load Balancer → Servidor 1
                      → Servidor 2
                      → Servidor 3
```

---

## 2. Localização em tempo real

### O problema

O cliente quer saber "onde está minha comida?". Precisa mostrar no mapa a posição do entregador em tempo real.

### Como resolver

- GPS do celular do entregador mandando posição a cada 5 segundos
- Mapa que atualiza automaticamente
- Notificação push quando muda de status

**Como fica:
```
Entregador (GPS) → Servidor → Mapa do Cliente
```

---

## 3. Segurança do pagamento

### O problema

Ninguém quer colocar cartão de crédito num app desconhecido. Se vazar os dados, ferrou.

### Como resolver

| Medida | O que faz |
|--------|-----------|
| **Criptografia** | Transforma os dados em código impossível de ler |
| **Não guardar cartão** | Usa gateway de pagamento (PagSeguro, Mercado Pago) |
| **HTTPS** | Conexão segura o tempo todo |
| **Tokenização** | O cartão vira um token, não dados reais |
| **Rate limiting** | Bloqueia tentativas de ataque |

### Princípios de segurança (Saltzer & Schroeder)

- **Negar por padrão** – Se não tem permissão, não entra
- **Mínimo privilégio** – Cada um só vê o que precisa
- **Verificar sempre** – Checar permissão em cada requisição

---

## 4. Integração com restaurantes

### O problema

Cada restaurante tem um sistema diferente. Como fazer o nosso app conversar com todos?

### Como resolver

- **API padronizada** – Todo mundo usa o mesmo formato
- **Adapter pattern** – Tradutor pro sistema de cada restaurante
- **Filas de mensagem** – Pedido chega sem travar o sistema

**Como fica:
```
App → Fila de Mensagens → Adapter → Sistema do Restaurante
```

---

## 5. Consistência dos dados

### O problema

Se o pedido foi confirmado mas o pagamento deu errado, o que acontece? Os dados precisam estar sempre coerentes.

### Como resolver

- **Transações** – Tudo ou nada (ou paga tudo ou não salva nada)
- **Eventos** – Registrar cada mudança de estado
- **Retry automático** – Se der erro, tenta de novo

---

## 6. Monitoramento

### O problema

Como saber se o sistema está funcionando? Se der problema, como descobrir o que foi?

### Como resolver

| Ferramenta | Pra que serve |
|------------|---------------|
| **Prometheus** | Coleta métricas (quantos pedidos, tempo de resposta) |
| **Grafana** | Mostra gráficos bonitinhos |
| **Logs** | Registro de tudo que acontece |
| **Alertas** | Avisa quando algo fica lento ou cai |

---

## 7. Tabela de riscos

| Risco | O que pode acontecer | Como resolver |
|-------|---------------------|---------------|
| Sistema lento | Cliente desiste de pedir | Cache + Auto scaling |
| Dados vazados | Problema巨大 com cliente | Criptografia forte |
| Integração falha | Pedido não chega no restaurante | Retry + Circuit breaker |
| Servidor cai | Ninguém consegue pedir | Múltiplas regiões |

---

## Próximos passos

- [ ] Fazer o banco de dados
- [ ] Criar a API básica
- [ ] Testar com poucos usuários
- [ ] Medir performance

---

*Desafios do projeto DeliveryZão – linguagem simples!*