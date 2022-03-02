# Ambiente de desenvolvimento java Debian Buster

Configurando anbiente de desenvolvimento Java no Gnu/Debian Buster

*instalando Java 11(instalado por defoult)<br>
*confira a versão<br>
$ java -version<br>

*se necessário<br>
$ sudo apt install -y openjdk-11-jdk -y<br>
$ java -version<br>

*instalando Apache Maven<br>
$ sudo apt-get update && sudo apt-get -y upgrade<br>

$ curl -O https://archive.apache.org/dist/maven/maven-3/3.8.2/binaries/apache-maven-3.8.2-bin.tar.gz<br>

$ sudo tar -zxvf apache-maven-3.8.2-bin.tar.gz<br>

*crie a pasta maven dentro de /opt<br>
$ sudo mv apache-maven-3.8.2 /opt/maven<br>

*veja se ta tudo no diretorio<br>
$ ls /opt/maven<br>

*Para executar qualquer comando maven,<br>
você precisa adicionar o diretório /opt/maven/bin à sua variável de ambiente PATH.<br>
Para fazer isso no shell bash, <br>
execute o comando abaixo para criar um novo arquivo e defina suas propriedades <br>
para que ele possa ser executado como um script<br>

$ sudo nano /etc/profile.d/maven.sh<br>

*Uma vez criado, copie e cole o seguinte código no arquivo.<br>
export JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64<br>
export M2_HOME=/opt/maven<br>
export PATH=${M2_HOME}/bin:${PATH}<br>
Salve e feche o arquivo quando terminar de inserir o conteúdo usando <br>
as teclas Ctrl+O e, em seguida, confirme com a tecla Enter e CTRL+X. <br>


*Agora, para certificar-se de que seus caminhos atualizados <br>
tenham efeito, execute o comando a seguir,
que informa ao seu shell bash para ler e <br>
anexar as alterações feitas no arquivo /etc/profile.d/maven.sh.<br> 

$ mvn -version<br>

*Agora você pode remover o arquivo apache-maven-3.8.2 <br>
que você baixou anteriormente para economizar espaço com o comando abaixo. <br>

$ sudo rm apache-maven-3.8.2-bin.tar.gz<br>

*Agora você pode executar qualquer comando do Maven no terminal.<br>
Por exemplo,se você deseja criar um novo projeto maven a partir de um modelo,<br>
pode fazê-lo digitando o seguinte comando. <br>

$ mvn archetype:generate -DgroupId={project-packaging} -DartifactId={project-name} 
-DarchetypeArtifactId={maven-template} -DinteractiveMode=fa

$ mvn archetype:generate -DgroupId=com.mkyong.hashing -DartifactId=java-project 
-DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

*Este comando diz ao Maven para criar um diretório com o groupId,<br>
o attributeId e o nome do pacote que acabei de fornecer.<br>
Esses valores também serão usados como números de versão do projeto.<br>
Ele gera uma saida no terminal onde vc pode obter informaçẽos de sucesso ou de erro.<br>

*instalando Gradle<br>
*supondo que vc tenha seguido a primeira parte |^|<br>

$ sudo mkdir /opt/gradle<br>
$ cd /opt/gradle<br>
$ wget https://downloads.gradle-dn.com/distributions/gradle-7.2-bin.zip<br>
$ unzip gradle-7.2-bin.zip<br>
$ ls /opt/gradle/<br>
$ echo "export PATH=/opt/gradle/bin:${PATH}" | sudo tee /etc/profile.d/gradle.sh<br>
$ sudo chmod +x /etc/profile.d/gradle.sh<br>
$ source /etc/profile.d/gradle.sh<br>
$ gradle -v<br>

*execute o comando ./gradlew<br>
para criação de wrappers para uso da ferramenta local e não a instalação global<br>

*gerando wrapper do maven<br>
mvn -N io.takari:maven:wrapper<br>

./maven -v<br>

## Tutorial baseado na aula do Prof. André Luis Gomes
Especialista em desenvolvimento de software - Invillia









