---
title: "&lt;claimTypeRequirements&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0146250c12c9c12e1f204c467a9a454b90e9f47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="f3803-102">&lt;claimTypeRequirements&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="f3803-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="f3803-103">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3803-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="f3803-104">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="f3803-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="f3803-105">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3803-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="f3803-106">Bu koleksiyondaki her alt öğesi bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3803-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="f3803-107">Bir talep türü gereksinim, türü verilen belirteç gerekli veya isteğe bağlı talep olup olmadığını belirten bir Boolean parametresiyle birlikte verilen belirteç istenen talep türü URI oluşur.</span><span class="sxs-lookup"><span data-stu-id="f3803-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3803-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3803-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f3803-109">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f3803-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="f3803-110">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="f3803-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f3803-111">Özel bağlamalarla güvenlik özellikleri</span><span class="sxs-lookup"><span data-stu-id="f3803-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="f3803-112">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="f3803-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f3803-113">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="f3803-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [<span data-ttu-id="f3803-114">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="f3803-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f3803-115">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="f3803-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f3803-116">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f3803-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f3803-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f3803-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="f3803-118">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3803-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="f3803-119">Özel bağlama güvenliği</span><span class="sxs-lookup"><span data-stu-id="f3803-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
