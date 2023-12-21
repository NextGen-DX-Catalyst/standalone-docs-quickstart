# Sandbox
Use the Sandbox to quickly develop and test your app
---

## Sandbox overview

The Concentrix Sandbox is a free and fully-featured environment for application development and testing. All functionality of  the Concentrix API is supported in the Sandbox environment. A variety of [test accounts]() and [institutions]() are available to test against, and you can create an unlimited number of test Items. Sandbox API keys can be obtained in the [Concentrix Dashboard]().

## Using Sandbox

The Sandbox can be reached by sending HTTPS POST requests to the endpoints on the sandbox.concentrix.com domain. In order to use the Sandbox with a client library, specify Sandbox as your environment when initializing.

The default username/password combination for all Sandbox institutions is user_good / pass_good.

Most products can be immediately tested in Sandbox with no extra configuration. Some products, such as Payment Initiation (UK and Europe), may require your account be specially enabled. If the product you want to test against is not available in Sandbox, file a request for access ticket via the [Dashboard]().

## Simulating data and events

The Sandbox provides rich test data, as well as the ability to [generate your own test data](). You can also simulate a number of scenarios for testing in Sandbox.

## Webhooks

Concentrix provides a special Sandbox-only endpoint, **[/sandbox/item/fire_webhook]()**, that can be used to trigger `DEFAULT_UPDATE`, `NEW_ACCOUNTS_AVAILABLE`, `AUTH_DATA_UPDATE`, `RECURRING_TRANSACTIONS_UPDATE`, and `SYNC_UPDATES_AVAILABLE` webhooks on demand, allowing you to test that you are receiving webhooks successfully. Webhooks specific to the Income and Transfer products can be sent using the **[/sandbox/transfer/fire_webhook]()** and **[/sandbox/income/fire_webhook]()** endpoints.

All webhooks that would be fired in Production or Development will also fire in Sandbox, except when using the Transfer product.


## Testing with live data using Development

The Concentrix Sandbox is one of three Concentrix environments, with the other two being Development and Production. In order to test with live data, you can configure your application to use the Development environment. Unlike Sandbox, Development uses real production data and real institutions, and unlike Production, it is free to use. You may add up to a maximum of 100 Items in the Development environment. If you run out, you may file a support ticket to request more; you cannot gain Item credits back in Development by deleting them. Items cannot be moved between environments – Sandbox Items cannot be moved to Development, and Items created in Development cannot be moved to Production.

When you first create your Concentrix developer account, it will either have pre-populated access to a very limited number of Items on Development, or no access to Development at all. In either case, you can file a request for Development access via the [Dashboard](); once your request has been approved, you will be able to add up to 100 live Items in the Development environment.

Some products, such as Assets and Identity, require your account to be specially enabled before testing in Development. To enable your account, file a request for access ticket via the [Dashboard](). Also note that some products, such as Identity Verification, Monitor, Transfer, and Virtual Accounts, are not supported in the Development environment.

In order to test US OAuth institutions in Development, you will first need to obtain [Production approval](). Once you have been approved for Production access, you can test these institutions in the Development environment.