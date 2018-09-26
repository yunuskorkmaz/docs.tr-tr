---
title: Özel belirteç işleyicileri
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: c27abb5df7f895a9dec5f7f784f1a3ff0b31edb7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200886"
---
# <a name="custom-token-handlers"></a>Özel belirteç işleyicileri
Bu konu, belirteç işleyicileri WIF ve belirteçleri işlemek için nasıl kullanılacağını açıklar. Özel belirteç işleyicileri için varsayılan olarak WIF desteklenmeyen belirteç türleri oluşturmak gerekli konu da kapsar.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>WIF belirteç işleyicileri giriş  
 Güvenlik belirteci işleyicileri oluşturma, okuma, yazma ve belirteçleri için bir bağlı olan taraf (RP) uygulaması veya bir güvenlik belirteci hizmeti (STS) doğrulamak için WIF kullanır. Belirteç işleyicileri için özel bir belirteci işleyicisi WIF ardışık düzeni içine eklemek veya mevcut bir belirteci işleyicisi belirteçleri yönetme biçimini özelleştirmek için genişletilebilirlik noktalarıdır. WIF, değiştirilen veya tamamen gerektiği gibi işlevlerini değiştirmek için geçersiz kılınan dokuz yerleşik güvenlik belirteci işleyicileri sağlar.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>WIF yerleşik güvenlik belirteci işleyicileri  
 WIF 4.5 soyut temel sınıfından türetilir dokuz güvenlik belirteci işleyici sınıflarını içerir <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Özel bir belirteci işleyicisi ekleme  
 Basit Web belirteçleri (SWT) ve JSON Web belirteçleri (JWT) gibi bazı belirteç türleri tarafından WIF sağlanan yerleşik belirteç işleyicileri yok. Bu belirteç türleri ve yerleşik bir işleyici olmayan diğer kişilerin, özel bir belirteci işleyicisi oluşturmak için aşağıdaki adımları gerçekleştirmek gerekir.  
  
#### <a name="adding-a-custom-token-handler"></a>Özel bir belirteci işleyicisi ekleme  
  
1.  Öğesinden türetilen yeni bir sınıf oluşturun <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Aşağıdaki yöntemleri geçersiz kılın ve kendi uygulamanız sağlayın:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Yeni özel belirteci işleyici içinde bir başvuru ekleyin *Web.config* veya *App.config* içinde dosya  **\<system.identityModel >** , bölüm WIF için geçerlidir. Örneğin, aşağıdaki yapılandırma biçimlendirme adlı yeni bir belirteci işleyicisi belirtir **MyCustomTokenHandler** , bulunduğu **CustomToken** ad alanı.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Yerleşik bir belirteci işleyicisi zaten olan bir belirteç türü işlemek için kendi belirteci işleyicisi sağlıyorsanız eklemeniz gerektiğini unutmayın. bir  **\<kaldırma >** öğesi varsayılan işleyici bırakıp özel işleyicinizi kullanın. Örneğin, aşağıdaki yapılandırmayı varsayılan değiştirir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> özel belirteci işleyicisi ile:  
  
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
