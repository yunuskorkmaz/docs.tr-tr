---
title: "Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0bf616b1af46c62166b0430c1b67b3a97f0613ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-security-token-provider"></a><span data-ttu-id="8ce4e-102">Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ce4e-102">How to: Create a Custom Security Token Provider</span></span>
<span data-ttu-id="8ce4e-103">Bu konu, yeni belirteç türleri sahip bir özel güvenlik belirteci sağlayıcı oluşturma ve sağlayıcı özel güvenlik belirteci yöneticisi ile tümleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-103">This topic shows how to create new token types with a custom security token provider and how to integrate the provider with a custom security token manager.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce4e-104">Sistem tarafından sağlanan belirteçleri bulunan özel bir belirteç sağlayıcısı oluşturun <xref:System.IdentityModel.Tokens> ad alanı gereksinimlerinizi eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-104">Create a custom token provider if the system-provided tokens found in the <xref:System.IdentityModel.Tokens> namespace do not match your requirements.</span></span>  
  
 <span data-ttu-id="8ce4e-105">Güvenlik belirteci sağlayıcısı istemci veya hizmet kimlik bilgileri temel alarak bir güvenlik belirteci temsilini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-105">The security token provider creates a security token representation based on information in the client or service credentials.</span></span> <span data-ttu-id="8ce4e-106">Özel güvenlik belirteci sağlayıcı kullanacak şekilde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik, özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-106">To use the custom security token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security, you must create custom credentials and security token manager implementations.</span></span>  
  
 <span data-ttu-id="8ce4e-107">Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="8ce4e-107">For more information about custom credentials and security token manager see the [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
 <span data-ttu-id="8ce4e-108">Kimlik bilgileri hakkında daha fazla bilgi için bkz: güvenlik belirteci yöneticisi, sağlayıcı ve Doğrulayıcı sınıfları [güvenlik mimarisi](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).</span><span class="sxs-lookup"><span data-stu-id="8ce4e-108">For more information about credentials, security token manager, provider and authenticator classes, see the [Security Architecture](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).</span></span>  
  
### <a name="to-create-a-custom-security-token-provider"></a><span data-ttu-id="8ce4e-109">Bir özel güvenlik belirteci sağlayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8ce4e-109">To create a custom security token provider</span></span>  
  
1.  <span data-ttu-id="8ce4e-110">Türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-110">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class.</span></span>  
  
2.  <span data-ttu-id="8ce4e-111">Uygulama <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-111">Implement the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="8ce4e-112">Yöntemi, oluşturma ve güvenlik belirteci örneğini döndüren sorumludur.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-112">The method is responsible for creating and returning an instance of the security token.</span></span> <span data-ttu-id="8ce4e-113">Aşağıdaki örnek adlı bir sınıf oluşturur `MySecurityTokenProvider`ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> örneği döndürülecek yöntemi <xref:System.IdentityModel.Tokens.X509SecurityToken> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-113">The following example creates a class named `MySecurityTokenProvider`, and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method to return an instance of the <xref:System.IdentityModel.Tokens.X509SecurityToken> class.</span></span> <span data-ttu-id="8ce4e-114">Sınıf oluşturucu örneği gerektirir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-114">The class constructor requires an instance of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> class.</span></span>  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a><span data-ttu-id="8ce4e-115">Özel güvenlik belirteci sağlayıcı özel güvenlik belirteci yöneticisi ile tümleştirmek için</span><span class="sxs-lookup"><span data-stu-id="8ce4e-115">To integrate a custom security token provider with a custom security token manager</span></span>  
  
1.  <span data-ttu-id="8ce4e-116">Türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-116">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span> <span data-ttu-id="8ce4e-117">(Aşağıdaki örnekte türetilen <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> türeyen sınıf <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı.)</span><span class="sxs-lookup"><span data-stu-id="8ce4e-117">(The example below derives from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class, which derives from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.)</span></span>  
  
2.  <span data-ttu-id="8ce4e-118">Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> değil zaten geçersiz kılınırsa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-118">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if is not already overridden.</span></span>  
  
     <span data-ttu-id="8ce4e-119"><xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Yöntemi örneği döndürmek için sorumlu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı için uygun <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> yöntemi tarafından geçirilen parametre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-119">The <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method is responsible for returning an instance of the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class appropriate to the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter passed to the method by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security framework.</span></span> <span data-ttu-id="8ce4e-120">(Önceki yordamda oluşturduğunuz) özel bir güvenlik belirteci sağlayıcı uygulaması döndürmek için yöntemini değiştirme zaman yöntemi çağrıldığında bir uygun güvenlik belirteci parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-120">Modify the method to return the custom security token provider implementation (created in the previous procedure) when the method is called with an appropriate security token parameter.</span></span> <span data-ttu-id="8ce4e-121">Güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="8ce4e-121">For more information about the security token manager, see the [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
3.  <span data-ttu-id="8ce4e-122">Temel, özel güvenlik belirteci sağlayıcı döndürülecek etkinleştirmek için yöntemi Özel mantık ekleme <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametresi.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-122">Add custom logic to the method to enable it to return your custom security token provider based on the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter.</span></span> <span data-ttu-id="8ce4e-123">Aşağıdaki örnek, belirteç gereksinimlerin karşılanması durumunda özel güvenlik belirteci sağlayıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-123">The following sample returns the custom security token provider if the token requirements are met.</span></span> <span data-ttu-id="8ce4e-124">Gereksinimleri, bir X.509 güvenlik belirteci ve (belirteç ileti çıktı için kullanıldığını) ileti yönü içerir.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-124">The requirements include an X.509 security token and the message direction (that the token is used for message output).</span></span> <span data-ttu-id="8ce4e-125">Tüm diğer durumlarda, diğer güvenlik belirteci gereksinimleri için sistem tarafından sağlanan davranışı sağlamak için temel sınıf kod çağırır.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-125">For all other cases, the code calls the base class to maintain the system-provided behavior for other security token requirements.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="8ce4e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ce4e-126">Example</span></span>  
 <span data-ttu-id="8ce4e-127">Aşağıdaki tam gösterir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> karşılık gelen yanı sıra uygulama <xref:System.IdentityModel.Selectors.SecurityTokenManager> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-127">The following shows a complete <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation along with a corresponding <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementation.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="8ce4e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ce4e-128">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [<span data-ttu-id="8ce4e-129">İzlenecek yol: Özel istemci ve hizmet kimlik bilgileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ce4e-129">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [<span data-ttu-id="8ce4e-130">Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ce4e-130">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [<span data-ttu-id="8ce4e-131">Güvenlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="8ce4e-131">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
