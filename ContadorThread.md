public class ContadorThread extends Thread {
    private String nome;

    public ContadorThread(String nome) {
        this.nome = nome;
    }

    @Override
    public void run() {
        for (int i = 1; i <= 10; i++) {
            System.out.println(nome + ": " + i);
            try {
                Thread.sleep(500); // pausa de 500 milissegundos
            } catch (InterruptedException e) {
                System.out.println(nome + " foi interrompida.");
            }
        }
    }

    public static void main(String[] args) {
        // Cria duas instâncias da thread
        ContadorThread thread1 = new ContadorThread("Thread 1");
        ContadorThread thread2 = new ContadorThread("Thread 2");

        // Inicia as duas threads
        thread1.start();
        thread2.start();
    }
}
