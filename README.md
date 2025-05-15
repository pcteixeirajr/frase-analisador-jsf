# 📘 Analisador de Frases - JSF + Java 8

Sistema Web desenvolvido com foco em simplicidade, clareza de arquitetura e boas práticas modernas em Java EE 7, para análise de frases.  
Permite ao usuário digitar uma frase e obter:

- Total de palavras distintas
- Total geral de palavras
- Palavra mais frequente
- Ocorrências de cada palavra, ordenadas

Este projeto é totalmente compatível com **Java 8**, **JSF 2.2**, **CDI 1.2** e **WildFly 10**.

A arquitetura segue o padrão **MVC desacoplado com JSF + CDI**, promovendo clareza, extensibilidade e testabilidade.

---

## ✅ Benefícios da Arquitetura

- ✨ Fácil manutenção e extensão
- 🧪 Camadas testáveis isoladamente
- 🔌 Pronto para conectar a banco, REST ou filtros
- 📚 Padronizado e compreensível por qualquer dev Java EE

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia     | Versão / Observação  |
|----------------|----------------------|
| Java           | 8 (Temurin/OpenJDK)  |
| JSF            | 2.2                  |
| PrimeFaces     | 6.2                  |
| CDI            | 1.2                  |
| Maven          | 3.x                  |
| Servidor       | WildFly 10.x         |
| HTML/CSS       | XHTML com PrimeFaces |
| Codificação    | UTF-8                |

---

## 📦 Estrutura de Pacotes

```text
src/main/java/br/com/contador/
│
├── controller       -> Backing Beans (JSF + CDI)
├── service          -> Lógica central de análise de frases
├── model            -> Representação da palavra e frequência
└── util             -> Utilitários para processamento textual

src/test/java/br/com/contador/
├── controller       -> Testes unitários do bean JSF
├── service          -> Testes da regra de negócio
├── model            -> Testes de equals, hashCode, toString
└── util             -> Testes de extração e normalização de palavras

```

##🔍 Funcionalidade

- O usuário digita uma frase no campo de texto.
- O sistema remove acentos, pontuação e normaliza espaços.
- A frase é dividida em palavras e analisada:
- Mapa de palavras e suas ocorrências
- Palavra mais frequente
- Total de palavras (incluindo repetições)

##💡 Boas Práticas Aplicadas

- Camadas separadas com responsabilidade única
- TreeMap para ordenação automática das palavras
- TextoUtils isolado e reutilizável
- Classe Palavra pronta para persistência (futura extensão com JPA)
- Testes unitários modernos com JUnit 5, AssertJ e Mockito
- Compatibilidade rigorosa com Java 8 (sem uso de recursos pós-Java 8)

---

##✅ Testes Automatizados
O projeto inclui cobertura completa dos principais componentes:

- Camada  Arquivo de Teste	Frameworks
- controller  FraseBeanTest	JUnit 5, Mockito
- service  AnalisadorFraseServiceTest	JUnit 5, AssertJ
- model  PalavraTest	JUnit 5, AssertJ
- util  TextoUtilsTest	JUnit 5, AssertJ

---

##🚀 Como Rodar o Projeto no Eclipse (Enterprise Java and Web Developers 2025-03)
O Eclipse EE já vem preparado para trabalhar com projetos Java Web e servidores como WildFly. Siga os passos abaixo:

###1. Importar o projeto Maven
Abra o Eclipse

Vá em File > Import...

Selecione Maven > Existing Maven Projects

Selecione a pasta frase-analisador-jsf

Conclua com Finish

###2. Adicionar o servidor WildFly
Vá em Window > Show View > Servers

Clique com o botão direito → New > Server

Escolha WildFly 10.x, informe o caminho do servidor

Finalize

###3. Adicionar o projeto ao servidor
Clique com o botão direito no WildFly → Add and Remove...

Adicione o projeto frase-analisador-jsf

###4. Iniciar o servidor
Clique com o botão direito no WildFly → Start

###5. Acessar no navegador
bash
Copiar
Editar
http://localhost:8080/frase-analisador-jsf/pages/index.xhtml

---

##🚀 Como Rodar o Projeto (IntelliJ Community + WildFly)
###1. Importar o projeto
File > New > Project from Existing Sources

Escolha pom.xml

Confirme as configurações de Maven

2. Gerar o .war
bash
Copiar
Editar
mvn clean install
3. Copiar para o WildFly
bash
Copiar
Editar
cp target/frase-analisador-jsf.war {WILDFLY_HOME}/standalone/deployments/
4. Iniciar o servidor
bash
Copiar
Editar
{WILDFLY_HOME}/bin/standalone.bat    (Windows)
{WILDFLY_HOME}/bin/standalone.sh     (Linux/macOS)
5. Acessar no navegador
bash
Copiar
Editar
http://localhost:8080/frase-analisador-jsf/pages/index.xhtml
🧪 Teste Manual
Basta abrir a aplicação, digitar qualquer frase e observar os resultados.

Frase de teste:

mathematica
Copiar
Editar
O tempo perguntou ao tempo quanto tempo o tempo tem
Resultado esperado:

Palavras distintas: 7

Palavra mais frequente: tempo (4x)

Total de palavras: 10

📌 Observações Técnicas
100% compatível com Java 8

Projeto empacotado como .war com dependências provided

Usa JSF + PrimeFaces + CDI com escopos leves

Nenhum banco de dados exigido

Fácil expansão para REST, JPA ou autenticação

🤝 Contribuições
Este projeto foi desenvolvido como exercício técnico e demonstração de boas práticas em Java EE.
Fique à vontade para bifurcar, adaptar ou evoluir.

🧠 Autor
Paulo Junior
Desenvolvedor Java | Arquiteto de Soluções

LinkedIn | GitHub

“Código limpo é aquele que você tem orgulho de entregar. Mesmo que ninguém veja.”
– Um dev sênior feliz 😄

yaml
Copiar
Editar

---

### ✅ Deseja que eu gere esse `README.md` como arquivo para download agora? Posso salvá-lo direto no projeto também.
