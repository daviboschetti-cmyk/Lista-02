#include <stdio.h>
#include <stdlib.h>

int main()
{
    int tipoVeiculo, tipoSeguro, idade, eixos;
    float valorBase = 0, adicionalCat = 0;
    float adicionalIdade = 0;
    float custoCobertura = 0, valorTotal;

    printf("===== SISTEMA DE CALCULO DE SEGURO =====\n");

    // Escolha do Veículo
    do{
        printf("Selecione o tipo do veiculo:\n");
        printf("1. Passeio\n2. Carga Pesada\n3. Caminhonete\n4. Motocicleta (<1000cc)\n5. Motocicleta (1000cc+)\n");
        printf("Opcao: ");

        if(scanf("%d",&tipoVeiculo)!=1){
            while(getchar()!= '\n');
        }

        if(tipoVeiculo < 1 || tipoVeiculo > 5){
            printf("[ERRO] Opcao invalida! Tente novamente.\n");
        }

    }while(tipoVeiculo < 1 || tipoVeiculo > 5);


    // Valor base e categoria
    if(tipoVeiculo >=4){
        valorBase = 1200.00;

        if (tipoVeiculo == 4)
            adicionalCat = valorBase * 0.80;
        else
            adicionalCat = valorBase * 0.90;

    }else{

        valorBase = 1000.00;

        if(tipoVeiculo == 1)
            adicionalCat = valorBase * 0.10;
        else if (tipoVeiculo == 2)
            adicionalCat = valorBase * 0.20;
        else
            adicionalCat = valorBase * 0.33;
    }


    // Idade
    printf("Digite sua idade: ");
    scanf("%d", &idade);

    if(idade <= 25)
        adicionalIdade = valorBase * 0.15;
    else if (idade < 30)
        adicionalIdade = valorBase * 0.10;
    else
        adicionalIdade = valorBase * 0.05;


    // Tipo de seguro
    printf("Selecione o Seguro:\n1. Base\n2. Parcial\n3. Completo\n");
    scanf("%d", &tipoSeguro);


    // Caminhão ou Caminhonete
    if(tipoVeiculo == 2 || tipoVeiculo == 3){

        printf("Quantidade de eixos: ");
        scanf("%d", &eixos);

        if(tipoSeguro == 1)
            custoCobertura = (valorBase * 0.03) * eixos;
        else if (tipoSeguro == 2)
            custoCobertura = (valorBase * 0.05) * eixos;
        else if (tipoSeguro == 3)
            custoCobertura = (valorBase * 0.10) * eixos;
    }

    // Passeio
    else if (tipoVeiculo == 1){

        if (tipoSeguro == 1 || tipoSeguro == 2)
            custoCobertura = 2.00;
        else
            custoCobertura = 10.00;
    }

    // Moto <1000cc
    else if (tipoVeiculo == 4){

        if(tipoSeguro == 1)
            custoCobertura = valorBase * 0.95;
        else if (tipoSeguro == 2)
            custoCobertura = valorBase * 0.15;
        else if (tipoSeguro == 3)
            custoCobertura = valorBase * 0.80;
    }

    // Moto 1000cc+
    else if (tipoVeiculo == 5){

        if(tipoSeguro == 1)
            custoCobertura = valorBase * 0.10;
        else if (tipoSeguro == 2)
            custoCobertura = valorBase * 0.20;
        else if (tipoSeguro == 3)
            custoCobertura = valorBase * 1.00;
    }


    // Cálculo final
    valorTotal = valorBase + adicionalCat + adicionalIdade + custoCobertura;


    // Saída
    printf("\n===== CUSTO DE SEGURO =====\n");
    printf("Valor Base: R$ %.2f\n", valorBase);
    printf("Adicional Categoria: R$ %.2f\n", adicionalCat);
    printf("Adicional Idade: R$ %.2f\n", adicionalIdade);
    printf("Valor Cobertura Plano: R$ %.2f\n", custoCobertura);
    printf("----------------------------------\n");
    printf("Valor Total: R$ %.2f\n", valorTotal);

    return 0;
}


