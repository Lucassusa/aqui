#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <locale.h>

void printSolution(int grid[9][9])
{
		puts("___ ___ ___ ___ ___ ___ ___ ___ ___ ");
    for(int i=0;i<9;i++)
    {
        for(int j=0;j<9;j++)
            {
                printf( ((j+1)%3) ? " %d |" : " %d |",grid[i][j]);
               }
                        putchar('\n');
            if(!((i+1)%1))
                puts("___ ___ ___ ___ ___ ___ ___ ___ ___ ");
    }
}
bool absentOnRow(int k,int grid[9][9],int i)
{
    for(int j=0;j<9;j++)
    {
        if(grid[i][j] == k)
            return false;
    }
    return true;
}
bool absentOnColumn(int k,int grid[9][9],int j)
{
    for(int i=0;i < 9;i++)
    {
        if(grid[i][j] == k)
            return false;
    }
    return true;
}
bool absentOnBloc(int k,int grid[9][9],int i,int j)
{
    int _i = i -(i%3),_j=j-(j%3);
    for(i = _i;i<_i+3;i++)
        for(j=_j;j<_j+3;j++)
            if(grid[i][j] == k)
                return false;
    return true;
}
bool isValid(int grid[9][9],int position)
{
    if(position == 9*9)
        return true;
    int i = position/9,j = position%9;
    if(grid[i][j] != 0)
        return isValid(grid,position+1);
    for(int k=1;k <= 9;k++)
    {
        if(absentOnRow(k,grid,i) && absentOnColumn(k,grid,j) && absentOnBloc(k,grid,i,j))
        {
            grid[i][j]=k;
            if(isValid(grid,position+1))
                return true;
        }
    }
    grid[i][j] = 0;
    return false;
}
//--------------------------------------------------------------------------------------
int level_dificil(void)                     //aqui era o main
{
    	
    int grille[9][9] =
    {
        {9,0,0,1,0,0,0,0,5},
        {0,0,5,0,9,0,2,0,1},
        {8,0,0,0,4,0,0,0,0},
        {0,0,0,0,8,0,0,0,0},
        {0,0,0,7,0,0,0,0,0},
        {0,0,0,0,2,6,0,0,9},
        {2,0,0,3,0,0,0,0,6},
        {0,0,0,2,0,0,9,0,0},
        {0,0,1,9,0,4,5,7,0}
    };
    printSolution(grille);
    isValid(grille,0);
//int verificar_correção(void){        
   // printf("Grille after\n");       //CORREÇÃO
  // printSolution(grille);
  // }
}
int level_medio(void)
{

    int grille[9][9] =
    {
        {9,7,0,1,0,0,0,0,5}, // 7 NESSA LINHA
        {0,0,5,0,9,0,2,0,1},
        {8,0,0,0,4,0,0,0,0},
        {0,0,0,0,8,0,0,0,0},
        {0,0,0,7,0,0,0,0,0},
        {0,3,0,0,2,6,0,0,9}, //ALTEREI COM UM 3 NESSA LINHA
        {2,0,0,3,0,0,0,0,6},
        {0,0,0,2,0,0,9,0,0},
        {0,0,1,9,0,4,5,7,0}
    };
    printSolution(grille);
    isValid(grille,0);	  
	//int verificar_correção(void){         //CORREÇÃO
 //   printf("Grille after\n"); 
  //  printSolution(grille);
  // }
}
int level_facil(void)
{
		
    int grille[9][9] =
    {
        {9,7,0,1,0,0,0,0,5}, //  alterei em todas as outras linhas
        {0,0,5,0,9,0,2,0,1},
        {8,0,0,0,4,0,3,0,0},
        {4,0,0,0,8,0,0,0,0},
        {0,0,0,7,3,0,0,0,0},
        {0,3,0,0,2,6,8,0,9}, 
        {2,0,0,3,0,0,0,0,6},
        {5,0,0,2,0,0,9,0,0},
        {0,0,1,9,0,4,5,7,0}
    };

    printSolution(grille);
    isValid(grille,0);	
    	//int verificar_correção(void){         //CORREÇÃO
 //   printf("Grille after\n"); 
  //  printSolution(grille);
  // }
}
int main(){
    	setlocale(LC_ALL, "Portuguese");
    	printf("                      - SUDOKU -\n");
         getchar();
	    printf("ESCOLHA UM NÍVEL!\n\n");
	    printf("(1)FÁCIL  (2)MÉDIO   (3)DIFÍCIL \n ");
	    int aux,aux2;
	    int vlinha;
	    int tecla=getchar();
		if(tecla==51){ //tabela
		   system("cls");
		printf("VOCÊ ESTÁ JOGANDO NO NÍVEL DIFÍCIL!\n\n");
	    level_dificil(); 
	        int mat[9][9];              //matriz para receber linha e coluna do usuário 
		printf("Digite a linha e a coluna que deseja alterar!\n");
		      printf("Linha:\n");                                        
	      		        for( aux=1;aux<=1;aux++){
	         	 	for ( aux2=1;aux2<=1;aux2++){ 		
			              	int vlinha[aux]={mat[aux][aux2]};             //vetor que recebe amatriz//                                     			             scanf("%d",&vlinha);	 
			   }  
						
  	        	    printf("Coluna:\n");
		   		    }
  	       			  for(aux=1;aux<1;aux++){
  	           	            for (aux2=1;aux2<=1;){
  	        	                 int vcoluna[aux2]= {mat[aux][aux2]}; 
					   scanf("%d",&vcoluna);
        	        	}
	        }
  	 	          
		}else if(tecla==50){
			system("cls");
		printf("VOCÊ ESTÁ JOGANDO NO NÍVEL MÉDIO!\n");
		level_medio();
		}else if(tecla==49){
		    system("cls");
		printf("VOCÊ ESTÁ JOGANDO NO NÍVEL FÁCIL!\n");
		level_facil();
		} 
}





