---
title: '&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea76a96597796b10c97ea57ca38c3bda453468c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="cd49e-102">&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="cd49e-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="cd49e-103">Bir STS ile iletişim kurarken kullanılacak bir uç noktası davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="cd49e-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd49e-104">Uç noktası davranışı içeriyorsa bir [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="cd49e-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="cd49e-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cd49e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd49e-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="cd49e-106">\<behaviors></span></span>  
<span data-ttu-id="cd49e-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="cd49e-107">endpointBehaviors section</span></span>  
<span data-ttu-id="cd49e-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="cd49e-108">\<behavior></span></span>  
<span data-ttu-id="cd49e-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cd49e-109">\<clientCredentials></span></span>  
<span data-ttu-id="cd49e-110">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="cd49e-110">\<issuedToken></span></span>  
<span data-ttu-id="cd49e-111">\<issuerChannelBehaviors > öğesi</span><span class="sxs-lookup"><span data-stu-id="cd49e-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="cd49e-112">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="cd49e-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd49e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd49e-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd49e-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd49e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="cd49e-115">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="cd49e-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd49e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cd49e-116">Attributes</span></span>  
  
|<span data-ttu-id="cd49e-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cd49e-117">Attribute</span></span>|<span data-ttu-id="cd49e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd49e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd49e-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="cd49e-119">issuerAddress</span></span>|<span data-ttu-id="cd49e-120">İle iletişim kurmak için güvenlik belirteci verenin URI'si.</span><span class="sxs-lookup"><span data-stu-id="cd49e-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="cd49e-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="cd49e-121">behaviorConfiguration</span></span>|<span data-ttu-id="cd49e-122">Aynı yapılandırma dosyasında tanımlanan bir uç noktası davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="cd49e-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd49e-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd49e-123">Child Elements</span></span>  
 <span data-ttu-id="cd49e-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="cd49e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd49e-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd49e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cd49e-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd49e-126">Element</span></span>|<span data-ttu-id="cd49e-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd49e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd49e-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cd49e-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="cd49e-129">Bir koleksiyonu içerir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] istemci uç nokta davranışları belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="cd49e-129">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd49e-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd49e-130">Remarks</span></span>  
 <span data-ttu-id="cd49e-131">`issuerAddress`istemci ile iletişim kurmak istediği güvenlik belirteci hizmeti URI içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cd49e-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="cd49e-132">`behaviorConfiguration`uygulama tarafından oluşturulan kanaldaki kullanan bir uç noktası davranışı işaret [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] verilen belirteçler güvenlik belirteci hizmetlerinden almak için.</span><span class="sxs-lookup"><span data-stu-id="cd49e-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd49e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd49e-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="cd49e-134">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="cd49e-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="cd49e-135">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="cd49e-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cd49e-136">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="cd49e-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="cd49e-137">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="cd49e-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cd49e-138">İstemcilerinin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="cd49e-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cd49e-139">Nasıl yapılır: federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd49e-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="cd49e-140">Nasıl yapılır: yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cd49e-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="cd49e-141">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="cd49e-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="cd49e-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cd49e-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
