import java.util.Scanner;

public class MediaEscolar {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double[] notas = new double[8];

        System.out.println("=== Cadastro de Notas Anuais ===");
        for (int i = 0; i < 8; i++) {
            System.out.printf("Digite a nota %d: ", i + 1);
            notas[i] = scanner.nextDouble();
        }

        // Cálculo das médias bimestrais
        double[] mediasBimestrais = new double[4];
        for (int i = 0; i < 4; i++) {
            mediasBimestrais[i] = (notas[i * 2] + notas[i * 2 + 1]) / 2;
        }

        // Cálculo das médias semestrais
        double mediaSemestre1 = (notas[0] + notas[1] + notas[2] + notas[3]) / 4;
        double mediaSemestre2 = (notas[4] + notas[5] + notas[6] + notas[7]) / 4;

        // Cálculo da média final
        double somaTotal = 0;
        for (double nota : notas) {
            somaTotal += nota;
        }
        double mediaFinal = somaTotal / 8;

        // Apresentação dos resultados
        System.out.println("\n=== Resultados ===");
        for (int i = 0; i < 4; i++) {
            System.out.printf("Média do %dº bimestre: %.2f%n", i + 1, mediasBimestrais[i]);
        }
        System.out.printf("Média do 1º semestre: %.2f%n", mediaSemestre1);
        System.out.printf("Média do 2º semestre: %.2f%n", mediaSemestre2);
        System.out.printf("Média final: %.2f%n", mediaFinal);

        // Verificação da situação do aluno
        System.out.print("Situação: ");
        if (mediaFinal >= 6.0) {
            System.out.println("Aprovado :) ");
        } else if (mediaFinal >= 5.0) {
            System.out.println("Recuperação :/ ");
        } else {
            System.out.println("Reprovado :( ");
        }

        scanner.close();
    }
}

//  Aprovado: média final ≥ 7,0
//  Recuperação: média final entre 5,0 e 6,9
//  Reprovado: média final < 5,0
