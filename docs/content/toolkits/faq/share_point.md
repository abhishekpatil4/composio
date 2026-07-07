## Why does my SharePoint `/teams/...` site resolve as `/sites/...`?

If a user's SharePoint site URL is under `/teams/<site>` instead of `/sites/<site>`, do not tell them to pass only `<site>` in the SharePoint Subsite field. A bare subsite value is interpreted as `/sites/<site>` by the toolkit.

Re-initiate or reconnect the SharePoint account and set SharePoint Subsite to the full server-relative path, for example `/teams/<site>`. For per-call overrides, pass `site_name: "/teams/<site>"`.

## Why does Microsoft OAuth require a multitenant Azure app?

For user OAuth connections, this toolkit uses Microsoft's `/common` authorization endpoint. If your Microsoft Entra app registration is set to **Single tenant**, OAuth may not complete for users outside that tenant, the connected account can remain `INITIATED`, and Test Connection will fail because the account is not yet `ACTIVE`.

In Microsoft Entra / Azure Portal, open the app registration, go to **Authentication**, and set **Supported account types** to **Accounts in any organizational directory** / **Multitenant**. Save the change, then start a fresh connection.
