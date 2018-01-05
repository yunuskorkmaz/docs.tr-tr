---
title: "Özel belirteç işleyicileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 56fb7fcb162025ec05bc1171cb137d445c4dfee5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-token-handlers"></a>Özel belirteç işleyicileri
Bu konu, belirteç işleyicileri WIF ve belirteçleri işlemek için nasıl kullanılacağını açıklar. Varsayılan olarak WIF desteklenmeyen belirteç türleri için özel belirteç işleyiciler oluşturmak için gerekli nedir konu da kapsar.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>WIF belirteci işleyicileri giriş  
 WIF güvenlik belirteci işleyicileri oluşturma, okuma, yazma ve bağlı olan taraf (RP) uygulama veya bir güvenlik belirteci hizmeti (STS) belirteçleri doğrulamak için kullanır. Belirteç işleyicileri için özel bir belirteç işleyici WIF ardışık düzeninde ekleyin ya da varolan bir belirteci işleyicisi belirteçleri yönetme biçimini özelleştirmek için genişletilebilirlik noktalarıdır. WIF değiştirilen veya tamamen gerektiği gibi işlevlerini değiştirmek için geçersiz kılındı dokuz yerleşik güvenlik belirteci işleyicileri sağlar.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>WIF yerleşik güvenlik belirteci işleyicileri  
 WIF 4.5 soyut taban sınıfından türetilen dokuz güvenlik belirteci işleyicisi sınıflarını içerir <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Özel belirteç işleyici ekleme  
 Basit Web belirteçleri (SWT) ve JSON Web belirteçleri (JWT) gibi bazı belirteç türleri tarafından WIF sağlanan yerleşik belirteci işleyicileri gerekmez. Bu belirteç türleri ve başkalarının yerleşik bir işleyiciye sahip değil, özel belirteç işleyici oluşturmak için aşağıdaki adımları uygulamanız gerekir.  
  
#### <a name="adding-a-custom-token-handler"></a>Özel belirteç işleyici ekleme  
  
1.  Öğesinden türetilen yeni bir sınıf oluşturun <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Aşağıdaki yöntemleri geçersiz kılmak ve kendi uygulamanızı sağlar:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Yeni özel belirteç işleyici içinde bir başvuru ekleyin *Web.config* veya *App.config* içinde dosya  **\<System.IdentityModel >** , bölüm WIF geçerlidir. Örneğin, aşağıdaki yapılandırma biçimlendirme adlı yeni bir belirteç işleyici belirtir **MyCustomTokenHandler** , bulunduğu **CustomToken** ad alanı.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Yerleşik bir belirteç işleyici zaten olan bir belirteç türü işlemek için kendi belirteci işleyicisi sağlıyorsanız eklemek gerektiğini unutmayın bir  **\<kaldırma >** öğesi varsayılan işleyici bırakın ve bunun yerine özel işleyicinizi kullanın. Örneğin, aşağıdaki yapılandırma varsayılan değiştirir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> özel belirteç işleyici ile:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
