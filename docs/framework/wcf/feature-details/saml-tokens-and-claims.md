---
title: "SAML Belirteçleri ve Talepleri"
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
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2b35ba4da503663a2bb92597ed193c408e7c99b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="2083b-102">SAML Belirteçleri ve Talepleri</span><span class="sxs-lookup"><span data-stu-id="2083b-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="2083b-103">Güvenlik onaylar biçimlendirme dili (SAML) *belirteçleri* talep XML gösterimlerini şunlardır.</span><span class="sxs-lookup"><span data-stu-id="2083b-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="2083b-104">Varsayılan olarak, SAML belirteçlerini [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] federe güvenlik senaryolarda kullanımları *verilen belirteçler*.</span><span class="sxs-lookup"><span data-stu-id="2083b-104">By default, SAML tokens [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="2083b-105">SAML belirteçleri başka bir varlık hakkında bir varlık tarafından yapılan talepleri kümeleridir deyimleri taşır.</span><span class="sxs-lookup"><span data-stu-id="2083b-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="2083b-106">Örneğin, Federasyon güvenlik senaryolarda, sistemde bir kullanıcıyla ilgili bir güvenlik belirteci hizmeti tarafından deyimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="2083b-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="2083b-107">Güvenlik belirteci hizmeti belirtecinde yer alan deyimleri belki belirtmek için SAML belirteci imzalar.</span><span class="sxs-lookup"><span data-stu-id="2083b-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="2083b-108">Ayrıca, SAML belirteci SAML belirteci kullanıcı bilgisi kanıtlar şifreleme anahtar malzemesi ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="2083b-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="2083b-109">SAML belirteci olduğu, bağlı olan taraf aslında, o kullanıcıya verilen bu kanıt karşılar.</span><span class="sxs-lookup"><span data-stu-id="2083b-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="2083b-110">Örneğin, tipik bir senaryoda:</span><span class="sxs-lookup"><span data-stu-id="2083b-110">For example, in a typical scenario:</span></span>  
  
1.  <span data-ttu-id="2083b-111">Bir istemci, bu güvenlik belirteci hizmeti Windows kimlik bilgilerini kullanarak kimlik doğrulaması, bir güvenlik belirteci Hizmeti'nden bir SAML belirtecine ister.</span><span class="sxs-lookup"><span data-stu-id="2083b-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="2083b-112">Güvenlik belirteci hizmeti istemciye bir SAML belirteci verir.</span><span class="sxs-lookup"><span data-stu-id="2083b-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="2083b-113">SAML belirteci güvenlik belirteci hizmeti ile ilişkili bir sertifikayla imzalanmış ve hedef hizmet için şifrelenmiş bir kanıt anahtarı içerir.</span><span class="sxs-lookup"><span data-stu-id="2083b-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3.  <span data-ttu-id="2083b-114">İstemci ayrıca bir kopyasını alır *kanıt anahtarı*.</span><span class="sxs-lookup"><span data-stu-id="2083b-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="2083b-115">İstemci uygulama hizmeti SAML belirtecine sonra sunar ( *bağlı olan taraf*) ve ileti bu kanıtını anahtarıyla imzalar.</span><span class="sxs-lookup"><span data-stu-id="2083b-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4.  <span data-ttu-id="2083b-116">SAML belirteci üzerinden imza, güvenlik belirteci hizmeti belirteç verilen bağlı olan taraf söyler.</span><span class="sxs-lookup"><span data-stu-id="2083b-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="2083b-117">Kanıt anahtarı ile oluşturulan ileti imzası, belirteci istemciye verilmiş bağlı olan taraf söyler.</span><span class="sxs-lookup"><span data-stu-id="2083b-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="2083b-118">SamlAttributes talepleri</span><span class="sxs-lookup"><span data-stu-id="2083b-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="2083b-119">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], SAML belirteçlerini deyimlerinde olarak modellenir <xref:System.IdentityModel.Tokens.SamlAttribute> doğrudan doldurulmuş nesneleri <xref:System.IdentityModel.Claims.Claim> sağlanan nesnelerini <xref:System.IdentityModel.Claims.Claim> nesnesi bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliği <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> özellik türüdür <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2083b-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="2083b-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2083b-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  <span data-ttu-id="2083b-121">SAML belirteçleri iletilerinde, bir güvenlik belirteci hizmeti tarafından verildiğinde veya hizmetleri için istemciler tarafından kimlik doğrulaması bir parçası olarak sunulduklarında serileştirildiği zaman maksimum ileti boyutu kotası SAML belirteci karşılamak için yeterli büyüklükte olması gerekir ve diğer ileti bölümleri.</span><span class="sxs-lookup"><span data-stu-id="2083b-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="2083b-122">Normal durumlarda, varsayılan ileti boyutu kotalarını yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="2083b-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="2083b-123">Ancak, talep yüzlerce içerdiğinden bir SAML belirtecine büyük olduğu durumlarda, serileştirilmiş belirteci uyum sağlamak için kotaları artırma gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2083b-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2083b-124">[Veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="2083b-124"> [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="2083b-125">Talepler için SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="2083b-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="2083b-126">SAML belirteçleri iletilerinde alındığında SAML belirteci çeşitli deyimlerinde içine açık olan <xref:System.IdentityModel.Policy.IAuthorizationPolicy> içine yerleştirilen nesneleri <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="2083b-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="2083b-127">Talepleri her SAML ifadesi tarafından döndürülen <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> ve kimlik doğrulama ve kullanıcı yetkilendirme yazılıp yazılmayacağını incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="2083b-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2083b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2083b-128">See Also</span></span>  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="2083b-129">Federasyon</span><span class="sxs-lookup"><span data-stu-id="2083b-129">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="2083b-130">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2083b-130">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="2083b-131">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2083b-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="2083b-132">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="2083b-132">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="2083b-133">Talepler ve Belirteçler</span><span class="sxs-lookup"><span data-stu-id="2083b-133">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [<span data-ttu-id="2083b-134">Talep Oluşturma ve Kaynak Değerleri</span><span class="sxs-lookup"><span data-stu-id="2083b-134">Claim Creation and Resource Values</span></span>](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [<span data-ttu-id="2083b-135">Nasıl yapılır: Özel Talep Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2083b-135">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
