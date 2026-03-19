![alt text](image-1.png)

## UC01 — Realizar Login

### Ator Principal
Usuario

### Objetivo
Permitir que o usuario autenticado acesse o sistema de acordo com seu perfil.

### Pre-condicoes
- Usuario deve possuir cadastro ativo.
- Usuario deve possuir credenciais validas.

### Pos-condicoes
- Sessao iniciada com sucesso.
- Perfil do usuario carregado com as permissoes correspondentes.

### Fluxo Principal
1. O usuario informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema identifica o perfil (Aluno, Recepcionista, Instrutor ou Gerente).
4. O sistema redireciona para a tela inicial apropriada.

### Fluxos Alternativos
- **A1 — Senha incorreta:**
  O sistema exibe mensagem de erro e permite nova tentativa.

- **A2 — Conta inativa:**
  O sistema impede o login e informa que o cadastro precisa ser regularizado.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02
- RNF04

### RN Relacionadas
- RN06

![alt text](image.png)

---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema com dados pessoais e plano inicial.

### Pre-condicoes
- Recepcionista autenticado.
- Plano ativo disponivel para contratacao.

### Pos-condicoes
- Cadastro do aluno criado.
- Vinculo inicial com plano registrado.

### Fluxo Principal
1. O recepcionista acessa a tela de cadastro de alunos.
2. O recepcionista informa dados pessoais, contato e endereco.
3. O recepcionista seleciona o plano contratado.
4. O sistema valida os dados obrigatorios.
5. O sistema grava o cadastro e confirma a matricula.

### Fluxos Alternativos
- **A1 — Dados obrigatorios ausentes:**
  O sistema destaca os campos pendentes e solicita correcao.

- **A2 — Plano inativo:**
  O sistema impede a vinculacao e solicita selecao de plano ativo.

### RF Relacionados
- RF01
- RF02

### RNF Relacionados
- RNF04
- RNF05

### RN Relacionadas
- RN06

![alt text](image-2.png)

---

## UC03 — Atualizar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Manter dados cadastrais do aluno atualizados.

### Pre-condicoes
- Recepcionista autenticado.
- Aluno previamente cadastrado.

### Pos-condicoes
- Dados do aluno atualizados no sistema.

### Fluxo Principal
1. O recepcionista busca o aluno.
2. O sistema exibe os dados atuais.
3. O recepcionista altera os campos necessarios.
4. O sistema valida as alteracoes.
5. O sistema salva os novos dados.

### Fluxos Alternativos
- **A1 — Aluno nao encontrado:**
  O sistema informa que nao ha cadastro com os criterios informados.

- **A2 — Formato invalido de contato:**
  O sistema rejeita a gravacao e solicita ajuste.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

![alt text](image-3.png)

---

## UC04 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Criar, editar, ativar e desativar planos da academia.

### Pre-condicoes
- Gerente autenticado.

### Pos-condicoes
- Catalogo de planos atualizado.

### Fluxo Principal
1. O gerente acessa o modulo de planos.
2. O gerente escolhe criar, editar, ativar ou desativar um plano.
3. O gerente informa nome, duracao, valor e modalidade.
4. O sistema valida os dados.
5. O sistema confirma a alteracao do plano.

### Fluxos Alternativos
- **A1 — Dados incompletos do plano:**
  O sistema impede o salvamento e informa os campos faltantes.

- **A2 — Tentativa de desativar plano com regra impeditiva:**
  O sistema apresenta alerta e solicita confirmacao ou ajuste.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF04
- RNF05

### RN Relacionadas
- RN06

![alt text](image-4.png)

---

## UC05 — Registrar Matricula em Plano

### Ator Principal
Recepcionista

### Objetivo
Vincular aluno a um plano ativo no momento da matricula ou troca.

### Pre-condicoes
- Recepcionista autenticado.
- Aluno cadastrado.
- Plano ativo disponivel.

### Pos-condicoes
- Matricula vinculada ao plano selecionado.

### Fluxo Principal
1. O recepcionista seleciona o aluno.
2. O recepcionista escolhe o plano ativo.
3. O sistema apresenta resumo financeiro.
4. O recepcionista confirma a matricula.
5. O sistema registra a vinculacao do plano.

### Fluxos Alternativos
- **A1 — Plano indisponivel:**
  O sistema bloqueia a vinculacao e lista planos ativos.

- **A2 — Dados cadastrais pendentes:**
  O sistema solicita atualizacao cadastral antes da matricula.

### RF Relacionados
- RF01
- RF02

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

![alt text](image-5.png)

---

## UC06 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade na recepcao.

### Pre-condicoes
- Recepcionista autenticado.
- Aluno com cobranca em aberto.

### Pos-condicoes
- Pagamento registrado.
- Situacao financeira atualizada.

### Fluxo Principal
1. O recepcionista seleciona o aluno e a cobranca.
2. O sistema exibe valor integral devido.
3. O recepcionista escolhe forma de pagamento (dinheiro, cartao ou PIX).
4. O sistema registra o pagamento.
5. O sistema atualiza a regularidade do aluno.

### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:**
  O sistema bloqueia a operacao e informa que somente valor integral e permitido.

- **A2 — Falha na confirmacao de transacao:**
  O sistema nao conclui o registro e orienta nova tentativa.

### RF Relacionados
- RF03
- RF04

### RNF Relacionados
- RNF02
- RNF03

### RN Relacionadas
- RN04
- RN07
- RN06

![alt text](image-6.png)

---

## UC07 — Gerar Cobranca Online

### Ator Principal
Recepcionista

### Objetivo
Emitir boleto ou cobranca digital para pagamento online.

### Pre-condicoes
- Recepcionista autenticado.
- Aluno com mensalidade a vencer ou vencida.

### Pos-condicoes
- Cobranca online emitida e vinculada ao aluno.

### Fluxo Principal
1. O recepcionista seleciona o aluno.
2. O recepcionista escolhe emitir cobranca online.
3. O sistema gera boleto/cartao com valor da mensalidade.
4. O sistema registra a cobranca e disponibiliza comprovante.

### Fluxos Alternativos
- **A1 — Aluno sem plano ativo:**
  O sistema impede a emissao da cobranca.

- **A2 — Erro no servico de cobranca:**
  O sistema exibe falha de integracao e agenda nova tentativa.

### RF Relacionados
- RF03

### RNF Relacionados
- RNF02
- RNF03

### RN Relacionadas
- RN04
- RN06

![alt text](image-7.png)

---

## UC08 — Atualizar Regularidade do Aluno

### Ator Principal
Sistema

### Objetivo
Atualizar automaticamente a situacao de regularidade apos eventos financeiros.

### Pre-condicoes
- Existencia de evento financeiro (pagamento ou vencimento).

### Pos-condicoes
- Status do aluno atualizado para regular ou irregular.

### Fluxo Principal
1. O sistema detecta o evento financeiro.
2. O sistema consulta a data de vencimento e o status de pagamento.
3. O sistema calcula a situacao de regularidade.
4. O sistema grava o status atualizado.

### Fluxos Alternativos
- **A1 — Inconsistencia de dados financeiros:**
  O sistema marca o registro para revisao e notifica a recepcao.

- **A2 — Falha temporaria de processamento:**
  O sistema reprocessa o evento em fila.

### RF Relacionados
- RF04
- RF03

### RNF Relacionados
- RNF03
- RNF05

### RN Relacionadas
- RN01
- RN07

![alt text](image-8.png)

---

## UC09 — Validar Acesso na Catraca

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Autorizar ou negar entrada do aluno com base em RFID e regularidade.

### Pre-condicoes
- Aluno identificado por RFID.
- Integracao com API de catraca disponivel.

### Pos-condicoes
- Entrada autorizada ou negada com registro de tentativa.

### Fluxo Principal
1. A catraca envia o identificador RFID ao sistema.
2. O sistema localiza o aluno correspondente.
3. O sistema verifica regularidade do aluno.
4. O sistema retorna autorizacao ou bloqueio para a catraca.
5. O sistema registra o evento de acesso.

### Fluxos Alternativos
- **A1 — Aluno inadimplente ha mais de 5 dias:**
  O sistema nega o acesso.

- **A2 — Falha de comunicacao com a catraca:**
  O sistema registra erro e orienta contingencia na recepcao.

### RF Relacionados
- RF05
- RF04

### RNF Relacionados
- RNF03
- RNF06
- RNF01

### RN Relacionadas
- RN01

![alt text](image-10.png)

---

## UC10 — Consultar Horarios de Aulas

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize turmas e horarios disponiveis.

### Pre-condicoes
- Aluno autenticado.

### Pos-condicoes
- Grade de aulas exibida ao aluno.

### Fluxo Principal
1. O aluno acessa a area de agendamento.
2. O sistema exibe aulas por data, horario e modalidade.
3. O aluno filtra por tipo de aula, se desejado.

### Fluxos Alternativos
- **A1 — Sem aulas disponiveis para o periodo:**
  O sistema informa indisponibilidade.

- **A2 — Falha de carregamento temporaria:**
  O sistema sugere nova tentativa.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04
- RNF03

### RN Relacionadas
- RN02

![alt text](image-11.png)

---

## UC11 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Reservar vaga em uma aula da grade.

### Pre-condicoes
- Aluno autenticado e regular.
- Aula com vagas disponiveis.

### Pos-condicoes
- Reserva registrada para o aluno.
- Confirmacao enviada ao aluno.

### Fluxo Principal
1. O aluno escolhe uma aula disponivel.
2. O sistema verifica vagas e situacao do aluno.
3. O aluno confirma a reserva.
4. O sistema registra o agendamento.
5. O sistema envia notificacao de confirmacao.

### Fluxos Alternativos
- **A1 — Turma lotada:**
  O sistema impede o agendamento por limite de vagas.

- **A2 — Aluno irregular:**
  O sistema bloqueia a reserva e informa pendencia financeira.

### RF Relacionados
- RF06
- RF10
- RF04

### RNF Relacionados
- RNF03
- RNF04

### RN Relacionadas
- RN02
- RN01

![alt text](image-12.png)

---

## UC12 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Permitir cancelamento de reserva dentro do prazo permitido.

### Pre-condicoes
- Aluno autenticado.
- Reserva existente para aula futura.

### Pos-condicoes
- Reserva cancelada e vaga liberada.

### Fluxo Principal
1. O aluno acessa seus agendamentos.
2. O aluno seleciona a reserva a cancelar.
3. O sistema valida o prazo de cancelamento.
4. O sistema confirma o cancelamento e libera a vaga.

### Fluxos Alternativos
- **A1 — Prazo inferior a 1 hora para inicio:**
  O sistema impede o cancelamento.

- **A2 — Reserva inexistente:**
  O sistema informa que a reserva nao foi encontrada.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF03
- RNF04

### RN Relacionadas
- RN03
- RN02

![alt text](image-13.png)

---

## UC13 — Registrar Presenca em Aula

### Ator Principal
Instrutor

### Objetivo
Registrar os alunos presentes em uma aula realizada.

### Pre-condicoes
- Instrutor autenticado.
- Aula iniciada e lista de alunos agendados disponivel.

### Pos-condicoes
- Lista de presenca registrada.

### Fluxo Principal
1. O instrutor abre a aula do horario atual.
2. O sistema exibe lista de alunos agendados.
3. O instrutor marca presencas e ausencias.
4. O sistema salva o registro da aula.

### Fluxos Alternativos
- **A1 — Aluno nao agendado solicita entrada:**
  O sistema permite ajuste apenas conforme regra operacional definida.

- **A2 — Queda de conexao durante o registro:**
  O sistema salva rascunho e permite retomar o preenchimento.

### RF Relacionados
- RF07

### RNF Relacionados
- RNF03
- RNF04

### RN Relacionadas
- RN06

![alt text](image-14.png)

---

## UC14 — Registrar Avaliacao Fisica

### Ator Principal
Instrutor

### Objetivo
Registrar medidas e resultados da avaliacao fisica do aluno.

### Pre-condicoes
- Instrutor autenticado.
- Aluno ativo e regular.

### Pos-condicoes
- Avaliacao fisica registrada no historico do aluno.

### Fluxo Principal
1. O instrutor seleciona o aluno.
2. O sistema verifica se o aluno esta ativo e regular.
3. O instrutor informa peso, IMC, percentual de gordura e observacoes.
4. O sistema grava os dados da avaliacao.

### Fluxos Alternativos
- **A1 — Aluno irregular ou inativo:**
  O sistema bloqueia a avaliacao.

- **A2 — Dados fisiologicos fora de faixa esperada:**
  O sistema solicita confirmacao antes de salvar.

### RF Relacionados
- RF08
- RF04

### RNF Relacionados
- RNF02
- RNF04

### RN Relacionadas
- RN05
- RN06

![alt text](image-15.png)

---

## UC15 — Anexar Arquivos na Avaliacao Fisica

### Ator Principal
Instrutor

### Objetivo
Anexar arquivos complementares a uma avaliacao fisica.

### Pre-condicoes
- Instrutor autenticado.
- Avaliacao fisica em criacao ou existente.

### Pos-condicoes
- Arquivo anexado e vinculado ao registro da avaliacao.

### Fluxo Principal
1. O instrutor acessa uma avaliacao fisica.
2. O instrutor seleciona arquivo para anexo.
3. O sistema valida formato e tamanho permitidos.
4. O sistema armazena e vincula o arquivo a avaliacao.

### Fluxos Alternativos
- **A1 — Formato nao permitido:**
  O sistema rejeita o upload e informa formatos aceitos.

- **A2 — Falha no envio:**
  O sistema informa erro e permite nova tentativa.

### RF Relacionados
- RF08

### RNF Relacionados
- RNF02
- RNF03

### RN Relacionadas
- RN05
- RN06

![alt text](image-16.png)

---

## UC16 — Emitir Relatorio de Inadimplencia

### Ator Principal
Gerente

### Objetivo
Gerar relatorio de alunos com mensalidades em atraso.

### Pre-condicoes
- Gerente autenticado.

### Pos-condicoes
- Relatorio de inadimplencia exibido ou exportado.

### Fluxo Principal
1. O gerente acessa o modulo de relatorios.
2. O gerente seleciona relatorio de inadimplencia.
3. O sistema aplica filtros e consolida dados.
4. O sistema apresenta o relatorio.

### Fluxos Alternativos
- **A1 — Nenhum aluno inadimplente no periodo:**
  O sistema exibe resultado vazio.

- **A2 — Falha na geracao do relatorio:**
  O sistema registra erro e permite nova execucao.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF03
- RNF05

### RN Relacionadas
- RN01
- RN06

![alt text](image-17.png)

---

## UC17 — Emitir Relatorio de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Gerar relatorio com alunos ativos por unidade e periodo.

### Pre-condicoes
- Gerente autenticado.

### Pos-condicoes
- Relatorio de alunos ativos disponibilizado.

### Fluxo Principal
1. O gerente seleciona o relatorio de alunos ativos.
2. O gerente informa filtros de unidade e periodo.
3. O sistema consulta cadastros e status.
4. O sistema exibe o relatorio consolidado.

### Fluxos Alternativos
- **A1 — Filtros invalidos:**
  O sistema solicita ajuste dos criterios.

- **A2 — Sem resultados para os filtros:**
  O sistema exibe relatorio sem registros.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF05
- RNF03

### RN Relacionadas
- RN06

![alt text](image-18.png)

---

## UC18 — Emitir Relatorio de Historico de Acessos

### Ator Principal
Gerente

### Objetivo
Gerar historico de entradas e tentativas de acesso dos alunos.

### Pre-condicoes
- Gerente autenticado.
- Eventos de acesso registrados no sistema.

### Pos-condicoes
- Relatorio de historico de acessos gerado.

### Fluxo Principal
1. O gerente seleciona relatorio de historico de acessos.
2. O gerente define periodo e unidade.
3. O sistema consolida dados de acesso e bloqueios.
4. O sistema apresenta o relatorio para analise.

### Fluxos Alternativos
- **A1 — Integracao da catraca com registros incompletos:**
  O sistema sinaliza lacunas de dados no relatorio.

- **A2 — Periodo sem movimentacao:**
  O sistema retorna relatorio vazio.

### RF Relacionados
- RF09
- RF05

### RNF Relacionados
- RNF06
- RNF03

### RN Relacionadas
- RN01
- RN06

![alt text](image-19.png)

---

## UC19 — Emitir Relatorio de Ocupacao das Aulas

### Ator Principal
Gerente

### Objetivo
Gerar relatorio sobre taxa de ocupacao das turmas.

### Pre-condicoes
- Gerente autenticado.
- Registros de agendamento e presenca existentes.

### Pos-condicoes
- Relatorio de ocupacao das aulas disponibilizado.

### Fluxo Principal
1. O gerente acessa o relatorio de ocupacao.
2. O gerente informa periodo e modalidade.
3. O sistema calcula vagas totais, reservas e presencas.
4. O sistema exibe taxa de ocupacao por turma.

### Fluxos Alternativos
- **A1 — Modalidade sem turmas no periodo:**
  O sistema informa ausencia de dados.

- **A2 — Inconsistencia entre reserva e presenca:**
  O sistema destaca divergencias para revisao.

### RF Relacionados
- RF09
- RF06
- RF07

### RNF Relacionados
- RNF03
- RNF05

### RN Relacionadas
- RN02
- RN06

![alt text](image-20.png)

---

## UC20 — Enviar Notificacoes ao Aluno

### Ator Principal
Sistema

### Objetivo
Notificar o aluno sobre eventos importantes de pagamento e agenda.

### Pre-condicoes
- Evento elegivel gerado (vencimento, confirmacao de agendamento, liberacao de avaliacao).
- Dados de contato do aluno disponiveis.

### Pos-condicoes
- Notificacao enviada e registrada no historico.

### Fluxo Principal
1. O sistema identifica evento de notificacao.
2. O sistema monta mensagem conforme o tipo de evento.
3. O sistema envia a notificacao ao aluno.
4. O sistema registra status de envio.

### Fluxos Alternativos
- **A1 — Falha temporaria no canal de envio:**
  O sistema agenda retentativa automatica.

- **A2 — Contato invalido:**
  O sistema registra falha e sinaliza necessidade de atualizacao cadastral.

### RF Relacionados
- RF10
- RF03
- RF06
- RF08

### RNF Relacionados
- RNF03
- RNF05

### RN Relacionadas
- RN07

![alt text](image-21.png)
