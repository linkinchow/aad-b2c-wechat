# aad-b2c-wechat

## Scenario
This demo shows how to use Azure AD B2C with WeChat as identity provider for signing up/in. It contains two scenarios, web app and mobile app (Android). The user experience of these two scenarios are different. For web app, the user uses WeChat mobile app to scan the WeChat QR code on the web to login. There is no QR code scanning for mobile app, since it is unreasonable for the user to use a second mobile phone to scan the QR code on the first mobile phone. The mobile app will trigger the WeChat app to prompt and asks the user to login.

- Sign-up procedure for web app
  1. Click sign-up button in the web app
  2. Scan the WeChat QR code on the web
  3. Input name and mobile number (here mobile number will be checked with Azure function)
  4. MFA

- Sign-up procedure for mobile app (Android)
  1. Click sign-up button in the mobile app
  2. WeChat mobile app will prompt and ask the user to login
  3. Input name and mobile number (here mobile number will be checked with Azure function)
  4. MFA

## Project structure
There are two separated folders for web app and mobile app.

- web
  - custom-policy: It contains base, extension and sign-up/in custom policies for WeChat identity in web app scenario. You can find the reference below.
    - https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview-custom
    - https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack
  - custom-ui: Azure AD B2C supports customers to customize their own branding and style for sign-up/in pages. This folder contains sample HTML, CSS and images for customization. You can find the reference below.
    - https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-ui-customization-custom
    - https://github.com/azureadquickstarts/b2c-azureblobstorage-client
  - azure-function: With custom policy, you are able to call external Rest API, e.g., Azure function, in your custom policy. In our scenario, we check whether the mobile number is stored in a blob storage and return corresponding result. You can find the reference below.
    - https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-rest-api-validation-custom
  - active-directory-b2c-dotnet-webapp-and-webapi: In terms of web app, it consists of two parts, client app & backend API. The client app will call the protected backend API with access token. You can find the reference below.
    - https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-devquickstarts-web-dotnet-susi
    - https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-devquickstarts-api-dotnet
    - https://github.com/Azure-Samples/active-directory-b2c-dotnet-webapp-and-webapi

- mobile
  - custom-policy: It contains base, extension and sign-up/in custom policies for WeChat identity in mobile app scenario. You can find the reference below.
    - https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview-custom
    - https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack
  - WeixinTest-master: WeChat sample mobile app (Android). You can find the reference below.
    - https://github.com/ansen666/WeixinTest
