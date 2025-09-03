public class MensagemRunnable implements Runnable {

    private final String mensagem;

    public MensagemRunnable(String mensagem) {
        this.mensagem = mensagem;
    }

    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(mensagem);
            try {
                Thread.sleep(700); // pausa de 700ms
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                System.err.println("Thread interrompida: " + e.getMessage());
                break;
            }
        }
    }

    public static void main(String[] args) {
        Thread t1 = new Thread(new MensagemRunnable("Olá do Runnable 1"));
        Thread t2 = new Thread(new MensagemRunnable("Olá do Runnable 2"));

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
            System.err.println("Main thread interrompida: " + e.getMessage());
        }

        System.out.println("Execução finalizada.");
    }
}
