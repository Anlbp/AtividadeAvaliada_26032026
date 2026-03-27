# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: *André Luís Bertelli Pena*  
RA: *24000057*  
Data: *26/03/2026*  

---

# 1. Definição do MVP

> Meu MVP cobre o processo de venda, pesquisa de produtos, verificação de estoque, cadastro de clientes e finalização da venda com emissão de comprovante. Decidi atingir o mínimo, sem encher linguiça. O template foi utilizado fielmente, sem mudanças na estrutura original

- O que está **dentro** do MVP: vendas, clientes, produtos, verificação de estoque e contas a receber  
- O que está **fora** do MVP: compras, contas a serem pagas, relatórios avançados e gestão de fornecedores  
- Por que você fez essas escolhas: A venda é o processo principal da farmácia, conectando várias partes do sistema  

---

# 2. Regras de Negócio (mínimo: 5)

**RN01 —** Não pode vender produtos com estoque nulo (0)  
**RN02 —** Atualização automática do estoque depois da venda  
**RN03 —** Vendas a prazo devem criar uma conta a receber  
**RN04 —** Clientes devem estar cadastrados para compras a prazo  
**RN05 —** Produtos controlados exigem validação do farmaceutico  

---

# 3. Requisitos Funcionais (mínimo: 8)

**RF01 —** Pesquisa de produtos por nome ou código  
**RF02 —** Registro de vendas  
**RF03 —** Verificação do estoque antes da venda  
**RF04 —** Cadastro de clientes  
**RF05 —** Emissão do comprovante de venda  
**RF06 —** Registro de vendas a prazo  
**RF07 —** Criar contas a receber automaticamente  
**RF08 —** Atualizar estoque depois de cada venda  

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)

**RNF01 —** Sistema eficientemente responsivo (resposta até 2 segundos) 
**RNF02 —** Segurança garantida com login e senha  
**RNF03 —** Disponibilidade em horário comercial  
**RNF04 —** Facilidade de uso 

---

# 5. Casos de Uso (mínimo: 10)

### Casos:
- UC01: Fazer login  
- UC02: Pesquisar produto  
- UC03: Verificar estoque  
- UC04: Cadastrar cliente  
- UC05: Registrar venda  
- UC06: Finalizar venda  
- UC07: Emitir comprovante  
- UC08: Registrar venda a prazo  
- UC09: Criar conta a receber  
- UC10: Validar receita  

### Includes:
- Registrar Venda **include** Pesquisar produto  
- Registrar Venda **include** Verificar estoque  
- Finalizar Venda **include** Emitir comprovante  

### Extends:
- Cadastrar Cliente **extend** Registrar venda  
- Registrar Venda a Prazo **extend** Finalizar venda  
- Validar Receita **extend** Registrar venda  

---

# 6. Documentação dos Casos de Uso

## UC01 — Login
**Ator(es):** Usuário  
**Descrição:** Permite acesso ao sistema  
**Pré-condições:** Usuário cadastrado  
**Pós-condições:** Usuário autenticado  

### Fluxo Principal
1. Usuário coloca login  
2. Usuário coloca senha  
3. Sistema valida dados  
4. Sistema libera acesso  

### Fluxos Alternativos / Exceções
- FA01 — Dados inválidos/incompletos  

### Relacionamentos
- **Include:**    
- **Extend:**

<img width="324" height="312" alt="image" src="https://github.com/user-attachments/assets/3743e8c5-36df-4541-8958-02064de916ee" />

---

## UC02 — Pesquisar Produto
**Ator(es):** Atendente farmaceutico 
**Descrição:** Permite encontrar produtos
**Pré-condições:** Sistema online  
**Pós-condições:** Produto exibido  

### Fluxo Principal
1. Usuário coloca nome ou código  
2. Sistema exibe resultados  

### Fluxos Alternativos / Exceções
- FA01 — Produto não encontrado  

### Relacionamentos
- **Include:**    
- **Extend:**

<img width="347" height="257" alt="image" src="https://github.com/user-attachments/assets/25a3bc3a-087c-4ca1-9238-bb7b9f3a843c" />

---

## UC03 — Verificação Estoque
**Ator(es):** Sistema  
**Descrição:** Confere quantidade disponivel  
**Pré-condições:** Produto selecionado  
**Pós-condições:** Estoque exibido  

### Fluxo Principal
1. Sistema consulta estoque  
2. Sistema retorna quantidade  

### Fluxos Alternativos / Exceções
- FA01 — Estoque insuficiente  

### Relacionamentos
- **Include:**    
- **Extend:**    

<img width="330" height="257" alt="image" src="https://github.com/user-attachments/assets/49b2065e-8aad-40a9-bef8-a8f38d5551f0" />

---

## UC04 — Cadastrar Cliente
**Ator(es):** Atendente farmaceutico
**Descrição:** Registra novo cliente  
**Pré-condições:** Cliente sem cadastro
**Pós-condições:** Cliente salvo  

### Fluxo Principal
1. Usuário coloca dados  
2. Sistema salva cliente  

### Fluxos Alternativos / Exceções
- FA01 — Dados inválidos/incompletos 

### Relacionamentos
- **Include:**    
- **Extend:** Registrar venda  

<img width="308" height="257" alt="image" src="https://github.com/user-attachments/assets/0c298dbb-474e-499b-95c4-eee8c63bd9f5" />

---

## UC05 — Registrar Venda
**Ator(es):** Atendente farmaceutico
**Descrição:** Inicializa venda  
**Pré-condições:** Produto disponivel  
**Pós-condições:** Venda registrada  

### Fluxo Principal
1. Pesquisar produto  
2. Verificar estoque  
3. Adicionar item  

### Fluxos Alternativos / Exceções
- FA01 — Produto indisponivel  

### Relacionamentos
- **Include:** Pesquisa Produto, Verifica estoque  
- **Extend:** Valida receita

<img width="359" height="312" alt="image" src="https://github.com/user-attachments/assets/8df664da-bc8e-4fac-a737-d18cc609bc0c" />

---

## UC06 — Finalizar Venda
**Ator(es):** Atendente farmaceutico
**Descrição:** Conclui venda  
**Pré-condições:** Itens adicionados  
**Pós-condições:** Venda finalizada  

### Fluxo Principal
1. Confirmar pagamento  
2. Finalizar operação  

### Fluxos Alternativos / Exceções
- FA01 — Falha no pagamento  

### Relacionamentos
- **Include:** Emitir comprovante  
- **Extend:** Registrar venda a prazo

<img width="307" height="257" alt="image" src="https://github.com/user-attachments/assets/d6e9071f-d5aa-4ab2-8630-e194617235e3" />

---

## UC07 — Emitir Comprovante
**Ator(es):** Sistema  
**Descrição:** Emite comprovante  
**Pré-condições:** Venda finalizada  
**Pós-condições:** Comprovante emitido  

### Fluxo Principal
1. Sistema emite comprovante  

### Fluxos Alternativos / Exceções
- FA01 — Erro na emissão  

### Relacionamentos
- **Include:**    
- **Extend:**
   
<img width="255" height="257" alt="image" src="https://github.com/user-attachments/assets/3f372f8d-58a9-4c53-8caa-bc8bf7c5b786" />

---

## UC08 — Registrar Venda a Prazo
**Ator(es):** Atendente farmaceutico
**Descrição:** Venda com pagamento futuro  
**Pré-condições:** Cliente cadastrado  
**Pós-condições:** Conta criada 

### Fluxo Principal
1. Selecionar pagamento a prazo  
2. Confirmar venda  

### Fluxos Alternativos / Exceções
- FA01 — Cliente sem cadastro  

### Relacionamentos
- **Include:** Criar Conta a Receber  
- **Extend:** Finalizar Venda

<img width="366" height="312" alt="image" src="https://github.com/user-attachments/assets/cb446a0a-e8d1-46b4-bb58-2d90fdd471af" />

---

## UC09 — Criar Conta a Receber
**Ator(es):** Sistema  
**Descrição:** Registra dívida do cliente  
**Pré-condições:** Venda a prazo  
**Pós-condições:** Conta criada  

### Fluxo Principal
1. Sistema cria conta  
2. Define vencimento  

### Fluxos Alternativos / Exceções
- FA01 — Erro no registro  

### Relacionamentos
- **Include:**    
- **Extend:**

<img width="245" height="257" alt="image" src="https://github.com/user-attachments/assets/a13cd81c-4161-42e9-bf17-3d422ba314dc" />
  
---

## UC10 — Validar Receita
**Ator(es):** Farmaceutico  
**Descrição:** Autoriza venda controlada  
**Pré-condições:** Produto controlado  
**Pós-condições:** Venda autorizada  

### Fluxo Principal
1. Farmaceutico analisa receita  
2. Aprova venda  

### Fluxos Alternativos / Exceções
- FA01 — Receita inválida/incompleta 

### Relacionamentos
- **Include:**    
- **Extend:** Registrar Venda

<img width="235" height="257" alt="image" src="https://github.com/user-attachments/assets/2022bd68-955d-4774-807b-08d5cf7186c7" />

---
