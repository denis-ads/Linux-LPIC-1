Anotaçoes estudo LPI
inicio: 10/04/2018


Capitulo 103.1

	Principal shell do linux é o bash, mas existe sh, csh, ksh

	descobrir qual o shell que est sendo utilizado:
		echo $SHELL


	Comando type descobre qual a origem do comando, interno ou externo

	Caminho Relativo de dentro de qualquer diretorio ....
		denis/teste.sh

	caminho Absoluto: completo a partir da raiz /
		/home/denis/teste.sh

	Variaveis criadas dentro de uma sessao d shell so é visivel nessa sessão.

	Comando para verificar as variaveis declaradas e exportadas

	set - todas as variaveis declaradas, internas - comando interno

	env - so as variaveis que são globais. - comando externo

	unset - remove as variaveis

	Variaveis de ambiente dinamicas
		echo $$ -> mostra pid do shell atual
		
		echo $! -> mostra o pid do ultimo processo rodado em background

		echo $? -> mostra o codigo de retorno do ultimo processo:
			0 = sucesso
			qualquer coisa != 0 é um erro.

		echo ~ -> diretorio home do usuario atual
		echo ~root -> mostra o diretorio do usuario root

	Variaveis de ambientes:
		DISPLAY: Indica às aplicações gráficas onde as janelas deverão ser exibidas. Será estudado no Tópico 106.
		HISTFILE: Arquivo do histórico de comandos
		HISTFILESIZE: Quantidade de linhas/comandos armazenados no arquivo de histórico
		HOME: Indica o diretório do usuário atual
		LOGNAME e USER: Nome do usuário atual
		PATH: Diretórios em que o Linux irá procurar por arquivos executáveis
		PS1: Aparência do prompt do shell.
		PWD: Diretório atual
		OLDPWD: Diretório anterior


	Executar comandos sequencialmentes
		clear ; date ; ls
		clear && date && ls -> so executa o proximo comando se o primeiro for com sucesso.
		clear || date || ls -> so executa o segundo se o primeiro não for executado com sucesso.

	Comando !! -> executa o ultimo comando que foi executado.
	Comando !19 -> executa o comando no numero do historico.
	comando !<String> !uname -> executa o comando que contenha aquela string.

	history -c limpa o arquivo de historico


	Comandos de ajuda
	man cd
	man -k "update system"
	info cd
	whatis tar
	apropos

	Comandos de sistema
	uname 
	alias
	criando alias
		alias lt='ls /tmp'

Exercicios: Acertei todos - os 'ou'
	1 - echo $HISTFILE ou  set |grep HISTFILE
	  - uname -r
	  - echo $PATH ou env |grep “$PATH”
	  - hostname ou uname –n
	  - echo $$ ou ps |grep bash
	2 - export NOME="Denis Apolinario"
	3 - echo "O Nome do Próximo Certificado LPI 1 é:" $NOME


Capitulo 103.2

	
	








