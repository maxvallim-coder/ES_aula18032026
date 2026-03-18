


<img width="1020" height="1636" alt="DUC_01_FelipeGrossi_JoaoPedro" src="https://github.com/user-attachments/assets/5d5f5dfa-1a2a-4b5b-b267-9c5b78198169" />




---

## UC01 — Realizar Login

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário acesse o sistema de acordo com seu perfil.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso e redirecionamento conforme perfil.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema identifica o perfil de acesso (RN06).
4. O sistema autentica o usuário e redireciona para a tela inicial correspondente.

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro e solicita novas credenciais.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02 (Segurança / Criptografia)
- RNF03 (Performance)

### RN Relacionadas
- RN06 (Acesso restrito por perfil)


<img width="473" height="383" alt="01" src="https://github.com/user-attachments/assets/e75d2784-88cf-4da4-8ad8-7c60c8e2087d" />



---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno para permitir o uso da academia.

### Pré-condições
- Recepcionista autenticado no sistema.

### Pós-condições
- Registro do aluno salvo no banco de dados.

### Fluxo Principal
1. O recepcionista solicita a criação de novo cadastro.
2. O recepcionista insere dados pessoais, contato e endereço.
3. O recepcionista vincula um plano inicial ao aluno (RF02).
4. O sistema valida os dados e confirma o salvamento.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:**  
  O sistema alerta que o aluno já possui registro e impede a duplicidade.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF04 (Usabilidade)

### RN Relacionadas
- RN06 (Perfil de Recepcionista)

<img width="219" height="361" alt="02" src="https://github.com/user-attachments/assets/cb4a81b9-1c8b-4849-a0e6-0fb45c6b2193" />


---

## UC03 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Criar, editar ou desativar os planos de serviço da academia.

### Pré-condições
- Gerente autenticado no sistema.

### Pós-condições
- Plano disponível ou atualizado no catálogo de vendas.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O gerente define nome, valor, duração e regras do plano.
3. O sistema registra a configuração.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF04 (Usabilidade)

### RN Relacionadas
- RN06 (Perfil de Gerente)

<img width="183" height="240" alt="03" src="https://github.com/user-attachments/assets/3666c986-c4e4-465c-b9b0-b439e88f0ec6" />


---

## UC04 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Realizar a baixa financeira de mensalidades na recepção física.

### Pré-condições
- Aluno identificado.
- Fatura em aberto disponível.

### Pós-condições
- Status da mensalidade alterado para "Pago".
- Regularidade do aluno atualizada.

### Fluxo Principal
1. O recepcionista seleciona a conta a pagar do aluno.
2. O sistema exige o valor integral do pagamento (RN04).
3. O recepcionista informa o método (Dinheiro, Cartão ou PIX).
4. O sistema processa o pagamento e atualiza a situação do aluno imediatamente (RN07).

### RF Relacionados
- RF03
- RF04

### RNF Relacionados
- RNF03 (Performance)

### RN Relacionadas
- RN04 (Pagamento integral)
- RN07 (Atualização automática)

<img width="254" height="358" alt="04" src="https://github.com/user-attachments/assets/c41db23f-7d8c-4ea6-895c-7a59370a2aab" />


---

## UC05 — Validar Acesso (Catraca)

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Controlar a entrada física dos alunos na unidade.

### Pré-condições
- Aluno aproxima o dispositivo RFID da catraca.

### Pós-condições
- Acesso liberado ou bloqueado com registro de log.

### Fluxo Principal
1. A catraca envia o código RFID para o sistema via API.
2. O sistema verifica a regularidade financeira do aluno (RF04).
3. O sistema autoriza o desbloqueio da catraca.

### Fluxos Alternativos
- **A1 — Inadimplência:**  
  Se o atraso for superior a 5 dias, o sistema nega o acesso (RN01) e exibe mensagem na catraca.

### RF Relacionados
- RF04
- RF05

### RNF Relacionados
- RNF03 (Resposta rápida)
- RNF06 (Integração JSON)

### RN Relacionadas
- RN01 (Bloqueio por inadimplência)

<img width="252" height="308" alt="05" src="https://github.com/user-attachments/assets/6099b9cf-eed4-4a54-8d5a-3c6a8114a377" />


---

## UC06 — Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Garantir uma vaga em aulas com limite de participantes.

### Pré-condições
- Aluno com mensalidade regular.
- Vagas disponíveis.

### Pós-condições
- Reserva confirmada.

### Fluxo Principal
1. O aluno seleciona a aula e o horário desejado.
2. O sistema verifica o limite de vagas (RN02).
3. O sistema confirma o agendamento.
4. O sistema envia notificação de confirmação (RF10).

### RF Relacionados
- RF06
- RF10

### RNF Relacionados
- RNF04 (Interface responsiva)

### RN Relacionadas
- RN02 (Limite de vagas)

<img width="333" height="351" alt="06" src="https://github.com/user-attachments/assets/ed590350-d3d1-4082-8563-503ae66c824d" />


---

## UC07 — Cancelar Agendamento

### Ator Principal
Aluno

### Objetivo
Desistir de um agendamento prévio liberando a vaga.

### Pré-condições
- Possuir agendamento ativo.

### Fluxo Principal
1. O aluno visualiza seus agendamentos.
2. O aluno solicita o cancelamento.
3. O sistema valida antecedência mínima de 1 hora (RN03).
4. O sistema confirma o cancelamento.

### RF Relacionados
- RF06

### RN Relacionadas
- RN03 (Prazo de cancelamento)

<img width="258" height="246" alt="07" src="https://github.com/user-attachments/assets/ddc50abb-914c-4b78-b788-83f0135b890c" />


---

## UC08 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Confirmar presença dos alunos na aula.

### Pré-condições
- Aula em andamento ou finalizada.

### Fluxo Principal
1. O instrutor acessa a lista de alunos.
2. O instrutor marca presença.
3. O sistema salva as informações.

### RF Relacionados
- RF07

### RN Relacionadas
- RN06 (Perfil Instrutor)

<img width="166" height="240" alt="08" src="https://github.com/user-attachments/assets/c41dc802-72e0-4063-9d41-bcdd8c56c8fb" />


---

## UC09 — Realizar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar evolução física do aluno.

### Pré-condições
- Aluno ativo e regular (RN05).

### Pós-condições
- Avaliação salva no perfil do aluno.

### Fluxo Principal
1. O instrutor registra medidas corporais.
2. O instrutor anexa exames ou fotos (RF08).
3. O sistema salva a avaliação e notifica o aluno.

### RF Relacionados
- RF08
- RF10

### RN Relacionadas
- RN05

<img width="135" height="295" alt="09" src="https://github.com/user-attachments/assets/f62de20a-1fac-4302-a82b-6c8170897786" />


---

## UC10 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Identificar alunos com mensalidades em atraso.

### Fluxo Principal
1. O gerente solicita o relatório.
2. O sistema filtra alunos com dívidas.
3. O sistema gera lista exportável.

### RF Relacionados
- RF09

- <img width="147" height="234" alt="10" src="https://github.com/user-attachments/assets/bf14120c-fc61-4d9a-85bd-65e67d315ca6" />


---

## UC11 — Gerar Boleto Online

### Ator Principal
Aluno

### Objetivo
Emitir boleto para pagamento de mensalidade.

### Fluxo Principal
1. O aluno acessa área financeira.
2. O aluno seleciona fatura.
3. O sistema gera boleto ou linha digitável.

### RF Relacionados
- RF03

- <img width="168" height="243" alt="11" src="https://github.com/user-attachments/assets/66539005-da34-4af6-ac94-3df2a52ae4fb" />


---

## UC12 — Configurar Notificações Automáticas

### Ator Principal
Sistema

### Objetivo
Notificar alunos automaticamente.

### Fluxo Principal
1. O sistema verifica vencimentos diariamente.
2. O sistema envia notificações automáticas.

### RF Relacionados
- RF10

<img width="152" height="180" alt="12" src="https://github.com/user-attachments/assets/301c7fa7-d656-476c-b2b3-0941f9e2c75a" />


---

## UC13 — Consultar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Monitorar entradas e saídas de alunos.

### Fluxo Principal
1. O gerente seleciona período.
2. O sistema exibe registros da catraca.

### RF Relacionados
- RF09

- <img width="143" height="239" alt="13" src="https://github.com/user-attachments/assets/c0d9c240-b017-4516-be2c-451b5799f5aa" />


---

## UC14 — Inativar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Suspender acesso de um aluno.

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O recepcionista seleciona "inativar".
3. O sistema registra a alteração.

### RF Relacionados
- RF01

<img width="137" height="238" alt="14" src="https://github.com/user-attachments/assets/1fd204e8-24f9-4053-a9c5-08de6488d0b7" />


---

## UC15 — Consultar Ocupação das Aulas

### Ator Principal
Gerente

### Objetivo
Avaliar popularidade das aulas.

### Fluxo Principal
1. O gerente acessa relatórios.
2. O sistema mostra taxa de ocupação.

### RF Relacionados
- RF09

<img width="138" height="235" alt="15" src="https://github.com/user-attachments/assets/147d9ea4-d64d-48d4-87c1-355c989712aa" />


---

## UC16 — Anexar Documentos de Saúde

### Ator Principal
Instrutor

### Objetivo
Armazenar documentos médicos dos alunos.

### Fluxo Principal
1. O instrutor acessa perfil do aluno.
2. O instrutor envia arquivos.
3. O sistema armazena documentos.

### RF Relacionados
- RF08

<img width="137" height="236" alt="16" src="https://github.com/user-attachments/assets/6b56a7db-11b0-4c48-a730-239b179fe31e" />


---

## UC17 — Visualizar Grade de Horários

### Ator Principal
Aluno

### Objetivo
Consultar horários de aulas disponíveis.

### Fluxo Principal
1. O aluno acessa agenda.
2. O sistema exibe grade semanal.

### RF Relacionados
- RF06

- <img width="126" height="187" alt="17" src="https://github.com/user-attachments/assets/5d1a73e9-b7b5-4da0-910c-06344aca7b0c" />


---

## UC18 — Consultar Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Obter estatísticas de alunos matriculados.

### Fluxo Principal
1. O gerente solicita listagem.
2. O sistema gera relatório.

### RF Relacionados
- RF09

- <img width="128" height="187" alt="18" src="https://github.com/user-attachments/assets/5214fefa-abd9-4554-ad2f-169b0b7150e4" />


---

## UC19 — Atualizar Dados Cadastrais

### Ator Principal
Recepcionista

### Objetivo
Atualizar dados de contato ou endereço.

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O recepcionista altera dados.
3. O sistema salva alterações.

### RF Relacionados
- RF01

<img width="131" height="237" alt="19" src="https://github.com/user-attachments/assets/57f5ac23-b5bb-4b2c-aa75-7cd829fb2a08" />


---

## UC20 — Redefinir Senha de Acesso

### Ator Principal
Usuário

### Objetivo
Permitir recuperação segura da senha.

### Fluxo Principal
1. O usuário solicita redefinição.
2. O sistema envia link por e-mail.
3. O usuário define nova senha.
4. O sistema atualiza as credenciais.

### RNF Relacionados
- RNF02 (Segurança)

<img width="149" height="294" alt="20" src="https://github.com/user-attachments/assets/24a0880c-c660-448e-9762-d22cbc44f65d" />

