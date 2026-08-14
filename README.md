# DDD & Clean Architecture

### Projeto de estudos em arquitetura de software com Next.js e TypeScript

Este projeto foi desenvolvido com o objetivo de estudar e aplicar conceitos relacionados a **Domain-Driven Design (DDD)**, **Clean Architecture**, separação de responsabilidades e organização modular de aplicações.

A aplicação utiliza um domínio simplificado de cadastro de pacientes para explorar a separação entre entidades de domínio, casos de uso, infraestrutura e componentes de interface.

O foco principal do projeto não é a complexidade da interface, mas a **organização do código e a divisão das responsabilidades entre diferentes camadas da aplicação**.

---

## Objetivo

O projeto busca consolidar conhecimentos relacionados a:

- Domain-Driven Design
- Clean Architecture
- Separação de responsabilidades
- Organização modular
- Entidades de domínio
- Casos de uso
- Repository Pattern
- Programação Orientada a Objetos
- TypeScript
- React
- Next.js

---

## Tecnologias

| Área | Tecnologias |
|---|---|
| Linguagem | TypeScript |
| Framework | Next.js |
| Interface | React |
| Estilização | CSS, Tailwind CSS |
| Qualidade | ESLint |
| Gerenciamento de pacotes | NPM |
| Versionamento | Git e GitHub |

---

## Estrutura do projeto

O código principal está dividido entre a aplicação Next.js e os módulos responsáveis pelo domínio.

```text
src/
├── app/
│   ├── pacientes/
│   ├── layout.tsx
│   ├── globals.css
│   └── estilo.css
│
└── modules/
    ├── Documento/
    ├── Endereco/
    ├── Paciente/
    ├── Telefone/
    └── Usuario/
```

Cada módulo pode possuir responsabilidades organizadas em camadas como:

```text
Application/
Components/
Domain/
Infrastructure/
```

---

## Organização em camadas

### Domain

A camada de domínio representa os principais conceitos da aplicação.

Entre as entidades existentes estão:

- Usuário
- Paciente
- Documento
- Endereço
- Telefone

Essas classes concentram dados e comportamentos relacionados aos conceitos representados pelo sistema.

---

### Application

A camada `Application` contém os casos de uso responsáveis por coordenar as operações da aplicação.

No módulo de pacientes existem operações como:

```text
InserirPaciente
BuscarPacientePorId
ListarPacientes
AtualizarPaciente
RemoverPaciente
```

O objetivo dessa camada é manter a execução dos casos de uso separada dos detalhes da interface.

---

### Infrastructure

A camada de infraestrutura contém implementações responsáveis pelo armazenamento e recuperação dos dados utilizados pelos casos de uso.

Na versão atual, o projeto utiliza um **repository em memória**, permitindo estudar o Repository Pattern sem adicionar inicialmente a complexidade de um banco de dados.

Exemplo conceitual:

```text
Interface
    ↓
Application
    ↓
Repository
    ↓
Armazenamento em memória
```

Essa implementação poderá futuramente ser substituída por uma infraestrutura de persistência real sem alterar a responsabilidade central das outras camadas.

---

### Components

Os componentes React representam a camada visual utilizada para interação com o domínio.

O módulo de pacientes possui componentes responsáveis pelo formulário e pela listagem dos registros.

```text
PacienteForm
PacienteList
```

A interface utiliza os casos de uso da camada `Application` para executar as operações.

---

## Domínio

O domínio utilizado no projeto representa um cenário simplificado de cadastro de pacientes.

### Paciente

A entidade `Paciente` estende `Usuario` e acrescenta informações específicas, como:

- idade;
- peso;
- altura;
- endereço.

Também possui validações básicas para impedir valores inválidos de idade, peso e altura.

---

### Usuário

Representa informações comuns utilizadas pelas entidades relacionadas a usuários.

O conceito é utilizado como base para especializações dentro do domínio.

---

### Endereço

Representa os dados de localização associados ao paciente.

---

### Documento

Representa informações relacionadas aos documentos do usuário.

---

### Telefone

Representa informações de contato relacionadas ao domínio.

---

## Fluxo simplificado

Uma operação realizada pela interface segue, conceitualmente, o seguinte caminho:

```text
Componente React
      ↓
Caso de uso
      ↓
Entidade de domínio
      ↓
Repository
      ↓
Armazenamento
```

Essa separação permite estudar como diferentes responsabilidades podem permanecer desacopladas dentro de uma aplicação.

---

## Funcionalidades atuais

No módulo de pacientes, o projeto trabalha com operações relacionadas a:

- cadastro de pacientes;
- listagem de pacientes;
- busca de paciente por identificador;
- atualização de dados;
- remoção de pacientes;
- manipulação de entidades relacionadas;
- validações básicas no domínio.

---

## Interface

A rota principal implementada para interação com o módulo é:

```text
/pacientes
```

A página utiliza componentes React responsáveis pelo cadastro e pela exibição da lista de pacientes.

O fluxo da interface utiliza os casos de uso da aplicação em vez de concentrar toda a lógica diretamente nos componentes.

---

## Persistência atual

Nesta etapa do projeto, os pacientes são armazenados **em memória**.

O `PacienteRepository` mantém os registros em uma estrutura interna durante a execução da aplicação.

Isso significa que a versão atual **não utiliza banco de dados** e que os registros não devem ser considerados persistência permanente.

A escolha permite concentrar o estudo inicialmente em:

- domínio;
- casos de uso;
- repositories;
- separação em camadas;
- fluxo entre componentes e aplicação.

Uma evolução futura poderá substituir o repository em memória por uma implementação utilizando banco de dados.

---

## Conceitos estudados

### Domain-Driven Design

O projeto experimenta conceitos de organização do software em torno de elementos do domínio, utilizando entidades e módulos que representam conceitos da aplicação.

### Clean Architecture

A estrutura busca separar diferentes responsabilidades da aplicação e reduzir o acoplamento direto entre interface, regras e mecanismos de armazenamento.

### Repository Pattern

O acesso aos dados é concentrado em repositories, evitando que os componentes de interface manipulem diretamente o mecanismo de armazenamento.

### Casos de uso

As operações da aplicação são representadas por classes específicas na camada `Application`.

### Programação Orientada a Objetos

As entidades utilizam conceitos como:

- classes;
- encapsulamento;
- herança;
- getters e setters;
- validações;
- composição entre objetos.

---

## Executando o projeto

Clone o repositório:

```bash
git clone https://github.com/diegodemelo/ddd-clean-arch.git
```

Entre no diretório:

```bash
cd ddd-clean-arch
```

Instale as dependências:

```bash
npm install
```

Execute o ambiente de desenvolvimento:

```bash
npm run dev
```

Depois acesse:

```text
http://localhost:3000/pacientes
```

---

## Scripts

### Desenvolvimento

```bash
npm run dev
```

### Build

```bash
npm run build
```

### Produção

```bash
npm run start
```

### Lint

```bash
npm run lint
```

---

## Status

**Projeto de estudos em evolução.**

O objetivo do repositório é acompanhar a aplicação progressiva de conceitos relacionados a arquitetura de software.

Entre as possíveis evoluções estão:

- implementação de persistência em banco de dados;
- criação de interfaces para repositories;
- aplicação de inversão de dependência;
- ampliação das regras do domínio;
- melhoria da tipagem dos componentes;
- criação de testes automatizados;
- ampliação dos casos de uso;
- melhorias na interface;
- evolução da arquitetura.

---

## Aprendizados

Este projeto permite exercitar conhecimentos relacionados a:

- arquitetura de aplicações;
- Domain-Driven Design;
- Clean Architecture;
- TypeScript;
- React;
- Next.js;
- programação orientada a objetos;
- organização modular;
- casos de uso;
- Repository Pattern;
- separação de responsabilidades;
- desenvolvimento front-end.

---

## Observação

Este é um **projeto educacional voltado ao estudo de arquitetura de software**.

A implementação representa um processo de aprendizagem e evolução progressiva dos conceitos utilizados, não uma arquitetura de referência definitiva para ambientes de produção.

---

## Autor

**Diego de Melo**

Desenvolvedor Full Stack Júnior

**Stack:**  
JavaScript • TypeScript • React • Next.js • Node.js • PostgreSQL

**LinkedIn:** 
[Diego de Melo](https://www.linkedin.com/in/diegodemelodev)

**GitHub:**  
[@diegodemelo](https://github.com/diegodemelo)

---

### Estudos em DDD • Clean Architecture • TypeScript • Next.js
