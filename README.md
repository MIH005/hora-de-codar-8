
# Sistema de Caixa Eletrônico 🚀

Bem-vindo ao sistema de Caixa Eletrônico desenvolvido em **Java**! Este sistema possui funcionalidades básicas e avançadas para gerenciamento de contas, saldo, transferências e mais. Ele foi projetado para oferecer uma experiência de aprendizado prática e divertida. 😊

---

## Funcionalidades Implementadas 🛠️

1. **Saudação personalizada**: 
   - Ao iniciar, o sistema pergunta o nome do usuário e exibe uma mensagem de boas-vindas.
   
2. **Criação de contas**: 
   - Permite criar contas novas com um número personalizado.

3. **Consulta de saldo**: 
   - Exibe o saldo atual da conta do usuário.

4. **Extrato de transações**: 
   - Exibe um histórico detalhado de saques, depósitos e transferências.

5. **Saque de dinheiro**:
   - Validações:
     - O valor não pode ser igual ou menor que zero.
     - O saldo restante não pode ser negativo.

6. **Depósito de dinheiro**:
   - Validações:
     - O valor do depósito não pode ser igual ou menor que zero.

7. **Transferência de dinheiro**:
   - Validações:
     - O número da conta deve conter apenas dígitos.
     - O valor da transferência não pode ser maior que o saldo disponível.
     - O valor não pode ser igual ou menor que zero.

8. **Validação de senha**:
   - A senha padrão é `3589`. Operações como saldo, saque, extrato e transferência exigem autenticação.

9. **Menu principal organizado**:
   - Opções exibidas em ordem lógica: Criar Conta, Saldo, Extrato, Saque, Depósito, Transferência e Sair.

10. **Mensagem de saída personalizada**:
    - Ao sair, uma mensagem de despedida personalizada é exibida.

---

## Fluxo de Uso 💡

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

### Exemplo de Saudação:
```plaintext
Informe seu nome: João
Olá João, é um prazer ter você por aqui!
```

### Validação de Senha:
```plaintext
Informe sua senha: 
Senha incorreta. Tente novamente.
```

### Exemplo de Mensagem de Saída:
```plaintext
João, foi um prazer ter você por aqui!
```

---

## Código Fonte 📂

```
import java.util.ArrayList;
import java.util.Scanner;

public class CaixaEletronico {

    static Scanner scanner = new Scanner(System.in);
    static String nomeUsuario;
    static double saldo = 1000.00; // Saldo inicial fictício
    static String senhaCorreta = "3589";
    static ArrayList<String> extrato = new ArrayList<>();
    static ArrayList<String> contas = new ArrayList<>();

    public static void main(String[] args) {
        // Inicializa contas fictícias
        contas.add("12345");
        contas.add("67890");

        System.out.print("Informe seu nome: ");
        nomeUsuario = scanner.nextLine();
        System.out.println("Olá " + nomeUsuario + ", é um prazer ter você por aqui!");

        int opcao;
        do {
            exibirMenu();
            opcao = scanner.nextInt();
            scanner.nextLine(); // Limpar buffer
            switch (opcao) {
                case 1 -> criarConta();
                case 2 -> consultarSaldo();
                case 3 -> exibirExtrato();
                case 4 -> sacarDinheiro();
                case 5 -> depositarDinheiro();
                case 6 -> transferirDinheiro();
                case 7 -> sair();
                default -> System.out.println("Opção inválida. Tente novamente.");
            }
        } while (opcao != 7);
    }

    public static void exibirMenu() {
        System.out.println("\n--- Menu Principal ---");
        System.out.println("1. Criar Conta");
        System.out.println("2. Saldo");
        System.out.println("3. Extrato");
        System.out.println("4. Saque");
        System.out.println("5. Depósito");
        System.out.println("6. Transferência");
        System.out.println("7. Sair");
        System.out.print("Escolha uma opção: ");
    }

    public static void criarConta() {
        System.out.print("Informe o número da nova conta: ");
        String novaConta = scanner.nextLine();
        contas.add(novaConta);
        System.out.println("Conta " + novaConta + " criada com sucesso!");
    }

    public static void consultarSaldo() {
        if (validarSenha()) {
            System.out.println("Seu saldo atual é: R$" + saldo);
        }
    }

    public static void exibirExtrato() {
        if (validarSenha()) {
            System.out.println("\n--- Extrato ---");
            if (extrato.isEmpty()) {
                System.out.println("Nenhuma movimentação encontrada.");
            } else {
                for (String transacao : extrato) {
                    System.out.println(transacao);
                }
            }
        }
    }

    public static void sacarDinheiro() {
        if (validarSenha()) {
            System.out.print("Informe o valor do saque: R$");
            double valor = scanner.nextDouble();

            if (valor <= 0) {
                System.out.println("Operação não autorizada: valor inválido.");
            } else if (valor > saldo) {
                System.out.println("Operação não autorizada: saldo insuficiente.");
            } else {
                saldo -= valor;
                extrato.add("Saque: -R$" + valor);
                System.out.println("Saque de R$" + valor + " realizado com sucesso!");
            }
        }
    }

    public static void depositarDinheiro() {
        System.out.print("Informe o valor do depósito: R$");
        double valor = scanner.nextDouble();

        if (valor <= 0) {
            System.out.println("Operação não autorizada: valor inválido.");
        } else {
            saldo += valor;
            extrato.add("Depósito: +R$" + valor);
            System.out.println("Depósito de R$" + valor + " realizado com sucesso!");
        }
    }

    public static void transferirDinheiro() {
        if (validarSenha()) {
            System.out.print("Informe o número da conta de destino: ");
            String contaDestino = scanner.nextLine();

            if (!contaDestino.matches("\\d+")) {
                System.out.println("Operação não autorizada: número de conta inválido.");
                return;
            }

            System.out.print("Informe o valor da transferência: R$");
            double valor = scanner.nextDouble();

            if (valor <= 0) {
                System.out.println("Operação não autorizada: valor inválido.");
            } else if (valor > saldo) {
                System.out.println("Operação não autorizada: saldo insuficiente.");
            } else {
                saldo -= valor;
                extrato.add("Transferência para conta " + contaDestino + ": -R$" + valor);
                System.out.println("Transferência de R$" + valor + " para a conta " + contaDestino + " realizada com sucesso!");
            }
        }
    }

    public static boolean validarSenha() {
        System.out.print("Informe sua senha: ");
        String senha = scanner.nextLine();

        if (!senha.equals(senhaCorreta)) {
            System.out.println("Senha incorreta. Tente novamente.");
            return false;
        }
        return true;
    }

    public static void sair() {
        System.out.println(nomeUsuario + ", foi um prazer ter você por aqui!");
    }
}

```

---

## Como Executar o Projeto? ▶️

1. Certifique-se de ter o **Java JDK** instalado na sua máquina.
2. Copie o arquivo `CaixaEletronico.java` para o seu ambiente de desenvolvimento.
3. Compile o código com o comando:
   ```bash
   javac CaixaEletronico.java
   ```
4. Execute o programa com:
   ```bash
   java CaixaEletronico
   ```

---
