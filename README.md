🧮 Web Service RESTful de Calculadora com Spring Boot

Este repositório contém a implementação de um Sistema Distribuído Cliente-Servidor. O serviço backend (servidor) é uma API REST desenvolvida em Java com Spring Boot, e o frontend (cliente) é uma interface gráfica em HTML/JavaScript que consome esta API.
🌟 Visão Geral do Projeto

O projeto demonstra a aplicação dos conceitos de Sistemas Distribuídos (SD) e a arquitetura RESTful, garantindo que a lógica de negócio (cálculos) e a camada de apresentação (interface) sejam independentes e fracamente acopladas.

    Servidor: Spring Boot (Java)

    Cliente: HTML5 + JavaScript (comunicação via fetch())

    Comunicação: HTTP GET usando Path Variables.

🛠️ Tecnologias Utilizadas
Componente	Tecnologia	Versão	Função
Linguagem	Java	1.8	Lógica do backend
Framework	Spring Boot	2.1.6.RELEASE	Criação rápida da API REST
Build/Dependências	Apache Maven	(Qualquer versão recente)	Gerenciamento do projeto
Cliente	HTML5/JavaScript	N/A	Interface de Usuário (UI) e requisições
🚀 Como Executar o Projeto

Siga os passos abaixo para compilar e iniciar a aplicação.
1. Pré-requisitos

Certifique-se de ter o Java 8 (ou superior) e o Apache Maven instalados em sua máquina.
2. Compilação e Empacotamento

Navegue até o diretório raiz do projeto (/calculadora) no seu terminal e execute o Maven para limpar, compilar e empacotar o projeto em um arquivo JAR executável:
Bash

mvn clean install

3. Execução do Servidor

Execute o aplicativo usando o plugin do Spring Boot, que iniciará o servidor web embutido (Tomcat) na porta padrão 8080:
Bash

mvn spring-boot:run

🌐 Endpoints da API REST

O servidor estará acessível em http://localhost:8080/. A API REST utiliza o padrão /operacao/{operando1}/{operando2}.
Operação	Método	URL (Padrão)	Exemplo de Teste	Resposta Esperada
Soma	GET	/somar/{a}/{b}	/somar/10/5	Resultado: 15.0
Subtração	GET	/subtrair/{a}/{b}	/subtrair/10/5	Resultado: 5.0
Multiplicação	GET	/multiplicar/{a}/{b}	/multiplicar/4/3	Resultado: 12.0
Divisão	GET	/dividir/{a}/{b}	/dividir/9/2	Resultado: 4.5
Divisão por Zero	GET	/dividir/10/0	/dividir/10/0	Erro: Divisão por zero!
🖥️ Acessando a Interface Cliente

Após iniciar o servidor (Passo 3), abra seu navegador e acesse a interface gráfica:

http://localhost:8080/index.html

A interface usará JavaScript para enviar requisições HTTP GET aos endpoints listados acima.
📂 Estrutura do Projeto

A estrutura de diretórios segue o padrão de uma aplicação Maven e Spring Boot:

calculadora/
├── src/main/
│   ├── java/com/calculadora/
│   │   ├── Main.java         <-- Controlador REST e Entry Point
│   │   └── CalculatorController.java (Removido para seguir o roteiro)
│   └── resources/
│       └── static/
│           └── index.html    <-- Interface Cliente (Frontend)
├── pom.xml                   <-- Configuração e Dependências Maven
└── target/                   <-- Artefato executável (.jar)

📝 Autor

    Pedro Wilson

    Disciplina: Sistemas Distribuídos - UFC