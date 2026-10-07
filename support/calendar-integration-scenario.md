# Investigating a calendar integration failure

**Fictional worked scenario.** This is a support writing exercise, not a customer incident or a live Microsoft integration test. The observations below are invented inputs for reasoning; no successful fix is claimed.

## Report and supplied observations

A customer reports: "New meetings appear in Outlook on the web, but they stopped appearing in our scheduling app this morning."

For this exercise, assume:

- One connected work account is affected; another user's connection still updates.
- The missing event appears in the intended calendar in Outlook on the web.
- The scheduling app's latest calendar request returned HTTP 401.
- The app shows a connection warning and has not completed a successful sync since that request.

These observations narrow the investigation to the connection or application path. They do not establish why authentication failed or rule out every wider service issue.

## Investigation plan

1. Confirm the affected account, calendar, approximate start time and time zone. Ask whether older events remain visible and whether all new events are missing.
2. Compare the calendar in the scheduling app with the one that contains the event in Outlook on the web. Confirm the app's date range and filters.
3. Record the failed request's time, error code and available correlation identifier from approved diagnostics. Do not collect passwords, access tokens or meeting contents.
4. Check the app's documented connection state and authentication error handling. A 401 indicates missing or invalid authentication information; it does not by itself prove that a password change or expired token caused the failure. [Microsoft Graph error reference](https://learn.microsoft.com/en-us/graph/errors)
5. If the application provides a documented reconnect flow for this warning, explain the action and its effects before asking the customer to use it. Follow the application's supported process rather than deleting the connection or clearing local calendar data speculatively.
6. If reconnection fails or the next sync still fails, retain the new error details and escalate the specific failure. For Microsoft Graph, an expired or invalid access token is one possible authentication problem; permission errors require a different investigation. [Microsoft authentication troubleshooting](https://learn.microsoft.com/en-us/graph/resolve-auth-errors)

## Example customer reply

> Thanks for checking that the meeting is visible in Outlook. The scheduling app is reporting a problem with its connection to your account. That gives us a useful next step, although we haven't yet confirmed the cause.
>
> Please confirm that the app lists the same account and calendar as Outlook. You don't need to send your password, meeting details or any security codes. I'll then guide you through the app's supported reconnect steps and check that a new test event appears before we consider the issue resolved.

## Verification before closing

- Confirm the expected account and calendar are still selected after any supported reconnect.
- Confirm that a subsequent sync completes successfully, using the app's documented status or diagnostics.
- With the customer's agreement, create a non-sensitive test event and check that it appears within the app's documented sync interval.
- Check an update as well as initial creation, and inspect a previously missing event for recovery or duplication.
- Confirm the customer's original problem is resolved. A sign-in success alone is not proof of calendar synchronisation.

## Escalation note template

**Impact:** Which account/calendar workflow is affected, without event contents.

**Timeline:** Last known success, first observed failure and diagnostic timestamps, with time zones.

**Evidence:** Sanitised error code, request/correlation identifier, app version and connection status.

**Checks completed:** Account/calendar selection, filters, source-calendar visibility and any supported reconnect attempted.

**Result:** What changed, what still fails and whether a test event synchronised.

**Request to engineering:** Investigate the failing authentication or sync stage using the supplied diagnostic identifiers.

## Limits

This exercise demonstrates a written investigation approach. It does not demonstrate hands-on Apple/iCloud experience, operation of a live OAuth integration or a measured support outcome.

[Back to portfolio](../README.md)
