## Diagramas de Caso de Uso

<img width="746" height="420" alt="DUC_01_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/0e36565e-56d8-4584-a907-41014b8454cc" />

<img width="468" height="338" alt="DUC_02_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/b6d85da3-c3d3-4591-b89c-a97020b8bddb" />

<img width="332" height="112" alt="DUC_03_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/ead333ec-f4e5-4e47-a29c-9033598ff344" />

<img width="377" height="119" alt="DUC_04_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/b5aa6124-f67a-456b-ad88-712c13db47dd" />

<img width="657" height="122" alt="DUC_05_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/8202f818-8ce9-4de6-ac7c-500880ddf8e3" />

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
3. O sistema autentica o usuário e redireciona para a tela inicial conforme o seu perfil (aluno, recepcionista, instrutor ou gerente).

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- RF01, RF09

### RNF Relacionados
- RNF02, RNF03

### RN Relacionadas
- RN06

<img width="1566" height="571" alt="DA_UC01_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/1c7ee0e1-9d5c-4c90-8b60-78057e010faf" />


## UC02 — Cadastrar Novo Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema FitPass.

### Pré-condições
- Recepcionista logada no sistema.

### Pós-condições
- Aluno cadastrado e apto a vincular um plano.

### Fluxo Principal
1. A recepcionista preenche dados pessoais, contato e endereço.
2. A recepcionista seleciona o plano inicial.
3. O sistema salva os dados e gera o registro de matrícula.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:**  
  O sistema alerta que o aluno já possui registro.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

<img width="823" height="610" alt="DA_UC02_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/f084e8e4-06bd-4e0c-9422-6bdb4a2ee6a9" />


## UC03 — Criar Plano de Academia

### Ator Principal
Gerente

### Objetivo
Configurar novas modalidades de planos (ex: Anual, Musculação).

### Pré-condições
- Usuário logado com perfil de Gerente.

### Pós-condições
- Novo plano disponível para a venda.

### Fluxo Principal
1. O gerente informa nome do plano, valor e periodicidade.
2. O gerente define as atividades inclusas.
3. O sistema armazena a configuração.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

<img width="650" height="446" alt="DA_UC03_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/29b373cc-5bcc-45a4-81c9-f11654c4dce5" />


## UC04 — Registrar Pagamento na Recepção

### Ator Principal
Recepcionista

### Objetivo
Realizar a baixa de mensalidade de forma presencial.

### Pré-condições
- Aluno identificado no sistema.

### Pós-condições
- Status do aluno atualizado para "Regular".

### Fluxo Principal
1. A recepcionista seleciona a parcela em aberto.
2. Informa a forma de pagamento.
3. O sistema confirma a transação e atualiza a situação financeira.

### Fluxos Alternativos
- **A1 — Pagamento Parcial:**  
  O sistema bloqueia a operação.

### RF Relacionados
- RF03, RF04

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN04, RN07

<img width="903" height="556" alt="DA_UC04_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/bd14c632-daa7-4f47-9967-d7573fbcd00f" />


## UC05 — Validar Acesso na Catraca

### Ator Principal
Aluno

### Objetivo
Controlar a entrada física do aluno na unidade.

### Pré-condições
- Aluno aproxima a tag RFID da catraca.

### Pós-condições
- Acesso liberado ou bloqueado.

### Fluxo Principal
1. O sistema lê o RFID.
2. O sistema verifica a regularidade financeira do aluno.
3. O sistema envia comando de liberação para a catraca.

### Fluxos Alternativos
- **A1 — Inadimplência maior que 5 dias:**  
  O sistema nega o acesso e exibe mensagem na tela da catraca.

### RF Relacionados
- RF04, RF05

### RNF Relacionados
- RNF03, RNF06

### RN Relacionadas
- RN01

<img width="695" height="514" alt="DA_UC05_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/5a323d9d-97a2-49cd-a4aa-8c65628b35fa" />


## UC06 — Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em aula com limite de ocupação.

### Pré-condições
- Aluno logado no sistema e com a mensalidade em dia.

### Pós-condições
- Vaga reservada para o aluno.

### Fluxo Principal
1. O aluno consulta o quadro de horários de aulas.
2. O aluno seleciona a aula desejada e clica em "Reservar".
3. O sistema confirma a reserva e abate uma vaga do total disponível.

### Fluxos Alternativos
- **A1 — Aula lotada:**  
  O sistema impede a reserva.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN02

<img width="426" height="600" alt="DA_UC06_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/9f37dbfa-4b87-442e-9939-5eb030e4f588" />


## UC07 — Cancelar Reserva da Aula

### Ator Principal
Aluno

### Objetivo
Cancelar uma vaga previamente agendada.

### Pré-condições
- Reserva ativa no sistema.

### Pós-condições
- Vaga é liberada para outros alunos.
  
### Fluxo Principal
1. O aluno acessa seus agendamentos.
2. Solicita o cancelamento da aula.
3. O sistema valida o tempo limite e confirma a exclusão.

### Fluxos Alternativos
- **A1 — Menos de 1 hora para a aula:**  
  O sistema impede o cancelamento da aula.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN03

<img width="814" height="486" alt="DA_UC07_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/9a87b15a-f817-4c51-8866-3f1457c4a671" />


## UC08 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Lançar dados biométricos e de desempenho do aluno.

### Pré-condições
- Aluno deve estar presente e ativo.

### Pós-condições
- Avaliação salva no histórico do aluno.
  
### Fluxo Principal
1. O instrutor seleciona o aluno.
2. Insere peso, IMC e percentual de gordura.
3. O instrutor anexa fotos ou PDFs se necessário.
4. O sistema salva e notifica o aluno.

### Fluxos Alternativos
- **A1 — Aluno irregular:**  
  O sistema impede o início da avaliação.

### RF Relacionados
- RF08, RF10

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN05, RN06

<img width="747" height="769" alt="DA_UC08_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/be8eb9e6-c43f-4ff2-a302-8663949d6085" />


## UC09 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Confirmar quais alunos agendados compareceram à aula.

### Pré-condições
- Aula iniciada ou finalizada.

### Pós-condições
- Lista de presença atualizada.
  
### Fluxo Principal
1. O instrutor acessa a lista de agendados daquela aula.
2. Marca o check-in dos alunos presentes.
3. O sistema salva o histórico de participação.

### RF Relacionados
- RF07

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

<img width="445" height="488" alt="DA_UC09_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/ee6659d5-08a6-4886-9fa3-a9b8b7cbe594" />


## UC10 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Identificar alunos com pagamentos atrasados.

### Pré-condições
- Usuário logado como Gerente.

### Pós-condições
- Relatório gerado em tela ou PDF.
  
### Fluxo Principal
1. O gerente seleciona o período de referência.
2. O sistema filtra todos os alunos com débitos não quitados.
3. O sistema exibe a lista com valores e dias de atraso em tela.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

<img width="755" height="578" alt="DA_UC10_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/88ce7953-a250-4070-813f-e4e3dbff1a9c" />


## UC11 — Editar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Atualizar dados de contato ou endereço do aluno.

### Pré-condições
- Usuário logado como Recepcionista.

### Pós-condições
- Dados do aluno atualizados no sistema.
  
### Fluxo Principal
1. A recepcionista consulta as informações do aluno.
2. A recepcionista edita os dados do aluno.
3. O sistema salva os dados e atualiza o perfil do aluno.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

<img width="588" height="497" alt="DA_UC11_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/23662f93-1b85-4ca6-8a2c-afab16167af9" />


## UC12 — Desativar Plano Existente

### Ator Principal
Gerente

### Objetivo
Tornar um plano indisponível para as novas vendas.

### Pré-condições
- Usuário logado como Gerente.

### Pós-condições
- Plano dado como indisponível no sistema.
  
### Fluxo Principal
1. O gerente consulta os planos disponíveis.
2. O gerente seleciona o plano e altera para "indisponível".
3. O sistema salva o plano e o torna indisponível para novas vendas.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF02, RNF04

### RN Relacionadas
- RN06

<img width="469" height="512" alt="DA_UC12_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/9da64eed-621d-431e-8f3f-6029e6dfc68e" />


## UC13 — Gerar Boleto para Pagamento Online

### Ator Principal
Aluno

### Objetivo
Obter meio de pagamento via aplicativo.

### Pré-condições
- Usuário logado como Aluno.

### Pós-condições
- Boleto gerado via PDF.
  
### Fluxo Principal
1. O aluno consulta sua área financeira.
2. O aluno seleciona o boleto disponível e o baixa.
3. O sistema gera um PDF do boleto.

### RF Relacionados
- RF03

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN01

<img width="498" height="482" alt="DA_UC13_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/a4324504-31fb-4537-9fa7-64b03c4657b9" />


## UC14 — Consultar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Auditar as entradas e saídas pela catraca.

### Pré-condições
- Usuário logado como Gerente.

### Pós-condições
- Visualização do histórico de acessos.
  
### Fluxo Principal
1. Usuário acessa o sistema com o perfil de Gerente.
2. Acessa a funcionalidade de histórico de acessos.
3. Define os filtros de consulta (período, aluno, etc.).
4. O Sistema consulta os registros da catraca.
5. Exibe o histórico de entradas e saídas.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF01, RNF04

### RN Relacionadas
- RN06

<img width="576" height="661" alt="DA_UC14_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/5a2fb735-5566-4db2-8aaa-927fd74a3423" />


## UC15 — Enviar Notificação de Vencimento

### Ator Principal
Sistema

### Objetivo
Alertar o aluno antes da mensalidade vencer.

### Pré-condições
- Usuário logado como Aluno.

### Pós-condições
- Visualização da notificação de vencimento.
  
### Fluxo Principal
1. O aluno acessa o seu perfil.
2. O aluno seleciona a área de notificações.
3. O sistema gera o alerta antes do vencimento de sua mensalidade.

### RF Relacionados
- RF10

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN06

<img width="522" height="567" alt="DA_UC15_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/9e67126a-497d-49bd-baf6-c19a23287c0d" />


## UC16 — Emitir Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Analisar quais horários e aulas são mais procurados.

### Pré-condições
- Usuário logado como Gerente.

### Pós-condições
- Emissão do relatório de ocupação das aulas.
  
### Fluxo Principal
1. O gerente consulta os horários e as aulas.
2. O gerente seleciona as mais procuradas e registra o relatóprio.
3. O sistema emite esse relatório e armazena.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN06

<img width="525" height="552" alt="DA_UC16_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/5f5925fc-0db1-4067-80bc-833c21073d07" />


## UC17 — Visualizar Grade de Horários

### Ator Principal
Aluno

### Objetivo
Consultar as aulas disponíveis na semana.

### Pré-condições
- Usuário logado como Aluno.

### Pós-condições
- Visualização das aulas disponíveis na semana.
  
### Fluxo Principal
1. O aluno consulta suas aulas da semana.
2. O sistema permite a visualização.

### RF Relacionados
- RF06

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

<img width="491" height="442" alt="DA_UC17_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/319dcaaa-1b00-43ce-bcc3-d1db7e8945e3" />


## UC18 — Recuperar Senha de Acesso

### Ator Principal
Aluno

### Objetivo
Redefinir credenciais de acesso esquecidas.

### Pré-condições
- Usuário logado como Aluno.

### Pós-condições
- Senha alterada e recuperada.
  
### Fluxo Principal
1. O aluno acessa o "esqueceu sua senha?" no login, envia o seu email cadastrado.
2. O aluno acessa o email enviado para redefinir sua senha.
3. O sistema atualiza a nova senha e permite o seu acesso, retornando para tela de login.

### Fluxos Alternativos
- **A1 — Email não cadastrado:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN06

<img width="718" height="847" alt="DA_UC18_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/aea263f5-cb8c-40a7-af57-21441ecb1ec8" />


## UC19 — Anexar Arquivo de Exame Médico

### Ator Principal
Instrutor

### Objetivo
Guardar exames externos no prontuário do aluno.

### Pré-condições
- Usuário logado como Instrutor.

### Pós-condições
- Arquivo de exame anexado no sistema.
  
### Fluxo Principal
1. O instrutor consulta o prontuário do aluno.
2. O instrutor anexa o arquivo de exame médico.
3. O sistema guarda esse arquivo e atualiza o prontuário do aluno.

### Fluxos Alternativos
- **A1 — Arquivo inválido:**  
  O sistema emite mensagem de erro.

### RF Relacionados
- RF08

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN05, RN06

<img width="678" height="662" alt="DA_UC19_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/35bdfb54-22db-4833-8b0e-912dc6a11f94" />


## UC20 — Atualizar Situação Financeira Pós-Pagamento

### Ator Principal
Sistema

### Objetivo
Garantir que o acesso seja liberado imediatamente após a confirmação do pagamento.

### Pré-condições
- Usuário logado como Aluno.

### Pós-condições
- Situação financeira atualizada com sucesso para regular.
  
### Fluxo Principal
1. O aluno realiza o pagamento integral.
2. O sistema consulta se o pagamento é devido e atualiza a situação financeira.

### Fluxos Alternativos
- **A1 — Pagamento inválido e indevido:**  
  O sistema registra inconsistência e aguarda validação.

### RF Relacionados
- RF04, RF05

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN07

<img width="763" height="647" alt="DA_UC20_BeatrizBettio_JoaoSerafim" src="https://github.com/user-attachments/assets/212cf778-34b9-4ac5-b19f-31bd87ba5743" />






