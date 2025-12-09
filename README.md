# 🧮 Web Service RESTful de Calculadora com Spring Boot

## 📋 Sobre o Projeto
Este repositório contém a implementação de um **Sistema Distribuído Cliente-Servidor** desenvolvido como parte das atividades da disciplina de Sistemas Distribuídos. O projeto consiste em uma calculadora web onde o cliente (interface HTML/JavaScript) se comunica com o servidor (API Java/Spring Boot) através de APIs RESTful utilizando o protocolo HTTP.

## 🎯 Objetivo
Demonstrar na prática os conceitos fundamentais de sistemas distribuídos através da implementação de um sistema cliente-servidor completo, destacando:
- Separação clara entre camadas (apresentação e lógica de negócio)
- Comunicação assíncrona entre componentes distribuídos
- Princípios da arquitetura RESTful
- Tratamento básico de exceções em APIs

## 🛠️ Tecnologias Utilizadas

| Componente | Tecnologia | Versão | Função |
|------------|------------|--------|---------|
| **Linguagem Backend** | Java | 1.8 | Lógica do servidor e API |
| **Framework** | Spring Boot | 2.1.6.RELEASE | Criação da API REST |
| **Gerenciador de Dependências** | Apache Maven | - | Build e gerenciamento |
| **Frontend** | HTML5 + JavaScript | - | Interface do usuário |
| **Servidor Web** | Tomcat (embarcado) | - | Hospedagem da aplicação |
| **Protocolo** | HTTP | 1.1 | Comunicação cliente-servidor |

## 📁 Estrutura do Projeto
```
calculadora/
├── src/main/
│   ├── java/com/calculadora/
│   │   └── Main.java              # Classe principal
│   └── resources/
│       └── static/
│           └── index.html         # Interface do cliente
├── pom.xml                        # Configuração Maven
└── README.md                      # Documentação
```


## 🚀 Como Executar o Projeto

### Pré-requisitos
- **Java 8** ou superior
- **Apache Maven**
- Navegador web moderno

### Passo a Passo

**Clone o projeto**
```bash
git clone https://github.com/seu-usuario/calculadora.git
cd calculadora
```
Compile o projeto

```bash
mvn clean install
```

Execute o servidor
```bash
mvn spring-boot:run
```

 Acesse a aplicação
 ```
Interface Web: http://localhost:8080/index.html
API: http://localhost:8080/somar/10/5
```

💻 Código Fonte
Main.java (Servidor Spring Boot)
```
java

package com.calculadora;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@RestController
@SpringBootApplication
public class Main {
    
    @GetMapping("/somar/{a}/{b}")
    public String somar(@PathVariable double a, @PathVariable double b) {
        return "Resultado: " + (a + b);
    }
    
    @GetMapping("/subtrair/{a}/{b}")
    public String subtrair(@PathVariable double a, @PathVariable double b) {
        return "Resultado: " + (a - b);
    }

    @GetMapping("/multiplicar/{a}/{b}")
    public String multiplicar(@PathVariable double a, @PathVariable double b) {
        return "Resultado: " + (a * b);
    }

    @GetMapping("/dividir/{a}/{b}")
    public String dividir(@PathVariable double a, @PathVariable double b) {
        if (b == 0) {
            return "Erro: Divisão por zero!";
        }
        return "Resultado: " + (a / b);
    }

    public static void main(String[] args) {
        SpringApplication.run(Main.class, args);
    }
}
```

index.html (Interface do Cliente)
```
html

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Calculadora Web</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .container { max-width: 400px; margin: auto; }
        input, button { margin: 5px 0; padding: 8px; width: 100%; }
        button { background-color: #4CAF50; color: white; border: none; cursor: pointer; }
        button:hover { background-color: #45a049; }
    </style>
</head>
<body>
    <div class="container">
        <h2>Calculadora Web</h2>
        <input type="number" id="num1" placeholder="Número 1">
        <input type="number" id="num2" placeholder="Número 2">
        <button onclick="calcular('somar')">Somar</button>
        <button onclick="calcular('subtrair')">Subtrair</button>
        <button onclick="calcular('multiplicar')">Multiplicar</button>
        <button onclick="calcular('dividir')">Dividir</button>
        <p id="resultado"></p>
    </div>
    <script>
        function calcular(operacao) {
            const num1 = parseFloat(document.getElementById("num1").value);
            const num2 = parseFloat(document.getElementById("num2").value);
            
            fetch(`http://localhost:8080/${operacao}/${num1}/${num2}`)
                .then(response => response.text())
                .then(data => document.getElementById("resultado").innerText = data)
                .catch(error => console.error("Erro:", error));
        }
    </script>
</body>
</html>

```
```
┌─────────────────┐     HTTP GET     ┌─────────────────┐
│                 │─────────────────▶│                 │
│   Cliente Web   │                  │   Servidor API  │
│   (HTML/JS)     │◀─────────────────│   (Spring Boot) │
│                 │   JSON/Texto     │                 │
└─────────────────┘                  └─────────────────┘
```

📝 Autor

Pedro Wilson

    Matrícula: 541491

    Curso: Engenharia de Computação

    Disciplina: Sistemas Distribuídos

    Instituição: Universidade Federal do Ceará (UFC)

    Data de Conclusão: 08 de dezembro de 2025

📚 Referências

    Documentação oficial Spring Boot: https://spring.io/projects/spring-boot

    REST API Tutorial: https://restfulapi.net/

    MDN Web Docs (Fetch API): https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
