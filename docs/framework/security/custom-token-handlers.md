---
title: Özel Belirteç İşleyicileri
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: ccf794b4c229bbc9b40ae7ec2fd649825122cecf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040553"
---
# <a name="custom-token-handlers"></a>Özel Belirteç İşleyicileri
Bu konuda, WıF 'deki belirteç işleyicileri ve belirteçleri işlemek için nasıl kullanıldıkları açıklanmaktadır. Bu konuda, WıF içinde varsayılan olarak desteklenmeyen belirteç türleri için özel belirteç işleyicileri oluşturmak için gerekli olan özellikler de ele alınmaktadır.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>WıF içindeki belirteç Işleyicilerine giriş  
 WıF, bir bağlı olan taraf (RP) uygulaması veya bir güvenlik belirteci hizmeti (STS) için belirteçleri oluşturmak, okumak, yazmak ve doğrulamak üzere güvenlik belirteci işleyicilerini kullanır. Belirteç işleyicileri, WıF ardışık düzeninde özel bir belirteç işleyicisi eklemenize veya var olan bir belirteç işleyicisinin belirteçleri yönetme şeklini özelleştirmenize yönelik genişletilebilirlik noktalarıdır. WıF, işlevselliği gerektiği şekilde değiştirmek için değiştirilebilen ve tamamen geçersiz kılınabilen dokuz yerleşik güvenlik belirteci işleyicisi sağlar.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>WıF 'de yerleşik güvenlik belirteci Işleyicileri  
 WıF 4,5, soyut temel sınıftan türetilen dokuz güvenlik belirteci işleyici sınıfı içerir <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Özel belirteç Işleyicisi ekleme  
 Basit Web belirteçleri (SWT) ve JSON Web belirteçleri (JWT) gibi bazı belirteç türlerinde, WıF tarafından sunulan yerleşik belirteç işleyicileri yoktur. Bu belirteç türleri ve yerleşik işleyicisi olmayan diğerleri için, bir özel belirteç işleyicisi oluşturmak için aşağıdaki adımları gerçekleştirmeniz gerekir.  
  
#### <a name="adding-a-custom-token-handler"></a>Özel belirteç işleyicisi ekleme  
  
1. <xref:System.IdentityModel.Tokens.SecurityTokenHandler>türetilen yeni bir sınıf oluşturun.  
  
2. Aşağıdaki yöntemleri geçersiz kılın ve kendi uygulamanızı sağlayın:  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. *Web. config* veya *app. config* dosyasındaki yeni özel belirteç işleyicisine, WIF için geçerli olan **\<System. IdentityModel >** bölümü içinde bir başvuru ekleyin. Örneğin, aşağıdaki yapılandırma biçimlendirmesi **CustomToken** ad alanında bulunan **MyCustomTokenHandler** adlı yeni bir belirteç işleyicisini belirtir.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Zaten yerleşik bir belirteç işleyicisine sahip olan bir belirteç türünü işlemek için kendi belirteç işleyicinizi sağlıyorsanız, varsayılan işleyiciyi bırakmak ve bunun yerine özel işleyicinizi kullanmak için bir **\<** öğesi eklemeniz gerektiğini unutmayın. Örneğin, aşağıdaki yapılandırma varsayılan <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> özel belirteç işleyicisiyle değiştirir:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789" />  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
