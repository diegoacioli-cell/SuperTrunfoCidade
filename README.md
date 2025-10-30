#include <stdio.h>
#include <string.h>

typedef struct {
    char nome[30];
    char estado[30];
    int populacao;
    float area;
    float pib;
    char ponto_turistico[50];
} Cidade;

int main() {
    Cidade recife = {"Recife", "Pernambuco", 1600000, 218.5, 65.0, "Marco Zero"};
    Cidade salvador = {"Salvador", "Bahia", 2900000, 692.8, 82.0, "Pelourinho"};
    int escolha;

    printf("===== SUPER TRUNFO DAS CIDADES =====\n\n");
    printf("Carta 1: %s (%s)\n", recife.nome, recife.estado);
    printf("Populacao: %d habitantes\n", recife.populacao);
    printf("Area: %.1f km²\n", recife.area);
    printf("PIB: R$ %.1f bilhões\n", recife.pib);
    printf("Ponto turistico: %s\n\n", recife.ponto_turistico);

    printf("Carta 2: %s (%s)\n", salvador.nome, salvador.estado);
    printf("Populacao: %d habitantes\n", salvador.populacao);
    printf("Area: %.1f km²\n", salvador.area);
    printf("PIB: R$ %.1f bilhões\n", salvador.pib);
    printf("Ponto turistico: %s\n\n", salvador.ponto_turistico);

    printf("Escolha o atributo para comparar:\n");
    printf("1 - População\n");
    printf("2 - Área\n");
    printf("3 - PIB\n");
    printf("4 - Índice Super Trunfo (PIB / Área)\n");
    printf("Opção: ");
    scanf("%d", &escolha);

    printf("\n===== RESULTADO =====\n");

    switch(escolha) {
        case 1:
            if(recife.populacao > salvador.populacao)
                printf("%s venceu! (%d vs %d)\n", recife.nome, recife.populacao, salvador.populacao);
            else if(salvador.populacao > recife.populacao)
                printf("%s venceu! (%d vs %d)\n", salvador.nome, salvador.populacao, recife.populacao);
            else
                printf("Empate na população!\n");
            break;

        case 2:
            if(recife.area > salvador.area)
                printf("%s venceu! (%.1f km² vs %.1f km²)\n", recife.nome, recife.area, salvador.area);
            else if(salvador.area > recife.area)
                printf("%s venceu! (%.1f km² vs %.1f km²)\n", salvador.nome, salvador.area, recife.area);
            else
                printf("Empate na área!\n");
            break;

        case 3:
            if(recife.pib > salvador.pib)
                printf("%s venceu! (R$ %.1f bi vs R$ %.1f bi)\n", recife.nome, recife.pib, salvador.pib);
            else if(salvador.pib > recife.pib)
                printf("%s venceu! (R$ %.1f bi vs R$ %.1f bi)\n", salvador.nome, salvador.pib, recife.pib);
            else
                printf("Empate no PIB!\n");
            break;

        case 4: {
            float indiceRecife = recife.pib / recife.area;
            float indiceSalvador = salvador.pib / salvador.area;
            printf("Índice Recife: %.3f\n", indiceRecife);
            printf("Índice Salvador: %.3f\n", indiceSalvador);

            if(indiceRecife > indiceSalvador)
                printf("\nRecife venceu no índice Super Trunfo!\n");
            else if(indiceSalvador > indiceRecife)
                printf("\nSalvador venceu no índice Super Trunfo!\n");
            else
                printf("\nEmpate no índice Super Trunfo!\n");
            break;
        }

        default:
            printf("Opção inválida!\n");
    }

    printf("\nPontos turísticos: %s (Recife) vs %s (Salvador)\n",
           recife.ponto_turistico, salvador.ponto_turistico);

    printf("\n===== FIM DO JOGO =====\n");
    return 0;
}
