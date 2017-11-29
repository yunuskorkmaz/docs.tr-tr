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
ms.openlocfilehash: d471e860e74c9a01770c95671401bdbbc23643cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-token-handlers"></a><span data-ttu-id="b26ff-102">Özel belirteç işleyicileri</span><span class="sxs-lookup"><span data-stu-id="b26ff-102">Custom Token Handlers</span></span>
<span data-ttu-id="b26ff-103">Bu konu, belirteç işleyicileri WIF ve belirteçleri işlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b26ff-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="b26ff-104">Varsayılan olarak WIF desteklenmeyen belirteç türleri için özel belirteç işleyiciler oluşturmak için gerekli nedir konu da kapsar.</span><span class="sxs-lookup"><span data-stu-id="b26ff-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="b26ff-105">WIF belirteci işleyicileri giriş</span><span class="sxs-lookup"><span data-stu-id="b26ff-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="b26ff-106">WIF güvenlik belirteci işleyicileri oluşturma, okuma, yazma ve bağlı olan taraf (RP) uygulama veya bir güvenlik belirteci hizmeti (STS) belirteçleri doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b26ff-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="b26ff-107">Belirteç işleyicileri için özel bir belirteç işleyici WIF ardışık düzeninde ekleyin ya da varolan bir belirteci işleyicisi belirteçleri yönetme biçimini özelleştirmek için genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="b26ff-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="b26ff-108">WIF değiştirilen veya tamamen gerektiği gibi işlevlerini değiştirmek için geçersiz kılındı dokuz yerleşik güvenlik belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b26ff-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="b26ff-109">WIF yerleşik güvenlik belirteci işleyicileri</span><span class="sxs-lookup"><span data-stu-id="b26ff-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="b26ff-110">WIF 4.5 soyut taban sınıfından türetilen dokuz güvenlik belirteci işleyicisi sınıflarını içerir <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="b26ff-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="b26ff-111">Özel belirteç işleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="b26ff-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="b26ff-112">Basit Web belirteçleri (SWT) ve JSON Web belirteçleri (JWT) gibi bazı belirteç türleri tarafından WIF sağlanan yerleşik belirteci işleyicileri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b26ff-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="b26ff-113">Bu belirteç türleri ve başkalarının yerleşik bir işleyiciye sahip değil, özel belirteç işleyici oluşturmak için aşağıdaki adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b26ff-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="b26ff-114">Özel belirteç işleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="b26ff-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="b26ff-115">Öğesinden türetilen yeni bir sınıf oluşturun <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="b26ff-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="b26ff-116">Aşağıdaki yöntemleri geçersiz kılmak ve kendi uygulamanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="b26ff-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="b26ff-117">Yeni özel belirteç işleyici içinde bir başvuru ekleyin *Web.config* veya *App.config* içinde dosya  **\<System.IdentityModel >** , bölüm WIF geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b26ff-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="b26ff-118">Örneğin, aşağıdaki yapılandırma biçimlendirme adlı yeni bir belirteç işleyici belirtir **MyCustomTokenHandler** , bulunduğu **CustomToken** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b26ff-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="b26ff-119">Yerleşik bir belirteç işleyici zaten olan bir belirteç türü işlemek için kendi belirteci işleyicisi sağlıyorsanız eklemek gerektiğini unutmayın bir  **\<kaldırma >** öğesi varsayılan işleyici bırakın ve bunun yerine özel işleyicinizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b26ff-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="b26ff-120">Örneğin, aşağıdaki yapılandırma varsayılan değiştirir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> özel belirteç işleyici ile:</span><span class="sxs-lookup"><span data-stu-id="b26ff-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
