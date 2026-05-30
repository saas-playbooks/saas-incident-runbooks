# Background Jobs Not Running

> Background Jobs Not Running

**Severity:** Medium — async work stalls  
**Full playbook:** [Background Jobs Not Running](https://saasplaybooks.dev/playbook/background-jobs-not-running)

## Symptoms

- Emails/exports/webhooks never process.
- Queue depth grows without draining.

## Likely causes

1. Worker process not running.
2. Broker (Redis/RabbitMQ) unreachable.
3. Tasks erroring and silently retrying forever.
4. Worker listening on a different queue than the producer.

## Immediate triage

- [ ] Confirm the worker process is alive.
- [ ] Check broker connectivity.
- [ ] Inspect queue length and failed-task count.

## Diagnosis

- Read worker logs for tracebacks.
- Confirm producer and consumer use the same queue name.
- Check the broker for stuck/unacked messages.

## Resolution

- Start/restart the worker under a supervisor.
- Fix broker connectivity/credentials.
- Fix the failing task and clear the dead-letter backlog.

## Prevention

- Run workers under systemd/supervisor with auto-restart.
- Monitor queue depth and failure rate; alert on growth.
- Set sane retry limits with a dead-letter queue.

## Related

- 📖 Full step-by-step playbook: [Background Jobs Not Running](https://saasplaybooks.dev/playbook/background-jobs-not-running)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
