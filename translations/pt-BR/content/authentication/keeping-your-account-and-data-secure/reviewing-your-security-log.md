---
title: Revisar seus logs de segurança
intro: Você pode revisar o log de segurança da sua conta pessoal para entender melhor as ações que você realizou e ações realizadas por outras pessoas que envolvem você.
miniTocMaxHeadingLevel: 3
redirect_from:
  - /articles/reviewing-your-security-log
  - /github/authenticating-to-github/reviewing-your-security-log
  - /github/authenticating-to-github/keeping-your-account-and-data-secure/reviewing-your-security-log
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Identity
  - Access management
shortTitle: Log de segurança
---

## Acessar o log de segurança

O log de segurança lista todas as ações realizadas nos últimos 90 dias.

{% data reusables.user-settings.access_settings %}
{% ifversion fpt or ghec or ghes > 3.4 or ghae-issue-5658 %}
1. Na seção "Arquivos" da barra lateral, clique em **Registro de segurança de {% octicon "log" aria-label="The log icon" %}**.
{% else %}
1. Na barra lateral de configurações do usuário, clique em **log de segurança**. ![Aba do log de segurança](/assets/images/help/settings/audit-log-tab.png)
{% endif %}

## Pesquisar no seu registro de segurança

{% data reusables.audit_log.audit-log-search %}

### Pesquisar com base na ação

Os eventos listados no seu registro de segurança são acionados por suas ações. As ações são agrupadas nas seguintes categorias:

| Categoria                                                                              | Descrição                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |{% ifversion fpt or ghec %}
| [`cobrança`](#billing-category-actions)                                                | Contém todas as atividades relacionadas às suas informações de cobrança.                                                                                                                                                                                                                                                                                                                                            |
| [`espaços de código`](#codespaces-category-actions)                                    | Contém todas as atividades relacionadas a {% data variables.product.prodname_codespaces %}. Para obter mais informações, consulte "[Sobre o {% data variables.product.prodname_codespaces %}](/github/developing-online-with-codespaces/about-codespaces)".                                                                                                                                                         |
| [`marketplace_agreement_signature`](#marketplace_agreement_signature-category-actions) | Contém todas as atividades relacionadas à assinatura do Contrato de desenvolvedor do {% data variables.product.prodname_marketplace %}.                                                                                                                                                                                                                                                                             |
| [`marketplace_listing`](#marketplace_listing-category-actions)                         | Contém todas as atividades relacionadas aos aplicativos listados no {% data variables.product.prodname_marketplace %}.{% endif %}
| [`oauth_access`](#oauth_access-category-actions)                                       | Contém todas as atividades relacionadas aos [{% data variables.product.prodname_oauth_apps %}](/github/authenticating-to-github/keeping-your-account-and-data-secure/authorizing-oauth-apps) com os quais você se conectou.{% ifversion fpt or ghec %}
| [`payment_method`](#payment_method-category-actions)                                   | Contém todas as atividades relacionadas ao pagamento da sua assinatura do {% data variables.product.prodname_dotcom %}.{% endif %}
| [`profile_picture`](#profile_picture-category-actions)                                 | Contém todas as atividades relacionadas à imagem do seu perfil.                                                                                                                                                                                                                                                                                                                                                     |
| [`project`](#project-category-actions)                                                 | Contém todas as atividades relacionadas aos quadros de projeto.                                                                                                                                                                                                                                                                                                                                                     |
| [`public_key`](#public_key-category-actions)                                           | Contém todas as atividades relacionadas às [chaves SSH públicas](/articles/adding-a-new-ssh-key-to-your-github-account).                                                                                                                                                                                                                                                                                            |
| [`repo`](#repo-category-actions)                                                       | Contém todas as atividades relacionadas aos repositórios que você possui.{% ifversion fpt or ghec %}
| [`sponsors`](#sponsors-category-actions)                                               | Contém todos os eventos relacionados a {% data variables.product.prodname_sponsors %} e botões de patrocinador (consulte "[Sobre {% data variables.product.prodname_sponsors %}](/sponsors/getting-started-with-github-sponsors/about-github-sponsors)" e "[ Exibir um botão de patrocinador no seu repositório](/articles/displaying-a-sponsor-button-in-your-repository)"){% endif %}{% ifversion ghes or ghae %}
| [`equipe`](#team-category-actions)                                                     | Contém todas as atividades relacionadas a equipes das quais você faz parte.{% endif %}{% ifversion not ghae %}
| [`two_factor_authentication`](#two_factor_authentication-category-actions)             | Contem todas as atividades relacionadas a [autenticação de dois fatores](/articles/securing-your-account-with-two-factor-authentication-2fa).{% endif %}
| [`usuário`](#user-category-actions)                                                    | Contém todas as atividades relacionadas à sua conta.                                                                                                                                                                                                                                                                                                                                                                |

{% ifversion fpt or ghec %}

## Exportar o seu log de segurança

{% data reusables.audit_log.export-log %}
{% data reusables.audit_log.exported-log-keys-and-values %}

{% endif %}

## Ações do log de segurança

Uma visão geral de algumas das ações mais comuns que são registradas como eventos no log de segurança.

{% ifversion fpt or ghec %}

### ações de categoria de `cobrança`

| Ação                  | Descrição                                                                                                                                        |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `change_billing_type` | Acionada quando você [altera o modo de pagamento](/articles/adding-or-editing-a-payment-method) do {% data variables.product.prodname_dotcom %}. |
| `change_email`        | Acionada quando você [altera o endereço de e-mail](/articles/changing-your-primary-email-address).                                               |

### ações da categoria `codespaces`

| Ação                                 | Descrição                                                                                                                                                                                                                                 |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `create`                             | Acionada ao [criar codespace](/github/developing-online-with-codespaces/creating-a-codespace).                                                                                                                                            |
| `resume`                             | Acionada ao retomar um codespace suspenso.                                                                                                                                                                                                |
| `delete`                             | Acionada quando você [exclui um codespace](/github/developing-online-with-codespaces/deleting-a-codespace).                                                                                                                               |
| `manage_access_and_security`         | Acionada quando você atualiza [os repositórios aos quais um codespace tem acesso](/github/developing-online-with-codespaces/managing-access-and-security-for-codespaces).                                                                 |
| `trusted_repositories_access_update` | Acionada quando você altera o [acesso e as configurações de segurança da sua conta pessoal para {% data variables.product.prodname_codespaces %}](/github/developing-online-with-codespaces/managing-access-and-security-for-codespaces). |

### ações de categoria de `marketplace_agreement_signature`

| Ação     | Descrição                                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------- |
| `create` | Acionada quando você assina o Contrato de desenvolvedor do {% data variables.product.prodname_marketplace %}. |

### ações de categoria de `marketplace_listing`

| Ação      | Descrição                                                                                                    |
| --------- | ------------------------------------------------------------------------------------------------------------ |
| `aprovar` | Acionada quando sua lista é aprovada para inclusão no {% data variables.product.prodname_marketplace %}.     |
| `create`  | Acionada quando você cria uma lista para seu app no {% data variables.product.prodname_marketplace %}.       |
| `delist`  | Acionada quando sua lista é removida do {% data variables.product.prodname_marketplace %}.                   |
| `redraft` | Triggered when your listing is sent back to draft state.                                                     |
| `reject`  | Acionada quando sua lista não é aprovada para inclusão no {% data variables.product.prodname_marketplace %}. |

{% endif %}

### Ações da categoria `oauth_authorization`

| Ação      | Descrição                                                                                                                                                                                                                                                                                                                                                                                  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `create`  | Acionada quando você [concede acesso a um {% data variables.product.prodname_oauth_app %}](/github/authenticating-to-github/keeping-your-account-and-data-secure/authorizing-oauth-apps).                                                                                                                                                                                                |
| `destroy` | Triggered when you [revoke an {% data variables.product.prodname_oauth_app %}'s access to your account](/articles/reviewing-your-authorized-integrations){% ifversion fpt or ghae or ghes > 3.2 or ghec %} and when [authorizations are revoked or expire](/github/authenticating-to-github/keeping-your-account-and-data-secure/token-expiration-and-revocation).{% else %}.{% endif %}

{% ifversion fpt or ghec %}

### ações de categoria `payment_method`

| Ação     | Descrição                                                                                                  |
| -------- | ---------------------------------------------------------------------------------------------------------- |
| `create` | Acionada quando um novo método de pagamento, como um novo cartão de crédito ou conta PayPal, é adicionado. |
| `update` | Acionada quando um método de pagamento é atualizado.                                                       |

{% endif %}

### ações de categoria `profile_picture`

| Ação     | Descrição                                                                                                 |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `update` | Acionada quando você [configura ou atualiza sua foto do perfil](/articles/setting-your-profile-picture/). |

### ações de categoria `project`

| Ação                     | Descrição                                                                                                                       |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| `access`                 | Acionada quando a visibilidade de um quadro de projeto é alterada.                                                              |
| `create`                 | Acionada quando um quadro de projeto é criado.                                                                                  |
| `rename`                 | Acionada quando um quadro de projeto é renomeado.                                                                               |
| `update`                 | Acionada quando um quadro de projeto é atualizado.                                                                              |
| `delete`                 | Acionada quando um quadro de projeto é excluído.                                                                                |
| `link`                   | Acionada quando um repositório é vinculado a um quadro de projeto.                                                              |
| `unlink`                 | Acionada quando um repositório é desvinculado de um quadro de projeto.                                                          |
| `update_user_permission` | Acionada quando um colaborador externo é adicionado ou removido de um quadro de projeto ou tem seu nível de permissão alterado. |

### ações de categoria `public_key`

| Ação     | Descrição                                                                                                                                                                                                                                                           |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `create` | Acionada quando você [adiciona uma nova chave SSH pública à sua conta em {% ifversion ghae %}{% data variables.product.product_name %}{% else %}{% data variables.product.product_location %}{% endif %}](/articles/adding-a-new-ssh-key-to-your-github-account). |
| `delete` | Acionada quando você [remove uma chave SSH pública na sua conta em {% ifversion ghae %}{% data variables.product.product_name %}{% else %}{% data variables.product.product_location %}{% endif %}](/articles/reviewing-your-ssh-keys).                           |

### ações de categoria `repo`

| Ação                                  | Descrição                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `access`                              | Acionada quando um repositório seu é [alterado de "privado" para "público"](/articles/making-a-private-repository-public) (ou vice-versa).                                                                                                                                                                                                  |
| `add_member`                          | Acionada quando um usuário do {% data variables.product.product_name %} {% ifversion fpt or ghec %}[é convidado para ter acesso de colaboração](/articles/inviting-collaborators-to-a-personal-repository){% else %}[recebe acesso de colaboração](/articles/inviting-collaborators-to-a-personal-repository){% endif %} em um repositório. |
| `add_topic`                           | Acionada quando um proprietário do repositório [adiciona um tópico](/articles/classifying-your-repository-with-topics) a um repositório.                                                                                                                                                                                                    |
| `archived`                            | Acionada quando um proprietário do repositório [arquiva um repositório](/articles/about-archiving-repositories).{% ifversion ghes %}
| `config.disable_anonymous_git_access` | Acionada quando um [acesso de leitura anônimo do Git é desabilitado](/enterprise/{{ currentVersion }}/user/articles/enabling-anonymous-git-read-access-for-a-repository) em um repositório público.                                                                                                                                         |
| `config.enable_anonymous_git_access`  | Acionada quando um [acesso de leitura anônimo do Git é habilitado](/enterprise/{{ currentVersion }}/user/articles/enabling-anonymous-git-read-access-for-a-repository) em um repositório público.                                                                                                                                           |
| `config.lock_anonymous_git_access`    | Acionada quando a [configuração de acesso de leitura anônimo do Git de um repositório é bloqueada](/enterprise/{{ currentVersion }}/admin/guides/user-management/preventing-users-from-changing-anonymous-git-read-access).                                                                                                                 |
| `config.unlock_anonymous_git_access`  | Acionada quando a [configuração de acesso de leitura anônimo do Git de um repositório é desbloqueada](/enterprise/{{ currentVersion }}/admin/guides/user-management/preventing-users-from-changing-anonymous-git-read-access).{% endif %}
| `create`                              | Acionada quando [um repositório é criado](/articles/creating-a-new-repository).                                                                                                                                                                                                                                                             |
| `destroy`                             | Acionada quando [um repositório é excluído](/articles/deleting-a-repository).{% ifversion fpt or ghec %}
| `desabilitar`                         | Acionada quando um repositório é desabilitado (por exemplo, por [fundos insuficientes](/articles/unlocking-a-locked-account)).{% endif %}{% ifversion fpt or ghec %}
| `download_zip`                        | Acionada quando é feito o download de um arquivo ZIP ou TAR de um repositório.                                                                                                                                                                                                                                                              |
| `habilitar`                           | Acionada quando um repositório é habilitado novamente.{% endif %}
| `remove_member`                       | Acionada quando um usuário do {% data variables.product.product_name %} é [removido de um repositório como um colaborador](/articles/removing-a-collaborator-from-a-personal-repository).                                                                                                                                                   |
| `remove_topic`                        | Acionada quando um proprietário do repositório remove um tópico de um repositório.                                                                                                                                                                                                                                                          |
| `rename`                              | Acionada quando [um repositório é renomeado](/articles/renaming-a-repository).                                                                                                                                                                                                                                                              |
| `transferir`                          | Acionada quando [um repositório é transferido](/articles/how-to-transfer-a-repository).                                                                                                                                                                                                                                                     |
| `transfer_start`                      | Acionada quando uma transferência de repositório está prestes a ocorrer.                                                                                                                                                                                                                                                                    |
| `unarchived`                          | Acionada quando um proprietário do repositório desarquiva um repositório.                                                                                                                                                                                                                                                                   |

{% ifversion fpt or ghec %}
### ações de categoria de `patrocinadores`

| Ação                                          | Descrição                                                                                                                                                                                                                                                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `custom_amount_settings_change`               | Acionada quando você habilita ou desabilita os valores personalizados ou quando altera os valores sugeridos (consulte "[Gerenciar as suas camadas de patrocínio](/github/supporting-the-open-source-community-with-github-sponsors/managing-your-sponsorship-tiers)")                                                                |
| `repo_funding_links_file_action`              | Acionada quando você altera o arquivo FUNDING no repositório (consulte "[Exibir botão de patrocinador no repositório](/articles/displaying-a-sponsor-button-in-your-repository)")                                                                                                                                                    |
| `sponsor_sponsorship_cancel`                  | Acionada quando você cancela um patrocínio (consulte "[Fazer downgrade de um patrocínio](/articles/downgrading-a-sponsorship)")                                                                                                                                                                                                      |
| `sponsor_sponsorship_create`                  | Acionada quando você patrocina uma conta (consulte "[Patrocinar um contribuidor de código aberto](/sponsors/sponsoring-open-source-contributors/sponsoring-an-open-source-contributor)")                                                                                                                                             |
| `sponsor_sponsorship_payment_complete`        | Acionada depois que você patrocinar uma conta e seu pagamento ser processado (consulte [Patrocinando um colaborador de código aberto](/sponsors/sponsoring-open-source-contributors/sponsoring-an-open-source-contributor)")                                                                                                         |
| `sponsor_sponsorship_preference_change`       | Acionada quando você altera o recebimento de atualizações de e-mail de um desenvolvedor patrocinado (consulte "[Gerenciar o patrocínio](/sponsors/sponsoring-open-source-contributors/managing-your-sponsorship)")                                                                                                                   |
| `sponsor_sponsorship_tier_change`             | Acionada quando você faz upgrade ou downgrade do patrocínio (consulte "[Atualizar um patrocínio](/articles/upgrading-a-sponsorship)" e "[Fazer downgrade de um patrocínio](/articles/downgrading-a-sponsorship)")                                                                                                                    |
| `sponsored_developer_approve`                 | Acionada quando sua conta do {% data variables.product.prodname_sponsors %} é aprovada (consulte "[Configuração de {% data variables.product.prodname_sponsors %} para sua conta pessoal](/sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-user-account)")                               |
| `sponsored_developer_create`                  | Acionada quando sua conta de {% data variables.product.prodname_sponsors %} é criada (consulte "[Configurar {% data variables.product.prodname_sponsors %} para sua conta pessoal](/sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-user-account)")                                      |
| `sponsored_developer_disable`                 | Acionada quando sua conta {% data variables.product.prodname_sponsors %} está desabilitado                                                                                                                                                                                                                                           |
| `sponsored_developer_redraft`                 | Acionada quando sua conta de {% data variables.product.prodname_sponsors %} é retornada ao estado de rascunho a partir do estado aprovado                                                                                                                                                                                            |
| `sponsored_developer_profile_update`          | Acionada quando você edita seu perfil de desenvolvedor patrocinado (consulte "[Editar informações de perfil para {% data variables.product.prodname_sponsors %}](/sponsors/receiving-sponsorships-through-github-sponsors/editing-your-profile-details-for-github-sponsors)")                                                        |
| `sponsored_developer_request_approval`        | Acionada quando você enviar seu aplicativo para {% data variables.product.prodname_sponsors %} para aprovação (consulte "[Configurar {% data variables.product.prodname_sponsors %} para sua conta pessoal](/sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-user-account)")             |
| `sponsored_developer_tier_description_update` | Acionada quando você altera a descrição de uma camada de patrocínio (consulte "[Gerenciar suas camadas de patrocínio](/sponsors/receiving-sponsorships-through-github-sponsors/managing-your-sponsorship-tiers)")                                                                                                                    |
| `sponsored_developer_update_newsletter_send`  | Acionada quando você envia uma atualização por e-mail aos patrocinadores (consulte "[Entrar em contato com os patrocinadores](/sponsors/receiving-sponsorships-through-github-sponsors/contacting-your-sponsors)")                                                                                                                   |
| `waitlist_invite_sponsored_developer`         | Acionada quando você é convidado a juntar-se a {% data variables.product.prodname_sponsors %} a partir da lista de espera (consulte "[Configurar {% data variables.product.prodname_sponsors %} para sua conta pessoal](/sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-user-account)") |
| `waitlist_join`                               | Acionada quando você se junta à lista de espera para tornar-se um desenvolvedor patrocinado (consulte "[Configurar {% data variables.product.prodname_sponsors %} para sua conta pessoal](/sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-user-account)")                               |
{% endif %}

{% ifversion fpt or ghec %}
### ações de categoria `successor_invitation`

| Ação       | Descrição                                                                                                                                                                                                                                                                  |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `aceitar`  | Acionada quando você aceita um convite de sucessão (consulte "[Manter a continuidade da propriedade dos repositórios da conta pessoal](/github/setting-up-and-managing-your-github-user-account/maintaining-ownership-continuity-of-your-user-accounts-repositories)")     |
| `cancelar` | Acionada quando você cancela um convite de sucessão (consulte "[Manter a continuidade da propriedade dos repositórios da conta pessoal](/github/setting-up-and-managing-your-github-user-account/maintaining-ownership-continuity-of-your-user-accounts-repositories)")    |
| `create`   | Acionada quando você cancela um convite de sucessão (consulte "[Manter a continuidade da propriedade dos repositórios da conta pessoal](/github/setting-up-and-managing-your-github-user-account/maintaining-ownership-continuity-of-your-user-accounts-repositories)")    |
| `recusar`  | Acionado quando você recusa um convite de sucessão (consulte "[Manter a continuidade da propriedade dos repositórios da sua conta pessoal](/github/setting-up-and-managing-your-github-user-account/maintaining-ownership-continuity-of-your-user-accounts-repositories)") |
| `revogar`  | Acionada quando você revoga um convite de sucessão (consulte "[Manter a continuidade da propriedade dos repositórios da conta pessoal](/github/setting-up-and-managing-your-github-user-account/maintaining-ownership-continuity-of-your-user-accounts-repositories)")     |
{% endif %}

{% ifversion ghes or ghae %}

### ações de categoria de `equipe`

| Ação                | Descrição                                                                                                                                                |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `add_member`        | Acionada quando um integrante de uma organização à qual você pertence [adiciona você em uma equipe](/articles/adding-organization-members-to-a-team).    |
| `add_repository`    | Acionada quando uma equipe da qual você faz parte recebe o controle de um repositório.                                                                   |
| `create`            | Acionada quando uma equipe é criada em uma organização à qual você pertence.                                                                             |
| `destroy`           | Acionada quando uma equipe da qual você faz parte é excluída da organização.                                                                             |
| `remove_member`     | Acionada quando um integrante de uma organização é [removido de uma equipe](/articles/removing-organization-members-from-a-team) da qual você faz parte. |
| `remove_repository` | Acionada quando um repositório deixa de ser controlado por uma equipe.                                                                                   |

{% endif %}

{% ifversion not ghae %}
### ações de categoria`two_factor_authentication`

| Ação       | Descrição                                                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `enabled`  | Acionada quando a [autenticação de dois fatores](/articles/securing-your-account-with-two-factor-authentication-2fa) é habilitada. |
| `disabled` | Acionada quando a autenticação de dois fatores é desabilitada.                                                                     |
{% endif %}

### ações de categoria `user`

| Ação                                                                                                                                                                                             | Descrição                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `add_email`                                                                                                                                                                                      | Acionada quando você                                                                                                                                                                                                                      |
| {% ifversion not ghae %}[adiciona um novo endereço de e-mail](/articles/changing-your-primary-email-address){% else %}adiciona um novo endereço de e-mail{% endif %}.{% ifversion fpt or ghec %} |                                                                                                                                                                                                                                           |
| `codespaces_trusted_repo_access_granted`                                                                                                                                                         | Acionada quando você [permite codespaces criados para um repositório acessar outros repositórios pertencentes à sua conta pessoal](/github/developing-online-with-codespaces/managing-access-and-security-for-codespaces).                |
| `codespaces_trusted_repo_access_revoked`                                                                                                                                                         | Acionada quando você [cancela a permissão de codespaces criados para um repositório acessar outros repositórios pertencentes à sua conta pessoal](/github/developing-online-with-codespaces/managing-access-and-security-for-codespaces). |{% endif %}
| `create`                                                                                                                                                                                         | Acionada quando você cria uma nova conta pessoal.{% ifversion not ghae %}
| `change_password`                                                                                                                                                                                | Acionada quando você altera a senha.                                                                                                                                                                                                      |
| `forgot_password`                                                                                                                                                                                | Acionada quando você solicita [a redefinição da senha](/articles/how-can-i-reset-my-password).{% endif %}
| `hide_private_contributions_count`                                                                                                                                                               | Acionada quando você [oculta as contribuições privadas no seu perfil](/articles/publicizing-or-hiding-your-private-contributions-on-your-profile).                                                                                        |
| `login`                                                                                                                                                                                          | Acionada quando você efetua o login em {% data variables.product.product_location %}.{% ifversion ghes or ghae %}


`mandatory_message_viewed`  | Acionada quando você visualiza uma mensagem obrigatória (consulte "[Personalizar mensagens de usuário](/admin/user-management/customizing-user-messages-for-your-enterprise)" para obter detalhes) e ├{% endif %}➲ ├ `falhou_login` | Acionada quando você não efetuou o login com sucesso. | `remove_email` | Acionado quando você remove um endereço de e-mail. | `rename` | Acionado quando você renomeia a sua conta.{% ifversion fpt or ghec %} | `report_content` | Acionado quando você [relata um problema ou pull request ou um comentário em um problema, pull request ou commit](/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam).{% endif %} | `show_private_contributions_count` | Acionado quando você [publica contribuições privadas no seu perfil](/articles/publicizing-or-hiding-your-private-contributions-on-your-profile).{% ifversion not ghae %} | `two_factor_requested` | Acionado quando {% data variables.product.product_name %} solicita [a o seu código de autenticação de dois fatores](/articles/accessing-github-using-two-factor-authentication).{% endif %}

### ações de categoria `user_status`

| Ação      | Descrição                                                                                                                                                                            |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `update`  | Acionada quando você configura ou altera o status no perfil. Para obter mais informações, consulte "[Configurar um status](/articles/personalizing-your-profile/#setting-a-status)". |
| `destroy` | Acionada quando você remove o status no perfil.                                                                                                                                      |
