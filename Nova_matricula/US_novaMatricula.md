# <green> ADMISSÃO DE NOVA MATRÍCULA </green>

> **Nome da requisição**: ‘Requisição de Nova Matrícula’

## INPUT

> Eu, Autoseg, leio a tbl_estacio_pessoal, seleciono as entradas tipo “A” e ignoro tipo “P”.

## CENÁRIO 1: Identidade Ativa / Credencial de rede ativa com mesma matrícula

> Eu, Autoseg, verifico a existência de uma identidade ativa com aquele CPF/MATRICULA; em caso positivo, verifico também se há uma credencial de rede habilitada com aquele CPF/MATRÍCULA, em caso positivo, não crio requisição de criação de nova matrícula e carrego no arquivo de erros a mensagem: `"já existe uma credencial de rede habilitada com a matrícula “069” no domínio “ESTACIO.CORP: jane.sreis@yduqs.com.br"`, conforme demonstração abaixo.

    ADP

| NOME                   |    CARGO     |    MATR    |     ADMISSÃO      | DEMISSÃO |
| ---------------------- | :----------: | :--------: | :---------------: | :------: |
| JANE SILVA REIS        |     PROF     |    055     |    01/08/2019     |          |
| <brown>JANE SILVA REIS | <brown>COORD | <brown>069 | <brown>22/02/2024 |  :bulb:  |

    IDENTIDADE (Header)

| NOME            | CARGO | MATRÍCULA | STATUS |
| --------------- | :---: | :-------: | :----: |
| JANE SILVA REIS | PROF  |    055    | ATIVO  |

    REDE

| LOGIN                   | DOMINIO |       STATUS       | MATRÍCULA | CARGO |
| ----------------------- | :-----: | :----------------: | :-------: | :---: |
| jane.reis@estacio.br    |  YDUQS  | :white_check_mark: |    055    | PROF  |
| jane.sreis@yduqs.com.br | ESTACIO | :white_check_mark: |    069    | COORD |

<br/>
:white_check_mark: enable <br/>
:lock: disable
<br/>
<br/>

## CENÁRIO 2: Identidade Ativa / Credencial de rede inativa com mesma matrícula

Eu, Autoseg, verifico a existência de uma identidade com aquele CPF/MATRICULA e verifico se existe conta de rede inativa com a mesma matrícula vinda do ADP; em caso positivo

Ativar a conta de rede e atualizar o cargo de acordo o ADP

Eu, Autoseg, caso a credencial de rede que possui a matrícula entrante NÃO esteja ativa no AD, atualizo a conta AD com os dados mais recentes obtidos do ADP e reativo a respectiva credencial de rede, disparando a credencial (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP seguido do e-mail para o gestor do colaborador, conforme coluna `‘nome_chefia’` constante no ADP. Eu, Autoseg, atualizo a identidade com os dados provenientes do ADP e atualizo o header da identidade com a matrícula administrativa ‘A’ recém-chegada.

    ADP

| NOME                   |    CARGO     |    MATR    |     ADMISSÃO      | DEMISSÃO |
| ---------------------- | :----------: | :--------: | :---------------: | :------: |
| JANE SILVA REIS        |     PROF     |    055     |    01/08/2019     |          |
| <brown>JANE SILVA REIS | <brown>COORD | <brown>069 | <brown>22/02/2024 |          |

    IDENTIDADE (Header)

| NOME            | CARGO | MATRÍCULA | STATUS |
| --------------- | :---: | :-------: | :----: |
| JANE SILVA REIS | PROF  |    055    | ATIVO  |

    REDE

| LOGIN                   | DOMINIO |       STATUS       | MATRÍCULA | CARGO |
| ----------------------- | :-----: | :----------------: | :-------: | :---: |
| jane.reis@estacio.br    |  YDUQS  | :white_check_mark: |    055    | PROF  |
| jane.sreis@yduqs.com.br | ESTACIO |       :lock:       |    069    | COORD |

<br/>

## CENÁRIO 3: Identidade Ativa / Credencial de Rede inexistente

Eu, Autoseg, caso a nova matrícula não possua correspondente na identidade, crio requisição criação de nova credencial com disparo da credencial (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP seguido do e-mail para o gestor do colaborador, conforme coluna ‘nome_chefia’ constante no ADP. Eu, Autoseg, ativo e atualizo a identidade com os dados provenientes do ADP, colocando a nova matrícula no header da identidade e incluindo a nova matrícula na ‘Matrícula de todos os domínios’.

## CENÁRIO 4: IDENTIDADE INATIVA / CREDENCIAL DE REDE INEXISTENTE

Eu, Autoseg, caso a nova matrícula não possua correspondente na identidade, crio requisição criação de nova credencial com disparo da credencial (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP seguido do e-mail para o gestor do colaborador, conforme coluna ‘nome_chefia’ constante no ADP. Eu, Autoseg, ativo e atualizo a identidade com os dados provenientes do ADP, colocando a nova matrícula no header da identidade, incluindo a nova matrícula na ‘Matrícula de todos os domínios’ e alterando o status da matrícula para ‘ativo’.

## CENÁRIO 5: IDENTIDADE INATIVA / CREDENCIAL DE REDE EXISTENTE

Eu, Autoseg, caso a nova matrícula possua correspondente na identidade, porém inativa, crio requisição criação de atualização de credencial com disparo (conta/senha) para o e-mail pessoal do colaborador proveniente do ADP seguido do e-mail para o gestor do colaborador, conforme coluna ‘nome_chefia’ constante no ADP. Eu, Autoseg, ativo e atualizo a identidade com os dados provenientes do ADP, colocando a nova matrícula no header da identidade e alterando o status da matrícula na ‘Matrícula de todos os domínios’ para ‘ativo’.

<style>
red { color: red }
yellow { color: yellow }
green { color: green; font-weight: 700 }
brown { color: brown; font-weight: 700 }
</style>
