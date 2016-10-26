# BASH_3

#!/bin/bash
#

# Trabalho engenharia de Software
#

principal() {           # Função principal do programa
    clear               # limpa a tela

    echo "Bem vindo ao File Manager"
    echo "-------------------------"

    echo "[1] Mostrar a localização atual do usuário no sistema de arquivos"
    pwd #Mostrar a localização atual do usuário no sistema de arquivos
    echo "[2] Mostrar o tipo de um arquivo"
    echo "[3] Criar um diretório"
    echo "[4] Apagar um diretório não vazio"
    echo "[5] ler 2 números e indicar qual é o maior deles e qual é o menor"
    echo "[6] Exibir as últimas linhas de um arquivo(pedir ao usuário a quantidade de linhas a
    mostrar)"
    echo "[7] Exibir as primeiras linhas de um arquivo(pedir ao usuário a quantidade de linhas a
    mostrar)"
    echo "[8] Mostrar a localização de um comando específico utilizar which ou whereis"
    echo "[9] Mostra um diretório informado pelo usuário em formato de árvore (instalar comando
    tree)"
    echo "[10] Copiar um arquivo para um outro diretório (usuário deve informar qual é o arquivo e
    qual é o diretório)"
    echo "[11] Mover um arquivo para outro diretório"
    echo "[12] Sair"


    echo
    echo -n "Qual a opcao desejada ? "

    read opcao          # faz a leitura da variável "opcao",
                        # que será utilizada no comando case
                        # para indicar qual a opção a ser utilizada

                        # caso o valor da variável "opcao"...
    case $opcao in
        1)              # seja igual a "1", então faça as instruções abaixo
            clear
            localizacao     # executa os comandos da função "laranja"

            ;;          # os 2 ";;" (ponto e virgula)
                        # significam que chegou ao final
                        # esta opção do comando case
        3)
            clear
            criarDiretorio ;;  # usa a função martelo e finaliza a opção do case com ";;"
        4)
            clear
            removerDiretorio ;;   
        12)
            clear
            exit ;;
         
        *)              # esta opçao existe para caso o usuário digite um
                        # valor diferente de 1, 2 ou 3
            opcao_invalida ;;
    esac
}

localizacao() {  
    echo "Diretório"          # função da opção laranja
    pwd
    read pause          # usado para pausar a execução do script
    principal           # volta para a função principal
}

criarDiretorio(){
    echo "Digite o Caminho e o nome do diretório"
    echo "Ex: /caminho-do-diretório/nome-do-diretório"
    read  DIR
    mkdir $DIR
    echo "Diretório Criado => $DIR"
    dir
    read pause
    principal 
}

removerDiretorio(){
    echo "Digite o Caminho e o nome do diretório que deseja remover"
    echo "Ex: /caminho-do-diretório/nome-do-diretório"
    read  DIR
    rm -rf $DIR
    echo "Diretório removido => $DIR"
    dir
    read pause
    principal 
}


opcao_invalida() {      # função da opção inválida
    clear
    echo "Opcao desconhecida."
    read pause
    principal
}

principal               # o script começa aqui, as funções das linhas anteriores
                        # são lidas pelo interpretador bash e armazenadas em memória.

                        # o bash não tem como adivinhar qual das funções ele deve
                        # executar, por isto o a execução do script realmente começa
                        # quando aparece uma instrução fora de uma função, neste caso,
                        # chamando a função principal
