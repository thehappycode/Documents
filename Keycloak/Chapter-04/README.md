# Chapter 4: Authenticating Users with OpenID Connect

Trong chương này chúng ta sẽ hiểu sâu về cách Keycloak cho phép bạn authentication user trong applications bằng cách tận dụng ***OpenID Connect (OIDC) standard***.
Trong chương này chúng ta sẽ tìm hiểu các topics chính sau:

- Running the OpenID Connect playground.
- Understanding the Discovery endpoint.
- Authenticating a user.
- Understanding the ID token.
- Invoking the UserInfo endpoint.
- Dealing with users logging out.

## Running the OpendID Connect playground

Runing được application trong thư mục **ch4**

## Understanding the Discovery endpoint

***OIDC Discovery*** rõ ràng quan trọng với cả khả năng tương tác và sử dụng thư viện **OIDC Relying Party**. Ngoài ra bạn có thể phải manual configuration để có app thể authenticate với **OpenID Provider**
Base URL `<base URL>/.well-know/openid-configuration`để biết về *OpendID Provider* của bạn, một *Relying Party* và tìm hiểu nhiều thông tin bạn được cung cấp. Bạn có thể load từ standard endpoint trên và gọi nó là ***OpenId Provider Metadata***

## Authenticating a user

Hầu hết các trường hợp user authenticate với Keycloak đều sữ dụng ***OpenID Connect authorization code flow***

<!--
```
    @startuml TheAuthorizationCodeFlow
    
        header Keycloak-Identity-and-Access-Management-for-Modern-Applications
        title The Authorization Code Flow

        actor "User" as user
        participant "Application" as app
        participant "Keycloak" as keycloak

        autonumber 1
        
        user -> app: Login \nUser click vào nút login trên //Application//.

        app -> app: Generate authentication request \n//Application// sẽ tạo một **authentication request**.
        
        app --_> user: Redirect to Keycloak \n//Authentication request// sẽ chuyển //User// đến form **302 redirect**, \n**user-agent** sẽ hướng dẫn và **redirect** đến **authorization endpoint** được cung cấp bởi //Keycloak//.
        
        user -> keycloak: Send authentication request to Keycloak \n//User-agent// mở //authorization endpoint// với chính xác **query parameters** \nđược tạo bởi //Application// thông qua //authentication request//.
        
        user <-> keycloak: Authenticate user \n//Keycloak// sẽ hiện thị **login page** cho user nhập **username, password** sau đó //submit form//.
        
        keycloak --_> app: Return authorization code \nSau khi //Keycloak// xác thực đúng user, nó sẽ tạo một **authorization code** và trả về cho //Application//.
        
        app <-> keycloak: Send token request to Keycloak \n//Application// bấy giờ có thể **exchange** //authorization code// để lấy **ID token và refresh token**.

        footer %page% of %lastpage%
    @enduml
```
-->
![TheAuthorizationCodeFlow](./assets/TheAuthorizationCodeFlow.svg)