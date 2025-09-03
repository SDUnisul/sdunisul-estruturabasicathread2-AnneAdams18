public class MisturaNumerosLetras {
    public static void main(String[] args) {
        // Thread para imprimir números de 1 a 5
        Thread numerosThread = new Thread(() -> {
            for (int i = 1; i <= 5; i++) {
                System.out.println("Número: " + i);
                try {
                    Thread.sleep(300);
                } catch (InterruptedException e) {
                    System.out.println("Thread de números foi interrompida.");
                }
            }
        });

        // Thread para imprimir letras de A a E
        Thread letrasThread = new Thread(() -> {
            for (char c = 'A'; c <= 'E'; c++) {
                System.out.println("Letra: " + c);
                try {
                    Thread.sleep(300);
                } catch (InterruptedException e) {
                    System.out.println("Thread de letras foi interrompida.");
                }
            }
        });

        // Iniciar as duas threads
        numerosThread.start();
        letrasThread.start();

        // Esperar as duas terminarem
        try {
            numerosThread.join();
            letrasThread.join();
        } catch (InterruptedException e) {
            System.out.println("Thread principal foi interrompida.");
        }

        // Mensagem final
        System.out.println("Execução finalizada!");
    }
}
