BeautifulSoup converte documentos HTML/XML em diferentes tipos de objetos criados pela biblioteca.

# O primeiro passo é criar um objeto BeautifulSoup. Isto é feito passando uma string ou um "arquivo".

- String

helloworld = "<p>Hello World</p>"
soup_string = BeautifulSoup(helloworld)
print(soup_string)

- Um arquivo/objeto

url = "http://www.packtpub.com/books"
page = urllib2.urlopen(url)
soup_packtpage = BeautifulSoup(page)

- Também é possível abrir arquivos locais

with open("foo.html","r") as foo_file:
	soup_foo = BeautifulSoup(foo_file)

# BeautifulSoup também pode ser usado para parsear arquivos xml

- Até agora nós só temos passado um argumento quando construímos nosso objeto BeutifulSoup.

Ex: soup_string = BeautifulSoup(helloworld)

Ao criar um objeto, BS seleciona a classe TreeBuilder para criar uma árvore HTML/XML do input passado para a função BeautifulSoup. Por padrão, BS seleciona qqr um dos objetos TreeBuilder para HTML para construir a árvore, o que constrói uma árvore HTML, que usa o parser HTML por padrão.

Obs: Para Entender Melhor Estrutura do HTML:
https://pt.wikipedia.org/wiki/Modelo_de_Objeto_de_Documentos

- Por isso até temos recebido o seguinte aviso:

UserWarning: No parser was explicitly specified, so I'm using the best available HTML parser for this system ("html.parser"). This usually isn't a problem, but if you run this code on another system, or in a different virtual environment, it may use a different parser and behave differently.

•	lxml
•	html5lib
•	html.parser

A melhor maneira de determinar qual parser utilizar é especificando o argumento fetures.

Se não houver um parser que possa lidar com oa feature, será preciso instalar um.

bs4.FeatureNotFound: Couldn't find a tree builder with the features you requested: xml. Do you need to install a parser library?

Para instalar o lxml parser no nosso ambiente:

pip install lxml

Obs: Caso haja o seguinte erro:


 #include "libxml/xmlversion.h"

                               ^

compilation terminated.

Compile failed: command 'x86_64-linux-gnu-gcc' failed with exit status 1

creating tmp

cc -I/usr/include/libxml2 -c /tmp/xmlXPathInit0spKkR.c -o tmp/xmlXPathInit0spKkR.o

cc tmp/xmlXPathInit0spKkR.o -lxml2 -o a.out

error: command 'x86_64-linux-gnu-gcc' failed with exit status 1


Rode o comando sudo apt-get install libxml2-dev libxslt-dev

Mais informações:
- https://stackoverflow.com/questions/13019942/why-cant-i-get-pip-install-lxml-to-work-within-a-virtualenv


## Tags 
Quando criamos o objeto BS, outros objetos tb são criados. São eles:

•	 Tag
•	 NavigableString

As tags são objetos que representam diferente objetos do documento HTML/XML.

Já o objeto NavigableString armazena o texto da tag.
