---
title: <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926152"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="b33f4-102">\<claimTypeRequirements > öğesi</span><span class="sxs-lookup"><span data-stu-id="b33f4-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="b33f4-103">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b33f4-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="b33f4-104">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b33f4-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b33f4-105">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b33f4-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b33f4-106">Bu koleksiyondaki her alt öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b33f4-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="b33f4-107">Talep türü gereksinimi, verilen belirteçte istenen belirteç için talep türünün URI 'sinden ve bu talep türünün verilen belirteçte gerekli olup olmadığını belirten bir Boolean parametresiyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="b33f4-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b33f4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b33f4-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b33f4-109">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b33f4-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b33f4-110">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b33f4-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b33f4-111">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b33f4-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b33f4-112">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b33f4-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b33f4-113">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="b33f4-113">\<add></span></span>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="b33f4-114">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b33f4-114">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b33f4-115">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b33f4-115">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b33f4-116">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b33f4-116">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b33f4-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b33f4-117">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b33f4-118">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="b33f4-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b33f4-119">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b33f4-119">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
