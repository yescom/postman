# yes® Postman Collection
Postman collection for trying out the yes® flows.

This collection covers the yes® identity and signing services. Note that they do
not encompass the first steps of each flow, the call to the yes® account
chooser. Instead, an IDP needs to be configured in the postman environment.

The postman collection contains steps for the authentication and authorization at the Test-IDP. If you use a different IDP, you need to either modify these steps or to run these steps manually in a web browser.

## Configuration

1. Ensure that you **have a client ID registered** in the yes® ecosystem. For the first steps, you can use the Sandbox Demo Client ID published [here](https://yes.com/docs/rp-devguide/2.0/ONBOARDING/index.html#_sandbox_demo_client). 
2. Make sure to **configure the client certificate** that belongs to the client ID for all relevant hosts. For identity, it needs to be configured for the host of the IDP (`testidp.sandbox.yes.com` for the Test-IDP). For signing, configure it for the QTSP as well!
3. Configure the **variables** according to the description below.

## Variables for Identity

You need to set the following variables in your environment:

| Name                | Value                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------- |
| `rp.client_id`      | Your Client ID.                                                                                       |
| `rp.redirect_uri`   | Redirect URI as registered with yes®.                                                                 |
| `stage`             | `sandbox.` for the yes® Sandbox. Leave empty for production.                                          |
| `rp.idp.issuer_uri` | Issuer URI of the IDP to use. Use `https://testidp.sandbox.yes.com/issuer/10000001` for the Test-IDP. |

## Variables for Signing

Additionally to the variables for identity, set the following variables:

| Name                  | Value                                                                                                                                                                                                                                                |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rp.sp.client_id`     | Set to the ID of the QTSP to use. For example, `sp:sandbox.yes.com:85ac6820-8518-4aa1-ba85-de4307175b64` for the Namirial QTSP. See the developer guide for ways to discover other valid values (→ service configuration).                           |
| `rp.signdoc_endpoint` | Set to the signDoc endpoint of the QTSP to use. For example, `https://yesqtsp.test.namirialtsp.com/qtsp-rest-api/signature/signDoc` for the Namirial QTSP. See the developer guide for ways to discover other valid values (→ service configuration) |

