---
title: "&lt;issuedTokenParameters&gt; için &lt;issuerMetadata&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee0f6b2abe6ddfa81f236da47425ae586b56f0ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="8d3cd-102">&lt;issuedTokenParameters&gt; için &lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="8d3cd-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="8d3cd-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8d3cd-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-104">\<bindings></span></span>  
<span data-ttu-id="8d3cd-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-105">\<customBinding></span></span>  
<span data-ttu-id="8d3cd-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-106">\<binding></span></span>  
<span data-ttu-id="8d3cd-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-107">\<security></span></span>  
<span data-ttu-id="8d3cd-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="8d3cd-109">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d3cd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d3cd-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d3cd-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d3cd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8d3cd-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d3cd-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d3cd-113">Attributes</span></span>  
  
|<span data-ttu-id="8d3cd-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8d3cd-114">Attribute</span></span>|<span data-ttu-id="8d3cd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d3cd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d3cd-116">adres</span><span class="sxs-lookup"><span data-stu-id="8d3cd-116">address</span></span>|<span data-ttu-id="8d3cd-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-117">Required.</span></span> <span data-ttu-id="8d3cd-118">Uç nokta adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="8d3cd-119">Adres bir mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-119">The address must be an absolute URI.</span></span> <span data-ttu-id="8d3cd-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d3cd-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d3cd-121">Child Elements</span></span>  
  
|<span data-ttu-id="8d3cd-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d3cd-122">Element</span></span>|<span data-ttu-id="8d3cd-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d3cd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d3cd-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="8d3cd-125">Adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="8d3cd-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8d3cd-127">Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d3cd-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d3cd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="8d3cd-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d3cd-129">Element</span></span>|<span data-ttu-id="8d3cd-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d3cd-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d3cd-131">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="8d3cd-132">Bir federe güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d3cd-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d3cd-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8d3cd-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="8d3cd-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8d3cd-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="8d3cd-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="8d3cd-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d3cd-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="8d3cd-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="8d3cd-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="8d3cd-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8d3cd-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8d3cd-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8d3cd-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8d3cd-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8d3cd-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8d3cd-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8d3cd-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="8d3cd-142">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d3cd-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="8d3cd-143">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8d3cd-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
