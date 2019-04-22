---
title: <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 236ae880fff24f7ccbf5d6c9c03c0208d446688f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085850"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="c572c-102">\<claimTypeRequirements > öğesi</span><span class="sxs-lookup"><span data-stu-id="c572c-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="c572c-103">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c572c-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="c572c-104">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="c572c-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="c572c-105">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c572c-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="c572c-106">Bu koleksiyondaki her bir alt öğesi bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c572c-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="c572c-107">Bir talep türü gereksinimi, türü verilen belirteç gerekli veya isteğe bağlı talep olup olmadığını gösteren bir Boole parametresi ile birlikte verilen belirteç istenen talep türü URI oluşur.</span><span class="sxs-lookup"><span data-stu-id="c572c-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c572c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c572c-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c572c-109">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c572c-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c572c-110">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c572c-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c572c-111">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c572c-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c572c-112">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c572c-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c572c-113">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="c572c-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)
- [<span data-ttu-id="c572c-114">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c572c-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c572c-115">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c572c-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c572c-116">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c572c-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c572c-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c572c-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c572c-118">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="c572c-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c572c-119">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c572c-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
