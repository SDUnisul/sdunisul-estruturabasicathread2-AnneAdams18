public class CorredorThread extends Thread {
    private String nome;

    public CorredorThread(String nome) {
        this.nome = nome;
    }

    @Override
    public void run() {
        for (int i = 10; i <= 100; i += 10) {
            System.out.println(nome + " percorreu " + i + " metros");
            try {
                Thread.sleep(400); // espera 400ms entre cada "passo"
            } catch (InterruptedException e) {
                System.out.println(nome + " foi interrompido.");
            }
        }
        System.out.println(nome + " terminou a corrida!");
    }

    public static void main(String[] args) {
        // Criando 3 corredores
        CorredorThread corredor1 = new CorredorThread("Corredor 1");
        CorredorThread corredor2 = new CorredorThread("Corredor 2");
        CorredorThread corredor3 = new CorredorThread("Corredor 3");

        // Iniciando as threads
        corredor1.start();
        corredor2.start();
        corredor3.start();

        // Esperando todas as threads terminarem
        try {
            corredor1.join();
            corredor2.join();
            corredor3.join();
        } catch (InterruptedException e) {
            System.out.println("A thread principal foi interrompida.");
        }

        // Mensagem final
        System.out.println("Corrida finalizada!");
    }
}
