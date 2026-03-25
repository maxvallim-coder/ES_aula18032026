# FitPass Gym Management – Estudo de Caso

# Diagramas de Casos de Uso:

<img width="521" height="1583" alt="image" src="https://github.com/user-attachments/assets/b6e53ae0-4dab-48c1-831e-71a0cf6c9367" />

---

## UC01 — Realizar Login 

### Ator Principal
Usuário

### Objetivo
Permitir que o usuário acesse o sistema.

### Pré-condições
- Usuário deve possuir cadastro ativo.

### Pós-condições
- Sessão iniciada com sucesso.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02 

### RN Relacionadas
- RN01 e RN06

## UC17 — Autenticar Usuário (Login)

### Ator Principal
Usuário

### Objetivo
Garantir acesso seguro às funcionalidades de acordo com o perfil.

### Pré-condições
- Usuário possuir credenciais cadastradas.
  
### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema identifica o perfil (Gerente, Instrutor, etc.) e libera o acesso.
   
### Fluxos Alternativos
- **A1 — Credenciais inválidas:** O sistema exibe mensagem de erro.
  
### RF Relacionados
- RF01
  
### RN Relacionadas
- RN06

<img width="589" height="417" alt="image" src="https://github.com/user-attachments/assets/77fa3c88-0b57-40da-b76e-83416cc87f17" />

---

## UC18 — Recuperar Senha de Acesso

### Ator Principal
Usuário

### Objetivo
Permitir a criação de uma nova senha em caso de esquecimento.

### Fluxo Principal
1. O usuário clica em "Esqueci minha senha".
2. Informa o e-mail cadastrado.
3. O sistema envia um código de verificação.
4. O usuário define a nova senha.
   
### RNF Relacionados
- RNF02

<img width="407" height="461" alt="image" src="https://github.com/user-attachments/assets/4d23c6a6-70d8-47a5-8574-ecd88fd6bd3d" />

---

## UC02 — Gerenciar Planos de Academia

### Ator Principal
Gerente

### Objetivo
Criar, editar ou desativar modalidades de planos (mensal, trimestral, etc.).

### Pré-condições
- Usuário autenticado com perfil de Gerente.

### Pós-condições
- Grade de planos atualizada para novas matrículas.
  
### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. Define o nome, valor, periodicidade e modalidade da aula.
3. O sistema salva as alterações e atualiza a disponibilidade.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF02, RNF05
  
### RN Relacionadas
- RN06

<img width="480" height="338" alt="image" src="https://github.com/user-attachments/assets/5df88d1e-c759-4cee-aa9f-fc8ffb1cc787" />

---

## UC03 — Registrar Pagamento na Recepção

### Ator Principal
Recepcionista

### Objetivo
Processar o pagamento presencial das mensalidades.

### Pré-condições
- Aluno deve possuir uma pendência financeira no sistema.
  
### Pós-condições
- Pagamento registrado e situação do aluno atualizada imediatamente.
  
### Fluxo Principal
1. O recepcionista busca o aluno pelo nome ou CPF.
2. Seleciona a mensalidade em aberto e a forma de pagamento (Dinheiro, Cartão ou PIX).
3. O sistema registra o valor integral.
4. O sistema gera o comprovante.
   
### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:** O sistema impede a transação e exibe a RN04.
  
### RF Relacionados
- RF03, RF04

### RNF Relacionados
- RNF02, RNF03
  
### RN Relacionadas
- RN04, RN07

<img width="528" height="472" alt="image" src="https://github.com/user-attachments/assets/8fff07fa-5251-420f-832f-27102b1a9845" />

---

## UC04 — Gerar Cobrança Online

### Ator Principal
Sistema

### Objetivo
Gerar boletos ou links de pagamento para o aluno.

### Pré-condições
- Existência de título financeiro gerado pelo sistema.
  
### Pós-condições
- Documento de cobrança disponibilizado ao aluno.
  
### Fluxo Principal
1. O sistema identifica a conta a receber.
2. Gera o boleto bancário ou QR Code PIX via integração bancária.
3. Envia o link para o e-mail/app do aluno.
   
### RF Relacionados
- RF03
  
### RNF Relacionados
- RNF06

<img width="404" height="283" alt="image" src="https://github.com/user-attachments/assets/c7787d8d-0fdc-4b99-9aca-ec6c32994ec5" />

---

## UC05 — Validar Acesso na Catraca

### Ator Principal
Aluno

### Objetivo
Controlar a entrada física na academia via hardware de catraca.

### Pré-condições
- Aluno deve aproximar o RFID no leitor.
  
### Pós-condições
- Giro da catraca liberado e registro de acesso salvo.
  
### Fluxo Principal
1. O aluno utiliza seu RFID na catraca.
2. O sistema verifica o status financeiro do aluno.
3. Se regular, o sistema envia o sinal de liberação para a catraca.
   
### Fluxos Alternativos
- **A1 — Aluno Inadimplente (> 5 dias):** O sistema nega o acesso e exibe mensagem na tela da catraca.
  
### RF Relacionados
- RF04, RF05
  
### RNF Relacionados
- RNF03, RNF06
  
### RN Relacionadas
- RN01

<img width="584" height="417" alt="image" src="https://github.com/user-attachments/assets/2dd87fc3-4713-4c6b-9298-a454bb634859" />

---

## UC06 — Reservar Vaga em Aula

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno agende sua participação em aulas com limite de vagas.

### Pré-condições
- Aluno autenticado e com plano compatível com a aula.
  
### Pós-condições
- Vaga reservada para o aluno.
  
### Fluxo Principal
1. O aluno visualiza a grade de horários no app.
2. Seleciona a aula desejada.
3. O sistema verifica se há vagas disponíveis.
4. O sistema confirma a reserva e abate uma vaga da turma.
   
### Fluxos Alternativos
- **A1 — Limite de vagas atingido:** O sistema informa que a aula está lotada e bloqueia o botão de reserva.
  
### RF Relacionados
- RF06
  
### RN Relacionadas
- RN02

<img width="541" height="472" alt="image" src="https://github.com/user-attachments/assets/a0eb9342-4008-4109-b57b-013709b26a2e" />

---

## UC07 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Liberar a vaga em uma aula agendada previamente.

### Fluxo Principal
1. O aluno acessa suas reservas no aplicativo.
2. Solicita o cancelamento da aula selecionada.
3. O sistema valida o horário (limite de 1 hora antes).
4. O sistema remove o nome do aluno da lista de presença.
   
### Fluxos Alternativos
- **A1 — Cancelamento fora do prazo:** O sistema exibe mensagem informando que o prazo de 1h expirou.
  
### RF Relacionados
- RF06
  
### RN Relacionadas
- RN03

<img width="521" height="402" alt="image" src="https://github.com/user-attachments/assets/ded4c1cb-6e32-4d43-b621-7c04ee136203" />

---

## UC08 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Validar quem compareceu à aula agendada.

### Pré-condições
- Aula estar em horário de início ou término.
  
### Fluxo Principal
1. O instrutor acessa a lista de alunos que reservaram a aula.
2. Marca a presença dos alunos em sala.
3. O sistema salva a lista de presença final.
   
### RF Relacionados
- RF07
  
### RN Relacionadas
- RN06

<img width="227" height="286" alt="image" src="https://github.com/user-attachments/assets/1ad29388-4450-421a-b05f-419b7491b904" />

---

## UC09 — Realizar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar dados de desempenho e saúde do aluno.

### Pré-condições
- Aluno deve estar com status "Ativo" e "Regular".
  
### Pós-condições
- Avaliação física disponível no perfil do aluno.
  
### Fluxo Principal
1. O instrutor inicia a avaliação para o aluno selecionado.
2. Insere peso, percentual de gordura e IMC.
3. O sistema salva os dados e gera o gráfico de evolução.
   
### Fluxos Alternativos
- **A1 — Aluno Irregular:** O sistema impede o início da avaliação conforme RN05.
  
### RF Relacionados
- RF08
  
### RN Relacionadas
- RN05, RN06

<img width="572" height="402" alt="image" src="https://github.com/user-attachments/assets/87605a5e-9ea8-46cc-af07-dd9e1257484c" />

---

## UC16 — Consultar Horários e Aulas

### Ator Principal
Aluno

### Objetivo
Permitir a visualização da grade horária da academia.

### Fluxo Principal
1. O aluno acessa a aba "Horários" no app.
2. O sistema exibe as aulas disponíveis por dia da semana e instrutor.
   
### RF Relacionados
- RF06
  
### RNF Relacionados
- RNF04

<img width="224" height="286" alt="image" src="https://github.com/user-attachments/assets/c0538cac-4a8c-4a78-bd0d-6b4a898b8c20" />

---

## UC19 — Anexar Arquivos à Avaliação

### Ator Principal
Instrutor

### Objetivo
Armazenar exames externos ou fotos de progresso no perfil do aluno.

### Fluxo Principal
1. Durante a avaliação física, o instrutor seleciona a opção "Anexar Arquivo".
2. Seleciona o documento (PDF ou Imagem) no computador.
3. O sistema armazena o arquivo de forma criptografada.
   
### RF Relacionados
- RF08
  
### RNF Relacionados
- RNF02

### RN Relacionadas
- RN06

<img width="223" height="393" alt="image" src="https://github.com/user-attachments/assets/e3e22b03-74c1-45f0-b33b-93890bc83dde" />

---

## UC10 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Identificar alunos com mensalidades atrasadas.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios financeiros.
2. Seleciona o filtro "Inadimplência".
3. O sistema gera a lista de alunos com débitos e tempo de atraso.
   
### RF Relacionados
- RF09

## UC11 — Emitir Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Obter dados quantitativos sobre a base de clientes atual.

### Fluxo Principal
1. O gerente solicita o relatório de ocupação de planos.
2. O sistema filtra por alunos com contrato vigente.
3. O sistema exibe o total de alunos ativos por plano.
   
### RF Relacionados
- RF09

## UC12 — Consultar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Auditar o fluxo de pessoas na academia por período.

### Fluxo Principal
1. O gerente informa o período (data inicial e final).
2. O sistema exibe todos os registros de entrada registrados pela catraca.
   
### RF Relacionados
- RF09

## UC20 — Emitir Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Analisar quais horários e aulas estão com maior demanda.

### Fluxo Principal
1. O gerente seleciona a modalidade da aula.
2. O sistema apresenta a porcentagem de ocupação nos últimos 30 dias.
   
### RF Relacionados
- RF09

### RNF Relacionados
- RNF02, RNF05

### RN Relacionadas
- RN06

<img width="362" height="393" alt="image" src="https://github.com/user-attachments/assets/f4fc3f54-c46c-47b2-a49f-e5e8867b9aed" />

---

## UC13 — Notificar Vencimento de Mensalidade

### Ator Principal
Sistema

### Objetivo
Avisar o aluno automaticamente sobre o prazo de pagamento.

### Pós-condições
- Notificação push ou e-mail enviada.
  
### Fluxo Principal
1. O sistema varre o banco de dados em busca de vencimentos no dia seguinte.
2. Dispara a notificação para os alunos identificados.
   
### RF Relacionados
- RF10

## UC14 — Notificar Confirmação de Agendamento

### Ator Principal
Sistema

### Objetivo
Confirmar para o aluno que sua vaga foi garantida.

### Fluxo Principal
1. Após a conclusão do UC06, o sistema gera uma mensagem automática.
2. O sistema envia a confirmação para o dispositivo do aluno.
   
### RF Relacionados
- RF10

## UC15 — Notificar Liberação de Avaliação Física

### Ator Principal
Sistema

### Objetivo
Avisar ao aluno que ele já pode visualizar seus resultados.

### Fluxo Principal
1. Ao finalizar o UC09, o sistema detecta a nova entrada de dados.
2. O sistema envia um alerta ao aluno.
   
### RF Relacionados
- RF10

<img width="458" height="338" alt="image" src="https://github.com/user-attachments/assets/93ab6ed0-3ab9-455f-bf59-ae52cfa641cc" />

---





