## Why does Microsoft OAuth require a multitenant Azure app?

For user OAuth connections, this toolkit uses Microsoft's `/common` authorization endpoint. If your Microsoft Entra app registration is set to **Single tenant**, OAuth may not complete for users outside that tenant, the connected account can remain `INITIATED`, and Test Connection will fail because the account is not yet `ACTIVE`.

In Microsoft Entra / Azure Portal, open the app registration, go to **Authentication**, and set **Supported account types** to **Accounts in any organizational directory** / **Multitenant**. Save the change, then start a fresh connection.
