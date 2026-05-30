# Payment Webhooks Failing

> Payment Webhooks Failing

**Severity:** High — billing state drifts from reality  
**Full playbook:** [Payment Webhooks Failing](https://saasplaybooks.dev/playbook/payment-webhooks-failing)

## Symptoms

- Subscriptions not activating after payment.
- Stripe dashboard shows failed webhook deliveries.

## Likely causes

1. Signature verification failing (wrong signing secret).
2. Endpoint returning non-2xx (app error).
3. Reading the raw body after it was parsed/modified.
4. Handler too slow → provider times out.

## Immediate triage

- [ ] Check the provider webhook dashboard for failed attempts + response codes.
- [ ] Read app logs for the webhook route.
- [ ] Confirm the signing secret matches the endpoint.

## Diagnosis

- Replay a failed event from the dashboard.
- Verify you read the *raw* request body for signature checks.
- Time the handler — is it under the provider timeout?

## Resolution

- Fix signature verification / signing secret.
- Return 2xx fast: enqueue heavy work and process async.
- Make handlers idempotent and replay missed events.

## Prevention

- Acknowledge quickly, process in the background.
- Store processed event IDs to dedupe.
- Alert on webhook failure rate.

## Related

- 📖 Full step-by-step playbook: [Payment Webhooks Failing](https://saasplaybooks.dev/playbook/payment-webhooks-failing)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
