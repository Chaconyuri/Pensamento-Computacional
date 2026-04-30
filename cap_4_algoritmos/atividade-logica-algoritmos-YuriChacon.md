# Controle de Acesso - Sala de Aula

**Aluno:** Yuri Chacon  
**Matéria:** Lógica e Algoritmos

---

## Algoritmo

```
INÍCIO
    lista ← ["Ana Clara", "Bruno Costa", "Carlos Eduardo", "Yuri Chacon", "Emily", "Felipe", "Gabriela", "Henrique", "Isabella", "João Pedro"]
    fila ← ["Yuri Chacon", "Maria Eduarda", "Ana Clara", "Pedro Henrique", "Carlos Eduardo"]
    
    PARA cada nome EM fila FAÇA
        SE nome ESTÁ EM lista ENTÃO
            ESCREVER nome, " - OK"
        SENÃO
            ESCREVER nome, " - NEGADO"
        FIMSE
    FIMPARA
FIM
```

---

## Explicação

1. **Lista** = alunos matriculados
2. **Fila** = alunos que querem entrar
3. **Para cada** aluno na fila, verifica se está na lista
4. Se estiver → OK, se não → NEGADO