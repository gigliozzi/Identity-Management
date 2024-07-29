![image](fingerprint-svgrepo-com_sm.svg)

# IAM Project Doc

## Índice

- [Servidores](#servers)
- [VPN](#vpn)
- [Fluxos](#flows)
- [Admissão](#admittance)
- [Contas privilegiadas](#adminAccounts)
- [Contas .ADMIN](#adminAccounts)

<a id="servers"></a>

### Servidores (Azure)

```js
PR: 10.200.0.29
QA: 10.200.0.37
```

<a id="flows"></a>

### Fluxos e Horários

| Fluxo         | Horário       |
| ------------- | ------------- |
| Provisionador | a cada 5 min  |
| Load¹ AD EST  | 00:00         |
| Load¹ AD YDC  | 01:00         |
| Load¹ AD EDC  | 02:00         |
| Rev. terceiro | 04:00         |
| Admissão      | 05:00 / 17:00 |
| Férias        | 07:00         |
| Revogação     | 19:00         |
| Update        | 21:00         |
| Afastamento   | 08:00         |

> :eyes: Provisionador: job responsável por aplicar as requisições geradas pelos fluxos automáticos.

> :eyes: Load: rotina de leitura dos ADs para criação de novas identidades

:warning: A rotina de leitura do AD tem gerado backlogs

<br>

### :hammer: Funcionalidades do projeto

<a id="admittance"></a>

#### Admissão

- Primarização do terceiro
- Primarização do estagiário
- Geração de novas matrículas
- Reformulação dos logs
- Criação de funcionários em massa
- Métricas

#### Revogação

- Identificação de erros
- Revogação diária: ocorre todos os dias às 19h
- Revogação retroativa[^1]: ocorrerá todos os dias às 23:00
- Reformulação dos logs
  Here's a simple footnote,[^1] and here's a longer one.[^bignote]

#### Contas Privilegiadas

**Estatísticas do Projeto**

| Admissões 2024 | Solicitações         | Requisições                | Conversão                |
| -------------- | -------------------- | -------------------------- | ------------------------ |
| jan            | <center>48</center>  | <center>46</center>        | <center>96%</center>     |
| fev            | <center>306</center> | <center>252</center>       | <center>82%</center>     |
| mar            | <center>479</center> | <center>397</center>       | <center>83%</center>     |
|                |                      | <center>**Média**</center> | <center>**87%**</center> |

<details>

--<summary>Outras</summary>

### Funcionalidades desejáveis

- Conceder as mesmas opções que fluxo automático para operações manuais realizadas na tela de helpdesk
- Permitir a criação em massa de funcionários quando o IAM não tiver realizado em seu fluxo regular ou por falha sistêmica
-

```ruby
   puts "Hello World"
```

</details>

[^1]:
    A revogação retroativa visa alcançar colaboradores desligados que tiveram a sua demissão lançada de forma retroativa ou devido à uma falha sistêmica na rotina de transporte entre o ADP e o Oracle
    abrange um período de até 60 dias a partir da data atual.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.
