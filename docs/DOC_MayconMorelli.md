# FitPass Gym Management
# Documento Único — Casos de Uso e Diagramas de Atividade

**Aluno:** Maycon Gabriel da Silva Morelli (24001786)
**Disciplina:** Engenharia de Software | **Professor:** Marcelo Marud | **UNIFEOB — 2026**

---

## Índice

| # | Caso de Uso | Ator Principal |
|---|---|---|
| UC01 | [Cadastrar Aluno](#uc01--cadastrar-aluno) | Recepcionista |
| UC02 | [Atualizar Dados do Aluno](#uc02--atualizar-dados-do-aluno) | Recepcionista |
| UC03 | [Criar Plano](#uc03--criar-plano) | Gerente |
| UC04 | [Editar Plano](#uc04--editar-plano) | Gerente |
| UC05 | [Registrar Pagamento](#uc05--registrar-pagamento) | Recepcionista |
| UC06 | [Verificar Regularidade](#uc06--verificar-regularidade) | Sistema |
| UC07 | [Liberar Acesso na Catraca](#uc07--liberar-acesso-na-catraca) | Aluno |
| UC08 | [Visualizar Aulas](#uc08--visualizar-aulas) | Aluno |
| UC09 | [Agendar Aula](#uc09--agendar-aula) | Aluno |
| UC10 | [Cancelar Agendamento](#uc10--cancelar-agendamento) | Aluno |
| UC11 | [Registrar Presença](#uc11--registrar-presença) | Instrutor |
| UC12 | [Visualizar Lista de Presença](#uc12--visualizar-lista-de-presença) | Instrutor |
| UC13 | [Registrar Avaliação Física](#uc13--registrar-avaliação-física) | Instrutor |
| UC14 | [Consultar Avaliação Física](#uc14--consultar-avaliação-física) | Instrutor |
| UC15 | [Gerar Relatório de Alunos](#uc15--gerar-relatório-de-alunos) | Gerente |
| UC16 | [Gerar Relatório de Inadimplência](#uc16--gerar-relatório-de-inadimplência) | Gerente |
| UC17 | [Gerar Relatório de Acessos](#uc17--gerar-relatório-de-acessos) | Gerente |
| UC18 | [Enviar Notificação de Pagamento](#uc18--enviar-notificação-de-pagamento) | Sistema |
| UC19 | [Enviar Confirmação de Aula](#uc19--enviar-confirmação-de-aula) | Sistema |
| UC20 | [Notificar Nova Avaliação Física](#uc20--notificar-nova-avaliação-física) | Sistema |

---

## Diagrama de Casos de Uso

```plantuml
@startuml FitPass_CasosDeUso_Maycon

skinparam actorStyle awesome
left to right direction

actor Aluno as AL
actor Recepcionista as RE
actor Instrutor as IN
actor Gerente as GE
actor "Sistema" as SI

rectangle "FitPass Gym Management" {

  package "Gestão de Alunos" {
    usecase "UC01 - Cadastrar Aluno" as UC01
    usecase "UC02 - Atualizar Dados do Aluno" as UC02
  }

  package "Gestão de Planos" {
    usecase "UC03 - Criar Plano" as UC03
    usecase "UC04 - Editar Plano" as UC04
  }

  package "Financeiro" {
    usecase "UC05 - Registrar Pagamento" as UC05
    usecase "UC06 - Verificar Regularidade" as UC06
  }

  package "Controle de Acesso" {
    usecase "UC07 - Liberar Acesso na Catraca" as UC07
  }

  package "Agendamentos" {
    usecase "UC08 - Visualizar Aulas" as UC08
    usecase "UC09 - Agendar Aula" as UC09
    usecase "UC10 - Cancelar Agendamento" as UC10
  }

  package "Presença e Avaliação" {
    usecase "UC11 - Registrar Presença" as UC11
    usecase "UC12 - Visualizar Lista de Presença" as UC12
    usecase "UC13 - Registrar Avaliação Física" as UC13
    usecase "UC14 - Consultar Avaliação Física" as UC14
  }

  package "Relatórios" {
    usecase "UC15 - Relatório de Alunos" as UC15
    usecase "UC16 - Relatório de Inadimplência" as UC16
    usecase "UC17 - Relatório de Acessos" as UC17
  }

  package "Notificações" {
    usecase "UC18 - Notificar Pagamento" as UC18
    usecase "UC19 - Confirmar Aula" as UC19
    usecase "UC20 - Notificar Nova Avaliação" as UC20
  }
}

RE --> UC01
RE --> UC02
RE --> UC05

GE --> UC03
GE --> UC04
GE --> UC15
GE --> UC16
GE --> UC17

AL --> UC07
AL --> UC08
AL --> UC09
AL --> UC10

IN --> UC11
IN --> UC12
IN --> UC13
IN --> UC14

SI --> UC06
SI --> UC18
SI --> UC19
SI --> UC20

UC09 ..> UC19 : <<include>>
UC06 ..> UC07 : <<include>>
UC14 ..> UC13 : <<extend>>

@enduml
```

---

## UC01 — Cadastrar Aluno

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Recepcionista |
| **Objetivo** | Cadastrar um novo aluno no sistema. |
| **Pré-condições** | Recepcionista autenticado. |
| **Pós-condições** | Aluno registrado no sistema. |
| **RF Relacionados** | RF01 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O recepcionista acessa a opção de cadastro.
2. O sistema solicita os dados do aluno.
3. O recepcionista preenche as informações.
4. O sistema salva o cadastro.

**Fluxos Alternativos:**
- **A1 — Dados incompletos:** O sistema solicita correção.

### Diagrama de Atividade

```plantuml
@startuml DA_UC01_CadastrarAluno

|Recepcionista|
start
:Acessa a opção de cadastro de aluno;

|Sistema|
:Exibe formulário com campos obrigatórios;

|Recepcionista|
:Preenche os dados do aluno;
:Confirma o envio;

|Sistema|
:Valida os campos preenchidos;

if (Dados completos e válidos?) then (sim)
  :Salva o cadastro do aluno;
  :Exibe confirmação de sucesso;
  |Recepcionista|
  :Informa ao aluno que o cadastro foi realizado;
else (não)
  :Destaca os campos com problema;
  :Solicita correção (A1);
  |Recepcionista|
  :Corrige os dados e reenvia;
endif

stop
@enduml
```

---

## UC02 — Atualizar Dados do Aluno

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Recepcionista |
| **Objetivo** | Atualizar informações de um aluno já cadastrado. |
| **Pré-condições** | Aluno já cadastrado no sistema. |
| **Pós-condições** | Dados do aluno atualizados. |
| **RF Relacionados** | RF01 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O recepcionista busca o aluno.
2. O sistema mostra os dados atuais.
3. O recepcionista altera as informações.
4. O sistema salva as alterações.

**Fluxos Alternativos:**
- **A1 — Aluno não encontrado:** O sistema informa erro.

### Diagrama de Atividade

```plantuml
@startuml DA_UC02_AtualizarAluno

|Recepcionista|
start
:Busca o aluno pelo nome ou CPF;

|Sistema|
:Pesquisa na base de dados;

if (Aluno encontrado?) then (sim)
  :Exibe os dados atuais do aluno;
  |Recepcionista|
  :Altera as informações desejadas;
  :Confirma as alterações;
  |Sistema|
  :Salva as novas informações;
  :Exibe confirmação de atualização;
  |Recepcionista|
  :Confirma a operação concluída;
else (não)
  :Exibe mensagem de aluno não encontrado (A1);
  |Recepcionista|
  :Verifica os dados da busca;
endif

stop
@enduml
```

---

## UC03 — Criar Plano

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Criar um novo plano de academia. |
| **Pré-condições** | Gerente autenticado no sistema. |
| **Pós-condições** | Novo plano cadastrado e disponível. |
| **RF Relacionados** | RF02 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O gerente acessa a área de planos.
2. O gerente informa os dados do plano.
3. O sistema salva o plano.

**Fluxos Alternativos:**
- **A1 — Dados inválidos:** O sistema solicita correção.

### Diagrama de Atividade

```plantuml
@startuml DA_UC03_CriarPlano

|Gerente|
start
:Acessa a área de gerenciamento de planos;
:Seleciona a opção de criar novo plano;
:Preenche nome, valor, duração e modalidades;

|Sistema|
:Valida os dados informados;

if (Dados válidos?) then (sim)
  :Salva o novo plano;
  :Disponibiliza para uso nas matrículas;
  :Exibe mensagem de sucesso;
  |Gerente|
  :Confirma a criação do plano;
else (não)
  :Exibe campos com erro (A1);
  :Solicita correção;
  |Gerente|
  :Corrige e reenvia os dados;
endif

stop
@enduml
```

---

## UC04 — Editar Plano

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Modificar informações de um plano existente. |
| **Pré-condições** | Plano já cadastrado no sistema. |
| **Pós-condições** | Plano atualizado com as novas informações. |
| **RF Relacionados** | RF02 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O gerente seleciona o plano.
2. O sistema mostra as informações.
3. O gerente altera os dados.
4. O sistema salva as alterações.

**Fluxos Alternativos:**
- **A1 — Plano inexistente:** O sistema informa erro.

### Diagrama de Atividade

```plantuml
@startuml DA_UC04_EditarPlano

|Gerente|
start
:Pesquisa o plano desejado;

|Sistema|
:Localiza o plano na base de dados;

if (Plano encontrado?) then (sim)
  :Exibe as informações atuais do plano;
  |Gerente|
  :Altera os dados necessários;
  :Salva as alterações;
  |Sistema|
  :Valida e persiste as mudanças;
  :Exibe confirmação de atualização;
  |Gerente|
  :Confirma a edição concluída;
else (não)
  :Exibe mensagem de plano não encontrado (A1);
  |Gerente|
  :Verifica os dados da pesquisa;
endif

stop
@enduml
```

---

## UC05 — Registrar Pagamento

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Recepcionista |
| **Objetivo** | Registrar o pagamento da mensalidade de um aluno. |
| **Pré-condições** | Aluno cadastrado no sistema. |
| **Pós-condições** | Pagamento registrado e situação do aluno atualizada. |
| **RF Relacionados** | RF03 |
| **RNF Relacionados** | RNF02 |
| **RN Relacionadas** | RN04, RN07 |

**Fluxo Principal:**
1. O recepcionista busca o aluno.
2. O sistema mostra a mensalidade.
3. O recepcionista confirma o pagamento.
4. O sistema registra o pagamento.

**Fluxos Alternativos:**
- **A1 — Falha no pagamento:** O sistema cancela a operação.

### Diagrama de Atividade

```plantuml
@startuml DA_UC05_RegistrarPagamento

|Recepcionista|
start
:Busca o aluno no sistema;

|Sistema|
:Exibe mensalidade em aberto;

|Recepcionista|
:Seleciona a forma de pagamento;
:Confirma o valor recebido;

|Sistema|
:Processa o pagamento (RN04);

if (Pagamento processado com sucesso?) then (sim)
  :Registra o pagamento;
  :Atualiza situação financeira do aluno (RN07);
  :Gera comprovante;
  |Recepcionista|
  :Entrega comprovante ao aluno;
else (não)
  :Cancela a operação (A1);
  :Exibe mensagem de falha;
  |Recepcionista|
  :Informa o aluno e tenta novamente;
endif

stop
@enduml
```

---

## UC06 — Verificar Regularidade

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Sistema |
| **Objetivo** | Verificar se o aluno está com o pagamento em dia. |
| **Pré-condições** | Aluno cadastrado no sistema. |
| **Pós-condições** | Situação financeira do aluno atualizada. |
| **RF Relacionados** | RF04 |
| **RNF Relacionados** | RNF03 |
| **RN Relacionadas** | RN01 |

**Fluxo Principal:**
1. O sistema verifica a data de pagamento.
2. O sistema define a situação do aluno.

**Fluxos Alternativos:**
- **A1 — Mensalidade vencida:** O sistema marca como inadimplente.

### Diagrama de Atividade

```plantuml
@startuml DA_UC06_VerificarRegularidade

|Sistema|
start
:Inicia rotina de verificação;
:Consulta datas de vencimento de todos os alunos;

if (Pagamento em dia?) then (sim)
  :Define situação como Regular;
else (não)
  :Calcula dias de atraso;
  if (Atraso superior a 5 dias?) then (sim)
    :Define situação como Inadimplente (A1 / RN01);
    :Bloqueia acesso à catraca;
  else (não)
    :Mantém acesso com aviso de pendência;
  endif
endif

:Atualiza situação do aluno na base de dados;
:Registra log da verificação;
stop
@enduml
```

---

## UC07 — Liberar Acesso na Catraca

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Aluno |
| **Objetivo** | Entrar na academia utilizando RFID. |
| **Pré-condições** | Aluno com plano ativo. |
| **Pós-condições** | Entrada liberada ou bloqueada conforme situação. |
| **RF Relacionados** | RF05 |
| **RNF Relacionados** | RNF03, RNF06 |
| **RN Relacionadas** | RN01 |

**Fluxo Principal:**
1. O aluno aproxima o cartão.
2. O sistema valida o cadastro.
3. O sistema libera o acesso.

**Fluxos Alternativos:**
- **A1 — Aluno inadimplente:** A catraca permanece bloqueada.

### Diagrama de Atividade

```plantuml
@startuml DA_UC07_LiberarAcesso

|Aluno|
start
:Aproxima o cartão RFID do leitor;

|Sistema|
:Recebe o sinal do cartão;
:Localiza o aluno pelo RFID;

if (Aluno encontrado?) then (sim)
  :Consulta situação financeira (UC06);
  if (Aluno regular?) then (sim)
    :Envia sinal de liberação para a catraca;
    :Registra entrada no histórico;
    |Aluno|
    :Passa pela catraca;
  else (não)
    :Mantém catraca bloqueada (A1 / RN01);
    :Exibe aviso de inadimplência;
    |Aluno|
    :Dirige-se à recepção;
  endif
else (não)
  :Rejeita acesso por RFID inválido;
  |Aluno|
  :Solicita ajuda na recepção;
endif

stop
@enduml
```

---

## UC08 — Visualizar Aulas

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Aluno |
| **Objetivo** | Visualizar as aulas disponíveis na grade de horários. |
| **Pré-condições** | Aluno autenticado no sistema. |
| **Pós-condições** | Lista de aulas exibida ao aluno. |
| **RF Relacionados** | RF06 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN02 |

**Fluxo Principal:**
1. O aluno acessa o menu de aulas.
2. O sistema mostra os horários disponíveis.

**Fluxos Alternativos:**
- **A1 — Nenhuma aula disponível:** O sistema informa ao aluno.

### Diagrama de Atividade

```plantuml
@startuml DA_UC08_VisualizarAulas

|Aluno|
start
:Acessa o menu de aulas;

|Sistema|
:Consulta aulas cadastradas e disponíveis;

if (Aulas disponíveis?) then (sim)
  :Exibe lista com modalidade, horário e vagas;
  |Aluno|
  :Visualiza a grade de aulas;
else (não)
  :Exibe mensagem informativa (A1);
  |Aluno|
  :Consulta em outro horário ou data;
endif

stop
@enduml
```

---

## UC09 — Agendar Aula

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Aluno |
| **Objetivo** | Reservar vaga em uma aula disponível. |
| **Pré-condições** | Aula com vaga disponível. |
| **Pós-condições** | Reserva registrada no sistema. |
| **RF Relacionados** | RF06 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN02 |

**Fluxo Principal:**
1. O aluno escolhe a aula.
2. O sistema verifica vagas.
3. O sistema confirma a reserva.

**Fluxos Alternativos:**
- **A1 — Aula lotada:** O sistema bloqueia o agendamento.

### Diagrama de Atividade

```plantuml
@startuml DA_UC09_AgendarAula

|Aluno|
start
:Seleciona a aula desejada na grade;
:Solicita reserva de vaga;

|Sistema|
:Verifica disponibilidade de vagas (RN02);

if (Vagas disponíveis?) then (sim)
  :Registra a reserva do aluno;
  :Decrementa o número de vagas disponíveis;
  :Aciona UC19 — Confirmação de Aula;
  |Aluno|
  :Recebe confirmação do agendamento;
else (não)
  :Bloqueia o agendamento (A1 / RN02);
  :Exibe mensagem de aula lotada;
  |Aluno|
  :Escolhe outra aula disponível;
endif

stop
@enduml
```

---

## UC10 — Cancelar Agendamento

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Aluno |
| **Objetivo** | Cancelar uma reserva de aula previamente realizada. |
| **Pré-condições** | Aula previamente reservada pelo aluno. |
| **Pós-condições** | Reserva cancelada e vaga liberada. |
| **RF Relacionados** | RF06 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN03 |

**Fluxo Principal:**
1. O aluno acessa suas reservas.
2. O aluno seleciona cancelar.
3. O sistema confirma o cancelamento.

**Fluxos Alternativos:**
- **A1 — Cancelamento fora do prazo:** O sistema bloqueia o cancelamento.

### Diagrama de Atividade

```plantuml
@startuml DA_UC10_CancelarAgendamento

|Aluno|
start
:Acessa suas reservas ativas;
:Seleciona a aula que deseja cancelar;
:Confirma intenção de cancelamento;

|Sistema|
:Verifica prazo de cancelamento (RN03);

if (Dentro do prazo permitido?) then (sim)
  :Cancela a reserva;
  :Libera a vaga para outros alunos;
  :Exibe confirmação do cancelamento;
  |Aluno|
  :Recebe confirmação do cancelamento;
else (não)
  :Bloqueia o cancelamento (A1 / RN03);
  :Informa que o prazo expirou;
  |Aluno|
  :A reserva permanece ativa;
endif

stop
@enduml
```

---

## UC11 — Registrar Presença

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Instrutor |
| **Objetivo** | Registrar a presença dos alunos em uma aula. |
| **Pré-condições** | Aula em andamento no sistema. |
| **Pós-condições** | Presenças registradas no histórico dos alunos. |
| **RF Relacionados** | RF07 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O instrutor acessa a aula.
2. O sistema mostra os alunos inscritos.
3. O instrutor marca a presença.

**Fluxos Alternativos:**
- **A1 — Aluno ausente:** O sistema registra ausência.

### Diagrama de Atividade

```plantuml
@startuml DA_UC11_RegistrarPresenca

|Instrutor|
start
:Acessa a aula em andamento;

|Sistema|
:Exibe lista de alunos com reserva ativa;

|Instrutor|
:Para cada aluno da lista, marca presente ou ausente;

|Sistema|
if (Aluno marcado como presente?) then (sim)
  :Registra presença com data e hora;
else (não)
  :Registra ausência do aluno (A1);
endif

|Instrutor|
:Finaliza o registro da chamada;

|Sistema|
:Salva todas as presenças e ausências;
:Atualiza histórico de frequência dos alunos;

stop
@enduml
```

---

## UC12 — Visualizar Lista de Presença

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Instrutor |
| **Objetivo** | Visualizar os alunos inscritos em uma aula. |
| **Pré-condições** | Aula agendada no sistema. |
| **Pós-condições** | Lista de alunos inscritos exibida. |
| **RF Relacionados** | RF07 |
| **RNF Relacionados** | RNF04 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O instrutor seleciona a aula.
2. O sistema exibe os alunos inscritos.

**Fluxos Alternativos:**
- **A1 — Nenhum aluno inscrito:** O sistema informa ao instrutor.

### Diagrama de Atividade

```plantuml
@startuml DA_UC12_VisualizarListaPresenca

|Instrutor|
start
:Seleciona a aula no sistema;

|Sistema|
:Consulta alunos com reserva ativa na aula;

if (Há alunos inscritos?) then (sim)
  :Exibe lista com nome e situação de cada aluno;
  |Instrutor|
  :Visualiza os inscritos na turma;
else (não)
  :Informa que nenhum aluno está inscrito (A1);
  |Instrutor|
  :Toma ciência da turma vazia;
endif

stop
@enduml
```

---

## UC13 — Registrar Avaliação Física

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Instrutor |
| **Objetivo** | Registrar dados físicos do aluno no sistema. |
| **Pré-condições** | Aluno ativo no sistema. |
| **Pós-condições** | Avaliação física salva no perfil do aluno. |
| **RF Relacionados** | RF08 |
| **RNF Relacionados** | RNF02 |
| **RN Relacionadas** | RN05 |

**Fluxo Principal:**
1. O instrutor seleciona o aluno.
2. O instrutor registra peso e medidas.
3. O sistema salva os dados.

**Fluxos Alternativos:**
- **A1 — Aluno irregular:** O sistema bloqueia a avaliação.

### Diagrama de Atividade

```plantuml
@startuml DA_UC13_RegistrarAvaliacaoFisica

|Instrutor|
start
:Seleciona o aluno para avaliação física;

|Sistema|
:Verifica se o aluno está ativo e regular (RN05);

if (Aluno elegível?) then (sim)
  :Exibe formulário de avaliação;
  |Instrutor|
  :Registra peso, altura e medidas corporais;
  |Sistema|
  :Calcula indicadores como IMC;
  :Salva a avaliação no perfil do aluno;
  :Exibe confirmação do registro;
  |Instrutor|
  :Confirma avaliação salva com sucesso;
else (não)
  :Bloqueia o início da avaliação (A1 / RN05);
  :Exibe motivo do bloqueio;
  |Instrutor|
  :Orienta o aluno a regularizar a situação;
endif

stop
@enduml
```

---

## UC14 — Consultar Avaliação Física

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Instrutor |
| **Objetivo** | Consultar avaliações físicas anteriores do aluno. |
| **Pré-condições** | Avaliação física previamente registrada. |
| **Pós-condições** | Histórico de avaliações exibido. |
| **RF Relacionados** | RF08 |
| **RNF Relacionados** | RNF02 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O instrutor busca o aluno.
2. O sistema mostra as avaliações registradas.

**Fluxos Alternativos:**
- **A1 — Nenhuma avaliação registrada:** O sistema informa.

### Diagrama de Atividade

```plantuml
@startuml DA_UC14_ConsultarAvaliacaoFisica

|Instrutor|
start
:Busca o aluno pelo nome;

|Sistema|
:Localiza o aluno na base de dados;
:Verifica avaliações físicas registradas;

if (Avaliações encontradas?) then (sim)
  :Exibe histórico de avaliações em ordem cronológica;
  |Instrutor|
  :Analisa a evolução do aluno;
else (não)
  :Informa ausência de avaliações (A1);
  |Instrutor|
  :Decide iniciar a primeira avaliação (UC13);
endif

stop
@enduml
```

---

## UC15 — Gerar Relatório de Alunos

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Visualizar relatório com os alunos ativos no sistema. |
| **Pré-condições** | Gerente autenticado. |
| **Pós-condições** | Relatório de alunos ativos exibido. |
| **RF Relacionados** | RF09 |
| **RNF Relacionados** | RNF03 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O gerente acessa relatórios.
2. O gerente seleciona alunos ativos.
3. O sistema gera o relatório.

**Fluxos Alternativos:**
- **A1 — Falha na geração:** O sistema informa erro.

### Diagrama de Atividade

```plantuml
@startuml DA_UC15_RelatorioAlunos

|Gerente|
start
:Acessa o módulo de relatórios;
:Seleciona "Alunos Ativos";

|Sistema|
:Consulta alunos com plano ativo;

if (Relatório gerado com sucesso?) then (sim)
  :Exibe lista de alunos ativos;
  |Gerente|
  :Analisa os dados do relatório;
else (não)
  :Exibe mensagem de falha na geração (A1);
  |Gerente|
  :Tenta gerar o relatório novamente;
endif

stop
@enduml
```

---

## UC16 — Gerar Relatório de Inadimplência

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Visualizar alunos com pagamento em atraso. |
| **Pré-condições** | Gerente autenticado. |
| **Pós-condições** | Relatório de inadimplência exibido. |
| **RF Relacionados** | RF09 |
| **RNF Relacionados** | RNF03 |
| **RN Relacionadas** | RN01 |

**Fluxo Principal:**
1. O gerente acessa relatórios.
2. Seleciona inadimplência.
3. O sistema gera o relatório.

**Fluxos Alternativos:**
- **A1 — Nenhum aluno inadimplente:** O sistema informa.

### Diagrama de Atividade

```plantuml
@startuml DA_UC16_RelatorioInadimplencia

|Gerente|
start
:Acessa o módulo de relatórios;
:Seleciona "Inadimplência";

|Sistema|
:Filtra alunos com parcelas vencidas;

if (Alunos inadimplentes encontrados?) then (sim)
  :Gera relatório com nome, valor e dias de atraso;
  :Exibe ao gerente;
  |Gerente|
  :Analisa a lista de inadimplentes;
else (não)
  :Informa que não há inadimplência no período (A1);
  |Gerente|
  :Encerra a consulta;
endif

stop
@enduml
```

---

## UC17 — Gerar Relatório de Acessos

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Visualizar o histórico de entradas na academia. |
| **Pré-condições** | Gerente autenticado. |
| **Pós-condições** | Relatório de acessos exibido. |
| **RF Relacionados** | RF09 |
| **RNF Relacionados** | RNF03 |
| **RN Relacionadas** | RN06 |

**Fluxo Principal:**
1. O gerente acessa relatórios.
2. Seleciona histórico de acesso.
3. O sistema gera o relatório.

**Fluxos Alternativos:**
- **A1 — Sem registros:** O sistema informa.

### Diagrama de Atividade

```plantuml
@startuml DA_UC17_RelatorioAcessos

|Gerente|
start
:Acessa o módulo de relatórios;
:Seleciona "Histórico de Acessos";
:Define período para consulta;

|Sistema|
:Recupera registros de entrada do período;

if (Registros encontrados?) then (sim)
  :Gera relatório com data, hora e status;
  :Exibe ao gerente;
  |Gerente|
  :Analisa o histórico de acessos;
else (não)
  :Informa ausência de registros (A1);
  |Gerente|
  :Ajusta o período de consulta;
endif

stop
@enduml
```

---

## UC18 — Enviar Notificação de Pagamento

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Sistema |
| **Objetivo** | Avisar o aluno sobre o vencimento próximo da mensalidade. |
| **Pré-condições** | Mensalidade próxima do vencimento. |
| **Pós-condições** | Notificação enviada ao aluno. |
| **RF Relacionados** | RF10 |
| **RNF Relacionados** | RNF01 |
| **RN Relacionadas** | RN07 |

**Fluxo Principal:**
1. O sistema identifica mensalidade próxima do vencimento.
2. O sistema envia notificação ao aluno.

**Fluxos Alternativos:**
- **A1 — Falha no envio:** O sistema tenta novamente.

### Diagrama de Atividade

```plantuml
@startuml DA_UC18_NotificarPagamento

|Sistema|
start
:Verifica mensalidades com vencimento próximo;

if (Há mensalidades a vencer?) then (sim)
  :Monta notificação personalizada por aluno;
  :Tenta enviar via e-mail ou push;

  if (Envio bem-sucedido?) then (sim)
    :Registra envio no log;
    |Aluno|
    :Recebe notificação de vencimento;
  else (não)
    :Registra falha (A1);
    :Agenda nova tentativa automática;
  endif
else (não)
  :Encerra sem envios;
endif

stop
@enduml
```

---

## UC19 — Enviar Confirmação de Aula

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Sistema |
| **Objetivo** | Confirmar ao aluno que o agendamento de aula foi realizado. |
| **Pré-condições** | Aula agendada pelo aluno (UC09). |
| **Pós-condições** | Confirmação enviada com detalhes da aula. |
| **RF Relacionados** | RF10 |
| **RNF Relacionados** | RNF01 |
| **RN Relacionadas** | RN02 |

**Fluxo Principal:**
1. O sistema registra o agendamento.
2. O sistema envia confirmação ao aluno.

**Fluxos Alternativos:**
- **A1 — Falha no envio:** O sistema tenta reenviar.

### Diagrama de Atividade

```plantuml
@startuml DA_UC19_ConfirmacaoAula

|Sistema|
start
:Recebe evento de agendamento confirmado (UC09);
:Monta mensagem com dados da aula;
:Tenta enviar notificação ao aluno;

if (Envio bem-sucedido?) then (sim)
  :Registra confirmação no log;
  |Aluno|
  :Recebe confirmação com dados da aula;
else (não)
  :Registra falha no log (A1);
  :Agenda reenvio automático;
  |Sistema|
  :Tenta reenviar após intervalo;
endif

stop
@enduml
```

---

## UC20 — Notificar Nova Avaliação Física

| Atributo | Descrição |
|---|---|
| **Ator Principal** | Sistema |
| **Objetivo** | Informar ao aluno que uma nova avaliação física está disponível. |
| **Pré-condições** | Avaliação anterior já registrada no sistema. |
| **Pós-condições** | Notificação de nova avaliação enviada ao aluno. |
| **RF Relacionados** | RF10 |
| **RNF Relacionados** | RNF01 |
| **RN Relacionadas** | RN05 |

**Fluxo Principal:**
1. O sistema identifica necessidade de nova avaliação.
2. O sistema envia notificação ao aluno.

**Fluxos Alternativos:**
- **A1 — Falha no envio:** O sistema tenta novamente.

### Diagrama de Atividade

```plantuml
@startuml DA_UC20_NotificarNovaAvaliacao

|Sistema|
start
:Verifica alunos com avaliação física vencida ou pendente;

if (Há alunos para notificar?) then (sim)
  :Monta notificação informando disponibilidade;
  :Tenta enviar ao aluno;

  if (Envio bem-sucedido?) then (sim)
    :Registra envio no log;
    |Aluno|
    :Recebe notificação de nova avaliação disponível;
  else (não)
    :Registra falha (A1);
    :Agenda nova tentativa;
  endif
else (não)
  :Encerra sem envios pendentes;
endif

stop
@enduml
```

---

*Documento elaborado por Maycon Gabriel da Silva Morelli (24001786) — UNIFEOB 2026.*
