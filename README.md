# hora-de-codar-8

# 💳 Caixa Eletrônico em Java

Bem-vindo ao sistema de **Caixa Eletrônico**! Este projeto simula operações bancárias básicas, como saques, depósitos, transferências e consulta de saldo. Além disso, possui uma interface simples de menu para interação com o usuário, incluindo mensagens personalizadas e validações de segurança.

---

## 📋 Funcionalidades

1. **Saudação Inicial**  
   - Ao acessar o sistema, o usuário informa seu nome e recebe uma mensagem personalizada:  
     _"Olá {Nome}, é um prazer ter você por aqui!"_

2. **Menu Principal**  
   - Opções disponíveis:
     1. Criar Conta  
     2. Saldo  
     3. Extrato  
     4. Saque  
     5. Depósito  
     6. Transferência  
     7. Sair  

3. **Validação de Senha**  
   - Para realizar operações como consultar saldo, saque, extrato ou transferência, o sistema solicita uma senha (padrão: `3589`).  
   - Se a senha for incorreta, o sistema solicita novamente antes de prosseguir.

4. **Criação de Contas**  
   - O usuário pode criar novas contas informando um número exclusivo.

5. **Consulta de Saldo**  
   - Permite verificar o saldo atual da conta, desde que a senha esteja correta.

6. **Exibição do Extrato**  
   - Exibe um histórico das transações realizadas, como saques, depósitos e transferências.

7. **Saques com Validação**  
   - Não permite:
     - Saques maiores que o saldo disponível.
     - Valores iguais ou menores que zero.

8. **Depósitos com Validação**  
   - Não permite:
     - Depósitos com valores iguais ou menores que zero.

9. **Transferências com Validação**  
   - Permite transferir para qualquer número de conta (desde que seja numérico).  
   - Não permite:
     - Transferências maiores que o saldo disponível.
     - Valores iguais ou menores que zero.

10. **Mensagem de Despedida**  
    - Ao sair, o sistema exibe:  
      _"{Nome}, foi um prazer ter você por aqui!"_

---

## 🛠️ Tecnologias Utilizadas

- **Java**: Linguagem principal do projeto.
- **Scanner**: Para leitura de entrada do usuário.
- **ArrayList**: Para armazenar contas e histórico do extrato.

---

## 🚀 Como Executar o Sistema

1. Clone este repositório em sua máquina:
   ```bash
   git clone https://github.com/seu-usuario/caixa-eletronico-java.git
   ```
2. Navegue até o diretório do projeto:
   ```bash
   cd caixa-eletronico-java
   ```
3. Compile o arquivo principal:
   ```bash
   javac CaixaEletronico.java
   ```
4. Execute o programa:
   ```bash
   java CaixaEletronico
   ```

---

## 📂 Estrutura do Projeto

```plaintext
├── CaixaEletronico.java    # Arquivo principal do sistema
├── README.md               # Documentação do projeto
```

---

## 🔐 Regras e Validações

- **Senha padrão**: `3589` (para operações críticas).
- Operações não permitidas:
  - Saques ou transferências com valores maiores que o saldo disponível.
  - Depósitos, saques ou transferências com valores iguais ou menores que zero.
  - Transferências para contas com caracteres inválidos.

---

## 📝 Exemplo de Execução

### Menu Principal:
```plaintext
--- Menu Principal ---
1. Criar Conta
2. Saldo
3. Extrato
4. Saque
5. Depósito
6. Transferência
7. Sair
Escolha uma opção: 
```

### Saudação:
```plaintext
Informe seu nome: João
Olá João, é um prazer ter você por aqui!
```

### Operações com Validação:
```plaintext
Informe sua senha: 1234
Senha incorreta. Tente novamente.

Informe sua senha: 3589
Seu saldo atual é: R$1000.0
```

### Mensagem ao Sair:
```plaintext
João, foi um prazer ter você por aqui!
```

---
