# Calendar synchronisation troubleshooting

A practical guide to investigating a calendar that updates in the provider's web interface but fails to update in a connected application.

## 1. Establish the scope

Confirm the affected account and calendar, when the issue started, and the user's time zone. Ask whether older events remain visible, whether new events or edits are affected, and whether other accounts have the same problem.

Check the event in the provider's web interface. Compare the calendar, date range and filters with those selected in the connected application.

## 2. Locate the failing stage

Use the application's connection status, last successful sync and available diagnostics to distinguish between:

- An account or calendar selection problem.
- An authentication or permission failure.
- A synchronisation problem after the connection succeeds.
- An event that is present but hidden by the current view.

Record diagnostic timestamps and request identifiers. Keep passwords, tokens and meeting contents out of support notes.

## 3. Follow the error evidence

For Microsoft Graph integrations, a **401** points to missing or invalid authentication information. Check the application's supported authentication flow and connection state. A **403** calls for checking permissions, consent, licensing or applicable access policies. Use the full error details to narrow the cause. [Microsoft Graph authentication troubleshooting](https://learn.microsoft.com/en-us/graph/resolve-auth-errors)

If the application provides a reconnect flow for the observed error, explain what it changes and follow that documented process. Preserve unsynchronised information before any step that clears local data or removes an account.

## 4. Keep the customer informed

Explain what you have established, what you are checking next and what the customer needs to do.

**Reply template for a confirmed connection warning:**

> Thanks for confirming that the event appears in your web calendar. The connected app is reporting an account-connection warning, so our next step is to check that connection.
>
> Please confirm that the same account and calendar are selected in both places. I'll guide you through the app's reconnect process if needed, then check that a test event comes through and an update synchronises correctly.

## 5. Verify the complete workflow

After any change:

- Confirm the intended account and calendar remain selected.
- Check that the app records a successful sync.
- With the user's agreement, create a non-sensitive test event and check its arrival within the documented sync interval.
- Update the event and check that the change also synchronises.
- Review a previously missing event for recovery or duplication.
- Confirm that the original issue is resolved before closing the request.

## 6. Escalate with a useful record

| Include | Detail |
| --- | --- |
| Impact | Affected account/calendar workflow and extent of disruption |
| Timeline | Last known success, first failure and timestamps with time zones |
| Diagnostics | Sanitised error code, request identifier, app version and connection status |
| Checks | Account/calendar selection, filters, source visibility and supported reconnect steps |
| Current result | What changed, what still fails and whether the test event synchronised |
| Next action | The failing authentication or sync stage that needs engineering investigation |

[Back to portfolio](../README.md)
