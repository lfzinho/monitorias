# Monitoria 1 (15/02)

- [Monitoria 1 (15/02)](#monitoria-1-1502)
	- [1. Configuração C++](#1-configuração-c)
		- [1.1 Linux](#11-linux)
			- [1.1.1 Configuração VSCode](#111-configuração-vscode)
		- [1.2 Windows](#12-windows)
			- [1.2.1 Instalar o compilador MinGW](#121-instalar-o-compilador-mingw)
			- [1.2.2 Instalar o compilador g++ via WSL](#122-instalar-o-compilador-g-via-wsl)
	- [2. Revisão C++](#2-revisão-c)
		- [2.1 Hello World](#21-hello-world)
		- [2.2 Tipos de dados](#22-tipos-de-dados)
			- [2.2.1 int, float](#221-int-float)
			- [2.2.3 char](#223-char)
			- [2.2.4 bool](#224-bool)
		- [2.3 Funções](#23-funções)
		- [2.4 Controle de fluxo](#24-controle-de-fluxo)
			- [2.4.1 if/else](#241-ifelse)
			- [2.4.2 for](#242-for)
			- [2.4.3 While](#243-while)
			- [2.4.4 Break, continue](#244-break-continue)

## 1. Configuração C++

C++ é uma linguagem compilada, dessa forma, para transformar o código em um arquivo executável, é necessário a instalação de um compilador, geralmente falamos sobre essa instalação como "instalar o C++". Existem diferentes compiladores, e entre eles os mais comuns são o MinGW (especial para Windows) e o g++. Aqui vamos falar brevemente como instalar eles, com referências para tutoriais mais completos. A instalação é diferente para sistemas Linux e Windows, dessa forma será apresentado separadamente.

### 1.1 Linux

Utilizar do C++ em um ambiente Linux pode acabar sendo mais fácil devido uma maior comunidade online e maior quantidade de ferramentas adaptadas para esse sistema. Para instalar o compilador g++ nesse ambiente, use-os comandos: (Obs.: esses comandos são baseados na distribuição Ubuntu 20.04).

Utilize o comando para se certificar que o apt está atualizado:

```
sudo apt-get update
```

E instale com o comando:

```
sudo apt install g++
```

#### 1.1.1 Configuração VSCode
Nós recomendamos a utilização do VSCode para criar seus programas em C++, é uma ferramenta com uma grande quantidade de extensões que facilitam o desenvolvimento. O download é possível no [link](https://code.visualstudio.com/Download), e também pode ser obtido na Central de programas do Ubuntu. Em seguida, instale a extensão "C/C++" no VSCode e criei um diretório com seu primeiro arquivo `main.cpp`, crie um código "hello world":

```c
#include<iostream>

int main(){
  std::cout << "Hello world!" << std::endl;
  return 0;
}

```

Agora, para executar esse código com o VSCode (e não no terminal), precisamos configurar o arquivo de build. Vá em _Terminal -> Configurar Tarefa de Build Padrão_ e selecione  _g++ arquivo de build ativo_. Isso irá criar o arquivo `tasks.json` que contém configurações sobre o comando que o terminal irá executar para compilar o arquivo, que por enquanto pode ser mantido do jeito que está. Volte para o `main.cpp` e use as teclas Ctrl+Shift+B para executar a tarefa de build, que irá compilar o arquivo e criar o executável. Para mais detalhes, utilize da seguinte [referência](https://medium.com/floppy-disk-f/setting-up-visual-studio-code-vs-code-with-c-on-ubuntu-linux-506aa02cacb5).

### 1.2 Windows

Em certas situações pode ser desvantajoso utilizar c++ em um ambiente Windows, com uma grande dificuldade de instalar algumas bibliotecas, por exemplo. No entanto, nos últimos anos esse problema vem sendo solucionado. Existem diferentes maneiras de se instalar um compilador no Windows, vamos aprensentar algumas delas:

#### 1.2.1 Instalar o compilador MinGW

Para a instalação do MinGW, recomendamos seguir os passos apresentados no seguinte [vídeo](https://www.youtube.com/watch?v=BAa7ftan_Fo&t). As etapas consistem no download do MinGW disponível no seguinte [link](https://sourceforge.net/projects/mingw/), a instalação seguida por adicionar o MinGW nas variáveis de ambiente do Windows, seguidas pela configuração do VSCode.

#### 1.2.2 Instalar o compilador g++ via WSL

WSL é uma adição recente do Windows em que uma máquina virtual Linux é criada dentro do ambiente Windows. Essa máquina virtual é bastante "pequena" e possui boa relação com as outras ferramentas do ambiente Windows. Existe o tutorial [oficial](https://docs.microsoft.com/pt-br/windows/wsl/install) que apresentaremos de forma resumida aqui.

É necessário ter Windows 11 ou Windows 10 com versão superior a 19041 (possível de se verificar em "Informações do sistema"). No Prompt de comando use:

```
wsl --install
```

Esse comando instalará uma distribuição Ubuntu no seu ambiente Windows. No final do processo irá pedir por um nome de usuário e senha, escolha essas credenciais. Agora, para instalar o g++, basta abrir o Ubuntu e utilizar os mesmos passos do tutorial de [[#1 1 Linux]].

É possível utilizar o VSCode com o WSL, para isso, seguinte a referência [oficial](https://code.visualstudio.com/docs/cpp/config-wsl). Com o VSCode e o WSL instalados, crie um repositório e um arquivo dentro do Ubuntu e use o comando `code .` para chamar o VSCode de dentro da distribuição, na primeira vez isso irá instalar um pacote e logo após abrir o VSCode. Nele, instale a extensão "Remote - WSL", e após isso basta seguir os mesmos passos da [[#1 1 1 Configuração VSCode]] de VSCode em um Ubuntu.

## 2. Revisão C++

### 2.1 Hello World

Vamos olhar o exemplo de um _Hello world_, observe o código:

```c
#include<iostream>

int main(){

	std::cout << "Hello world!" << std::endl;
	return 0;
}

```

Vamos entender o código por parte?

- `#include<iostream>`:  o comando `#include` é utilizado para incluir bibliotecas, em particular, estamos chamando a biblioteca _iostream_ que é utilizada para _inputs/outputs_.
- `int main(){ ...` :  `main` é o nome do _escopo_ principal do C++ que se é executado ao compilar-se, o termo `int` logo atrás é a sintaxe básica do C++ de representar o tipo de dado que a função irá retornar, nesse caso será um inteiro. Isso é um padrão do C++.
- `return 0`: pulando agora para o final, essa linha indica que será retorna 0, um inteiro como definido no início da função. O valor 0 é escolhido para o sistema/usuário saber se o código foi capaz de ser completo, caso outro valor seja retornado, ocorreu um erro.
- `std::cout`, `std::endl`: esses são comandos da biblioteca _iostream_, o primeiro passa a receber valores para exibir no terminal, e o segundo é um comando para terminar a linha. O `std::` indica que o comando está presente no _namespace_ std.
- `<<` : é a sintaxe utilizada para "adicionar conteúdo" a uma _stream_, nesse caso a _stream_ é o `std::cout` que exibe o conteúdo no terminal.
### 2.2 Tipos de dados

A linguagem C++ possui tipos de dados bases, os tipos mais utilizados são: _int_, _float_, _char_ e _bool_. 

#### 2.2.1 int, float
Como o próprio nome já diz, variáveis _int_ são para valores numéricos inteiros positivos ou negatives. Variáveis _float_ são para números "ponto flutuante", isso é, é uma representão na memória que permite amarzemanento de casas decimais. Observe o exemplo:

```c
int num1 = 1;
float num2 = 1;
float num3 = 3.1415;
```

Observe que os valores _num1_ e _num2_ são idênticos, o número 1. Mas se é possível representar qualquer inteiro como um _float_, para que eu usaria o tipo _int_? A vantagem é pois _float_ é uma aproximação de uma representação de um número real, e dessa forma, se é possível utilizar-se de um int, uma exatidão maior é obtida.
Existem outros tipos de dados como o _int_ e o _float_ que representam valores maiores e dessa forma ocupam mais espaço na memória, respectivamente, o _long int_ e o _double_.
Usando o pacote _limits_, é possível se verificar o limite superior desses tipos:

```c
#include <iostream>
#include<limits>

using namespace std;

int main()
{
    cout << "Valor máximo int:" <<  numeric_limits<int>::max() << endl;
    cout << "Valor máximo long int:" << numeric_limits<long int>::max() << endl;
    cout << "Valor máximo float:" << numeric_limits<float>::max() << endl;
    cout << "Valor máximo double:" << numeric_limits<double>::max() << endl;

    return 0;
}

/*

Valor máximo int:2147483647
Valor máximo long int:9223372036854775807
Valor máximo float:3.40282e+38
Valor máximo double:1.79769e+308

*/

```

#### 2.2.3 char

O tipo _char_ é utilizado para representar caracteres ASCII, isso é, um total de 128 caracteres presentes na tabela ASCII, cada um representado por um número único. Observe o exemplo:

```c

char a1 = 'A';
char a2 = 65;

cout << (a1 == a2) << endl;

```

No exemplo acima, _a1_ e _a2_ são idênticos pois são o número referente ao caracter 'A' é 65.
#### 2.2.4 bool
Uma das mais simples, variáveis _bool_ podem assumir dois valores, verdadeiro ou falso. 

```c
bool b1 = true;
bool b2 = false;
bool b3 = (1 > 3);

```

Um _bool_ é o resultado de uma expressão com os operadores lógicos (>, <, &).

### 2.3 Funções
As funções no C++ são definidas fora do escopo _main_ da seguinte maneira:

```c
tipo nome_func(tipo param1, tipo param2){
	Etapas funções
	return;
}
```

O _tipo_ é o tipo da variável que a função irá retornar, em caso que não vá retornar algo, esse tipo deve ser substituido por _void_, e o comando _return;_ deve estar presente vazio. Os parâmetros que a função recebe também devem ter o tipo definido anteriormente.

```c
int dobro(int num){
	return 2*num;
}

void exibir_hello_world(){
	cout << "Hello world" << endl;
	return;
}
```

Também é possível definir parâmetros com valores já pré-definidos utilizando um símbolo _=_ na declaração, observe o exemplo:

```c
void(int cod = 12345){
	cout << "Hello world, student nº" << cod << endl;
	return;
}
```

### 2.4 Controle de fluxo
O C++ também possui os controladores de fluxo comus: _if/else_, _for_, _while_. A sintaxe deles é bastante similar a usada no Javascript.

#### 2.4.1 if/else

```c
if(condition){
	Executado quando condition é verdade
}else if(other condition){
	Executado quando other condition é verdade
}else{
	Executado quando todas as condition são falsas
}


int num = 5;
if(num < 5){
	num = 1;
}else if(num > 5){
	num = 2;
}else{
	num = 3;
}

```

Caso a os passos de if/else sejam de apenas uma linha podemos escrever da seguinte forma:

```c
if(condition) Executado quando condition é verdade;
else if(other condition) Executado quando other condition é verdade;
else Executado quando todas as condições são falsas;

num = 5;
if(num < 5) num = 1;
else if(num > 5) num = 2;
else num = 3;

```

Uma maneira mais curta ainda para problemas com 1 condição é o operador ternário:

```c
condition ? (expressão se a condition verdadeira) : (expressão se falsa)

int num2 = num > 0 : 1000 ? -1000;
```

A condição dentro do _if_ é executada seguindo uma ordem (parentêses, da esquerda para direita), e caso não seja necessário executar tudo para saber se é verdade ou não, o C++ não executa, por exemplo:

```C

3/0; //Essa linha vai dar erro

if(1 > 10 && 3/0) int i = 0;
//Não vai dar erro pois apenas verificar que 1 > 10 é falso é suficiente 
//para saber se a condição é verdade ou não

```

#### 2.4.2 for

```c
for(initialization; condition; update){
	Código executado repetidas vezes
}

/*
 O initialization é executado apenas uma vez antes do loop, é uma atribuição
 O condition é a condição se o código vai ser executado ou não 
 O update é executado sempre que que o código interno é executado
*/


//Estrutura comum de um for
for(int i = 0; i < 10; i++){
	continue;
}

// Caso seja uma única linha
for(int i = 0; i < 10; i++) continue;

```

De maneira similar ao if, a condição pode não ser executada por completo, apenas o necessário para saber o valor que ela assume. Outro detalhe é que a inicialização e a atualização podem ter mais de uma expressão separadas por vírgulas:

```c
for(int i = 0, int j = 10; i < j; i++, j--) continue;

```

Um detalhe é que uma variável inicializada dentro de uma expressão for, só vai existir dentro do escopo desse for, e não fora dele.

#### 2.4.3 While

```c
while(condition){
	Código executado
}


int i = 10;
while(i < 20){
	i++;
}

```

#### 2.4.4 Break, continue
Os comandos _break_ e _continue_ são usados dentro de loops para interromper  as iterações (break) ou para pular para a próxima (continue). Podem ser usados tanto em for quanto em whiles.

```c
int k = 0;
for(int i = 0; i < 10; i++){
	if(i >= 5) break;
	if(i == 3) continue;
	k++;
}

// Qual o valor de k?

```

