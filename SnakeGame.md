//Snake Game


#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <locale.h>
#include <time.h>
#include <conio2.h>
#include <string.h>
struct desenho{											//Estrutura que contem as posições (x,y)
    int x, y;
};
void draw(struct desenho ply,int *randx,int *randy,int *placar, int *tamanho){
	srand(time(NULL));
	int x,y;
	system("color 01");
	for(x=0;x<80;x++){									//Mapa do jogo para as dificuldades Fácil e Médio
		for(y=0;y<29;y++){
			if(x==1 || x==79 && y){
				gotoxy(x,y);
				textbackground(BLUE);
				printf(" ");
			}
		if(y==1 && x){
				gotoxy(x,y);
				textbackground(BLUE);
				printf(" ");
			}
			if(y==28 && x){
				gotoxy(x,y);
				textbackground(BLUE);
				printf(" ");
			}
		}
	}
		
	
	if(ply.x==*randx && ply.y==*randy){      				//Alimento da Cobrinha
	
		textbackground(BLUE+WHITE);
		textcolor(WHITE);
	*randx=(rand() % 77);
	*randy=(rand() % 27);
	(*placar)++;
	
	if((*placar)%1==0 && *tamanho>0 && *tamanho<120 ){
		(*tamanho)++;
	}
	
	if(*randx==0){
		(*randx)+=2;
	}
	if(*randx==1){
		(*randx)++;
	}
	if(*randy==0){
		(*randy)+=2;
	}
	if(*randy==1){
		(*randy)++;
	}
		gotoxy(*randx,*randy);
	printf(".");
	}else{
		
		if(*randx==0){
		(*randx)+=2;
	}
	if(*randx==1){
		(*randx)++;
	}
	if(*randy==0){
		(*randy)+=2;
	}
	if(*randy==1){
		(*randy)++;
	}
		gotoxy(*randx,*randy);
		textbackground(BLUE+WHITE);
		textcolor(WHITE);
	printf(".");
	}													
}

void drawDificil(struct desenho ply,int *randx,int *randy,int *placar, int *tamanho){
	srand(time(NULL));
	int x,y;
	system("color 01");
	for(x=0;x<40;x++){									//Mapa do jogo para a dificuldade Difícil
		for(y=0;y<20;y++){
			if(x==1 || x==39 && y){
				gotoxy(x,y);
				textbackground(BLUE);
				printf(" ");
			}
		if(y==1 && x){
				gotoxy(x,y);
				textbackground(BLUE);
				printf(" ");
			}
			if(y==19 && x){
				gotoxy(x,y);
				textbackground(BLUE);
				printf(" ");
			}
		}
	}

		
	
	if(ply.x==*randx && ply.y==*randy){    			  //Alimento da Cobrinha
	
		textbackground(BLUE+WHITE);
		textcolor(WHITE);
		*randx=(rand() % 38);
		*randy=(rand() % 18);
	(*placar)++;
	
	if((*placar)%1==0 && *tamanho>0 && *tamanho<120 ){
		(*tamanho)++;
	}

	if(*randx==0){
		(*randx)+=2;
	}else if(*randx==1){
		(*randx)++;
	}
	if(*randy==0){
		(*randy)+=2;
	}else if(*randy==1){
		(*randy)++;
	}

		gotoxy(*randx,*randy);
	printf(".");
	}else{
		if(*randx>38){
		*randx=(rand() % 38);
	}	
	if(*randy>18){
		*randy=(rand() % 18);
	}
		if(*randx==0){
		(*randx)+=2;
	}
	if(*randx==1){
		(*randx)++;
	}
	if(*randy==0){
		(*randy)+=2;
	}
	if(*randy==1){
		(*randy)++;
	}
	
		gotoxy(*randx,*randy);
		textbackground(BLUE+WHITE);
		textcolor(WHITE);
	printf(".");
	}												
	
}
void Pintar_Cobra(struct desenho ply,struct desenho *PCobra[],int *tamanho, int *placar){
	int i,AuxX=0,AuxY=0,AuxX1=0,AuxY1=0, Xgo, Ygo;
	
		
	
	for(i=0;i<*tamanho;i++){
		if(i==0){									

		
		AuxX=((*PCobra)[i].x);						//Pega um novo valor de posição (x,y) 
		AuxY=((*PCobra)[i].y);						
		((*PCobra)[i].x)=ply.x;						
		((*PCobra)[i].y)=ply.y;						//Desenha a cobra e transfere os valores (x,y) anteriores da cobra
		
		}else if(i % 2!=0 && i!=0){

		
		AuxX1=((*PCobra)[i].x);
		AuxY1=((*PCobra)[i].y);
		((*PCobra)[i].x)=AuxX;
		((*PCobra)[i].y)=AuxY;
		}else if(i % 2==0 && i!=0){

		
		AuxX=((*PCobra)[i].x);
		AuxY=((*PCobra)[i].y);
		((*PCobra)[i].x)=AuxX1;
		((*PCobra)[i].y)=AuxY1;
		
		}

	textbackground(RED);
	Xgo=((*PCobra)[i].x);
	Ygo=((*PCobra)[i].y);
	
	gotoxy(Xgo,Ygo);					//Pinta a Cobrinha
	printf(" ");
	
}

}
bool CompCobra(struct desenho *PCobra[], int *tamanho, int dificuldade){
	int i,x,y;

	
	for(i=1;i<*tamanho;i++){
		if (((*PCobra)[0].x)==((*PCobra)[i].x) && ((*PCobra)[0].y)==((*PCobra)[i].y) ){
			return true;
	}
}

	if(dificuldade==3){													//Verifica se os valores de posição da Cobra-cabeça são iguais
		for(x=0;x<80;x++){												//aos valores do limite do mapa ou da propria cobra	
		for(y=0;y<29;y++){												
			 if(((*PCobra)[0].x)==1 && ((*PCobra)[0].y)>0 ){			
			return true;
		}else if(((*PCobra)[0].x)==39 && ((*PCobra)[0].y)>0 ){
			return true;
		}else if(((*PCobra)[0].y)==1 && ((*PCobra)[0].x)>0 ){
			return true;
		}else if (((*PCobra)[0].y)==19 && ((*PCobra)[0].x)>0 ){
			return true;
		}else{
			return false;
		}
	}
}
	}else{
		for(x=0;x<80;x++){									
		for(y=0;y<29;y++){
			 if(((*PCobra)[0].x)==1 && ((*PCobra)[0].y)>0 ){
			return true;
		}else if(((*PCobra)[0].x)==79 && ((*PCobra)[0].y)>0 ){
			return true;
		}else if(((*PCobra)[0].y)==1 && ((*PCobra)[0].x)>0 ){
			return true;
		}else if (((*PCobra)[0].y)==28 && ((*PCobra)[0].x)>0 ){
			return true;
		}else{
			return false;
		}
		}
	}
}
}

void VoltaCobra(struct desenho *ply){
		int i,x,y;
		
			 if(((*ply).x)<=1 && ((*ply).y)>0){			//Utilizada para fazer a cobra passar de um lado para o outro da tela na dificuldade - Fácil
			((*ply).x)=79;									
		}else if(((*ply).x)>=79 && ((*ply).y)>0){
			((*ply).x)=1;
		}else if(((*ply).y)<=1 && ((*ply).x)>0 ){
			((*ply).y)=28;
		}else if (((*ply).y)>=28 && ((*ply).x)>0){
			((*ply).y)=1;
	
		}
	}

void Jogo(struct desenho ply,struct desenho *PCobra[],int *randx,int *randy, int *placar, int *tamanho, int dificuldade){
	
		void draw(struct desenho ply,int *randx,int *randy, int *placar, int *tamanho);
		void Pintar_Cobra(struct desenho ply,struct desenho *PCobra[],int *tamanho, int *placar);
		bool CompCobra(struct desenho *PCobra[], int *tamanho, int dificuldade);
		
		void VoltaCobra(struct desenho *ply);
		
		void drawDificil(struct desenho ply,int *randx,int *randy,int *placar, int *tamanho);
		
		char tecla='a',plytecla;
			bool chave=false;
			
		if (dificuldade<3){
			draw(ply,randx,randy,placar,tamanho);
		Pintar_Cobra(ply,PCobra,tamanho,placar);
	}else{
		ply.x=15;
		ply.y=15;
		drawDificil(ply,randx,randy,placar,tamanho);
		Pintar_Cobra(ply,PCobra,tamanho,placar);
	}
		
		
		while(chave==false){
	
	if(kbhit()){
		plytecla=getch();
											//No Médio e no Difícil se uma tecla for apertada, a tecla oposta é desabilitada (Ex: 'a' e 'd')
		if(dificuldade>1){
			if(plytecla=='a' && tecla=='d' ||plytecla=='d' && tecla=='a'||plytecla=='w' && tecla=='s'||plytecla=='s' && tecla=='w'){
			tecla = tecla;
			}else {
			tecla=plytecla;
			} 
		}else{
			tecla=plytecla;
		}
	
			switch (tecla){				//Movimento
			case 'a':
		
			(ply.x--);
			break;
			
			case 'd':
		
			(ply.x++);
			break;
			
			case 'w':
		
			(ply.y--);
		
			break;
			case 's':
		
			(ply.y++);
			break;
			
			case 'l':
			chave=true;
			break;
	}
	
	gotoxy(2,1);
	printf("Pontuação: %d",*placar);
	if(dificuldade==1){
			draw(ply,randx,randy,placar,tamanho);
			Pintar_Cobra(ply,PCobra,tamanho,placar);
			textbackground(BLUE);
			printf("\n");
		VoltaCobra(&ply);
	
		sleep(0,95);
	}else if(dificuldade==2){
			draw(ply,randx,randy,placar,tamanho);
			Pintar_Cobra(ply,PCobra,tamanho,placar);
			textbackground(BLUE);
			printf("\n");
	chave=CompCobra(PCobra,tamanho, dificuldade);
	sleep(0,6);
	}else if (dificuldade==3){
		drawDificil(ply,randx,randy,placar,tamanho);
		Pintar_Cobra(ply,PCobra,tamanho,placar);
			textbackground(BLUE);
			printf("\n");
	chave=CompCobra(PCobra,tamanho, dificuldade);
		sleep(0,2);
	}
}else{
	switch (tecla){        		 //Movimento contínuo da tecla apertada
			case 'a':
			(ply.x--);
			break;
			
			case 'd':
			(ply.x++);
			break;
			
			case 'w':
			(ply.y--);
			break;
			
			case 's':
			(ply.y++);
			break;
			
			case 'l':
			chave=true;
			break;
}
		gotoxy(2,1);
	printf("Pontuação: %d",*placar);
if(dificuldade==1){

			draw(ply,randx,randy,placar,tamanho);
			Pintar_Cobra(ply,PCobra,tamanho,placar);
			textbackground(BLUE);
			printf("\n");
		VoltaCobra(&ply);
	
		sleep(0,95);						//Velocidade da cobrinha
	}else if(dificuldade==2){
	
			draw(ply,randx,randy,placar,tamanho);
			Pintar_Cobra(ply,PCobra,tamanho,placar);
			textbackground(BLUE);
			printf("\n");
	chave=CompCobra(PCobra,tamanho,dificuldade);
	sleep(0,6);
	}else if (dificuldade==3){
	
		drawDificil(ply,randx,randy,placar,tamanho);
		Pintar_Cobra(ply,PCobra,tamanho,placar);
			textbackground(BLUE);
			printf("\n");
	chave=CompCobra(PCobra,tamanho,dificuldade);
		sleep(0,2);
	}
	

}

		}
		if(dificuldade==3){				//Mostra o placar ao tocar em objetos ou em si mesmo
		gotoxy(14,10);
		printf("Você Perdeu!");
		gotoxy(12,11);
		printf("Sua pontuação: %d",*placar );
		fflush(stdin);
		sleep(1);
			
		}else{
		gotoxy(32,15);
		printf("Você Perdeu!");
		gotoxy(30,16);
		printf("Sua pontuação: %d",*placar );
		fflush(stdin);
		sleep(1);
		}
	
	
}


void Menu(struct desenho ply,struct desenho *PCobra[],int *randx,int *randy, int *placar, int *tamanho){
    void Jogo(struct desenho ply,struct desenho *PCobra[],int *randx,int *randy, int *placar, int *tamanho, int dificuldade);
    int Dificuldade();
    void Pontua(int pontos, int histDif);
    	
    bool escolha = false;
    int dificuldade=1, opcoes = 0, pontuacao=0,x,y,instruct=0,histDif=1;
    char choose;
    
															
	while(escolha == false){							//Menu de escolhas
		textbackground(BLACK);
		system("color 01");
		for(x=0;x<60;x++){						
			textbackground(RED);
			textcolor(BROWN);
					gotoxy(38,7);
				printf("Snake Game");
					for(y=0;y<10;y++){
						if(x==35 && y>4 && y<10){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");
						}
						if(x==50 && y>4 && y<10){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");	
						}
							if(y==5 && x>34 && x<51){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");	
						}
							if(y==9 && x>34 && x<51){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");	
						}
						if(y==6 && x>35 && x<38){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");	
						}
						if(y==6 && x>41 && x<44){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");	
						}
						if(y==6 && x>47 && x<51){
							gotoxy(x,y);
							textbackground(RED);
							printf(" ");	
						}
					}
				}
			textcolor(WHITE);
			if(opcoes == 0){
				
				if(instruct==0){
				textbackground(MAGENTA);
				gotoxy(70,5);
				printf("Pressione W para ir para cima");
				gotoxy(70,6);
				printf("Pressione A para ir para esquerda");
				gotoxy(70,7);
				printf("Pressione S para ir para baixo");
				gotoxy(70,8);
				printf("Pressione D para ir para direita");
				gotoxy(70,9);
				printf("Pressione X para confirmar");
				textbackground(CYAN);
				gotoxy(70,16);
				printf("Pressione L para abandonar a partida");
			}
		textbackground(RED);
		if(dificuldade==1){
			gotoxy(38,15);
		printf("Iniciar <- Fácil");
		}else if(dificuldade==2){
			gotoxy(38,15);
		printf("Iniciar <- Médio");
		}else{
			gotoxy(38,15);
		printf("Iniciar <- Difícil");
		}
		
		textbackground(BLUE);
		gotoxy(38,16);
		printf("Dificuldade");
		gotoxy(38,17);
		printf("Pontuação");
		gotoxy(38,18);
		printf("Sair");	
	}else 	if(opcoes == 1){
		instruct++;
		textbackground(BLUE);
		gotoxy(38,15);
		printf("Iniciar");
		gotoxy(38,16);
		textbackground(RED);
		printf("Dificuldade <-");
		textbackground(BLUE);
		gotoxy(38,17);
		printf("Pontuação");
		gotoxy(38,18);
		printf("Sair");		
	}else 	if(opcoes == 2){
		textbackground(BLUE);
		gotoxy(38,15);
		printf("Iniciar");
		gotoxy(38,16);
		printf("Dificuldade");
		gotoxy(38,17);
		textbackground(RED);
		printf("Pontuação <-");
		textbackground(BLUE);
		gotoxy(38,18);
		printf("Sair");	
	}else 	if(opcoes == 3){
		textbackground(BLUE);
		gotoxy(38,15);
		printf("Iniciar");
		gotoxy(38,16);
		printf("Dificuldade");
		gotoxy(38,17);
		printf("Pontuação");
		textbackground(RED);
		gotoxy(38,18);
		printf("Sair <-");	
	}
			fflush(stdin);
			choose=getch();
			switch(choose){
				case 'w':
					if(opcoes>0){
					opcoes--;	
					}
				break;
				
				case 's':
					if(opcoes<3){
					opcoes++;	
					}
				break;
				
				
				case 'x':
					if(opcoes==0){

						clrscr();
						Jogo(ply,PCobra,randx,randy,placar,tamanho,dificuldade);
						if(dificuldade>1){
						if((*placar)>pontuacao){
							pontuacao=*placar;
							histDif=dificuldade;
						}
					}
					
						*placar=0;
						*tamanho=1;
					}else if(opcoes==1){
						clrscr();
						dificuldade=Dificuldade();
						
					}else if(opcoes==2){
						clrscr();
						 Pontua(pontuacao,histDif);
						 
					}else{
					clrscr();
					textbackground(BLACK);
					system("color 01");
					gotoxy(39,14);
					printf("Obrigado por jogar :D\n");
					sleep(2);
						escolha=true;
					}
				break;
			}
			clrscr();
		
	}

}
int Dificuldade(){									//Escolha da Dificuldade
	bool escolha = false;
    int  opcoes = 0;
    char choose;
		
	while(escolha == false){
		textbackground(BLACK);
		system("color 01");
			textcolor(WHITE);
			textbackground(MAGENTA);
			gotoxy(34,9);
			printf("< Dificuldade >");
			
			if(opcoes == 0){
		textbackground(RED);
		gotoxy(38,15);
		printf("Fácil <- Pode atravessar objetos - Velocidade baixa - Pontuação não conta");
		textbackground(BLUE);
		gotoxy(38,16);
		printf("Médio");
		gotoxy(38,17);
		printf("Difícil");
	}else 	if(opcoes == 1){
	textbackground(BLUE);
		gotoxy(38,15);
		printf("Fácil");
		textbackground(RED);
		gotoxy(38,16);
		printf("Médio <- Não pode atravessar objetos - Velocidade média");
		textbackground(BLUE);
		gotoxy(38,17);
		printf("Difícil");	
	}else 	if(opcoes == 2){
		textbackground(BLUE);
		gotoxy(38,15);
		printf("Fácil");
		gotoxy(38,16);
		printf("Médio");
		textbackground(RED);
		gotoxy(38,17);
		printf("Difícil <- Não pode atravessar objetos - Velocidade alta - Mapa menor");	
	}

			choose=getch();
			switch(choose){
				case 'w':
					if(opcoes>0){
					opcoes--;	
					}
				break;
				
				case 's':
					if(opcoes<2){
					opcoes++;	
					}
				break;
				
				
				case 'x':
					if(opcoes==0){
						return 1;
						escolha=true;
						
						}
					else if(opcoes==1){
						return 2;
						escolha=true;
						
						
					}else if(opcoes==2){
						return 3;
							escolha=true;
						
					}
				break;
				
				
			}
			clrscr();
	}	
	}
	
void Pontua(int pontos, int histDif){        				   //Mostra a maior Pontuação obtida
	int x, y;
	char dificuldadeNome[8]="...",Dificil[]="Difícil",Media[]="Média";
	if(histDif==2){
		strcpy(dificuldadeNome,Media);
		
	}else if(histDif==3){
		strcpy(dificuldadeNome,Dificil);
	}
	textbackground(BLACK);
		system("color 01");
		for(x=0;x<60;x++){
			textbackground(CYAN);
			textcolor(WHITE);
					gotoxy(37,7);
				printf("< Pontuação >");
					for(y=0;y<10;y++){
						if(x>35 && x<51 && y>4 && y<10){
							gotoxy(x,y);
							textbackground(CYAN);
							printf(" ");
						}
					}
				}
				textcolor(BLACK);
				gotoxy(33,12);
				printf("* Maior pontuação: *");
			
				
				gotoxy(25,14);
				printf("Dificuldade: %s ------------------ %d",dificuldadeNome, pontos);
	
	sleep(3);
}	

int main(){
setlocale(LC_ALL,"");
	srand(time(NULL));
		void Menu(struct desenho ply,struct desenho *PCobra[],int *randx,int *randy, int *placar, int *tamanho);
	
			
		struct desenho ply={39,14};
		struct desenho VetCobra[120], *PCobra[120];
		VetCobra[0].x=ply.x;
		VetCobra[0].y=ply.y;
		PCobra[0]=&VetCobra;
		
		
		int rndx=(rand() % 78), rndy=(rand() % 28);
		int tamanho=1, placar=0;
		
		Menu(ply, PCobra, &rndx, &rndy,&placar,&tamanho);
		
return 0;
}
