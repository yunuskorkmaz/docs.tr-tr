---
title: "&lt;issuedTokenParameters&gt; &lt;yayınlayan&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b31214f5552283c40cdc93e6e72a374bbfef9997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="135f3-102">&lt;issuedTokenParameters&gt; &lt;yayınlayan&gt;</span><span class="sxs-lookup"><span data-stu-id="135f3-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="135f3-103">Güvenlik belirteci hizmeti (güvenlik belirteçleri veren STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="135f3-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="135f3-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="135f3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="135f3-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="135f3-105">\<bindings></span></span>  
<span data-ttu-id="135f3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="135f3-106">\<customBinding></span></span>  
<span data-ttu-id="135f3-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="135f3-107">\<binding></span></span>  
<span data-ttu-id="135f3-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="135f3-108">\<security></span></span>  
<span data-ttu-id="135f3-109">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="135f3-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="135f3-110">\<veren ></span><span class="sxs-lookup"><span data-stu-id="135f3-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135f3-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="135f3-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="135f3-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="135f3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="135f3-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="135f3-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="135f3-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="135f3-114">Attributes</span></span>  
  
|<span data-ttu-id="135f3-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="135f3-115">Attribute</span></span>|<span data-ttu-id="135f3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="135f3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="135f3-117">adres</span><span class="sxs-lookup"><span data-stu-id="135f3-117">address</span></span>|<span data-ttu-id="135f3-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="135f3-118">Required string.</span></span> <span data-ttu-id="135f3-119">STS URL'si.</span><span class="sxs-lookup"><span data-stu-id="135f3-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="135f3-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="135f3-120">Child Elements</span></span>  
  
|<span data-ttu-id="135f3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="135f3-121">Element</span></span>|<span data-ttu-id="135f3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="135f3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="135f3-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="135f3-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="135f3-124">Adres üstbilgileri Oluşturucu oluşturabilirsiniz uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="135f3-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="135f3-125">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="135f3-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="135f3-126">Verilen bir belirteç kullanırken, sunucu kimlik doğrulaması istemci etkinleştirme ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="135f3-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="135f3-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="135f3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="135f3-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="135f3-128">Element</span></span>|<span data-ttu-id="135f3-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="135f3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="135f3-130">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="135f3-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="135f3-131">Geçerli verilen belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="135f3-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="135f3-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="135f3-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="135f3-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="135f3-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="135f3-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="135f3-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="135f3-135">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="135f3-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="135f3-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="135f3-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="135f3-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="135f3-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="135f3-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="135f3-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="135f3-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="135f3-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="135f3-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="135f3-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="135f3-141">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="135f3-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="135f3-142">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="135f3-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
