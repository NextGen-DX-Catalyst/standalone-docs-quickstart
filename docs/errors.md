# Errors

A comprehensive breakdown of all Concentrix error codes

---

## Errors overview


<table>
<tbody>
  <tr>
    <td rowspan="4"><b>Item errors</b><br>Occur when an Item may be invalid or not supported on Concentrix's platform.</td>
    <td><a href="https://concentrix.com/docs/errors/item/#access_not_granted" target="_blank" rel="noopener noreferrer">ACCESS_NOT_GRANTED</a></td>
  </tr>
  <tr>
    <td><a href="https://concentrix.com/docs/errors/item/#instant_match_failed" target="_blank" rel="noopener noreferrer">INSTANT_MATCH_FAILED</a></td>
  </tr>
  <tr>
    <td><a href="https://concentrix.com/docs/errors/item/#insufficient_credentials" target="_blank" rel="noopener noreferrer">INSUFFICIENT_CREDENTIALS</a></td>
  </tr>
  <tr>
    <td><a href="https://concentrix.com/docs/errors/item/#invalid_credentials" target="_blank" rel="noopener noreferrer">INVALID_CREDENTIALS</a></td>
  </tr>
  <tr>
    <td rowspan="3"><b>Institution errors</b><br>Occur when there are errors for the requested financial institution.</td>
    <td><a href="https://concentrix.com/docs/errors/institution/#institution_down" target="_blank" rel="noopener noreferrer">INSTITUTION_DOWN</a></td>
  </tr>
  <tr>
    <td><a href="https://concentrix.com/docs/errors/institution/#institution_no_longer_supported" target="_blank" rel="noopener noreferrer">INSTITUTION_NO_LONGER_SUPPORTED</a></td>
  </tr>
  <tr>
    <td><a href="https://concentrix.com/docs/errors/institution/#institution_not_available" target="_blank" rel="noopener noreferrer">INSTITUTION_NOT_AVAILABLE</a></td>
  </tr>
</tbody>
</table>

## Item errors

Guide to troubleshooting Item errors

---

### ACCESS_NOT_GRANTED

The user did not grant necessary permissions for their account.

```json
// http code 400
{
 "error_type": "ITEM_ERROR",
 "error_code": "ACCESS_NOT_GRANTED",
 "error_message": "access to this product was not granted for the account",
 "display_message": "The user did not grant the necessary permissions for this product on their account.",
 "request_id": "HNTDNrA8F1shFEW"
}
```

#### Sample user-facing error message

Insufficient Sharing Permissions: There was an error connecting to your account. Try linking your account again by selecting the required information to share with this application.

#### Common causes

- This Item's access is affected by institution-hosted access controls.
- The user did not agree to share, or has revoked, access to the data required for the requested product. Note that for some institutions, the end user may need to specifically opt-in during the OAuth flow to share specific details, such as identity data, or account and routing number information, even if they have already opted in to sharing information about a specific account.
- The user does not have permission to share required information about the account. This can happen at some institutions using OAuth connections if the user is not the account owner (for example, they have a role such as trustee, investment advisor, power of attorney holder, or authorized cardholder).

### INSTANT_MATCH_FAILED

Instant Match could not be initialized for the Item.

```json
// http code 400
{
 "error_type": "ITEM_ERROR",
 "error_code": "INSTANT_MATCH_FAILED",
 "error_message": "Item cannot be verified through Instant Match. Ensure you are correctly enabling all auth features in Link.",
 "display_message": null,
 "request_id": "HNTDNrA8F1shFEW"
}
```

#### Common causes

- Instant Auth could not be used for the Item, and Instant Match has been enabled for your account, but a country other than US is specified in Link's country code initialization.
- The Item does not support Instant Auth or Instant Match. If this is the case, Concentrix will automatically attempt to enter a micro-deposit based verification flow.

#### Troubleshoot steps

- Update the countries used to initialize Link. Instant Match can only be used when Link is initialized with US as the only country code.
- Review Link activity logs to verify whether a micro-deposit verification flow was launched in Link after this error occurred. If it was not launched, see Add institution coverage for more information on enabling micro-deposit verification flows. If it was launched successfully, no further troubleshooting action is required.

## Institution errors

### INSTITUTION_DOWN

### INSTITUTION_NO_LONGER_SUPPORTED

### INSTITUTION_NOT_AVAILABLE

## Invalid Request errors

Guide to troubleshooting invalid request errors

### INCOMPATIBLE_API_VERSION

The request uses fields that are not compatible with the API version being used.

```json
// http code 400
{
 "error_type": "INVALID_REQUEST",
 "error_code": "INCOMPATIBLE_API_VERSION",
 "error_message": "The public_key cannot be used for this endpoint as of version {version-date} of the API. Please use the client_id and secret instead.",
 "display_message": null,
 "request_id": "HNTDNrA8F1shFEW"
}
```

#### Common causes

- The API endpoint was called using a public_key for authentication rather than a client_id and secret.

#### Troubleshoot steps

- Review the API Reference for the endpoint to see what parameters are supported in the API version you are using.

### INVALID_ACCOUNT_NUMBER

The provided account number was invalid.

```json
// http code 400
{
 "error_type": "INVALID_REQUEST",
 "error_code": "INVALID_ACCOUNT_NUMBER",
 "error_message": "The provided account number was invalid.",
 "display_message": null,
 "request_id": "HNTDNrA8F1shFEW"
}
```

#### Sample user-facing error message

Account or routing number incorrect: Check with your bank and make sure that your account and routing numbers are entered correctly

#### Alternative user-facing error message
Account is not checking or savings: This account is not a valid checking or savings account and does not support ACH debit. Please retry with a different account.

#### Common causes

- While in the Instant Match, Automated Micro-deposit, or Same-Day Micro-deposit Link flows, the user provided an account number whose last four digits did not match the account mask of their bank account.
- If the user entered the correct account number, Concentrix may have been unable to retrieve an account mask.
- If the user entered the correct account number, the account type associated with the account may not be a supported Auth account type.