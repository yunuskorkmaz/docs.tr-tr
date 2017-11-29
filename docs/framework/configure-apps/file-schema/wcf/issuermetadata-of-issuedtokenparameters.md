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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8df1ffb74c59bfed2b9fa2f1e87e7669fe3ad9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="67185-102">&lt;issuedTokenParameters&gt; için &lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="67185-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="67185-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="67185-103">\<system.serviceModel></span></span>  
<span data-ttu-id="67185-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="67185-104">\<bindings></span></span>  
<span data-ttu-id="67185-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="67185-105">\<customBinding></span></span>  
<span data-ttu-id="67185-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="67185-106">\<binding></span></span>  
<span data-ttu-id="67185-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="67185-107">\<security></span></span>  
<span data-ttu-id="67185-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="67185-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="67185-109">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="67185-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67185-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67185-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67185-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="67185-111">Attributes and Elements</span></span>  
 <span data-ttu-id="67185-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67185-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67185-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67185-113">Attributes</span></span>  
  
|<span data-ttu-id="67185-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67185-114">Attribute</span></span>|<span data-ttu-id="67185-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67185-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67185-116">adres</span><span class="sxs-lookup"><span data-stu-id="67185-116">address</span></span>|<span data-ttu-id="67185-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="67185-117">Required.</span></span> <span data-ttu-id="67185-118">Uç nokta adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="67185-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="67185-119">Adres bir mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="67185-119">The address must be an absolute URI.</span></span> <span data-ttu-id="67185-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="67185-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67185-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="67185-121">Child Elements</span></span>  
  
|<span data-ttu-id="67185-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="67185-122">Element</span></span>|<span data-ttu-id="67185-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67185-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67185-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="67185-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="67185-125">Adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="67185-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="67185-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="67185-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="67185-127">Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="67185-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67185-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="67185-128">Parent Elements</span></span>  
  
|<span data-ttu-id="67185-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="67185-129">Element</span></span>|<span data-ttu-id="67185-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67185-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67185-131">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="67185-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="67185-132">Bir federe güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="67185-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67185-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67185-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="67185-134">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="67185-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="67185-135">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="67185-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="67185-136">Özel bağlamalarla güvenlik özellikleri</span><span class="sxs-lookup"><span data-stu-id="67185-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="67185-137">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="67185-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="67185-138">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="67185-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="67185-139">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="67185-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="67185-140">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="67185-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="67185-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="67185-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="67185-142">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="67185-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="67185-143">Özel bağlama güvenliği</span><span class="sxs-lookup"><span data-stu-id="67185-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
