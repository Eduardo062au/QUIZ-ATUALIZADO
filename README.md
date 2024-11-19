import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

// Classe para representar uma pergunta
class Pergunta {
    private String questao;
    private List<String> alternativas;
    private String respostaCorreta;

    public Pergunta(String questao, List<String> alternativas, String respostaCorreta) {
        this.questao = questao;
        this.alternativas = alternativas;
        this.respostaCorreta = respostaCorreta;
    }

    public String getQuestao() {
        return questao;
    }

    public List<String> getAlternativas() {
        return alternativas;
    }

    public String getRespostaCorreta() {
        return respostaCorreta;
    }
}

public class Quiz {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Apresentação do Quiz
        System.out.println("CENTRO UNIVERSITARIO ALFREDO NASSER");
        System.out.println();
        System.out.println("ALUNO: EDUARDO MARTINS");
        System.out.println();
        System.out.println("PROFESSOR: BRENNO PIMENTA");
        System.out.println();
        System.out.println("ATIVIDADE AVALIATIVA DE CONHECIMENTO HISTÓRICO GERAIS");
        System.out.println();
        System.out.println("NESTE QUESTIONÁRIO VOCÊ IRÁ RESPONDER 15 PERGUNTAS. É NECESSÁRIO DIGITAR O NÚMERO CORRESPONDENTE À ALTERNATIVA.");
        System.out.println();

        // Lista para armazenar as perguntas
        List<Pergunta> perguntas = new ArrayList<>();
        List<Pergunta> acertadas = new ArrayList<>();
        List<Pergunta> erradas = new ArrayList<>();

        // Adicionar perguntas
        perguntas.add(new Pergunta(
                "Qual é a civilização mais antiga do mundo?",
                List.of("Grécia", "Roma", "Winterfell", "Mesopotâmia", "Hogwarts"),
                "Mesopotâmia"
        ));

        perguntas.add(new Pergunta(
                "Em que ano começou a Primeira Guerra Mundial?",
                List.of("1914", "1918", "1939", "1945", "1899"),
                "1914"
        ));

        perguntas.add(new Pergunta(
                "Quem é o primeiro presidente dos Estados Unidos?",
                List.of("Obama", "Biden", "Bush", "Washington", "Trump"),
                "Washington"
        ));
        perguntas.add(new Pergunta(
                "A civilização asteca se originou de qual país??",
                List.of("Brasil", "México", "Peru", "Argentina", "Inglaterra"),
                "México"
        ));

        perguntas.add(new Pergunta(
                "Quem foi o primeiro homem a pisar na lua?",
                List.of("Yuri Gagarin", "Nicolau Flamel", "Alfred Worden", "Neil Armstrong", "Anatoli Berezovoy"),
                "Neil Armstrong"
        ));

        perguntas.add(new Pergunta(
                "Durante qual evento, a Coréia foi separada em 2 nações?",
                List.of("Segunda Guerra Mundial", "Primeira Guerra Mundial", "Guerra dos Bastardos", "Guerras Médicas", "Guerra de Troia"),
                "Segunda Guerra Mundial"
        ));

        perguntas.add(new Pergunta(
                "Qual é outro nome para a Grande Pirâmide do Egito?",
                List.of("Anúbis", "Gon", "Rá", "Jiro", "Gizé"),
                "Gizé"
        ));

        perguntas.add(new Pergunta(
                "Quem é o inventor da luz elétrica?",
                List.of("Albert Einstein", "Thomas Edison", "Nikola Tesla", "Marie Curie", "Charles Darwin"),
                "Thomas Edison"
        ));

        perguntas.add(new Pergunta(
                "Quando aconteceu a Guerra Fria?",
                List.of("1947-1991", "1912-1931", "1982-1998", "1960-1980", "1937-1959"),
                "1947-1991"
        ));

        perguntas.add(new Pergunta(
                "Em que oceano o Titanic afundou?",
                List.of("Oceano Antártico", "Oceano Ártico", "Oceano Índico", "Oceano Pacífico Norte", "Oceano Atlântico"),
                "Oceano Atlântico"
        ));

        perguntas.add(new Pergunta(
                "Quem fez o famoso discurso “Eu tenho um sonho”?",
                List.of("Martin Luther King Jr", "Abdias Nascimento", "Elaine Brown", "Malcom X", "Rosa Parks"),
                "Martin Luther King Jr"
        ));

        perguntas.add(new Pergunta(
                "Mona Lisa é uma pintura famosa de qual artista?",
                List.of("Rafael Sanzio", "Donato di Niccoló", "Leonardo Davinci", "Michelangelo di Lodovico", "Mestre Splinter"),
                "Leonardo Davinci"
        ));

        perguntas.add(new Pergunta(
                "Em qual cidade começou a Primeira Guerra Mundial?",
                List.of("Paris", "Sarajevo", "Istambul", "Berlim", "Mostar"),
                "Sarajevo"
        ));

        perguntas.add(new Pergunta(
                "Qual era o nome da agência de inteligência soviética?",
                List.of("ICBM", "DMZ", "SSI", "KGB", "DBZ"),
                "KGB"
        ));

        perguntas.add(new Pergunta(
                "Quanto tempo durou a guerra dos 100 anos?",
                List.of("100 anos", "116 anos", "95 anos", "103 anos", "99 anos"),
                "116 anos"
        ));


        // Contador de acertos
        int acertos = 0;

        // Iterar sobre as perguntas
        for (Pergunta pergunta : perguntas) {
            boolean respostaRegistrada = false;
            while (!respostaRegistrada) {
                // Exibir a pergunta
                System.out.println(pergunta.getQuestao());

                // Embaralhar alternativas
                List<String> alternativas = new ArrayList<>(pergunta.getAlternativas());
                Collections.shuffle(alternativas);

                // Exibir alternativas
                for (int i = 0; i < alternativas.size(); i++) {
                    System.out.println("[" + i + "] " + alternativas.get(i));
                }

                // Solicitar resposta do usuário
                System.out.print("Digite o número da sua resposta: ");
                String resposta = scanner.nextLine();

                try {
                    // Verificar a resposta
                    int respostaInt = Integer.parseInt(resposta);
                    if (respostaInt < 0 || respostaInt >= alternativas.size()) {
                        System.out.println("Número inválido. Tente novamente.");
                    } else {
                        String valorDaResposta = alternativas.get(respostaInt);
                        if (valorDaResposta.equals(pergunta.getRespostaCorreta())) {
                            System.out.println("Resposta correta!");
                            acertos++;
                            acertadas.add(pergunta);
                        } else {
                            System.out.println("Resposta errada! A resposta correta era: " + pergunta.getRespostaCorreta());
                            erradas.add(pergunta);
                        }
                        respostaRegistrada = true; // Passar para a próxima pergunta
                    }
                } catch (NumberFormatException e) {
                    System.out.println("Entrada inválida! Digite um número correspondente à alternativa.");
                }
            }
        }

        // Exibir resultados
        System.out.println("\nRESULTADOS DO QUIZ:");
        System.out.println("Você acertou " + acertos + " de " + perguntas.size() + " perguntas.");
        double porcentagem = (acertos / (double) perguntas.size()) * 100;
        System.out.println("Porcentagem de acertos: " + String.format("%.2f", porcentagem) + "%");

        // Mostrar perguntas acertadas
        System.out.println("\nPerguntas Acertadas:");
        for (Pergunta pergunta : acertadas) {
            System.out.println("- " + pergunta.getQuestao() + " (Resposta correta: " + pergunta.getRespostaCorreta() + ")");
        }

        // Mostrar perguntas erradas
        System.out.println("\nPerguntas Erradas:");
        for (Pergunta pergunta : erradas) {
            System.out.println("- " + pergunta.getQuestao() + " (Resposta correta: " + pergunta.getRespostaCorreta() + ")");
        }

        scanner.close();
    }
}
