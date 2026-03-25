UC01 — Realizar Login
Ator Principal: Usuário (Geral)

Objetivo: Autenticar o usuário no sistema.

Pré-condições: Usuário cadastrado e ativo.

Pós-condições: Acesso liberado conforme o perfil.

Fluxo Principal: 1. Usuário informa e-mail e senha; 2. Sistema valida credenciais; 3. Sistema redireciona para o dashboard.

Fluxos Alternativos: A1: Senha incorreta (Erro); A2: Usuário inativo (Acesso negado).

RF: RF01 | RNF: RNF01 | RN: RN06
<img width="391" height="257" alt="imagem" src="https://github.com/user-attachments/assets/b5086678-7fbe-450d-8314-d4d14b8007b8" />

UC02 — Cadastrar Aluno
Ator Principal: Recepcionista

Objetivo: Registrar um novo aluno na base de dados.

Pré-condições: Recepcionista logada.

Pós-condições: Registro de aluno criado.

Fluxo Principal: 1. Recepcionista insere dados pessoais; 2. Sistema valida CPF; 3. Sistema salva registro.

Fluxos Alternativos: A1: CPF já cadastrado (Sistema alerta erro).

RF: RF02 | RNF: RNF02 | RN: RN06
<img width="364" height="297" alt="imagem" src="https://github.com/user-attachments/assets/4bb6eff9-7621-4a80-91e4-fae4d431571b" />

UC03 — Gerenciar Planos
Ator Principal: Gerente

Objetivo: Criar, editar ou excluir modalidades de planos.

Pré-condições: Gerente logado.

Pós-condições: Plano atualizado no sistema.

Fluxo Principal: 1. Gerente acessa área de planos; 2. Define nome, valor e duração; 3. Salva.

RF: RF03 | RNF: RNF02 | RN: RN06
<img width="244" height="298" alt="imagem" src="https://github.com/user-attachments/assets/e327f13d-9790-46dc-8c44-6da54fa606a6" />


UC04 — Registrar Matrícula
Ator Principal: Recepcionista

Objetivo: Vincular um aluno a um plano específico.

Pré-condições: Aluno cadastrado.

Pós-condições: Vínculo financeiro e contratual criado.

Fluxo Principal: 1. Seleciona aluno; 2. Seleciona plano; 3. Confirma vigência.

RF: RF04 | RNF: RNF02 | RN: RN06
<img width="209" height="303" alt="imagem" src="https://github.com/user-attachments/assets/c80fb6ae-053e-463d-96f2-e7f3876bd5b0" />


UC05 — Processar Pagamento de Mensalidade
Ator Principal: Recepcionista

Objetivo: Baixar débitos de mensalidade.

Pré-condições: Existência de débito aberto.

Pós-condições: Status do aluno atualizado para "Regular".

Fluxo Principal: 1. Recepcionista seleciona a parcela; 2. Registra o pagamento integral; 3. Sistema confirma transação.

Fluxos Alternativos: A1: Pagamento Parcial (Sistema bloqueia conforme RN04).

RF: RF05 | RNF: RNF01 | RN: RN04, RN07
<img width="405" height="257" alt="imagem" src="https://github.com/user-attachments/assets/09f15061-d08b-429f-bd00-96200cc1d7d6" />

UC06 — Validar Acesso na Catraca (RFID)
Ator Principal: Sistema de Catraca (API)

Objetivo: Controlar a entrada física do aluno.

Pré-condições: Leitura do cartão RFID.

Pós-condições: Catraca liberada ou travada.

Fluxo Principal: 1. Aluno aproxima cartão; 2. Sistema verifica adimplência; 3. Catraca libera.

Fluxos Alternativos: A1: Inadimplente > 5 dias (Acesso negado).

RF: RF06 | RNF: RNF03 | RN: RN01
<img width="257" height="257" alt="imagem" src="https://github.com/user-attachments/assets/de14748b-74cf-4586-bdd5-e6ad835b112e" />

UC07 — Agendar Aula Coletiva
Ator Principal: Aluno

Objetivo: Reservar vaga em uma aula.

Pré-condições: Aluno regular e logado.

Pós-condições: Vaga reservada.

Fluxo Principal: 1. Aluno escolhe aula; 2. Sistema verifica disponibilidade; 3. Reserva confirmada.

Fluxos Alternativos: A1: Turma lotada (Sistema impede agendamento).

RF: RF07 | RNF: RNF02 | RN: RN02
<img width="335" height="257" alt="imagem" src="https://github.com/user-attachments/assets/2e1175fe-39a7-4cef-9d89-645d314d82b1" />

UC08 — Cancelar Agendamento de Aula
Ator Principal: Aluno

Objetivo: Desistir da reserva de uma aula.

Pré-condições: Agendamento existente.

Pós-condições: Vaga liberada para outros.

Fluxo Principal: 1. Aluno seleciona "Cancelar"; 2. Sistema verifica horário; 3. Agendamento removido.

Fluxos Alternativos: A1: Menos de 1h para o início (Sistema bloqueia cancelamento).

RF: RF08 | RNF: RNF02 | RN: RN03
<img width="386" height="312" alt="imagem" src="https://github.com/user-attachments/assets/3e994ee6-e574-435b-a664-87dbc62ca5de" />

UC09 — Registrar Presença em Aula
Ator Principal: Instrutor

Objetivo: Confirmar quais alunos compareceram.

Pré-condições: Aula em andamento ou finalizada.

Pós-condições: Lista de presença salva.

Fluxo Principal: 1. Instrutor acessa lista de agendados; 2. Marca "Presente"; 3. Salva.

RF: RF09 | RNF: RNF02 | RN: RN06
<img width="284" height="298" alt="imagem" src="https://github.com/user-attachments/assets/7fcf3768-8c0c-44df-a4f2-c1e15a7c1d47" />

UC10 — Realizar Avaliação Física
Ator Principal: Instrutor

Objetivo: Registrar medidas e anamnese do aluno.

Pré-condições: Aluno estar regular e ativo.

Pós-condições: Laudo gerado no sistema.

Fluxo Principal: 1. Seleciona aluno; 2. Insere dados (peso, dobra, etc); 3. Salva.

Fluxos Alternativos: A1: Aluno inadimplente (Sistema impede a avaliação).

RF: RF10 | RNF: RNF02 | RN: RN05, RN06
<img width="390" height="312" alt="imagem" src="https://github.com/user-attachments/assets/d09369db-1d23-494e-ba68-e08b3ce1bf23" />

UC11 — Visualizar Relatório de Inadimplência
Ator Principal: Gerente

Objetivo: Listar alunos com pagamentos atrasados.

Pré-condições: Acesso de gerente.

Pós-condições: Relatório exibido em tela/PDF.

Fluxo Principal: 1. Gerente define período; 2. Sistema filtra débitos; 3. Exibe lista.

RF: RF11 | RNF: RNF02 | RN: RN06
<img width="197" height="248" alt="imagem" src="https://github.com/user-attachments/assets/34aaadce-ed50-4e33-b767-10ff3b5742c2" />

UC12 — Gerar Relatório de Faturamento
Ator Principal: Gerente

Objetivo: Analisar a saúde financeira mensal.

Pré-condições: Acesso de gerente.

Pós-condições: Totalizadores financeiros exibidos.

RF: RF12 | RNF: RNF02 | RN: RN06
<img width="210" height="248" alt="imagem" src="https://github.com/user-attachments/assets/8786aa99-219f-41f3-87ef-233242f0d6f4" />

UC13 — Consultar Histórico de Treinos
Ator Principal: Aluno

Objetivo: Visualizar evoluções e treinos anteriores.

Pré-condições: Aluno logado.

RF: RF13 | RNF: RNF02
<img width="259" height="298" alt="imagem" src="https://github.com/user-attachments/assets/c324b605-f68f-43a0-a523-8e5b0e58b8ba" />

UC14 — Cadastrar Horários de Aulas
Ator Principal: Gerente

Objetivo: Definir a grade horária da academia.

Pré-condições: Gerente logado.

RF: RF14 | RNF: RNF02 | RN: RN06
<img width="239" height="298" alt="imagem" src="https://github.com/user-attachments/assets/447b0fd7-4e26-49f0-9b79-cb3ea19ea8a0" />

UC15 — Vincular Instrutor a Turma
Ator Principal: Gerente

Objetivo: Designar um profissional para uma aula específica.

RF: RF15 | RNF: RNF02 | RN: RN06
<img width="208" height="248" alt="imagem" src="https://github.com/user-attachments/assets/6ae35cca-ebf7-4d77-a31f-b3359a82cc4b" />

UC16 — Alterar Dados Cadastrais
Ator Principal: Recepcionista

Objetivo: Atualizar endereço ou telefone do aluno.

RF: RF16 | RNF: RNF02
<img width="217" height="248" alt="imagem" src="https://github.com/user-attachments/assets/73a50a50-1e2f-4652-a6ee-9564f10a5412" />

UC17 — Emitir Comprovante de Pagamento
Ator Principal: Recepcionista

Objetivo: Fornecer recibo ao aluno.

RF: RF17 | RNF: RNF02
<img width="222" height="248" alt="imagem" src="https://github.com/user-attachments/assets/8ff462a0-22b5-4888-ad20-7b883eb8f83e" />

UC18 — Consultar Avaliação Física
Ator Principal: Aluno

Objetivo: Visualizar os resultados de seus exames.

RF: RF18 | RNF: RNF02
<img width="194" height="248" alt="imagem" src="https://github.com/user-attachments/assets/13488bac-c452-4848-a2bf-b91153b825bc" />

UC19 — Bloquear Acesso Manualmente
Ator Principal: Gerente

Objetivo: Impedir acesso por motivos administrativos (ex: suspensão).

RF: RF19 | RNF: RNF02 | RN: RN06
<img width="221" height="248" alt="imagem" src="https://github.com/user-attachments/assets/5092871b-b2ee-489d-81e2-4dab8cfd7237" />

UC20 — Configurar Limite de Vagas por Aula
Ator Principal: Gerente

Objetivo: Definir o capacity de cada sala/modalidade.

RF: RF20 | RNF: RNF02 | RN: RN02, RN06
<img width="229" height="248" alt="imagem" src="https://github.com/user-attachments/assets/a3242279-b2af-4e3b-9d9b-56436ed7e865" />

<img width="823" height="1425" alt="imagem" src="https://github.com/user-attachments/assets/82bbb099-8479-44bb-aec9-de8cf3af10d6" />
