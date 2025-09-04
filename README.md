 Sistema de Clínica e Consultas

 Ideia / Escopo
Um sistema simples para gestão de atendimentos ambulatoriais de uma clínica. Permite cadastrar **pacientes**, **médicos**, **especialidades**, **salas** e **convênios**, bem como **agendar/registrar consultas**. O foco é demonstrar a modelagem de dados com diferentes cardinalidades.

 Entidades (≥5)
- **Paciente** (`paciente`): dados básicos do paciente.
- **Prontuário** (`prontuario`): histórico clínico _1:1_ com paciente.
- **Médico** (`medico`): profissionais da clínica.
- **Especialidade** (`especialidade`): áreas de atuação (ex.: Cardiologia).
- **Médico_Especialidade** (`medico_especialidade`): relação _N:M_ entre médico e especialidade.
- **Consulta** (`consulta`): agendamentos/atendimentos.
- **Sala** (`sala`): sala/box onde a consulta ocorre.
- **Convênio** (`convenio`): operadoras/planos aceitos.

 Relacionamentos e justificativas
- **1:1 – Paciente ↔ Prontuário**  
  Cada paciente possui **um** prontuário exclusivo. Implementado com `prontuario.paciente_id` como **PK e FK** para `paciente.id` (_garante unicidade_).
- **1:N – Médico (1) → Consulta (N)**  
  Um médico realiza muitas consultas; cada consulta tem **um** médico responsável.
- **1:N – Paciente (1) → Consulta (N)**  
  Um paciente pode ter várias consultas; cada consulta pertence a **um** paciente.
- **1:N – Sala (1) → Consulta (N)**  
  Uma sala recebe muitas consultas em horários distintos; cada consulta ocupa **uma** sala.
- **1:N – Convênio (1) → Paciente (N)**  
  Um convênio pode atender muitos pacientes; cada paciente pode ter **um** convênio principal (campo opcional).
- **N:M – Médico ↔ Especialidade**  
  Um médico pode ter várias especialidades e uma especialidade pode ter vários médicos. Resolvido pela tabela associativa `medico_especialidade(medico_id, especialidade_id)` com **PK composta**.

 Arquivos do repositório
- `schema.sql` — DDL do banco (MySQL) com todas as tabelas e relacionamentos.
- `README.md` — este documento.

 Como gerar o arquivo .mwb no MySQL Workbench a partir do schema.sql
1. Abra o **MySQL Workbench** → **File** → **New Model**.  
2. Vá em **File** → **Import** → **Reverse Engineer MySQL Create Script…**.  
3. Selecione o arquivo `schema.sql` (deste repositório) → **Next** até concluir.  
4. O Workbench criará o diagrama EER com as tabelas e FKs.  
5. Salve o modelo: **File → Save Model** e salve como `projeto.mwb`.  

> Dica: se preferir, também é possível **Forward Engineer** o `schema.sql` para um banco local e depois usar **Database → Reverse Engineer** para obter o modelo.

Equipe
- **Aluno 1** – (criador do repositório)  
- **Aluno 2** – (colaborador)
