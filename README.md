# 4Health2.0

O objetivo desse software é registrar consultas médicas geral, especificas e vacinação, facilitando para a população realizar a manutenção da sua saúde.

## Como Usar

Autenticação e Cadastro de Usuário

A autenticação deve ser realizada utilizando um arquivo JSON que contenha as credenciais de acesso, incluindo usuário e senha. É importante ressaltar que o acesso pode ser realizado por usuários comuns ou por um administrador.

Para operações de cadastro ou atualização de dados, o conteúdo do arquivo JSON deve incluir todas as informações obrigatórias listadas abaixo:

- Paciente
> CPF, RG, Nome, Nascimento, Sexo, Senha, Situação, Problema, PCD e Alergia

- Médico
> CPF, RG, Nome, Nascimento, Sexo, Email, Senha, Situação, CRM, Especialidade e Horário

- Medicamento
> Tipo, Nome, Finalidade, Medida, Dosagem, Aplicação, Quantidade e Situação

- Consulta
> Tipo, Finalidade, Situação, Detalhes, id_paciente, id_medico, data_marcada, data_registrada, id_medicamento

## Endpoint e Rotas

Puxa todos que estão ativos:
- GET	{local}/pacientes/
- GET	{local}/médicos/
- GET	{local}/medicamentos/
- GET	{local}/consultas/

Puxa um elemento específico:
- GET	{local}/paciente/:id
- GET	{local}/medico/:id
- GET	{local}/medicamento/:id
- GET	{local}/consulta/:id

Inserir:
- POST	{local}/paciente/cadastrar/
- POST	{local}/medico/cadastrar/
- POST	{local}/medicamento /inserir/
- POST	{local}/consulta/inserir/

Atualizar:
- PATCH	{local}/paciente/atualizar/:id
- PATCH	{local}/medico/atualizar/:id
- PATCH	{local}/medicamento/atualizar/:id
- PATCH	{local}/consulta/atualizar/:id

Apagar:
- DELETE	{local}/paciente/apagar/:id
- DELETE	{local}/medico/apagar/:id
- DELETE	{local}/medicamento/apagar/:id
- DELETE	{local}/consulta/apagar/:id

Funções específicas:
- GET	{local}/consultas/data/:data =>
essa requisição puxa todas as consultas de um dia específico.

- GET	{local}/consultas/paciente/:id =>
essa requisição puxa todas as consultas de um paciente específico.

- GET	{local}/consultas/medico/:id =>
essa requisição puxa todas as consultas de um médico específico.

- PATCH	{local}/paciente/inativar/:id =>
essa requisição inativa um paciente específico.

- PATCH	{local}/medico/inativar/:id =>
essa requisição inativa um médico específico.

- PATCH	{local}/paciente/reativar/:id =>
essa requisição reativa um paciente específico.

- PATCH	{local}/medico/reativar/:id =>
essa requisição reativa um médico específico


## Exemplos Práticos

Exemplo de requisições corretas:
- POST	{local}/consulta/inserir/
~~~javascript
{
      “access”: {
            “user”: ”usuario”,
            “pass”: ”1234”
      },
      “info”: {
           “tipo”: ”ortopedia”,
           “finalidade”: ”verificação geral”,
           “id_paciente”: 1,
           “id_medico”: 1,
           “data_marcada”: ”2023-11-12”,
           “data_megistrada”: ”2023-11-10”,
           “detalhes”: ”paciente com dor nas costas”,
           “id_medicamento”: 1
      }
}
~~~
- POST	{local}/paciente/cadastrar/
~~~javascript
{
	"info":{
		"cpf": 11111111111,
		"rg": 111111111,
		"nome": "josé",
		"nascimento": "1980-12-01",
		"sexo": "m",
		"senha": "1234",
		"problema": "nenhum",
		"pcd": "nenhum",
		"alergia": "nenhum"
	}
}
~~~
- POST	{local}/medico/cadastrar/
~~~javascript
{
	"info":{
		"cpf": 19432749389,
		"rg": 123456798,
		"nome": "vacinação",
		"email":"josé@email",
		"nascimento": "1980-01-01",
		"sexo": "m",
		"senha": "1980",
		"crm": 123456,
		"especialidade": "terapeuta",
		"horario": "manhã"
	}
}
~~~
- POST	{local}/medicamento/cadastrar/
~~~javascript
{
		"access":{
			"user":"admin",
			"pass":"admin"
	},
		"info":{
			"tipo": "comprimido",
			"nome": "captopril",
			"finalidade": "comprimido",
			"medida": "mg",
			"dosagem": 25,
			"aplicacao": "oral",
			"quantidade": 33
	}
}
~~~

## Gestão de Erros

> Ainda sem um bom tratamento de erro verdadeiro

A API verifica se o paciente possui o CPF, RG, Nome e Senha vazios.
A API verifica se o médico possui o CPF, RG, Nome, Senha, CRM e Especialidade vazios.

## Exemplos de Respostas

Exemplos de respostas em JSON.
~~~javascript
{
	"status": "successo ao cadastrar"
}
~~~
~~~javascript
{
	"status": "sucesso ao atualizar"
}
~~~
~~~javascript
{
	"status": "sucesso ao apagar"
}
~~~

## Licença

MIT

## Mais informações

- [Documentação da API](./documents/documentação.docx)
- [Requisitos](./documents/Requisitos.docx)
