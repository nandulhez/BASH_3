# BASH_3

#!/bin/bash

														# Escrito p/ Luís Fernando de Carvalho



principal() 

{           # Função principal do programa
    clear               # limpa a tela

    echo "[1] Mostrar a localização atual do usuário no sistema de arquivos"  
    echo "[2] Mostrar o tipo de um arquivo"  
    echo "[3] Criar um diretório"
    echo "[4] Apagar um diretório não vazio"
    echo "[5] ler 2 números e indicar qual é o maior deles e qual é o menor"
    echo "[6] Exibir as últimas linhas de um arquivo"
    echo "[7] Exibir as primeiras linhas de um arquivo"
    echo "[8] Mostrar a localização de um comando específico"
    echo "[9] Mostra um diretório informado pelo usuário em formato de árvore"
    echo "[10] Copiar um arquivo para um outro diretório"
    echo "[11] Mover um arquivo para outro diretório"
    echo "[12] Sair"

    echo
    echo -n "Qual a opcao desejada ? "
    read opcao          # REALIZA A LEITURA DA VARIÁVEL "OPCAO", 
                        # QUE SERÁ UTILIZADA NO COMANDO CASE
                        # P/ INDICAR QUAL A OPÇÃO A SER UTILIZADA

                        # CASO O VALOR DA VARIÁVEL "OPCAO"...
    case $opcao in
        1)              # SEJA IGUAL A "1", ENTÃO FAÇA AS INSTRUÇÕES ABAIXO
            clear
			localizacao_arquivos
		;;                                
        2)
            clear
			mostrar_tipo_arquivo           
		;; 

        3)
            clear
           	criar_diretorio
		;; 
        4)
            clear
			deletar_diretorio		
		;; 
        5)
            clear
			mostra_maior   
		;;
        6)
			clear
			ultimas_linhas
        ;; 
        7)
            clear
			primeiras_linhas
        ;; 
		8)
            clear
			localizar_comando          
		;; 
        9)
            clear
			diretorio_form_arvore
        ;; 
        10)
            clear
			copiar_arquivo
        ;; 
        11)
            clear
           	mover_arquivo
		;; 
		12)
            clear
            exit ;;

        *)              
            clear
            echo "Opcao desconhecida."
            read pause
            principal   
        ;;
    esac
}







localizacao_arquivos() {             
    pwd 
    read pause          
    principal           
}

mostrar_tipo_arquivo() {              
    clear
    echo "digite arquivo"
	read ARQUIVO
	file $ARQUIVO	
    read pause
    principal
}

criar_diretorio() {             
    clear
    echo "digite o diretorio que quer criar"
	read DIRETORIO
	mkdir $DIRETORIO
    read pause
	principal	
}

deletar_diretorio() {             
    clear
	echo "digite o diretorio que quer deletar"
	read DIRETORIO
	rm -r $DIRETORIO 	
    read pause
    principal
}

mostra_maior() {             
    clear
	echo "digite o primeiro numero"
		read NUMERO1
		echo "digite o segundo numero"
		read NUMERO2
		if [ $NUMERO1 -gt $NUMERO2 ]; then
			
			echo "O numero maior é: " $NUMERO1
		else
			echo "O numero maior é: " $NUMERO2
		fi
	read pause
    principal		
    
}

ultimas_linhas() {             
    clear
	echo "digite o nome do arquivo"
	read ARQUIVO
	echo "digite a quantidade de linha que quer exibir"
	read LINHAS
	tail -$LINHAS $ARQUIVO
    read pause 
	principal	
}

primeiras_linhas() {             
    clear
	echo "digite o nome do arquivo"
	read ARQUIVO
	echo "digite a quantidade de linha que quer exibir"
	read LINHAS
	head -$LINHAS $ARQUIVO
    read pause
	principal	
}

localizar_comando() {             
	clear
    echo "Digite o comando"
	read COMANDO
	which $COMANDO 
    read pause          
    principal           
}

diretorio_form_arvore() {             
    clear
	echo "Digite o Diretorio"
	read DIRETORIO
	tree $DIRETORIO
    read pause          
    principal           
}

copiar_arquivo() {             
    clear
	echo "Digite o arquivo que deseja copiar"
	read ARQUIVO
	echo "Digite para onde deseja copiar o arquivo"
	read LOCAL
	cp $ARQUIVO $LOCAL  
    read pause          
    principal           
}

mover_arquivo() {             
    clear
    echo "Digite o arquivo que deseja mover"
	read ARQUIVO
	echo "Digite para onde deseja mover mais o nome do arquivo"
	read LOCAL
	mv $ARQUIVO $LOCAL  
    read pause          
    principal            
}

opcao_invalida() {      # FUNÇÃO DA OPÇÃO INVÁLIDA
    clear
    echo "Opcao desconhecida."
    read pause
    principal
}

principal               # O SCRIPT COMEÇA AQUI, AS FUNÇÕES DAS LINHAS ANTERIORES
                        # SÃO LIDAS PELO INTERPRETADOR BASH E ARMAZENADAS EM MEMÓRIA.

                        # O BASH NÃO TEM COMO ADIVINHAR QUAL DAS FUNÇÕES ELE DEVE 
                        # EXECUTAR, POR ISTO O A EXECUÇÃO DO SCRIPT REALMENTE COMEÇA
                        # QUANDO APARECE UMA INSTRUÇÃO FORA DE UMA FUNÇÃO, NESTE CASO,
# CHAMANDO A FUNÇÃO PRINCIPAL

