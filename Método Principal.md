    package jokenpoExercicio;
    import java.util.Scanner;
    import java.util.Random;
    /**
     *
     * @author Taina Soares Carvalho
     */
    public class JokenpoExercicio {
        public static boolean apenasNumeros(String cadeia){
            boolean teste = cadeia.matches("[0-9]+");
            return teste;
        }
    
        public static String sorteio(){
            Random random = new Random();
            int aux = random.nextInt(3);
            String sortSystem= null, jokenpo[] = {"", "Pedra", "Papel", "Tesoura"};
            if(aux == 3){
                sortSystem = jokenpo[aux];
            }else{
                sortSystem = jokenpo[aux+1];
            }
            return sortSystem;
        }

        public static String resultado(int escUsuario, String escUser, String escSistema){
            String res = "", jokenpo[] = {"Tesoura", "Pedra", "Papel"};
            int length = jokenpo.length;
            if(escSistema.equals(escUser)){
                res = "Deu empate!";
            }else{
                for (int i = 0; i < length; i++) {
                    if(escUsuario == i){
                        if(escSistema.equals(jokenpo[i])){
                            res = "Você ganhou!";
                        }else{
                            res = "Você perdeu!";
                        }
                        break;
                    }
                }
            }
            return res;
        }

        public static void main(String[] args) {
            Scanner leia = new Scanner(System.in);
            String escUsuario = null, aux, escSystem = sorteio(), jokenpo[] = {"Pedra", "Papel", "Tesoura"};
            int esc;
            System.out.println("------------------ SEJA BEM-VINDO AO JOKENPO! ------------------\n");
            System.out.println("Escolha uma das seguintes opções:\n0) Pedra\n1) Papel\n2) Tesoura");
            aux = leia.next();
            if(!apenasNumeros(aux)){
                System.err.println("Digite apenas números!!");
                System.exit(0);
            }
            esc = Integer.parseInt(aux);
            if(esc < 0 || esc > 2){
                System.err.println("Digite uma opção válida!!");
                System.exit(0);
            }
            escUsuario = jokenpo[esc];
            System.out.println("Você escolheu "+escUsuario+".\nO Sistema escolheu: "+escSystem);
            System.out.println("\n"+resultado(esc, escUsuario, escSystem));
        }
    }
