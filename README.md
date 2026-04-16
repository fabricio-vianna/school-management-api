# SchoolMaster 🎓

API de gestão acadêmica desenvolvida em Java, com foco em organização em camadas, separação de responsabilidades e acesso a dados via JDBC utilizando o padrão DAO.

O projeto simula um cenário real de controle acadêmico, incluindo gerenciamento de alunos, professores, cursos, disciplinas e avaliações, com persistência em banco relacional (MySQL).

---

## 📌 Visão Geral

O **SchoolMaster** foi projetado com uma arquitetura limpa e extensível, aplicando boas práticas comuns em sistemas backend corporativos:

- Separação em camadas (Application, Service, DAO, Domain)
- Uso de **JDBC puro** para controle explícito de persistência
- Implementação do padrão **DAO (Data Access Object)**
- Organização orientada a domínio (entities + regras de negócio)

---

## 🧱 Arquitetura

Estrutura baseada em camadas, promovendo baixo acoplamento e alta coesão:

```
src/
├── application/        # Camada de entrada (CLI / execução)
├── db/                 # Conexão, gerenciamento de recursos JDBC
├── model/
│   ├── entities/       # Domínio da aplicação (POJOs)
│   ├── dao/            # Contratos (interfaces)
│   └── dao/impl/       # Implementações JDBC (SQL)
└── services/           # Regras de negócio
```

### Principais responsabilidades

- **Entities**: Representação do domínio (Aluno, Professor, Curso, etc.)
- **DAO**: Abstração de acesso a dados
- **Service**: Orquestração de regras de negócio
- **Application**: Interface de interação (console)

---

## ⚙️ Funcionalidades

- Cadastro e gestão de **Cursos e Disciplinas**
- Gestão de **Alunos e Professores**
- Controle de **Matrículas**
- Registro de **Avaliações (nota e frequência)**
- Geração de **boletim acadêmico**

---

## 🗄️ Modelo de Domínio

Principais entidades:

- **Aluno**: possui histórico acadêmico e avaliações
- **Professor**: responsável por disciplinas
- **Curso**: agrega alunos e disciplinas
- **Disciplina**: vinculada a curso e professor
- **Matrícula**: relação entre aluno e curso
- **Avaliação**: desempenho do aluno por disciplina

Relacionamentos principais:

- Curso → Alunos / Disciplinas (1:N)
- Professor → Disciplinas (1:N)
- Aluno → Avaliações (1:N)

---

## 🛠️ Tecnologias

- Java 8+
- JDBC
- MySQL
- Padrão DAO

---

## 🚀 Execução

### 1. Configuração do banco

Criar o schema:

```sql
CREATE DATABASE schoolmaster;
```

Configurar o arquivo `db.properties`:

```properties
dburl=jdbc:mysql://localhost:3306/schoolmaster?useSSL=false
user=seu_usuario
password=sua_senha
```

### 2. Executar

Via IDE ou terminal:

```bash
javac -cp .:mysql-connector.jar application/Program.java
java -cp .:mysql-connector.jar application.Program
```

---

## 💡 Destaques Técnicos

- Controle manual de conexões e recursos JDBC
- Implementação explícita de SQL (sem ORM)
- Aplicação de padrões de projeto utilizados no mercado
- Estrutura preparada para evolução para frameworks como Spring Boot

---

## 📄 Licença

MIT License
