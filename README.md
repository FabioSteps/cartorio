#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <string.h>



int registro_usuario()
{
	char usuario [40];
	char senha [40];
    char arquivologin[40];
    
    setlocale(LC_ALL, "PORTUGUESE");
    
    printf ("nome de usuario:");
    scanf ("%s", usuario);
    
    printf ("senha: ");
    scanf ("%s", senha);
    
    strcpy (arquivologin, usuario);
	
	
	FILE *file = fopen (arquivologin, "w");
	if (file == NULL)
	{
		printf ("erro ao criar usuário");
		return 1;
	}
	fprintf (file, "%s,%s", usuario, senha);
	fclose (file);
	
	printf ("usuario registrado\n\n");
	system ("pause");
	return 0;
	
}

int login ()
{
	char usuario [40];
	
	char senha [40];
	
	char arquivo[40];
	
	char conteudo [80];
	
	char usuario_senha [40];
	
	
	 setlocale(LC_ALL, "portuguese");
	 
	printf("Nome de usuário: ");
    scanf("%s", usuario);
    
    printf("Senha: ");
    scanf("%s", senha);
    
    strcpy (arquivo, usuario);
    
    FILE *file = fopen (arquivo, "r");
    if (file == NULL)
	{
		printf ("usuario não cadastrado");
		system ("pause");
		return 0;
    	
	}
	 sprintf (usuario_senha, "%s,%s", usuario, senha);
	 
	 while (fgets(conteudo, 80 , file) != NULL)
	 {
	 	conteudo[strcspn(conteudo, "\n")] =0;
	 	if (strcmp(conteudo, usuario_senha)== 0){ fclose (file);
	 	printf ("login realizado com sucesso\n\n");
	 	return 1;
		 }
	 	
	 	
	 }
	 fclose (file);
	 
	 printf ("nome de usuário ou senha incorretor\n\n");
	 system ("pause");
	 return 0;
	
	
    
    
    
	
}























int registro()
{
	
	char cpf [40];
	char nome [40];
	char sobrenome [40];
	char cargo [40];
	char arquivo [40];
	
	setlocale(LC_ALL, "portuguese");
	
	printf("Cpf: ");
	scanf("%s",cpf);

	
	
	
	strcpy(arquivo, cpf);
	
	FILE *file;
	file = fopen(arquivo, "w");
	fprintf(file,cpf);
	fclose(file);
	
	file = fopen(arquivo, "a");
	fprintf(file, "," );
	fclose(file);
	
	
	printf("\n\nNome:");
	scanf("%s",nome);
	
	
	file = fopen (arquivo, "a");
	fprintf (file, nome);
	fclose (file);

	
    printf ("\n\nsobrenome:");
    scanf ("%s", sobrenome);

    
    file = fopen(arquivo, "a");
    fprintf (file,sobrenome);
    fclose (file);
    
    file = fopen (arquivo, "a");
	fprintf (file, "," );
	fclose(file);

	
	printf ("\n\ncargo:");
	
	scanf ("%s", cargo);

	
	file = fopen (arquivo,"a");
	fprintf (file, cargo);
	fclose (file);
	
	printf ("\n\ncadastro realizado com sucesso\n\n");
	system ("pause");
	}
	
	


int consulta()
{
   char cpf [40];
   char conteudo [200];
   setlocale(LC_ALL, "portuguese");
   
   
   printf ("Digite o cpf:");
   scanf("%s", cpf);
   
   FILE *file;
   file = fopen (cpf, "r");
   
   if (file== NULL)
   {
   	printf ("usuario não cadastrado\n\n");
   }
   
   while (fgets(conteudo,200,file)!=NULL)
   {
  
   printf ("%s", conteudo);
   printf ("\n\ninformaçoes do usuário\n\n");
    }
  system("pause");

}


int excluir()
{
   setlocale (LC_ALL, "portuguese");
   char cpf [40];
   
   printf ("Digite o cpf:\n");
   scanf ("%s", cpf);
   
   
   FILE *file;
   file = fopen (cpf, "r");
   
   if (file == NULL)
   {
   	printf ("usuario não cadastrado\n\n");
   	system ("pause");
   	return 0;
   }
   fclose (file);
   
   
   
   printf ("\ndeseja deletar esse usuario?\n");
   
   printf ("\ndigite (s) para sim ou (n) para não\n");
   
     char opcao;
     opcao = getchar();
     scanf ( "%c", &opcao);
     
   if (opcao == 's' || opcao == 'S')
   {
     remove (cpf);
	{
		printf ("\ncadastro excluido\n");
		
	}
        system ("pause");
   
   }
   
 
   else if (opcao == 'n' || opcao == 'N')
   {
   	 printf ("\nretorne para o menu\n");
   	 system ("\npause\n");
   }
    
    else
    {
    	printf ("\nopcao invalida\n");
    	system ("pause");
	}
 
 
   }
	

  
 int sair()
 {
 	printf ("sáindo....\n\n");
	exit (0);
 }
 


int main() {
	
setlocale(LC_ALL, "portuguese");

int opcao = 0;

int logado = 0;
	
 while (1) {
 	
 	system ("cls");
 	
 	printf("\tCartório Ebac\n\n");
 	
        printf("\tEscolha uma opção\n\n");
        
        printf("\t1: Registrar usuário\n\n");
        
        printf("\t2: Login\n\n");
        
        printf("Opção: ");
        
        scanf("%d", &opcao);
        
    system ("cls");
    
    if (opcao == 1) {
    	registro_usuario();
	}
 	
 	else if (opcao ==2){
 		logado = login();
 		if (logado) {
 			break;
		 }
	 } else {
	 	printf ("essa não é uma opção valida\n\n");
	 	system ("pause");
	 }
 }



while (logado)while (logado) {
        system("cls");
        printf("\tCartório Ebac\n\n");
        printf("\tEscolha uma opção\n\n");
        printf("\t1: Registro de nomes\n\n");
        printf("\t2: Consulta de nomes\n\n");
        printf("\t3: Excluir nomes\n\n");
        printf("\t4: Sair\n\n");
        printf("Opção: ");
        scanf("%d", &opcao);

        system("cls");

        switch (opcao) {
            case 1:
                registro();
                break;
            case 2:
                consulta();
                break;
            case 3:
                excluir();
                break;
            case 4:
                sair();
                break;
            default:
                printf("Essa não é uma opção válida\n\n");
                system("pause");
                break;
        }
    }

    return 0;
}
