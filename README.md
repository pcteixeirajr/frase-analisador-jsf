# 📘 Analisador de Frases - JSF + Java 8

Sistema Web desenvolvido com foco em simplicidade, clareza de arquitetura e boas práticas modernas em Java EE 7, para análise de frases.  
Permite ao usuário digitar uma frase e obter:

- Total de palavras distintas
- Total geral de palavras
- Palavra mais frequente
- Ocorrências de cada palavra, ordenadas

Este projeto é totalmente compatível com **Java 8**, **JSF 2.2**, **CDI 1.2** e **WildFly 10**.

Esta arquitetura deste projeto segue um modelo MVC desacoplado com JSF + CDI, respeitando boas práticas de projetos Java EE baseados em Web.

---

## ✅ Benefícios da Arquitetura

- ✨ Fácil manutenção e extensão
- 🧪 Testabilidade isolada das camadas
- 🔌 Pronto para conectar a banco, REST ou filtros
- 📚 Padronizado e fácil de entender por qualquer dev Java EE

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
src/main/java/br/com/teste/
│
├── controller       -> Backing Beans (JSF + CDI)
├── service          -> Regras de negócio centralizadas
├── model            -> Estrutura de dados (Palavra)
└── util             -> Utilitários para processamento de texto
```

---

## 🔍 Funcionalidade

1. O usuário digita uma frase no campo de texto.
2. O sistema limpa e normaliza a frase (remove pontuação, espaços redundantes).
3. A análise retorna:
   - Mapa de palavras e suas contagens
   - Palavra mais frequente
   - Total de palavras (incluindo repetições)

---

## 💡 Boas Práticas Aplicadas

- Separação clara de camadas (`controller`, `service`, `model`, `util`)
- Escopos CDI adequados (`@RequestScoped`, `@ApplicationScoped`)
- Utilização de `TreeMap` para ordenação alfabética automática
- `TextoUtils` centraliza regras de normalização de texto
- Classe `Palavra` estruturada para possíveis extensões (JPA-ready)
- 100% compatível com Java 8 (sem uso de `.isBlank()`, `var`, `stream().toList()` etc.)

---

## ✅ Testes Automatizados

Este projeto foi estruturado para oferecer **testabilidade completa** das principais camadas de negócio, utilizando ferramentas modernas e compatíveis com **Java 8**.

Foram aplicadas boas práticas como:

- **Testes isolados** por responsabilidade (`controller`, `service`, `util`, `model`)
- Uso de **JUnit 5** para definição de cenários
- Uso de **Mockito** para mocks em testes de beans com dependência de serviço
- Uso de **AssertJ** para asserções legíveis e robustas

### 📁 Estrutura dos testes

```text
src/test/java/br/com/teste/
│
├── controller       -> Testes unitários de FraseBean com Mockito
├── service          -> Testes puros da lógica de negócio
├── model            -> Testes de equals, hashCode, toString
└── util             -> Testes de normalização e extração de palavras
```

### 📌 Cobertura de Testes

| Camada       | Classe de Teste               | Frameworks Utilizados     |
|--------------|-------------------------------|----------------------------|
| Controller   | `FraseBeanTest`               | JUnit 5, Mockito, AssertJ  |
| Service      | `AnalisadorFraseServiceTest`  | JUnit 5, AssertJ           |
| Model        | `PalavraTest`                 | JUnit 5, AssertJ           |
| Utilitário   | `TextoUtilsTest`              | JUnit 5, AssertJ           |

### 🔧 Dependências necessárias (já inclusas no `pom.xml`)

```xml
<dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter</artifactId>
  <version>5.9.3</version>
  <scope>test</scope>
</dependency>
<dependency>
  <groupId>org.mockito</groupId>
  <artifactId>mockito-core</artifactId>
  <version>5.11.0</version>
  <scope>test</scope>
</dependency>
<dependency>
  <groupId>org.mockito</groupId>
  <artifactId>mockito-junit-jupiter</artifactId>
  <version>5.11.0</version>
  <scope>test</scope>
</dependency>
<dependency>
  <groupId>org.assertj</groupId>
  <artifactId>assertj-core</artifactId>
  <version>3.24.2</version>
  <scope>test</scope>
</dependency>
```

### ▶️ Executando os testes

```bash
mvn test
```

Ou através da IDE, clicando com o botão direito sobre as classes de teste.

---

## 🚀 Como Rodar o Projeto no Eclipse (Enterprise Java and Web Developers 2025-03)

### 1. Importar o projeto Maven

- Abra o Eclipse.
- Vá em File > Import...
- Selecione Maven > Existing Maven Projects
- Clique em Next, e selecione a pasta raiz do projeto (frase-analisador-jsf).
- Conclua com Finish.

### 2. Adicionar o servidor WildFly

- Vá em Window > Show View > Servers
- Clique com o botão direito → New > Server
- Escolha WildFly 10.x e informe o caminho
- Finalize

### 3. Adicionar o projeto ao servidor

- Clique com o botão direito sobre o WildFly → Add and Remove...
- Adicione o projeto `frase-analisador-jsf`

### 4. Iniciar o servidor

- Clique com o botão direito no WildFly e escolha Start

### 5. Acessar no navegador

```bash
http://localhost:8080/frase-analisador-jsf/pages/index.xhtml
```

---

## 🚀 Como Rodar o Projeto (IntelliJ Community + WildFly)

### 1. Clonar ou baixar o repositório

```bash
git clone https://github.com/seuusuario/frase-analisador-jsf.git
cd frase-analisador-jsf
```

### 2. Gerar o `.war` com Maven

```bash
mvn clean install
```

### 3. Fazer o deploy no WildFly

```bash
cp target/frase-analisador-jsf.war {WILDFLY_HOME}/standalone/deployments/
```

### 4. Iniciar o WildFly

```bash
{WILDFLY_HOME}/bin/standalone.bat    # Windows
{WILDFLY_HOME}/bin/standalone.sh     # Linux/macOS
```

### 5. Acessar no navegador

```bash
http://localhost:8080/frase-analisador-jsf/pages/index.xhtml
```

---

## 🧪 Teste Manual

Digite qualquer frase na aplicação e verifique os resultados.

**Exemplo:**

```
O tempo perguntou ao tempo quanto tempo o tempo tem
```

**Resultado esperado:**

- Palavras distintas: 7  
- Palavra mais frequente: tempo (4x)  
- Total de palavras: 10

---

## 📌 Observações Técnicas

- O projeto **não depende de banco de dados**
- Integração entre JSF e CDI com `@Named`, `@Inject`, `@RequestScoped`, `@ApplicationScoped`
- Estrutura pronta para REST, banco de dados, segurança, i18n

---

## 🤝 Contribuições

Projeto criado como exercício técnico.  
Sinta-se à vontade para bifurcar, adaptar ou evoluir.

---

## 🧠 Autor

**Paulo Junior**  
Software Developer

---

> “Código limpo é aquele que você tem orgulho de entregar. Mesmo que ninguém veja.”  
> – Um dev sênior feliz 😄
