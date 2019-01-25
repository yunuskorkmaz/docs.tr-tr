---
title: '&lt;claimTypeRequirements&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 32eafa3ce235b2087012bd5810a685ad5276e09d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632904"
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="c5233-102">&lt;claimTypeRequirements&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="c5233-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="c5233-103">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5233-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="c5233-104">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="c5233-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="c5233-105">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5233-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="c5233-106">Bu koleksiyondaki her bir alt öğesi bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5233-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="c5233-107">Bir talep türü gereksinimi, türü verilen belirteç gerekli veya isteğe bağlı talep olup olmadığını gösteren bir Boole parametresi ile birlikte verilen belirteç istenen talep türü URI oluşur.</span><span class="sxs-lookup"><span data-stu-id="c5233-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5233-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5233-108">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c5233-109">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c5233-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c5233-110">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c5233-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c5233-111">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5233-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c5233-112">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c5233-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c5233-113">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="c5233-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)
- [<span data-ttu-id="c5233-114">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c5233-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c5233-115">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c5233-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c5233-116">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c5233-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c5233-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c5233-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c5233-118">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5233-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c5233-119">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c5233-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
