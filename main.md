import java.util.Scanner;

public class SistemaBancario {
	protected  double saldo1;

	public SistemaBancario(double SaldoInicial) {
		this.saldo1 = SaldoInicial;
	}

	public void depositar1(double valor) {
		saldo1 += valor;
		System.out.println("Depósito de R$ " + valor + " realizado");
	}

	public void sacar(double valor) {
		if (valor <= saldo1) {
			
			saldo1 -= valor;
			System.out.printf("Saque de R$" + valor + " realizado.");

		} else {
			System.out.println("Saldo insuficiênte.");

		}

	}

	public double getSaldo1() {
		return saldo1;
	}

	public static void main(String[] args) {
		try (Scanner scanner = new Scanner(System.in)) {
			
			ContaCorrente contaCorrente = new ContaCorrente(0);
			ContaPoupanca contaPoupanca = new ContaPoupanca(0);
			
			char opcao;

			do {
				System.out.println("\n" + "**SISTEMA BANCÁRIO**");
				System.out.println("\n" + "Oque deseja realizar?");
				System.out.println("1. depositar -- Poupança");
				System.out.println("2. Sacar -- Poupança");
				System.out.println("3. depositar -- Corrente");
				System.out.println("4. Sacar -- Corrente");
				System.out.println("5. Consulta valores");
				System.out.println("0. Sair");
				opcao = scanner.next().charAt(0);

				switch (opcao) {

				case '1':
					System.out.printf("Valor deposito em conta poupança:");
					double depositoCP = scanner.nextDouble();
					contaPoupanca.depositar1(depositoCP);
					break;

				case '2':
					System.out.println("\n" + "Valor saque em conta poupança:");
					double saqueCP = scanner.nextDouble();
					contaPoupanca.sacar(saqueCP);
					break;

				case '3':
					System.out.printf("Valor deposito em conta Corrente:");
					double depositoCC = scanner.nextDouble();
					contaCorrente.depositar1(depositoCC);
					break;

				case '4':
					System.out.println("\n" + "Valor saque em conta Corrente:");
					double saqueCC = scanner.nextDouble();
					contaCorrente.sacar(saqueCC);
					break;
					
				case '5':

	                System.out.println("Conta Poupança: R$ "
	                        + contaPoupanca.getSaldo1());
	                
					   System.out.println("\nConta Corrente: R$ "
		                        + contaCorrente.getSaldo1());

					break;

				case '0':
					System.out.println("Encerrando ...");
					break;
					
					default:
						System.out.println("Opção invalida");
				}

			} while (opcao != '0');
		}

	}

}
