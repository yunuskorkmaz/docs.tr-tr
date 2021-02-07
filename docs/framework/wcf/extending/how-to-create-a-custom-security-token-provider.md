---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel güvenlik belirteci sağlayıcısı oluşturma'
title: 'Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 4e0970ff01be74d0eb9f4ae8968bd100a0dafe00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735042"
---
# <a name="how-to-create-a-custom-security-token-provider"></a><span data-ttu-id="5fb5e-103">Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb5e-103">How to: Create a Custom Security Token Provider</span></span>

<span data-ttu-id="5fb5e-104">Bu konuda, özel bir güvenlik belirteci sağlayıcısıyla yeni belirteç türleri oluşturma ve sağlayıcıyı özel bir güvenlik belirteci yöneticisiyle tümleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-104">This topic shows how to create new token types with a custom security token provider and how to integrate the provider with a custom security token manager.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fb5e-105">Ad alanında bulunan sistem tarafından sağlanmış belirteçler gereksinimlerle eşleşmezse özel bir belirteç sağlayıcısı oluşturun <xref:System.IdentityModel.Tokens> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-105">Create a custom token provider if the system-provided tokens found in the <xref:System.IdentityModel.Tokens> namespace do not match your requirements.</span></span>  
  
 <span data-ttu-id="5fb5e-106">Güvenlik belirteci sağlayıcısı, istemci veya hizmet kimlik bilgileriyle ilgili bilgileri temel alarak bir güvenlik belirteci temsili oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-106">The security token provider creates a security token representation based on information in the client or service credentials.</span></span> <span data-ttu-id="5fb5e-107">Windows Communication Foundation (WCF) güvenlik sürümünde özel güvenlik belirteci sağlayıcısını kullanmak için özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-107">To use the custom security token provider in Windows Communication Foundation (WCF) security, you must create custom credentials and security token manager implementations.</span></span>  
  
 <span data-ttu-id="5fb5e-108">Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-108">For more information about custom credentials and security token manager see the [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
### <a name="to-create-a-custom-security-token-provider"></a><span data-ttu-id="5fb5e-109">Özel bir güvenlik belirteci sağlayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5fb5e-109">To create a custom security token provider</span></span>  
  
1. <span data-ttu-id="5fb5e-110">Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.SecurityTokenProvider> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-110">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class.</span></span>  
  
2. <span data-ttu-id="5fb5e-111">Yöntemini uygulayın <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-111">Implement the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="5fb5e-112">Yöntemi, güvenlik belirtecinin bir örneğini oluşturup döndürmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-112">The method is responsible for creating and returning an instance of the security token.</span></span> <span data-ttu-id="5fb5e-113">Aşağıdaki örnek adlı bir sınıf oluşturur `MySecurityTokenProvider` ve <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> sınıfının bir örneğini döndürmek için yöntemini geçersiz kılar <xref:System.IdentityModel.Tokens.X509SecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-113">The following example creates a class named `MySecurityTokenProvider`, and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method to return an instance of the <xref:System.IdentityModel.Tokens.X509SecurityToken> class.</span></span> <span data-ttu-id="5fb5e-114">Sınıf oluşturucusu, sınıfının bir örneğini gerektirir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-114">The class constructor requires an instance of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> class.</span></span>  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a><span data-ttu-id="5fb5e-115">Özel bir güvenlik belirteci sağlayıcısını özel bir güvenlik belirteci Yöneticisi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="5fb5e-115">To integrate a custom security token provider with a custom security token manager</span></span>  
  
1. <span data-ttu-id="5fb5e-116">Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.SecurityTokenManager> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-116">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span> <span data-ttu-id="5fb5e-117">(Aşağıdaki örnek sınıfından türetilen sınıfından türetilir <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenManager> .)</span><span class="sxs-lookup"><span data-stu-id="5fb5e-117">(The example below derives from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class, which derives from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.)</span></span>  
  
2. <span data-ttu-id="5fb5e-118">Önceden geçersiz <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> kılınmamışsa yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-118">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if is not already overridden.</span></span>  
  
     <span data-ttu-id="5fb5e-119"><xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>Yöntemi, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> WCF güvenlik çerçevesi tarafından metoduna geçirilen parametreye uygun bir sınıf örneğini döndürmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-119">The <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method is responsible for returning an instance of the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class appropriate to the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter passed to the method by the WCF security framework.</span></span> <span data-ttu-id="5fb5e-120">Yöntemi uygun bir güvenlik belirteci parametresiyle çağrıldığında özel güvenlik belirteci sağlayıcısı uygulamasını (önceki yordamda oluşturulan) döndürmek için yöntemini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-120">Modify the method to return the custom security token provider implementation (created in the previous procedure) when the method is called with an appropriate security token parameter.</span></span> <span data-ttu-id="5fb5e-121">Güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-121">For more information about the security token manager, see the [Walkthrough: Creating Custom Client and Service Credentials](walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
3. <span data-ttu-id="5fb5e-122">Metoda göre özel güvenlik belirteci sağlayıcınızı döndürmesini sağlamak için yöntemine özel mantık ekleyin <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-122">Add custom logic to the method to enable it to return your custom security token provider based on the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter.</span></span> <span data-ttu-id="5fb5e-123">Aşağıdaki örnek, belirteç gereksinimleri karşılanıyorsa özel güvenlik belirteci sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-123">The following sample returns the custom security token provider if the token requirements are met.</span></span> <span data-ttu-id="5fb5e-124">Gereksinimler bir X. 509.440 güvenlik belirteci ve ileti yönü (belirtecin ileti çıktısı için kullanıldığı) içerir.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-124">The requirements include an X.509 security token and the message direction (that the token is used for message output).</span></span> <span data-ttu-id="5fb5e-125">Diğer tüm durumlarda, kod, diğer güvenlik belirteci gereksinimleri için sistem tarafından sağlanmış davranışı sürdürmek üzere temel sınıfı çağırır.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-125">For all other cases, the code calls the base class to maintain the system-provided behavior for other security token requirements.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="5fb5e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fb5e-126">Example</span></span>  

 <span data-ttu-id="5fb5e-127">Aşağıda, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> karşılık gelen bir uygulamayla birlikte tamamlanmış bir uygulama gösterilmektedir <xref:System.IdentityModel.Selectors.SecurityTokenManager> .</span><span class="sxs-lookup"><span data-stu-id="5fb5e-127">The following shows a complete <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation along with a corresponding <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementation.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="5fb5e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-128">See also</span></span>

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [<span data-ttu-id="5fb5e-129">İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb5e-129">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)
- [<span data-ttu-id="5fb5e-130">Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fb5e-130">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)
