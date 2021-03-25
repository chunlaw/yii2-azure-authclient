<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://avatars0.githubusercontent.com/u/993323" height="100px">
    </a>
    <h1 align="center">Azure AuthClient Extension for Yii 2</h1>
    <br>
</p>

This extension adds [Azure](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow) [OAuth2](http://oauth.net/2/) client for the extensions [Yii 2 AuthClient](https://github.com/yiisoft/yii2-authclient). This extension is able to handle both work/organization and personal accounts resided in Azure, while solely [Yii 2 AuthClient](https://github.com/yiisoft/yii2-authclient) is only able to handle personal accounts.

For license information check the [LICENSE](https://github.com/chunlaw/yii2-authclient/blob/master/LICENSE.md)-file.

Documentation is at [docs/guide/README.md](https://github.com/chunlaw/yii2-authclient/blob/master/docs/guide/README.md).

[![Latest Stable Version](https://poser.pugx.org/chunlaw/yii2-azure-authclient/v/stable.png)](https://packagist.org/packages/chunlaw/yii2-azure-authclient)
[![Total Downloads](https://poser.pugx.org/chunlaw/yii2-azure-authclient/downloads.png)](https://packagist.org/packages/yiisoft/yii2-azure-authclient)
[![Build Status](https://github.com/chunlaw/yii2-azure-authclient/actions/workflows/php.yml/badge.svg)](https://github.com/chunlaw/yii2-azure-authclient/actions)

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist chunlaw/yii2-azure-authclient
```

or add

```json
"chunlaw/yii2-azure-authclient": "~2.2.0"
```

to the `require` section of your composer.json.

Configuring application
-----------------------

After extension is installed, you need to setup auth client collection application component:

```
return [
    'components' => [
        'authClientCollection' => [
            'class' => 'yii\authclient\Collection',
            'clients' => array_filter([
                'azure' => [
                    'class' => 'chunlaw\authclient\Azure',
                    'returnUrl' => '<azure_return_url>',
                    'clientId' => '<azure_client_id>',
                    'clientSecret' => '<azure_client_secret>'
                ],
                'google' => [
                    'class' => 'yii\authclient\clients\Google',
                    'returnUrl' => '<google_return_url>',
                    'clientId' => '<google_client_id>',
                    'clientSecret' => '<google_client_secret>',
                ],
				// etc.
            ]),
        ],
    ],
    // ...
];
```

Other usage remains the same as [AuthClient Extension for Yii 2](https://www.yiiframework.com/extension/yiisoft/yii2-authclient/doc/guide/2.0/en/quick-start).
