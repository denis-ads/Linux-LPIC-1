Anotaçoes estudo LPI
inicio: 10/04/2018
Udemy

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
		clear || date || ls -> so executa o segundo se o primeiro for executado com problema.

	Comando !! -> executa o ultimo comando que foi executado.
	Comando !19 -> executa o comando no numero do historico.
	comando !<String> !uname -> executa o comando que contenha aquela string no historico.

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

Exercicios: Acertei todos menos os 'ou'
	
	103.1 Trabalhando na Linha de Comando

		1. Encontre as seguintes informações sobre a sua instalação Linux:

		O caminho completo do arquivo .bash_history para o seu usuário;
		O release do kernel instalado
		Os diretórios incluídos em seu PATH
		O hostname da máquina
		O PID da sua sessão shell atual
		2. Crie e exporte uma variável chamada "NOME" que contenha o seu nome completo.

		3. Crie um comando que escreva na tela a seguinte frase: "O Nome do Próximo Certificado LPI 1 é: <utilize a variável NOME>"

	Resp:
		1 - echo $HISTFILE ou  set |grep HISTFILE
		  - uname -r
		  - echo $PATH ou env |grep “$PATH”
		  - hostname ou uname –n
		  - echo $$ ou ps |grep bash
		2 - export NOME="Denis Apolinario"
		3 - echo "O Nome do Próximo Certificado LPI 1 é:" $NOME


Capitulo 103.2

	Aplicando filtros em arquivos.

	cat 
	cat -b alunos.txt -> numera so as linhas preenchidas
	cat -n alunos.txt -> numera todas as linhas 
	cat -s alunos.txt -> se tiver mais de uma linha em branco so mostra uma.
	cat -A alunos.txt -> mostra todos os caracteres especiais.


	tac -> mostra o arquivo de tras pra frente.

	head -> mostra as primeiras 10 linhas do arquivo.
	head -n2 -> mostra as quantidades de linhas
	head -c50 -> mostra os 50 primeiros bytes

	tail -> mostra as ultimas linhas do arquivo.


	less -> paginaçao de arquivos 
	/ para fazer busca
	n vai para proxima ocorrencia da busca
	shift + n vai para anterior.
	control + g -> mostra informaçoes do arquivo

	cat arquivoLongo.txt | less -> manda a saida do comando cat para less

	wc -> ler a quantidade de linhas, palavras e caracteres
	wc * -> para todos os arquivos do diretorio

	cat alunos.txt | wc -l
	tail -n10 alunos.txt |wc

	nl igual cat -b  -> numera as linhas preenchidas

	sort -> ordena o arquivo
	sort alunos.txt

	sort -k2 alunos.txt -> ordena a segunda palavra.

	cat alunos.txt |sort -r 

	uniq -> retira a duplicidade do arquivo, mas de palavras em linhas sequnciais

	usado com o comando sort
	sort alunos2.txt | uniq 

	sort alunos2.txt | uniq -d -> so o que esta duplicado

	sort alunos2.txt | uniq -c -> conta as duplicidade.

	expand -> troca tab por 8 espaços.
		expand alunos.txt |cat -A

	unexpand -> troca espaços no começo da linha por default.
	unexpand -a alunos.txt |cat -A  -> -a para olhar em qualquer lugar.


	od -> transforma a saida do arquivo em octal, hexa.

	join -> combina 2 arquivos por linha e indice.
		join -j2 codigo-aluno.txt notas-aluno.txt -> combina a segunda coluna

	paste -> combina 2 arquivos por linha.

	split -> divide arquivos.

	split -l20 arquivolongo.txt
	split -l20 arquivolongo.txt novo_arquivo_
	split -20 arquivolongo.txt novo_arquivo_


	tr -> troca caracteres, mas precisa pegar da saida de um comando.
	cat alunos.txt | tr a-z A-Z

	cat alunos.txt | tr A E
	cat alunos.txt | tr ai IE
	cat alunos.txt | tr [:upper:] [:lower:]


	fmt -> formata um arquivo, padrao 75 caracteres por linha.

	pr -> prepara um arquivo para impressão.

	cut -> recortar partes de um texto 
	cut -c1-5 alunos.txt 

	cut -d" "  -f1 alunos.txt -> usa espaço como delimitador.

	sed -> usado muito com expressoes regulares, procurar um conteudo e substituir.

	sed 's/Silva/Souza/' alunos.txt -> troca Silva por Souza apenas a primeira ocorrencia

	sed 's/Ana/Maria/g' alunos.txt -> troca todas as ocorrencias na linha 

	sed '3,5 d' alunos.txt -> apaga as linhas de 3 a 5.

	sed '/Claudia/d' alunos.txt -> apaga todas as palavras Claudia.

Exercicios:
	103.2 Aplicando Filtros a Textos e Arquivos

		4. O arquivo /etc/passwd contém a lista de usuários do Linux, os campos são separados pelo caractere :, o primeiro campo indica o nome do usuário e o terceiro o ID do usuário.

		Escreva um comando que mostre os últimos 15 registros do arquivo, exibindo apenas o nome do usuário e seu ID, e que esteja ordenado pelo ID numérico. Por exemplo:

		usuario1:10

		usuario2:12

		usuario:3:1000

		.......
			Resp: 
				tail -n 15 /etc/passwd | cut -d":" -f1,3|sort -t ":" -k2 -g

		- * No comando sort, o –t define o delimitador, o –k o campo referência para o ordenamento, e o –g ordena como números ao invés de como caracteres

		5. Gere um comando, ou sequência deles, que mostre o número de linhas do arquivo /etc/passwd excluindo-se as linhas que contenham a palavra "daemon". O resultado do comando deve ser o número de linhas.
			Resp:
		 		# sed '/daemon/d' /etc/passwd| wc –l ou
				# grep -v daemon /etc/passwd | wc –l


Capitulo 103.2

	Gerenciamento de arquivos e diretorios.
	

	Estrutura de diretorios do linux.

		caminhos absolutos
		caminhos relativos
	
	comandos:

	cd 

	ls
	ls -l Aula1*
	ls -l Aula1? -> ? tem que ser um numero
	ls -l Aula1?0
	ls -l Aula[1,2,3]
	ls -l Aula[!1,2,3] -> ! negando os itens
	ls -l Aula{10,20,30} -> sequencia de caracteres.
	ls -l A{ula,UAL}1


	file -> analisa o tipo do arquivo


















 
















	








