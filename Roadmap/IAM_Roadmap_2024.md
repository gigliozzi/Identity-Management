<img src="/Roadmap/assets/YDUQS_Logo.svg" style="width: 200px">

# IAM Roadmap 2024 ![image](/Roadmap/assets/fingerprint-svgrepo-com_sm.svg)

## Índice

- [KPIs](#kpis)
- [Metas](#metas)
- [Admissão](#admissao)
- [Revogação](#revogacao)
- [Afastamento](#afast)
- [Férias](#ferias)
- [Terceiros](#terceiros)
- [Cofre de Senhas](#vault)
- [Contas Privilegiadas](#privileged)
- [Sistema de Informações Acadêmicas (SIA)](#sia)

<a id="kpis">

### KPIs

Terminamos o ano de 2023 com uma taxa de automação consolidada de 75%.

**Admissões 2023 (consolidado)**

| Solicitações          | Requisições           | Automação             |
| --------------------- | --------------------- | --------------------- |
| <center>3202</center> | <center>2317</center> | <center>~75%</center> |

<details><summary><strong>Admissões 2023 (detalhado)</strong></summary>
<br>

|                            | Solicitações         | Requisições          | Automação                   |
| -------------------------- | -------------------- | -------------------- | --------------------------- |
| <center>Janeiro</center>   | <center>185</center> | <center>153</center> | <center>83%                 |
| <center>Fevereiro</center> | <center>310</center> | <center>222</center> | <center>72%                 |
| <center>Março</center>     | <center>359</center> | <center>263</center> | <center>73%                 |
| <center>Abril</center>     | <center>499</center> | <center>346</center> | <center>69%                 |
| <center>Maio</center>      | <center>286</center> | <center>188</center> | <center>66%                 |
| <center>Junho</center>     | <center>240</center> | <center>158</center> | <center>66%                 |
| <center>Julho</center>     | <center>155</center> | <center>88</center>  | <center>57%                 |
| <center>Agosto</center>    | <center>388</center> | <center>314</center> | <center>81%                 |
| <center>Setembro</center>  | <center>366</center> | <center>224</center> | <center>61%                 |
| <center>Outubro</center>   | <center>294</center> | <center>253</center> | <center>86%                 |
| <center>Novembro</center>  | <center>88</center>  | <center>77</center>  | <center>88%                 |
| <center>Dezembro</center>  | <center>32</center>  | <center>31</center>  | <center>97%                 |
|                            | <center>3202         | <center>2327         | <center><strong>75%<strong> |

</details>

**Revogação 2023 (consolidado)**

| Solicitações          | Requisições           | Automação             |
| --------------------- | --------------------- | --------------------- |
| <center>3893</center> | <center>2617</center> | <center>~66%</center> |

<details><summary><strong>Revogação 2023 (detalhado)</strong></summary>
<br>

|                            | Solicitações         | Requisições          | Automação                   |
| -------------------------- | -------------------- | -------------------- | --------------------------- |
| <center>Janeiro</center>   | <center>185</center> | <center>158</center> | <center>85%                 |
| <center>Fevereiro</center> | <center>307</center> | <center>141</center> | <center>46%                 |
| <center>Março</center>     | <center>359</center> | <center>259</center> | <center>72%                 |
| <center>Abril</center>     | <center>348</center> | <center>348 revisar</center> | <center>70%                 |
| <center>Maio</center>      | <center>175</center> | <center>175</center> | <center>100%                 |
| <center>Junho</center>     | <center>205</center> | <center>162</center> | <center>79%                 |
| <center>Julho</center>     | <center>341</center> | <center>278</center>  | <center>82%                 |
| <center>Agosto</center>    | <center>265</center> | <center>208</center> | <center>78%                 |
| <center>Setembro</center>  | <center>259</center> | <center>200</center> | <center>77%                 |
| <center>Outubro</center>   | <center>224</center> | <center>76</center> | <center>30%                 |
| <center>Novembro</center>  | <center>171</center>  | <center>75</center>  | <center>44%                 |
| <center>Dezembro</center>  | <center>792</center>  | <center>546</center>  | <center>69%                 |
|                            | <center>3202         | <center>2327         | <center><strong>75%<strong> |

</details>

<a id="metas">

### Metas

A administração de SI estabeleceu como alvo para 2024 o atingimento da meta 95% para os fluxos de admissão e revogação.

<a id="admissao">

### Admissão

- :heavy_check_mark: Primarização do terceiro (#21413 golive: 16.04.2024 (entregável))
- :heavy_check_mark: Contratação do estagiário (#21418 golive: 16.04.2024 - (entregável))
- ✔️ E-mail de boas-vindas #21475 (entregável)
- 🔄 Geração de novas matrículas #21464 (entregável)
- 🔄 Melhoria dos logs #23012
- 🆕 Criação de funcionários em massa através da interface do IAM

<a id="revogacao">

### Revogação

- 🆕 Remover trecho da US "Fluxo de Desligamento de Matrícula" (após análise cuidadosa sobre os possíveis impactos)
- :arrows_counterclockwise: Melhoria dos logs #21471
- 🆕 Normalização dos fluxos manuais vs fluxos automáticos (permitir que a operação manual via help desk, aplique as mesmas alterações que o fluxo automático, a exemplo do campo FAX)
- 🆕 Aviso prévio (Caso o IAM detectar data de desligamento no futuro, gerar requisição agendada para aplicação futura)

<a id="afast">

### Afastamento

- ✔️ Criação de um mapper de exceções #22135 (entregue em 29/07/2024)

<a id="ferias">

### Férias

- 🔄 Criação de um mapper de exceções #22526
- 🆕 Remover da US a cláusula que impede a leitura de docentes "P" no fluxo
- 🆕 O IAM deve funcionar como base autoritativa: precisar monitorar, alarmar e reverter alterações indevidas no sistemas (AD e outros)

<a id="terceiros">

### Terceiros

- ✔️ Tela de criação individual
- ✔️ Tela criação em massa
- ✔️ Criação da conta no AD
- ✔️ Disparo da credencial por e-mail
- ⏸️ Link para revalidação do acesso (o que acontece com o contrato?)
- ⏸️ Notificação de expiração por fim de atividade #21761
- :exclamation: Tela de renovação de atividade e contrato
- 🆕 Inclusão de e-mail adicional para recebimento de cópia da credencial
- 🆕 Reativação de conta desligada e reativação da identidade
- 🆕 Tela de consulta similar à do SISGDI
- 🆕 Migração do banco de dados do SISGDI (Alarmes do BI)
- 🆕 Trilha no Service Now
- 🆕 Validação de CPF
- 🆕 Customização da mensagem de erro na importação
- 🆕 Tela com visibilidade (30/60/90) dos terceiros que estão prestes a vencer
- 🆕 Tela para renovação múltipla
- 🆕 Inclusão de campos no cadastro do terceiro: `Modelo de contratação, Area contratante, Area de Atuação, Contrato SAP, Ccusto Contrato`

<a id="vault">

### Cofre de Senhas

- Connexão do IAM via cofre

<a id="privileged">

### Contas Privilegiadas

- Desenvolvimento de tela de criação
- Fluxo de aprovação
- Fluxo de revisão

<a id="sia">

### Sistema de Informações Acadêmicas (SIA)
