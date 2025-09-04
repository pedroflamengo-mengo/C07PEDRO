Sistema de Clínica e Consultas
O que é

Um sisteminha de exemplo para organizar atendimentos de uma clínica.
Dá pra cadastrar pacientes, médicos, especialidades, salas e convênios, e marcar consultas.
A ideia é mostrar como as coisas se relacionam no banco de dados.

O que tem no sistema (tabelas)

Paciente (paciente) – dados básicos do paciente.

Prontuário (prontuario) – histórico do paciente.

Médico (medico) – profissionais que atendem.

Especialidade (especialidade) – área do médico (ex.: cardiologia).

Médico_Especialidade (medico_especialidade) – liga médico com especialidade.

Consulta (consulta) – o agendamento/atendimento em si.

Sala (sala) – onde a consulta acontece.

Convênio (convenio) – plano de saúde (quando tiver).

Como as coisas se ligam (relacionamentos)

1:1 – Paciente ↔ Prontuário
Cada paciente tem um prontuário, e cada prontuário é de um paciente só.

1:N – Médico → Consulta
Um médico faz várias consultas; cada consulta tem um médico responsável.

1:N – Paciente → Consulta
Um paciente pode ter várias consultas; cada consulta é de um paciente.

1:N – Sala → Consulta
Uma sala recebe várias consultas (em horários diferentes); cada consulta usa uma sala.

1:N – Convênio → Paciente
Um convênio pode ter vários pacientes; o paciente pode ter zero ou um convênio principal.

N:M – Médico ↔ Especialidade
Um médico pode ter várias especialidades e cada especialidade pode ter vários médicos.
Guardamos essa ligação na tabela medico_especialidade.

O que vai no repositório

README.md (este arquivo)

projeto.mwb (arquivo do MySQL Workbench com o diagrama)

Equipe

Aluno 1 – Pedro Tiburcio Araujo de Andrade MATRICULA 2035

Aluno 2 – Joao Marcelo Dias Pereira de Carvalho MATRICULA 357
