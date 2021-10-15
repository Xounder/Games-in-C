//Memory Game


#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>
#include<locale.h>
#include<time.h>
int pontos1 = 0, pontos2 = 0, pontos3 = 0;
char Nome1[7], Nome2[7], Nome3[7];
void InicSair(){
    void GeraValor(int val, int *p1, int *p2, int *p3, char *n1[], char *n2[], char *n3[]);
    int Dificuldade();
    void Pontuacao(int p1, int p2, int p3, char n1[], char n2[], char n3[]);
    bool escolha = false;
    int dificuldade = 3, opcoes = 0;
    char choose;

    while(escolha == false){
        if(opcoes == 0){
        printf("\nIniciar");
        printf("\nDificuldade");
        printf("\nPontuação");
        printf("\nSair <-");

        choose = getch();
        fflush(stdin);
        if(choose == 'w' || choose == 'W'){
        opcoes++;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
                escolha = true;
                system("cls");
                printf("\tObrigado por jogar :D\n");
                return 0;
        }
        }else if (opcoes == 1){
           printf("\nIniciar");
            printf("\nDificuldade");
            printf("\nPontuação <-");
            printf("\nSair");

            choose = getch();
            fflush(stdin);

         if(choose == 'w' || choose == 'W'){
        opcoes++;
        choose = 'a';
        }
          if(choose == 's' || choose == 'S'){
        opcoes--;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
             Pontuacao(pontos1, pontos2, pontos3, Nome1, Nome2, Nome3);
            }

        }else if (opcoes == 2){
           printf("\nIniciar");
            printf("\nDificuldade <-");
            printf("\nPontuação");
            printf("\nSair");

            choose = getch();
            fflush(stdin);

         if(choose == 'w' || choose == 'W'){
        opcoes++;
        choose = 'a';
        }
          if(choose == 's' || choose == 'S'){
        opcoes--;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
                dificuldade = Dificuldade();
            }

        }else if (opcoes == 3){
           printf("\nIniciar <-");
            printf("\nDificuldade");
            printf("\nPontuação");
            printf("\nSair");
            choose = getch();
            fflush(stdin);
          if(choose == 's' || choose == 'S'){
        opcoes--;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
                GeraValor(dificuldade, &pontos1, &pontos2, &pontos3, &Nome1, &Nome2, &Nome3);
            }
        }
        system("cls");
    }
}
int CompValor(int valor1[], int valor2[], int val1){
    int cont=0, i, j, vetAux[10];
    for(i = 0; i < val1; i++)
        vetAux[i] = valor1[i];
    for(i = 0; i < val1; i++){
            for(j = 0; j < val1; j++){
        if(vetAux[i] == valor2[j]){
            vetAux[i] =- 1;
            cont++;
        }
        }
    }
    return cont;
}
void GeraValor(int val, int *p1, int *p2, int *p3, char *n1[], char *n2[], char *n3[]){
    int CompValor(int valor1[], int valor2[], int val1);
    void CompPontuacao(int pnts, int *p1, int *p2, int *p3, char *n1[], char *n2[], char *n3[]);
    void InicSair();
    int Aleat[10], PlyValor[10], i, pnts, rtrnComp;
    char espera, salva;
    bool chave = false;
    system("cls");
    printf("\n\n\n");
    for(i = 0; i < val; i++){
        Aleat[i] = (rand() % 100);
        printf("\t%d   ",Aleat[i]);
    }
    sleep(3);
    system("cls");
    printf("\nQuais são os valores?\n");
    for(i = 0; i < val; i++){
       scanf("%d", &PlyValor[i]);
    }
    pnts= CompValor(Aleat, PlyValor, val);
    printf("\nVocê acertou: %d\n", pnts);
    printf("\nOs valores reais:\n");
   for(i = 0; i < val; i++){
        printf("%d  ", Aleat[i]);
    }
    CompPontuacao(pnts, p1, p2, p3, n1, n2, n3);
    sleep(2);

        while(chave == false){
        printf("\nDeseja continuar jogando na mesma dificuldade? S/N? ");
    espera = getch();
    if(espera == 'S' || espera == 's'){
        GeraValor(val, &pontos1, &pontos2, &pontos3, &Nome1, &Nome2, &Nome3);
        return 0;
    }else if(espera == 'N' || espera == 'n'){
        chave = true;
        return 0;
    }
        }

}
int Dificuldade(){
    int opcoes = 0;
    char choose;
    bool escolha = false;
    system("cls");
    while(escolha == false){
        if(opcoes == 0){
        printf("\nEscolha a Dificuldade:\n");
        printf("\nFácil <-       3 números");
        printf("\nMédio");
        printf("\nDifícil");

        choose = getch();
         fflush(stdin);
        if(choose == 's' || choose == 'S'){
        opcoes++;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
                escolha = true;
                return 3;
        }
        }else if (opcoes == 1){
            printf("\nEscolha a Dificuldade:\n");
           printf("\nFácil");
            printf("\nMédio <-      5 números");
            printf("\nDifícil");

            choose = getch();
            fflush(stdin);

         if(choose == 's' || choose == 'S'){
        opcoes++;
        choose = 'a';
        }
          if(choose == 'w' || choose == 'W'){
        opcoes--;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
            escolha = true;
               return 5;
            }

        }else if (opcoes == 2){
            printf("\nEscolha a Dificuldade:\n");
           printf("\nFácil");
            printf("\nMédio");
            printf("\nDifícil <-    10 números");
            choose=getch();
            fflush(stdin);
          if(choose == 'w' || choose == 'W'){
        opcoes--;
        choose = 'a';
        }
            if(choose == 'x' || choose == 'X'){
                return 10;
            }
        }
        system("cls");
    }

    }
void CompPontuacao(int pnts, int *p1,int *p2, int *p3, char *n1[7], char *n2[7], char *n3[7]){
    if(pnts>*p1){
             *p1 = pnts;
            printf("\n\nParabéns você quebrou um recorde!!!\n");
        printf("\nColoque seu nome: ");
            scanf("%s", n1);
    }else if(pnts > *p2){
        *p2 = pnts;
        printf("\nParabéns você quebrou um recorde!!!\n");
        printf("\nColoque seu nome: ");
            scanf("%s", n2);
    }else if(pnts > *p3){
        *p3 = pnts;
        printf("\nParabéns você quebrou um recorde!!!\n");
        printf("\nColoque seu nome: ");
            scanf("%s", n3);
    }
}
void Pontuacao(int p1, int p2, int p3, char n1[], char n2[], char n3[]){
    void InicSair();
    system("cls");
    for(int i = 0; i < 25; i++)
        printf("=");
    printf("\n\tSCORE\n");
    for(int i = 0; i < 25; i++)
        printf("=");
        printf("\n%d ----------------- %s\n", p1, n1);
        printf("\n%d ----------------- %s\n", p2, n2);
        printf("\n%d ----------------- %s\n", p3, n3);

    printf("\nEspere 5s para voltar ao menu...");
    sleep(3);
    system("cls");
    return 0;

}
int main(){
    setlocale(LC_ALL,"");
    srand(time(NULL));
    printf("\nBem vindo!\n");
    printf("Pressione W para ir para cima\nPressione S para ir para baixo\nX para Confirmar");
    sleep(2);
    system("cls");
    InicSair();
return 0;
}
