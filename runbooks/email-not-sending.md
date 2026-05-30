# Email Not Sending

> Email Not Sending

**Severity:** Medium — verification/reset/notifications fail  
**Full playbook:** [Email Not Sending](https://saasplaybooks.dev/playbook/email-not-sending)

## Symptoms

- Signup verification / password reset emails never arrive.
- No SMTP errors, but nothing is delivered.

## Likely causes

1. Wrong SMTP credentials or port blocked.
2. Email sent from a background job that is not running.
3. Provider sandbox / unverified sender domain.
4. Landing in spam (missing SPF/DKIM/DMARC).

## Immediate triage

- [ ] Send a test email via the provider directly.
- [ ] Check spam folder and provider dashboard logs.
- [ ] Confirm the sending code path actually executes.

## Diagnosis

- Verify SMTP host/port/credentials in prod.
- Check the provider activity log for bounces/blocks.
- Confirm SPF/DKIM/DMARC DNS records.

## Resolution

- Fix credentials / use a transactional provider (API over raw SMTP).
- Verify the sender domain and add SPF/DKIM.
- Ensure the job/worker that sends mail is running.

## Prevention

- Use a transactional email provider with deliverability monitoring.
- Alert on bounce/complaint-rate spikes.

## Related

- 📖 Full step-by-step playbook: [Email Not Sending](https://saasplaybooks.dev/playbook/email-not-sending)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
