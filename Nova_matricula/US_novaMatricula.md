# <span style="color:green;">ADMISSÃO DE NOVA MATRÍCULA</span>

> **Nome da requisição**: ‘Requisição de Nova Matrícula’

## INPUT

> Eu, Autoseg, leio a tbl_estacio_pessoal, seleciono as entradas tipo “A” e ignoro tipo “P”.

## CENÁRIO 1: Identidade Ativa / Credencial de rede ativa

Eu, Autoseg, verifico a existência de uma identidade ativa com aquele CPF/MATRICULA e a existência de credencial de rede habilitada com aquele CPF/MATRÍCULA, em caso positivo, não crio requisição de nova matrícula e carrego no arquivo de erros a mensagem: `"Já existe uma credencial de rede habilitada com a matrícula “069” no domínio “ESTACIO.CORP: jane.sreis@yduqs.com.br"`, conforme demonstração abaixo.

Identidade: `atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Credencial: `atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Disparo: `não`

> ADP

| NOME            |    CARGO     | TIPO | MATRÍCULA |  ADMISSÃO  | DEMISSÃO |
| --------------- | :----------: | :--: | :-------: | :--------: | :------: |
| JANE SILVA REIS |   PROF AUX   |  P   |    055    | 01/08/2019 |          |
| JANE SILVA REIS | COORDERNADOR |  A   |    069    | 26/02/2024 |

> IDENTIDADE

| NOME            | CARGO | MATRÍCULA |       STATUS       |
| --------------- | :---: | :-------: | :----------------: |
| JANE SILVA REIS | PROF  |    055    | :white_check_mark: |

> REDE

| LOGIN                   | DOMINIO |       STATUS       | MATRÍCULA | CARGO |
| ----------------------- | :-----: | :----------------: | :-------: | :---: |
| jane.reis@estacio.br    |  YDUQS  | :white_check_mark: |    055    | PROF  |
| jane.sreis@yduqs.com.br | ESTACIO | :white_check_mark: |    069    | COORD |

<br/>
:white_check_mark: enable <br/>
:lock: disable
<br/>
<br/>

## CENÁRIO 2: Identidade Ativa / Credencial de rede inativa

Eu, Autoseg, verifico a existência de uma identidade ativa com aquele CPF/MATRICULA; em caso positivo, verifico também se há uma credencial de rede desabilitada com aquele CPF/MATRÍCULA, em caso positivo, ativo a referida conta de rede e disparo (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP e atualizo o `Cargo, Gestor, CPF, Departamento, Centro de Custo` e carrego mensagem no relatório diário de admissão': `"A conta jane.sreis@yduqs.com.br, matrícula "069", foi reativada no domínio ESTACIO.CORP.`

Identidade: `atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Credencial: `ativar e atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Disparo: `sim`

> ADP

| NOME            |    CARGO     | TIPO | MATRÍCULA |  ADMISSÃO  | DEMISSÃO |
| --------------- | :----------: | :--: | :-------: | :--------: | :------: |
| JANE SILVA REIS |   PROF AUX   |  P   |    055    | 01/08/2019 |          |
| JANE SILVA REIS | COORDERNADOR |  A   |    069    | 26/02/2024 |          |

> IDENTIDADE (Header)

| NOME            | CARGO | MATRÍCULA |       STATUS       |
| --------------- | :---: | :-------: | :----------------: |
| JANE SILVA REIS | PROF  |    055    | :white_check_mark: |

> REDE

| LOGIN                   | DOMINIO |       STATUS       | MATRÍCULA | CARGO |
| ----------------------- | :-----: | :----------------: | :-------: | :---: |
| jane.reis@estacio.br    |  YDUQS  | :white_check_mark: |    055    | PROF  |
| jane.sreis@yduqs.com.br | ESTACIO |       :lock:       |    069    | COORD |

<br/>

## CENÁRIO 3: Identidade Ativa / Credencial de rede inexistente

Eu, Autoseg, verifico a existência de uma identidade ativa com aquele CPF/matrícula e inexistência de credencial de rede com os mesmos CPF/matrícula, em caso positvo, crio requisição criação de nova credencial com disparo (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP, seguido do e-mail para o gestor do colaborador, conforme coluna `nome_chefia` da tabela de pessoal. Adicionalmente, atualizo a identidade com os dados mais recentes do ADP, colocando a nova matrícula no header da identidade e incluindo a nova matrícula na `‘Matrícula de todos os domínios’`.

Identidade: `atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Credencial: `criar nova`
Disparo: `sim`

:bulb: **A inclusão deve permitir o bloqueio via fluxo automático de desligamento.**

> ADP

| NOME            |    CARGO     | TIPO | MATR |  ADMISSÃO  | DEMISSÃO |
| --------------- | :----------: | :--: | :--: | :--------: | :------: |
| JANE SILVA REIS |   PROF AUX   |  P   | 055  | 01/08/2019 |          |
| JANE SILVA REIS | COORDERNADOR |  A   | 069  | 26/02/2024 |          |

> IDENTIDADE

| NOME            | CARGO | MATRÍCULA |       STATUS       |
| --------------- | :---: | :-------: | :----------------: |
| JANE SILVA REIS | PROF  |    055    | :white_check_mark: |

> REDE

| LOGIN                | DOMINIO |       STATUS       | MATRÍCULA | CARGO | Obs                 |
| -------------------- | :-----: | :----------------: | :-------: | :---- | ------------------- |
| jane.reis@estacio.br |  YDUQS  | :white_check_mark: |    055    | PROF  | conta pré-existente |

<br/>

## CENÁRIO 4: Identidade inativa / Credencial de rede inexistente

Eu, Autoseg, verifico a existência de uma identidade inativa com aquele CPF/matrícula e inexistência de credencial de rede¹ com os mesmos CPF/matrícula, em caso positvo, crio requisição de nova matrícula com disparo (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP, [seguido do e-mail para o gestor do colaborador]. Adicionalmente, ativo a identidade e atualizo-a com os dados mais recentes do ADP, colocando a nova matrícula no header da identidade e incluindo a nova matrícula na `‘Matrícula de todos os domínios’`. Por fim, eu, Autoseg, carrego no 'Relatório Diário de Admissão' a mensagem: `A conta jane.sreis@yduqs.com.br, matrícula "069", foi criada no domínio ESTACIO.CORP.`

Identidade: `ativar e atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Credencial: `criar nova`
Disparo: `sim`

> ADP

| NOME            |    CARGO     | TIPO | MATR |  ADMISSÃO  | DEMISSÃO |
| --------------- | :----------: | :--: | :--: | :--------: | :------: |
| JANE SILVA REIS |   PROF AUX   |  P   | 055  | 01/08/2019 |          |
| JANE SILVA REIS | COORDERNADOR |  A   | 069  | 26/02/2024 |          |

> IDENTIDADE

| NOME            | CARGO | MATRÍCULA | STATUS |
| --------------- | :---: | :-------: | :----: |
| JANE SILVA REIS | PROF  |    055    | :lock: |

> REDE

| LOGIN                | DOMINIO | STATUS | MATRÍCULA | CARGO | Obs                 |
| -------------------- | :-----: | :----: | :-------: | :---: | ------------------- |
| jane.reis@estacio.br |  YDUQS  | :lock: |    055    | PROF  | conta pré-existente |

<br/>

## CENÁRIO 5: Identidade inativa / Credencial de rede ativa

Eu, Autoseg, verifico a existência de uma identidade inativa com aquele CPF/matrícula e a existência de credencial de rede ativa com os mesmos CPF/matrícula, em caso positvo, não crio crio requisição de nova matrícula. Adicionalmente, ativo a identidade e atualizo-a com os dados mais recentes do ADP (CPF, Cargo, Gestor, Dept. e Centro de Custo) colocando a nova matrícula no header da identidade e incluindo a nova matrícula na `‘Matrícula de todos os domínios’`. Por fim, eu, Autoseg, carrego no 'relatório diário de admissão' a mensagem: `a conta jane.sreis@yduqs.com.br, matrícula "069", foi atualizada no domínio ESTACIO.CORP.`

Identidade: `ativar e atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Credencial: `atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Disparo: `não`

ADP

| NOME            |    CARGO     | TIPO | MATR |  ADMISSÃO  | DEMISSÃO |
| --------------- | :----------: | :--: | :--: | :--------: | :------: |
| JANE SILVA REIS |   PROF AUX   |  P   | 055  | 01/08/2019 |          |
| JANE SILVA REIS | COORDERNADOR |  A   | 069  | 26/02/2024 |          |

> IDENTIDADE

| NOME            | CARGO | MATRÍCULA | STATUS |
| --------------- | :---: | :-------: | :----: |
| JANE SILVA REIS | PROF  |    055    | :lock: |

> REDE

| LOGIN                   | DOMINIO |       STATUS       | MATRÍCULA | CARGO | Obs                 |
| ----------------------- | :-----: | :----------------: | :-------: | :---: | ------------------- |
| jane.reis@estacio.br    |  YDUQS  |       :lock:       |    055    | PROF  | conta pré-existente |
| jane.sreis@yduqs.com.br | ESTACIO | :white_check_mark: |    069    | COORD |

## CENÁRIO 6: Identidade inativa / Credencial de rede inativa

Eu, Autoseg, verifico a existência de uma identidade inativa com aquele CPF/matrícula e a existência de credencial de rede inativa com os mesmos CPF/matrícula, em caso positvo, crio requisição de nova matrícula e disparo e-mail com a credencial reativada (conta/senha) para o endereço cadastrado no campo e-mail da tabela de pessoal. Adicionalmente, ativo a identidade e atualizo-a com os dados mais recentes do ADP (CPF, Cargo, Gestor, Dept. e Centro de Custo) colocando a nova matrícula no header da identidade e incluindo-a na `‘Matrícula de todos os domínios’`. Por fim, eu, Autoseg, carrego no 'relatório diário de admissão' a mensagem: `a conta jane.sreis@yduqs.com.br, matrícula "069", foi reativada no domínio ESTACIO.CORP.`

Identidade: `ativar e atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Credencial: `ativar e atualizar Gestor, Cargo, CPF, Departamento, Centro de Custo`
Disparo: `sim`

ADP

| NOME            |    CARGO     | TIPO | MATR |  ADMISSÃO  | DEMISSÃO |
| --------------- | :----------: | :--: | :--: | :--------: | :------: |
| JANE SILVA REIS |   PROF AUX   |  P   | 055  | 01/08/2019 |          |
| JANE SILVA REIS | COORDERNADOR |  A   | 069  | 26/02/2024 |          |

> IDENTIDADE

| NOME            | CARGO | MATRÍCULA | STATUS |
| --------------- | :---: | :-------: | :----: |
| JANE SILVA REIS | PROF  |    055    | :lock: |

> REDE

| LOGIN                   | DOMINIO | STATUS | MATRÍCULA | CARGO | Obs                 |
| ----------------------- | :-----: | :----: | :-------: | :---: | ------------------- |
| jane.reis@estacio.br    |  YDUQS  | :lock: |    055    | PROF  | conta pré-existente |
| jane.sreis@yduqs.com.br | ESTACIO | :lock: |    069    | COORD |
