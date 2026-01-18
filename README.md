# 🏥 ClinicPed+

![NestJS](https://img.shields.io/badge/Backend-NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)
![React Native](https://img.shields.io/badge/Mobile-React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![TypeScript](https://img.shields.io/badge/Language-TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)

> **Uma solução Full Stack escalável para gestão clínica e agendamento de consultas.**

---

## 📖 Sobre o Projeto

O **ClinicPed+** é um ecossistema desenvolvido para modernizar o fluxo de atendimento em clínicas médicas. O projeto foi arquitetado com foco em **performance**, **segurança de dados** e **experiência do usuário (UX)**.

Diferente de um simples CRUD, o sistema implementa regras de negócio complexas, como validação de conflitos de horário, integração com APIs externas (CEP) e controle de acesso baseado em cargos (RBAC - Role Based Access Control).

---

## 🏗️ Arquitetura e Decisões Técnicas

O sistema foi desenhado seguindo os princípios de **Clean Architecture** e **SOLID**, garantindo que o código seja modular e testável.

### 🔌 Backend (NestJS)
A API foi construída pensando em escalabilidade vertical e horizontal.
- **Modularização:** Separação clara entre módulos (Auth, Users, Clinics, Appointments).
- **Security First:** Autenticação via **JWT (JSON Web Token)** e hash de senhas com **Bcrypt**.
- **Data Integrity:** Uso de **DTOs (Data Transfer Objects)** com `class-validator` para garantir que nenhum dado inválido chegue ao banco.
- **External Services:** Integração com API de CEP para preenchimento automático e normalização de endereços no banco de dados.

### 📱 Mobile (React Native)
O aplicativo foca na usabilidade e feedback visual imediato.
- **State Management:** Gerenciamento de estado otimizado para evitar re-renderizações desnecessárias.
- **UX Patterns:** Uso de máscaras (Input Masking) para CPF e Telefone, reduzindo erros de input do usuário.
- **Feedback Visual:** Tratamento de erros amigável e loadings skeleton para melhor percepção de performance.

---

## ✨ Funcionalidades

### 🔐 Controle de Acesso & Segurança
- [x] Login e Registro com validação robusta.
- [x] Proteção de rotas via **Guards** (NestJS).
- [x] Criptografia de dados sensíveis.

### 🏥 Gestão de Clínicas (Admin)
- [x] Cadastro completo de clínicas com busca automática de endereço via CEP.
- [x] Gerenciamento de médicos e especialidades.
- [x] Dashboard administrativo.

### 📅 Agendamento (Usuário)
- [x] Busca de clínicas e médicos por especialidade.
- [x] Visualização de horários disponíveis em tempo real.
- [x] Histórico de consultas agendadas.

---

## 🛠️ Tech Stack

| Camada | Tecnologia | Motivo da Escolha |
| :--- | :--- | :--- |
| **Backend** | **NestJS** | Framework opinionado que força boas práticas e arquitetura modular. |
| **Mobile** | **React Native** | Desenvolvimento ágil cross-platform (iOS/Android) com performance nativa. |
| **Linguagem** | **TypeScript** | Tipagem estática para reduzir bugs em tempo de compilação. |
| **Database** | **PostgreSQL** | Robustez, suporte a transações ACID e integridade relacional. |
| **ORM** | **Prisma / TypeORM** | Abstração segura e eficiente para queries no banco de dados. |

---

## 📂 Estrutura do Projeto (Monorepo Like)

```bash
ClinicPed/
├── backend/            # API Restful em NestJS
│   ├── src/
│   │   ├── modules/    # Módulos da aplicação (Auth, Users, Appointments)
│   │   ├── shared/     # Serviços compartilhados e Utils
│   │   └── main.ts     # Ponto de entrada
│   └── test/           # Testes automatizados
│
└── mobile/             # Aplicação React Native
    ├── src/
    │   ├── components/ # Componentes reutilizáveis (Inputs, Buttons, Cards)
    │   ├── screens/    # Telas da aplicação
    │   ├── services/   # Integração com a API (Axios)
    │   └── utils/      # Máscaras e Formatações
    └── package.json
