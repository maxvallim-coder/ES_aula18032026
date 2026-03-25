# Diagramas dos Casos de Uso - Sistema Fitpass Gym Management

---

<img width="635" height="499" alt="DUC_01_MuriloBarbosa_PedroBortolon png" src="https://github.com/user-attachments/assets/ff8993f4-68d6-4c82-9af0-4370c36380da" />

---

![DUC_02_MuriloBarbosa_PedroBortolon png](https://github.com/user-attachments/assets/1663f022-b3ed-4d22-a2ea-b58730e923bd)


---

![DUC_03_MuriloBarbosa_PedroBortolon png](https://github.com/user-attachments/assets/2cdcb57b-dee0-4cf6-b0dd-b97456aa8fb9)


# Casos de Uso — Sistema FitPass Gym Management

---

# UC01 — Realizar Login

### Ator Principal

Usuário

### Objetivo

Permitir que o usuário acesse o sistema conforme seu perfil.

### Pré-condições

* Usuário deve possuir cadastro ativo no sistema.

### Pós-condições

* Sessão iniciada e permissões aplicadas conforme perfil.

### Fluxo Principal

1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema identifica o perfil do usuário.
4. O sistema redireciona para a tela inicial correspondente ao perfil.

### Fluxos Alternativos

* *A1 — Credenciais inválidas:*
  O sistema exibe mensagem de erro.

* *A2 — Usuário inativo:*
  O sistema bloqueia o acesso.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF02
* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 50 20](https://github.com/user-attachments/assets/d7b19cf1-b755-444e-8063-d31106f298c7)

---

# UC02 — Cadastrar Aluno

### Ator Principal

Recepcionista

### Objetivo

Registrar um novo aluno no sistema.

### Pré-condições

* Recepcionista autenticado no sistema.

### Pós-condições

* Aluno registrado no banco de dados.

### Fluxo Principal

1. O recepcionista acessa a tela de cadastro de alunos.
2. O sistema solicita dados pessoais e de contato.
3. O recepcionista informa os dados.
4. O sistema valida as informações.
5. O sistema registra o aluno.

### Fluxos Alternativos

* *A1 — Dados obrigatórios ausentes:*
  O sistema solicita o preenchimento dos campos.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 50 43](https://github.com/user-attachments/assets/4080116c-61cb-41c5-9d4e-c275b10e4c4e)

---

# UC03 — Atualizar Dados do Aluno

### Ator Principal

Recepcionista

### Objetivo

Atualizar informações cadastrais do aluno.

### Pré-condições

* Aluno já cadastrado.

### Pós-condições

* Dados atualizados no sistema.

### Fluxo Principal

1. O recepcionista busca o aluno.
2. O sistema exibe os dados atuais.
3. O recepcionista altera as informações necessárias.
4. O sistema salva as alterações.

### Fluxos Alternativos

* *A1 — Aluno não encontrado:*
  O sistema informa que o aluno não foi localizado.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 51 08](https://github.com/user-attachments/assets/a8df3f36-d2fd-4eac-80c6-4e9d2754338b)

---

# UC04 — Criar Plano

### Ator Principal

Gerente

### Objetivo

Cadastrar novos tipos de planos no sistema.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Plano disponível para contratação.

### Fluxo Principal

1. O gerente acessa o módulo de planos.
2. O gerente seleciona a opção criar plano.
3. O sistema solicita informações do plano.
4. O gerente preenche os dados.
5. O sistema salva o plano.

### Fluxos Alternativos

* *A1 — Dados inválidos:*
  O sistema solicita correção.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 51 31](https://github.com/user-attachments/assets/b117bf45-8d86-48f0-961d-b29f39024993)

---

# UC05 — Editar Plano

### Ator Principal

Gerente

### Objetivo

Alterar informações de um plano existente.

### Pré-condições

* Plano previamente cadastrado.

### Pós-condições

* Plano atualizado no sistema.

### Fluxo Principal

1. O gerente seleciona um plano.
2. O sistema exibe as informações atuais.
3. O gerente altera os dados.
4. O sistema salva as alterações.

### Fluxos Alternativos

* *A1 — Plano não encontrado:*
  O sistema informa erro.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 51 59](https://github.com/user-attachments/assets/e06fb746-577c-47ae-89f8-022b8b0bc95e)

---

# UC06 — Desativar Plano

### Ator Principal

Gerente

### Objetivo

Desativar um plano para impedir novas contratações.

### Pré-condições

* Plano cadastrado.

### Pós-condições

* Plano marcado como inativo.

### Fluxo Principal

1. O gerente acessa a lista de planos.
2. Seleciona o plano desejado.
3. Escolhe a opção desativar.
4. O sistema atualiza o status do plano.

### Fluxos Alternativos

* *A1 — Plano em uso:*
  O sistema mantém o plano apenas para alunos ativos.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 52 48](https://github.com/user-attachments/assets/8ded383c-a20c-476b-9673-7d0790902a1c)

---

# UC07 — Registrar Pagamento

### Ator Principal

Recepcionista

### Objetivo

Registrar pagamento da mensalidade do aluno.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Pagamento registrado e situação atualizada.

### Fluxo Principal

1. O recepcionista busca o aluno.
2. O sistema exibe mensalidade pendente.
3. O recepcionista registra forma de pagamento.
4. O sistema confirma o pagamento.
5. O sistema atualiza a regularidade do aluno.

### Fluxos Alternativos

* *A1 — Pagamento parcial:*
  O sistema bloqueia o registro.

### RF Relacionados

* RF03

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN04
* RN07

![WhatsApp Image 2026-03-18 at 20 53 05](https://github.com/user-attachments/assets/4082faa8-25cf-4b9d-9d90-17fce6da0e55)

---

# UC08 — Gerar Cobrança Online

### Ator Principal

Recepcionista

### Objetivo

Gerar cobrança digital para pagamento.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Cobrança gerada.

### Fluxo Principal

1. O recepcionista seleciona o aluno.
2. O sistema gera boleto ou link de pagamento.
3. O sistema registra a cobrança.

### Fluxos Alternativos

* *A1 — Falha na geração:*
  O sistema informa erro.

### RF Relacionados

* RF03

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN04

![WhatsApp Image 2026-03-18 at 20 53 27](https://github.com/user-attachments/assets/06c19653-8929-4aca-855b-291c9c1844eb)

---

# UC09 — Verificar Regularidade do Aluno

### Ator Principal

Sistema

### Objetivo

Verificar automaticamente se o aluno está em dia.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Situação atualizada (regular ou inadimplente).

### Fluxo Principal

1. O sistema verifica a data do último pagamento.
2. O sistema compara com a data atual.
3. O sistema atualiza a situação do aluno.

### Fluxos Alternativos

* *A1 — Pagamento vencido:*
  O sistema marca como inadimplente.

### RF Relacionados

* RF04

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN01

![WhatsApp Image 2026-03-18 at 20 53 47](https://github.com/user-attachments/assets/6dc74bb2-d028-4e20-87cb-26bfa6eeca70)

---

# UC10 — Validar Entrada na Catraca

### Ator Principal

Sistema de Catraca

### Objetivo

Permitir ou negar acesso à academia.

### Pré-condições

* Aluno possuir RFID registrado.

### Pós-condições

* Acesso liberado ou bloqueado.

### Fluxo Principal

1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia solicitação ao sistema.
3. O sistema verifica a regularidade do aluno.
4. O sistema retorna autorização.
5. A catraca libera a entrada.

### Fluxos Alternativos

* *A1 — Aluno inadimplente:*
  O acesso é negado.

### RF Relacionados

* RF05

### RNF Relacionados

* RNF03
* RNF06

### RN Relacionadas

* RN01

![WhatsApp Image 2026-03-18 at 20 54 06](https://github.com/user-attachments/assets/da690207-a995-4fe4-bf7c-f24fb92e9ddf)

---

# UC11 — Visualizar Aulas Disponíveis

### Ator Principal

Aluno

### Objetivo

Permitir visualizar horários de aulas.

### Pré-condições

* Aluno autenticado.

### Pós-condições

* Lista de aulas exibida.

### Fluxo Principal

1. O aluno acessa o módulo de aulas.
2. O sistema lista aulas disponíveis.
3. O sistema exibe horários e vagas.

### Fluxos Alternativos

* *A1 — Nenhuma aula disponível:*
  O sistema informa ao usuário.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN02

![WhatsApp Image 2026-03-18 at 20 54 24](https://github.com/user-attachments/assets/47e3318a-a4ef-48fe-a854-38f25f61dde1)

---

# UC12 — Reservar Aula

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno reserve vaga em uma aula.

### Pré-condições

* Aula disponível.

### Pós-condições

* Reserva registrada.

### Fluxo Principal

1. O aluno seleciona uma aula.
2. O sistema verifica disponibilidade.
3. O aluno confirma a reserva.
4. O sistema registra o agendamento.

### Fluxos Alternativos

* *A1 — Aula lotada:*
  O sistema bloqueia a reserva.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN02

![WhatsApp Image 2026-03-18 at 20 54 47](https://github.com/user-attachments/assets/90c983ed-d366-49d2-b24b-0bbe61272e44)

---

# UC13 — Cancelar Reserva de Aula

### Ator Principal

Aluno

### Objetivo

Permitir cancelamento de agendamento.

### Pré-condições

* Reserva existente.

### Pós-condições

* Reserva cancelada.

### Fluxo Principal

1. O aluno acessa suas reservas.
2. Seleciona a reserva desejada.
3. Solicita cancelamento.
4. O sistema confirma o cancelamento.

### Fluxos Alternativos

* *A1 — Prazo expirado:*
  O sistema bloqueia cancelamento.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN03

![WhatsApp Image 2026-03-18 at 20 55 04](https://github.com/user-attachments/assets/a0461434-921a-4b59-9c1d-c98d72be23e1)

---

# UC14 — Registrar Presença em Aula

### Ator Principal

Instrutor

### Objetivo

Registrar presença dos alunos.

### Pré-condições

* Aula iniciada.

### Pós-condições

* Presença registrada.

### Fluxo Principal

1. O instrutor acessa a lista da aula.
2. O sistema exibe alunos inscritos.
3. O instrutor marca presença.
4. O sistema salva os registros.

### Fluxos Alternativos

* *A1 — Aluno não inscrito:*
  O sistema alerta o instrutor.

### RF Relacionados

* RF07

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 55 23](https://github.com/user-attachments/assets/e7f2ebab-14dc-44fd-97ac-8bab29a5f7ee)

---

# UC15 — Registrar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Registrar dados de avaliação física.

### Pré-condições

* Aluno ativo.

### Pós-condições

* Avaliação armazenada.

### Fluxo Principal

1. O instrutor busca o aluno.
2. O sistema apresenta formulário de avaliação.
3. O instrutor registra medidas físicas.
4. O sistema salva a avaliação.

### Fluxos Alternativos

* *A1 — Aluno inadimplente:*
  Avaliação bloqueada.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN05

![WhatsApp Image 2026-03-18 at 20 55 45](https://github.com/user-attachments/assets/1e6fef45-a284-4ef0-9b48-5f1d2524de6b)

---

# UC16 — Anexar Arquivo de Avaliação

### Ator Principal

Instrutor

### Objetivo

Adicionar documentos à avaliação física.

### Pré-condições

* Avaliação existente.

### Pós-condições

* Arquivo anexado.

### Fluxo Principal

1. O instrutor abre a avaliação.
2. Seleciona anexar arquivo.
3. O sistema faz upload do arquivo.
4. O sistema vincula ao registro.

### Fluxos Alternativos

* *A1 — Arquivo inválido:*
  O sistema bloqueia o envio.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF02

### RN Relacionadas

* RN05

![WhatsApp Image 2026-03-18 at 20 56 06](https://github.com/user-attachments/assets/495f52ee-4b0c-4895-93b5-c7dcafc034ed)

---

# UC17 — Emitir Relatório de Inadimplência

### Ator Principal

Gerente

### Objetivo

Gerar relatório de alunos inadimplentes.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente acessa relatórios.
2. Seleciona relatório de inadimplência.
3. O sistema processa os dados.
4. O sistema exibe o relatório.

### Fluxos Alternativos

* *A1 — Sem dados:*
  O sistema informa ausência de registros.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN01

![WhatsApp Image 2026-03-18 at 20 56 24](https://github.com/user-attachments/assets/60d9660c-2e6d-4d8f-b3f9-d91ec05d0fbb)

---

# UC18 — Emitir Relatório de Alunos Ativos

### Ator Principal

Gerente

### Objetivo

Consultar quantidade de alunos ativos.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente seleciona relatório de alunos ativos.
2. O sistema consulta o banco de dados.
3. O sistema exibe os resultados.

### Fluxos Alternativos

* *A1 — Falha na consulta:*
  O sistema informa erro.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN06

![WhatsApp Image 2026-03-18 at 20 56 42](https://github.com/user-attachments/assets/4432371c-9162-4c6c-8e03-df5d9b03c166)

---

# UC19 — Emitir Relatório de Ocupação de Aulas

### Ator Principal

Gerente

### Objetivo

Visualizar ocupação das aulas.

### Pré-condições

* Aulas cadastradas.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente seleciona relatório de ocupação.
2. O sistema analisa reservas e presenças.
3. O sistema exibe taxa de ocupação.

### Fluxos Alternativos

* *A1 — Sem aulas registradas:*
  O sistema informa ausência de dados.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN02

![WhatsApp Image 2026-03-18 at 20 56 59](https://github.com/user-attachments/assets/00cce71d-fdc2-41a8-84e7-4db293c571db)

---

# UC20 — Enviar Notificação ao Aluno

### Ator Principal

Sistema

### Objetivo

Enviar notificações automáticas ao aluno.

### Pré-condições

* Evento que gere notificação.

### Pós-condições

* Notificação enviada.

### Fluxo Principal

1. O sistema identifica um evento (vencimento, confirmação ou avaliação).
2. O sistema gera a notificação.
3. O sistema envia ao aluno.

### Fluxos Alternativos

* *A1 — Falha no envio:*
  O sistema registra tentativa para reenvio.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF01
* RNF03

### RN Relacionadas

* RN07

![WhatsApp Image 2026-03-18 at 20 57 15](https://github.com/user-attachments/assets/9fe21662-f7be-40a5-9e56-ab358e9b0ef2)

---
