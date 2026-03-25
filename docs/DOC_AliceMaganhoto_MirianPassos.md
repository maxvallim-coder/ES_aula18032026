## UC01 — Realizar Login (UC EXEMPLO - FAZER DESSA FORMA PARA TODOS OS CASOS DE USO, NESSE MESMO DOCUMENTO)

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
- (inserir RF aqui)

### RNF Relacionados
- (inserir RNF aqui)

### RN Relacionadas
- (inserir RN aqui)

- ## UC01 – Efetuar Matrícula de Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema vinculado a um plano.

### Pré-condições
- Aluno não deve possuir cadastro ativo.
- Usuário deve ter perfil de Recepcionista ou Gerente (RN06).

### Pós-condições
- Matrícula realizada e contrato gerado.

### Fluxo Principal
1. O recepcionista informa os dados pessoais, contato e endereço do aluno.
2. O sistema valida se o CPF já existe na base.
3. O recepcionista seleciona o plano de adesão (RF02).
4. O sistema salva o cadastro e gera a matrícula.

### Fluxos Alternativos
- **A1 – CPF já cadastrado:**
O sistema informa que já existe um registro e impede a duplicidade.

### RF Relacionados
- RF01, RF02

### RNF Relacionados
- RNF02, RNF04, RNF05

### RN Relacionadas
- RN06
<img width="442" height="80" alt="image" src="https://github.com/user-attachments/assets/717117a1-c7d4-48f5-89cf-6aa186b18283" />

---

## UC02 – Gerenciar Planos de Assinatura

### Ator Principal
Gerente

### Objetivo
Criar ou editar as modalidades de planos da academia.

### Pré-condições
- Usuário autenticado com perfil de Gerente (RN06).

### Pós-condições
- Plano disponível no sistema para novas vendas.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O gerente define nome, valor e periodicidade (RF02).
3. O sistema salva as configurações.

### Fluxos Alternativos
- **A1 – Plano Inativo:**
O gerente desativa um plano; o sistema impede novas matrículas nele.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF01, RNF02

### RN Relacionadas
- RN06
<img width="1301" height="311" alt="image" src="https://github.com/user-attachments/assets/7e8a27ff-f315-40ad-ba82-7d03567ebc6e" />

---

## UC03 – Registrar Pagamento de Mensalidade

### Ator Principal
Recepcionista

### Objetivo
Dar baixa em parcelas financeiras e atualizar a situação do aluno.

### Pré-condições
- Existência de débito integral (RN04).
- Perfil de Recepcionista (RN06).

### Pós-condições
- Pagamento registrado e situação do aluno atualizada imediatamente (RN07).

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O sistema exibe o valor integral da mensalidade.
3. O recepcionista registra o pagamento via dinheiro, cartão ou PIX (RF03).
4. O sistema atualiza o status do aluno para regular (RN07).

### Fluxos Alternativos
- **A1 – Tentativa de pagamento parcial:**
O sistema impede a operação conforme a regra RN04.

### RF Relacionados
- RF03, RF04

### RNF Relacionados
- RNF02, RNF03

### RN Relacionadas
- RN04, RN06, RN07

<img width="1657" height="429" alt="image" src="https://github.com/user-attachments/assets/15e214eb-b607-4273-ab68-7d41851faf53" />

---

## UC04 – Validar Acesso na Catraca (RFID)

### Ator Principal
Sistema de Catraca (API)

### Objetivo
Validar a entrada física do aluno baseada na regularidade financeira.

### Pré-condições
- Aluno possuir Tag RFID cadastrada.

### Pós-condições
- Acesso liberado ou bloqueado no hardware da catraca.

### Fluxo Principal
1. O aluno aproxima a tag do leitor.
2. O sistema verifica se o vencimento da mensalidade é superior a 5 dias (RN01).
3. O sistema libera a catraca se o aluno estiver regular.
4. A comunicação ocorre via JSON (RNF06).

### Fluxos Alternativos
- **A1 – Aluno com atraso > 5 dias:**
O sistema bloqueia a entrada conforme a regra RN01.

### RF Relacionados
- RF04, RF05

### RNF Relacionados
- RNF03, RNF06

### RN Relacionadas
- RN01

<img width="570" height="114" alt="image" src="https://github.com/user-attachments/assets/7e7040cc-647d-4de9-b672-932b0228c297" />

---

## UC05 – Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em aula respeitando o limite do espaço.

### Pré-condições
- Aluno deve estar com a situação regular e autenticado no sistema.

### Pós-condições
- Vaga reservada no sistema.

### Fluxo Principal
1. O aluno escolhe a aula e horário no App (RF06).
2. O sistema verifica se o limite de vagas foi atingido (RN02).
3. O sistema confirma a reserva se houver vaga.

### Fluxos Alternativos
- **A1 – Limite de vagas atingido:**
O sistema bloqueia novos agendamentos conforme RN02.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF03, RNF04

### RN Relacionadas
- RN02

<img width="442" height="89" alt="image" src="https://github.com/user-attachments/assets/de6130eb-d109-4ea7-8ef7-7eed75ab48cf" />

---

## UC06 – Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Registrar a presença dos alunos agendados.

### Pré-condições
- Perfil de Instrutor (RN06).

### Pós-condições
- Lista de frequência atualizada.

### Fluxo Principal
1. O instrutor acessa a lista da aula (RF07).
2. O instrutor marca os alunos presentes.
3. O sistema salva os dados de forma persistente.

### Fluxos Alternativos
- (não identificado)

### RF Relacionados
- RF07

### RNF Relacionados
- RNF01, RNF04

### RN Relacionadas
- RN06

<img width="493" height="127" alt="image" src="https://github.com/user-attachments/assets/668e1b21-fd89-4ff1-ab3b-8734c34f72c4" />

---

## UC07 – Realizar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar medições corporais apenas em alunos regulares.

### Pré-condições
- Aluno estar ativo e regular (RN05).
- Perfil de Instrutor (RN06).

### Pós-condições
- Avaliação registrada com dados sensíveis criptografados (RNF02).

### Fluxo Principal
1. O instrutor busca o aluno.
2. O sistema valida se o aluno está regular (RN05).
3. O instrutor insere peso, IMC e gordura (RF08).
4. O sistema salva os dados criptografados.

### Fluxos Alternativos
- **A1 – Aluno Irregular:**
O sistema impede o acesso ao formulário de avaliação conforme RN05.

### RF Relacionados
- RF08

### RNF Relacionados
- RNF02, RNF04

### RN Relacionadas
- RN05, RN06

<img width="579" height="192" alt="image" src="https://github.com/user-attachments/assets/759cd669-9463-4a06-a122-53b955cee71b" />

---

## UC08 – Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Cancelar uma reserva respeitando o prazo limite de 1 hora.

### Pré-condições
- Possuir agendamento ativo e ser via interface responsiva (RNF04).

### Pós-condições
- Vaga liberada no sistema.

### Fluxo Principal
1. O aluno solicita o cancelamento da aula pelo celular.
2. O sistema verifica se falta mais de 1 hora para o início (RN03).
3. O sistema confirma o cancelamento.

### Fluxos Alternativos
- **A1 – Fora do prazo:**
O sistema impede o cancelamento se faltar menos de 1 hora conforme RN03.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN03
<img width="572" height="155" alt="image" src="https://github.com/user-attachments/assets/e52cc40b-1bf9-4ea8-879b-b837a9a2357f" />

---

## UC09 – Emitir Relatórios Gerenciais

### Ator Principal
Gerente

### Objetivo
Listar dados de inadimplência, frequência e ocupação.

### Pré-condições
- Perfil de Gerente (RN06).

### Pós-condições
- Relatório exibido na interface desktop (RNF04).

### Fluxo Principal
1. O gerente solicita o relatório desejado (RF09).
2. O sistema varre a base de dados (criptografada).
3. O sistema exibe os resultados em tela.

### Fluxos Alternativos
- (não identificado)

### RF Relacionados
- RF09

### RNF Relacionados
- RNF01, RNF02, RNF04

### RN Relacionadas
- RN06
<img width="541" height="175" alt="image" src="https://github.com/user-attachments/assets/03c6ae38-73ef-4b51-9691-f984a37de40d" />

---

## UC10 – Enviar Notificação Push/E-mail

### Ator Principal
Sistema (Automático)

### Objetivo
Alertar o aluno sobre vencimentos ou agendamentos.

### Pré-condições
- Ocorrência de evento gatilho (vencimento ou agendamento).

### Pós-condições
- Notificação entregue no dispositivo do aluno.

### Fluxo Principal
1. O sistema identifica alunos com parcelas a vencer (RF04/RF10).
2. O sistema dispara notificação via serviço de mensageria.

### Fluxos Alternativos
- (não identificado)

### RF Relacionados
- RF10

### RNF Relacionados
- RNF01, RNF03

### RN Relacionadas
- (não se aplica)
  <img width="442" height="164" alt="image" src="https://github.com/user-attachments/assets/4dd0bcc3-d70e-4f8a-945c-fe86aff19fe2" />

---

## UC11 – Consultar Alunos Ativos por Unidade

### Ator Principal
Gerente

### Objetivo
Visualizar matrículas ativas em múltiplos polos da FitPass.

### Pré-condições
- Perfil de Gerente (RN06) e suporte a escalabilidade (RNF05).

### Pós-condições
- Listagem consolidada exibida.

### Fluxo Principal
1. O gerente seleciona a unidade desejada.
2. O sistema filtra os dados respeitando a escalabilidade (RNF05).
3. O sistema exibe o total de alunos ativos.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF05

### RN Relacionadas
- RN06
<img width="550" height="166" alt="image" src="https://github.com/user-attachments/assets/393a5bee-38b5-4d99-a170-05fdd071a53a" />

---

## UC12 – Monitorar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Auditar as entradas via catraca por período.

### Pré-condições
- Perfil de Gerente (RN06).

### Pós-condições
- Log de acessos disponível para visualização.

### Fluxo Principal
1. O gerente acessa o menu de histórico de acessos (RF09).
2. O sistema requisita dados via API REST (RNF06).
3. O histórico é exibido.

### RF Relacionados
- RF05, RF09

### RNF Relacionados
- RNF06

### RN Relacionadas
- RN06
<img width="538" height="165" alt="image" src="https://github.com/user-attachments/assets/2c381a76-4ed5-4c70-ad1e-a35d6a7cc5ec" />

---

## UC13 – Analisar Ocupação das Aulas

### Ator Principal
Gerente

### Objetivo
Verificar se o limite de vagas (RN02) está sendo eficiente.

### Pré-condições
- Presenças registradas pelos instrutores (RF07).

### Pós-condições
- Gráfico de ocupação gerado.

### Fluxo Principal
1. O gerente acessa o relatório de ocupação (RF09).
2. O sistema cruza vagas totais com presenças reais.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN02, RN06
<img width="521" height="131" alt="image" src="https://github.com/user-attachments/assets/24f72997-a815-4a7f-8f4a-061cf5901d29" />

---

## UC14 – Registrar Avaliação Física (Upload de Anexo)

### Ator Principal
Instrutor

### Objetivo
Anexar arquivos de resultados de exames.

### Pré-condições
- Aluno regular (RN05) e conexão estável (RNF01).

### Pós-condições
- Arquivo armazenado e criptografado (RNF02).

### Fluxo Principal
1. O instrutor seleciona o aluno.
2. O instrutor faz o upload do arquivo anexado (RF08).
3. O sistema criptografa e salva o documento.

### RF Relacionados
- RF08

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN05, RN06
<img width="506" height="200" alt="image" src="https://github.com/user-attachments/assets/5527f881-5922-4674-be3c-d4cdd0b9c76c" />

---

## UC15 – Editar Perfil do Aluno

### Ator Principal
Recepcionista

### Objetivo
Atualizar dados de contato e endereço.

### Pré-condições
- Perfil de Recepcionista (RN06).

### Pós-condições
- Cadastro atualizado com tempo de resposta rápido (RNF03).

### Fluxo Principal
1. O recepcionista busca o aluno.
2. Altera os dados e clica em salvar.
3. O sistema valida e processa em menos de 3 segundos (RNF03).

### RF Relacionados
- RF01

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN06
<img width="502" height="159" alt="image" src="https://github.com/user-attachments/assets/a8dca1e7-a9a1-4a9f-9629-2d951ba2b1d9" />

---

## UC16 – Bloquear Acesso via Gestão

### Ator Principal
Gerente

### Objetivo
Impedir acesso imediato por questões administrativas.

### Pré-condições
- Comunicação API REST ativa (RNF06).

### Pós-condições
- Hardware da catraca bloqueado para o ID específico.

### Fluxo Principal
1. O gerente aciona o bloqueio no sistema.
2. O sistema envia pacote JSON via API para a catraca (RNF06).

### RF Relacionados
- RF05

### RNF Relacionados
- RNF06

### RN Relacionadas
- RN06
<img width="489" height="161" alt="image" src="https://github.com/user-attachments/assets/851a0295-3373-4e4e-bfa8-171afff49eb6" />

---

## UC17 – Notificar Liberação de Resultado

### Ator Principal
Sistema (Automático)

### Objetivo
Avisar o aluno que sua avaliação foi concluída.

### Pré-condições
- Avaliação finalizada pelo instrutor (RF08).

### Pós-condições
- Aluno recebe alerta push (RF10).

### Fluxo Principal
1. O instrutor encerra a avaliação.
2. O sistema detecta a mudança e dispara a notificação (RF10).

### RF Relacionados
- RF10

### RNF Relacionados
- RNF01
<img width="397" height="156" alt="image" src="https://github.com/user-attachments/assets/4ed65a13-5d68-42ad-ac6a-ef0286e5faa4" />

---

## UC18 – Visualizar Grade Mobile

### Ator Principal
Aluno

### Objetivo
Consultar horários de aula via interface responsiva.

### Pré-condições
- Acesso ao aplicativo FitPass (RNF04).

### Pós-condições
- Grade carregada em tela.

### Fluxo Principal
1. O aluno abre o menu "Aulas".
2. O sistema carrega a grade respeitando o design mobile (RNF04).

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04
<img width="356" height="165" alt="image" src="https://github.com/user-attachments/assets/cdeca4cb-6112-43d6-a3c7-b444bc574944" />

---

## UC19 – Confirmar Agendamento de Vaga

### Ator Principal
Sistema (Automático)

### Objetivo
Garantir ao aluno que sua vaga foi reservada respeitando o limite (RN02).

### Pré-condições
- Reserva processada com sucesso.

### Pós-condições
- Confirmação exibida e enviada (RF10).

### Fluxo Principal
1. O sistema valida a reserva e retorna confirmação em menos de 3 segundos (RNF03).

### RF Relacionados
- RF06, RF10

### RNF Relacionados
- RNF03
<img width="408" height="185" alt="image" src="https://github.com/user-attachments/assets/5366ed85-e070-46c4-af7d-5aed24f7e871" />

---

## UC20 – Cancelar Matrícula

### Ator Principal
Recepcionista

### Objetivo
Inativar o aluno do sistema por solicitação.

### Pré-condições
- Perfil de Recepcionista (RN06).

### Pós-condições
- Status de matrícula alterado para Inativo.

### Fluxo Principal
1. O recepcionista localiza o cadastro.
2. O recepcionista confirma o encerramento da matrícula.
3. O sistema remove as permissões de acesso.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN06
<img width="472" height="157" alt="image" src="https://github.com/user-attachments/assets/87d83464-fcb2-42ca-bc46-14b6fa74ac79" />
