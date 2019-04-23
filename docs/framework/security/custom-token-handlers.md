---
title: Özel Belirteç İşleyicileri
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: b6b84271fc450a325270bad5f9e0355fe81a8a5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975682"
---
# <a name="custom-token-handlers"></a><span data-ttu-id="d11bd-102">Özel Belirteç İşleyicileri</span><span class="sxs-lookup"><span data-stu-id="d11bd-102">Custom Token Handlers</span></span>
<span data-ttu-id="d11bd-103">Bu konu, belirteç işleyicileri WIF ve belirteçleri işlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d11bd-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="d11bd-104">Özel belirteç işleyicileri için varsayılan olarak WIF desteklenmeyen belirteç türleri oluşturmak gerekli konu da kapsar.</span><span class="sxs-lookup"><span data-stu-id="d11bd-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="d11bd-105">WIF belirteç işleyicileri giriş</span><span class="sxs-lookup"><span data-stu-id="d11bd-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="d11bd-106">Güvenlik belirteci işleyicileri oluşturma, okuma, yazma ve belirteçleri için bir bağlı olan taraf (RP) uygulaması veya bir güvenlik belirteci hizmeti (STS) doğrulamak için WIF kullanır.</span><span class="sxs-lookup"><span data-stu-id="d11bd-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="d11bd-107">Belirteç işleyicileri için özel bir belirteci işleyicisi WIF ardışık düzeni içine eklemek veya mevcut bir belirteci işleyicisi belirteçleri yönetme biçimini özelleştirmek için genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d11bd-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="d11bd-108">WIF, değiştirilen veya tamamen gerektiği gibi işlevlerini değiştirmek için geçersiz kılınan dokuz yerleşik güvenlik belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d11bd-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="d11bd-109">WIF yerleşik güvenlik belirteci işleyicileri</span><span class="sxs-lookup"><span data-stu-id="d11bd-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="d11bd-110">WIF 4.5 soyut temel sınıfından türetilir dokuz güvenlik belirteci işleyici sınıflarını içerir <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="d11bd-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="d11bd-111">Özel bir belirteci işleyicisi ekleme</span><span class="sxs-lookup"><span data-stu-id="d11bd-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="d11bd-112">Basit Web belirteçleri (SWT) ve JSON Web belirteçleri (JWT) gibi bazı belirteç türleri tarafından WIF sağlanan yerleşik belirteç işleyicileri yok.</span><span class="sxs-lookup"><span data-stu-id="d11bd-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="d11bd-113">Bu belirteç türleri ve yerleşik bir işleyici olmayan diğer kişilerin, özel bir belirteci işleyicisi oluşturmak için aşağıdaki adımları gerçekleştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="d11bd-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="d11bd-114">Özel bir belirteci işleyicisi ekleme</span><span class="sxs-lookup"><span data-stu-id="d11bd-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="d11bd-115">Öğesinden türetilen yeni bir sınıf oluşturun <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="d11bd-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="d11bd-116">Aşağıdaki yöntemleri geçersiz kılın ve kendi uygulamanız sağlayın:</span><span class="sxs-lookup"><span data-stu-id="d11bd-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="d11bd-117">Yeni özel belirteci işleyici içinde bir başvuru ekleyin *Web.config* veya *App.config* içinde dosya  **\<system.identityModel >** , bölüm WIF için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d11bd-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="d11bd-118">Örneğin, aşağıdaki yapılandırma biçimlendirme adlı yeni bir belirteci işleyicisi belirtir **MyCustomTokenHandler** , bulunduğu **CustomToken** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d11bd-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="d11bd-119">Yerleşik bir belirteci işleyicisi zaten olan bir belirteç türü işlemek için kendi belirteci işleyicisi sağlıyorsanız eklemeniz gerektiğini unutmayın. bir  **\<kaldırma >** öğesi varsayılan işleyici bırakıp özel işleyicinizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d11bd-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="d11bd-120">Örneğin, aşağıdaki yapılandırmayı varsayılan değiştirir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> özel belirteci işleyicisi ile:</span><span class="sxs-lookup"><span data-stu-id="d11bd-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
