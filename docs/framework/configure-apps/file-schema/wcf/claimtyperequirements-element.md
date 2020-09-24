---
title: <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 6a4e5da3bd3ef6977d6258190d397130b33eb56c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148977"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="1a491-102">\<claimTypeRequirements> öğesi</span><span class="sxs-lookup"><span data-stu-id="1a491-102">\<claimTypeRequirements> element</span></span>

<span data-ttu-id="1a491-103">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a491-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="1a491-104">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="1a491-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1a491-105">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a491-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1a491-106">Bu koleksiyondaki her alt öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a491-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="1a491-107">Talep türü gereksinimi, verilen belirteçte istenen belirteç için talep türünün URI 'sinden ve bu talep türünün verilen belirteçte gerekli olup olmadığını belirten bir Boolean parametresiyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="1a491-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a491-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a491-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1a491-109">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="1a491-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1a491-110">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="1a491-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1a491-111">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="1a491-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="1a491-112">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="1a491-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="1a491-113">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1a491-113">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1a491-114">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="1a491-114">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1a491-115">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1a491-115">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="1a491-116">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a491-116">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="1a491-117">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1a491-117">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
