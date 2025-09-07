# CKAD — Questões Killer.sh

> Fonte: prints enviados pelo @peter. Apenas armazenando os enunciados. Quando quiser, preencho as respostas/soluções.

---

## Q1 — Namespaces (ckad5601)

* Listar todos os **Namespaces** do cluster (pode incluir colunas como **STATUS**/ **AGE**).
* Salvar a saída em **/opt/course/1/namespaces** no host **ckad5601**.

### Espaço para comandos/observações

---

## Q2 — Pod httpd e script de status (ckad5601)

* Criar um **Pod** (ns `default`) com **image** `httpd:2.4.41-alpine`.
* Pod **name**: `pod1`.
* Container **name**: `pod1-container`.
* Escrever um **comando kubectl** que imprime o **status** desse Pod e salvar em **/opt/course/2/pod1-status-command.sh** no **ckad5601**.

### Espaço para comandos/observações

---

## Q3 — Job com BusyBox (ckad7326)

* Criar **template** do Job em **/opt/course/3/job.yaml**.
* **image** `busybox:1.31.0` e **command**: `sleep 2 && echo done`.
* **namespace**: `neptune`.
* **completions**: 3; **parallelism**: 2.
* **label** nos Pods: `id=awesome-job`.
* **job name**: `neb-new-job`; **container name**: `neb-new-job-container`.
* Iniciar o Job e checar o **histórico**.

### Espaço para comandos/observações

---

## Q4 — Operações com Helm (ckad7326, ns `mercury`)

1. **Deletar** release `internal-issue-report-apiv1`.
2. **Upgrade** release `internal-issue-report-apiv2` para uma versão **mais nova** do chart `killershell/nginx`.
3. **Instalar** nova release `internal-issue-report-apache` do chart `killershell/apache` com **Deployment.replicas=2** via **values** na instalação.
4. Encontrar release com estado **pending-install** (quebrada) e **deletar**.

### Espaço para comandos/observações

---

## Q5 — Token de ServiceAccount (ckad7326)

* **ServiceAccount**: `neptune-sa-v2` no ns `neptune`.
* Pegar o **token** do **Secret** correspondente e gravar o **conteúdo decodificado (base64)** em **/opt/course/5/token** no **ckad7326**.

### Espaço para comandos/observações

---

## Q6 — Readiness por arquivo (ckad5601)

* Criar **Pod** `pod6` (ns `default`) com **image** `busybox:1.31.0`.
* **readinessProbe**: `exec: ["cat","/tmp/ready"]`, `initialDelaySeconds: 5`, `periodSeconds: 10`.
* Comando do container: `touch /tmp/ready && sleep 1d`.
* Confirmar que o Pod **inicia** e fica **Ready** após criação do arquivo.

### Espaço para comandos/observações

---

## Q7 — Mover Pod entre Namespaces (ckad7326)

* No ns `saturn`, identificar o Pod do e‑commerce **"my-happy-shop"**.
* **Mover** o Pod para o ns `neptune` (pode reiniciar/ recriar, não tem problema).

### Espaço para comandos/observações

---

## Q8 — Rollback de Deployment (ckad7326)

* **Deployment** existente: `api-new-c32` (ns `neptune`).
* A última atualização não entrou no ar; verificar o **histórico** e encontrar uma **revisão estável**.
* Fazer **rollback** para a revisão que funciona e registrar **qual foi o erro** da versão ruim.

### Espaço para comandos/observações

---

## Q9 — Converter Pod em Deployment (ckad9043)

* No ns `pluto`, existe o Pod `holy-api`.
* Converter para **Deployment** `holy-api` com **replicas: 3** e **deletar** o Pod standalone.
* Basear-se no template em **/opt/course/9/holy-api-pod.yaml**.
* Em nível de **container.securityContext**: `allowPrivilegeEscalation: false`, `privileged: false`.
* Salvar o YAML final em **/opt/course/9/holy-api-deployment.yaml** no **ckad9043**.

### Espaço para comandos/observações

---

## Q10 — Service + Teste de acesso (ckad9043)

* Criar **Pod** `project-plt-6cc-api` (image `nginx:1.17.3-alpine`, label `project=plt-6cc-api`) no ns `pluto`.
* Criar **Service** `project-plt-6cc-svc` (ClusterIP) expondo o Pod, com **port** 3333 -> **targetPort** 80 (TCP).
* Usar Pod temporário `nginx:alpine` para fazer **curl** no Service e gravar a **resposta** em **/opt/course/10/service\_test.html** no **ckad9043**.
* Verificar **logs** do Pod `project-plt-6cc-api` e gravar a linha do acesso em **/opt/course/10/service\_test.log** no **ckad9043**.

### Espaço para comandos/observações

---

## Q11 — Build e push com Docker/Podman (ckad9043)

* Arquivos em **/opt/course/11/image**.
* Ajustar **Dockerfile**: `ENV SUN_CIPHER_ID=5b9c1065-e39d-4a43-a04a-e59bcea3e03f`.
* **Docker**: build e push com tag `registry.killer.sh:5000/sun-cipher:v1-docker`.
* **Podman**: build e push com tag `registry.killer.sh:5000/sun-cipher:v1-podman`.
* Rodar container via **podman** em **detached**, name `sun-cipher`, usando a imagem `registry.killer.sh:5000/sun-cipher:v1-podman`.
* Gravar os **logs** do container em **/opt/course/11/logs** no **ckad9043**.

### Espaço para comandos/observações

---

## Q12 — PV/PVC + Deployment httpd (ckad5601)

* **PV** `earth-project-earthflower-pv`: 2Gi, **RWO**, `hostPath: /Volumes/Data`, **sem** storageClassName.
* **PVC** `earth-project-earthflower-pvc` (ns `earth`): 2Gi, **RWO**, **sem** storageClassName, deve **Bound** ao PV.
* **Deployment** `project-earthflower` (ns `earth`): image `httpd:2.4.41-alpine`, monta volume em `/tmp/project-data`.

### Espaço para comandos/observações

---

## Q13 — PVC com StorageClass custom e motivo do Pending (ckad9043)

* Criar **StorageClass** `moon-retain`: `provisioner: moon-retainer`, `reclaimPolicy: Retain`.
* **PVC** `moon-pvc-126` (ns `moon`): 3Gi, **RWO**, usa SC `moon-retain` (ficará **Pending** por enquanto).
* Escrever a **mensagem de evento** do PVC em **/opt/course/13/pvc-126-reason** no **ckad9043**.

### Espaço para comandos/observações

---

## Q14 — Secrets via env e volume no Pod existente (ckad9043)

* Pod existente: `secret-handler` (ns `moon`). YAML base: **/opt/course/14/secret-handler.yaml**.
* Criar **Secret** `secret1` com `user=test` e `pass=pwd`. Disponibilizar como envs `SECRET1_USER` e `SECRET1_PASS` no Pod.
* Criar **Secret** de **/opt/course/14/secret2.yaml** e **montar** no mesmo Pod em `/tmp/secret2`.
* Salvar novo YAML em **/opt/course/14/secret-handler-new\.yaml**. Ambos Secrets apenas em `moon`.

### Espaço para comandos/observações

---

## Q15 — ConfigMap com HTML para nginx (ckad9043)

* Ns `moon`, Deployment `web-moon` já preparado para usar um **ConfigMap**.
* Criar **ConfigMap** `configmap-web-moon-html` com chave `index.html` e conteúdo do arquivo **/opt/course/15/web-moon.html**.
* Testar com Pod temporário `nginx:alpine` usando `curl`.

### Espaço para comandos/observações

---

## Q16 — Sidecar logger com tail -f (ckad7326)

* Deployment `cleaner` (ns `mercury`), container `cleaner-con` escreve em volume `cleaner.log`.
* YAML base: **/opt/course/16/cleaner.yaml**; salvar alterações em **/opt/course/16/cleaner-new\.yaml** e garantir que o Deployment esteja **Running**.
* Adicionar **sidecar** `logger-con` (image `busybox:1.31.0`) montando o mesmo volume e executando `tail -f /path/para/cleaner.log` para stdout.
* Checar `kubectl logs` do sidecar por pistas.

### Espaço para comandos/observações

---

## Q17 — InitContainer que gera index.html (ckad5601)

* YAML do Deployment: **/opt/course/17/test-init-container.yaml** (imagem do app `nginx:1.17.3-alpine`).
* Adicionar **initContainer** `init-con` (image `busybox:1.31.0`) montando o mesmo volume e criando `/mounted/index.html` com conteúdo `check this out!`.
* Testar com Pod temporário `nginx:alpine` via `curl`.

### Espaço para comandos/observações

---

## Q18 — Corrigir Service quebrado (ckad5601)

* Ns `mars`: Service **ClusterIP** `manager-api-svc` deve expor Pods do Deployment `manager-api-deployment`.
* Teste esperado: `curl manager-api-svc.mars:4444` de um Pod `nginx:alpine`.
* Encontrar e corrigir a **misconfiguração** (selector/porta/targetPort/etc.).

### Espaço para comandos/observações

---

## Q19 — Trocar para NodePort e testar nós (ckad5601)

* Ns `jupiter`: Deployment `jupiter-crew-deploy` (apache) e Service `jupiter-crew-svc` (ClusterIP).
* Alterar para **NodePort** acessível em **30100** em todos os nós.
* Testar com `curl <IP-interno-do-nó>:30100` a partir do terminal principal e anotar em quais nós responde e em qual nó roda o Pod.

### Espaço para comandos/observações

---

## Q20 — NetworkPolicy de egress restrito (ckad7326)

* Ns `venus`: Deployments `api` e `frontend`, ambos com Services.
* Criar **NetworkPolicy** `np1` que **permite** apenas conexões **TCP** de egress do `frontend` para o `api` e libera DNS (UDP/TCP **53**).
* Testes: `wget www.google.com` (deve **falhar** exceto DNS) e `wget api:2222` (deve **funcionar**) a partir de um Pod do `frontend`.

### Espaço para comandos/observações

---

## Q21 — Deployment com SA e limits/requests (ckad7326)

* Ns `neptune`.
* Criar **Deployment** `neptune-10ab` (3 réplicas) com imagem `httpd:2.4-alpine`.
* **Container name**: `neptune-pod-10ab`.
* **resources**: `requests.memory=20Mi`, `limits.memory=50Mi`.
* **serviceAccountName**: `neptune-sa-v2`.

### Espaço para comandos/observações

---

## Q22 — Rotular e anotar Pods (ckad9043)

* Ns `sun`.
* Em **todos os Pods** com `type=worker` **ou** `type=runner`, adicionar label `protected=true`.
* Para **todos os Pods** que tiverem `protected=true`, adicionar a **annotation** `protected: "do not delete this pod"`.

### Espaço para comandos/observações
