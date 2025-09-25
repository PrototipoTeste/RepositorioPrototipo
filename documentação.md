# Checklist de Implementação - Change Velocity + GitHub

**Personal Access Token (PAT) PDI**: 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

---

## Conexão com GitHub
- [x] Criar uma conexão ao GitHub (Dev, Devmain, Stag e Prod)  
- [x] Validar autenticação via **Personal Access Token (PAT)**  
- [ ] Confirmar escopo de permissões necessárias:   
  - **repo** (full control sobre repositórios privados/públicos)  
  - **admin:repo_hook** (criação e gerenciamento de WebHooks)  
  - **read:org** (ler dados da organização)  
- [ ] Validar permissões aplicadas nos WebHooks de cada repositório  

---

## Configuração de WebHooks
> Se criar manualmente, é necessário 1 webhook **para cada tipo de ferramenta (tool)** integrada: `code`, `plan`, `orchestration`.

- [x] Criar WebHook manualmente no GitHub para cada tool necessária:  
  - **Payload URL**:  
    - Code → `https://{instancia}.service-now.com/api/sn_devops/v2/devops/tool/code?toolId={TOOL_ID}`  
    - Plan → `https://{instancia}.service-now.com/api/sn_devops/v2/devops/tool/plan?toolId={TOOL_ID}`  
    - Orchestration → `https://{instancia}.service-now.com/api/sn_devops/v2/devops/tool/orchestration?toolId={TOOL_ID}`  
  - **Content type**: `application/json`  
  - **Secret (Token)**: `JAAszw5sWqHS8EBS4X6eGMeurQCrLVAD`  

- [x] Configurar WebHook automático no momento da criação da conexão  
- [ ] Validar funcionamento do GitHub Actions **GitHub → Settings → Actions**  

---

## Recuperação de Dados do Repositório
- [ ] Recuperar **Pull Requests** existentes  
- [ ] Recuperar **Commits** existentes  
- [ ] Recuperar **Branches** existentes  
- [ ] Recuperar **Merges** existentes  
- [ ] Recuperar **Reverts** existentes  
- [ ] Recuperar **Pipelines** existentes  

---

## Artefatos Importantes

- [DevOps | Scripted REST API | ServiceNow](https://dev281007.service-now.com/now/nav/ui/classic/params/target/sys_ws_definition.do%3Fsys_id%3D9e08f5670f023300d08d9a0799767e16%26sysparm_record_target%3Dsys_ws_definition%26sysparm_record_row%3D1%26sysparm_record_rows%3D2%26sysparm_record_list%3DnameCONTAINSdevops%255EORDERBYname)  

- [Digital Product Release API | Scripted REST API | ServiceNow](https://dev281007.service-now.com/now/nav/ui/classic/params/target/sys_ws_definition.do%3Fsys_id%3D4a52ba3387c12910a6c397d73cbb3512%26sysparm_record_target%3Dsys_ws_definition%26sysparm_record_row%3D1%26sysparm_record_rows%3D1%26sysparm_record_list%3DnameCONTAINSgit%255EORDERBYname)  

---

**Objetivo final**: Garantir que a integração GitHub ↔ ServiceNow Change Velocity funcione ponta a ponta, desde eventos no repositório até métricas visíveis no dashboard.
