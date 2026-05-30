# 🔴 SaaS Incident Runbooks

> Ready-to-use, copy-pasteable runbooks for the incidents every SaaS hits in production. Each one is a fast path from **symptom → triage → resolution → prevention**, with a link to the full playbook.

When something breaks at 2am, you want a checklist, not a blog post. Drop these into your ops repo and make them yours.

## Runbooks

| Incident | Severity | Runbook |
|---|---|---|
| 502 Bad Gateway | High | [runbook](./runbooks/502-bad-gateway-fix.md) |
| App Crashes on Deployment | High | [runbook](./runbooks/app-crashes-on-deployment.md) |
| Static Files Not Loading | Medium | [runbook](./runbooks/static-files-not-loading.md) |
| Media Uploads Not Working | Medium | [runbook](./runbooks/media-uploads-not-working.md) |
| Database Connection Errors | High | [runbook](./runbooks/database-connection-errors.md) |
| Background Jobs Not Running | Medium | [runbook](./runbooks/background-jobs-not-running.md) |
| Email Not Sending | Medium | [runbook](./runbooks/email-not-sending.md) |
| Payment Webhooks Failing | High | [runbook](./runbooks/payment-webhooks-failing.md) |
| Session / Auth Issues in Production | High | [runbook](./runbooks/session-auth-issues.md) |
| High CPU / Memory Usage | Medium/High | [runbook](./runbooks/high-cpu-memory-usage.md) |

## How these are structured

Every runbook follows the same shape so you can move fast under pressure:

1. **Symptoms** — how you know this is the one
2. **Likely causes** — ranked by how often they're the culprit
3. **Immediate triage** — the first 3 things to check
4. **Diagnosis** — commands to pinpoint it
5. **Resolution** — how to fix it
6. **Prevention** — stop it recurring

See [`TEMPLATE.md`](./TEMPLATE.md) to add your own.

## Related

Working an incident? Start from the [Incident Response Playbook](https://saasplaybooks.dev/playbook/incident-response-playbook).

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
