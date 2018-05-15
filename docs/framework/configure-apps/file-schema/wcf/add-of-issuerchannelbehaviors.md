---
title: '&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="df4fa-102">&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="df4fa-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="df4fa-103">Bir STS ile iletişim kurarken kullanılacak bir uç noktası davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="df4fa-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df4fa-104">Uç noktası davranışı içeriyorsa bir [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="df4fa-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="df4fa-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="df4fa-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="df4fa-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="df4fa-106">\<behaviors></span></span>  
<span data-ttu-id="df4fa-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="df4fa-107">endpointBehaviors section</span></span>  
<span data-ttu-id="df4fa-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="df4fa-108">\<behavior></span></span>  
<span data-ttu-id="df4fa-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="df4fa-109">\<clientCredentials></span></span>  
<span data-ttu-id="df4fa-110">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="df4fa-110">\<issuedToken></span></span>  
<span data-ttu-id="df4fa-111">\<issuerChannelBehaviors > öğesi</span><span class="sxs-lookup"><span data-stu-id="df4fa-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="df4fa-112">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="df4fa-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df4fa-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df4fa-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df4fa-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df4fa-114">Attributes and Elements</span></span>  
 <span data-ttu-id="df4fa-115">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="df4fa-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df4fa-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df4fa-116">Attributes</span></span>  
  
|<span data-ttu-id="df4fa-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df4fa-117">Attribute</span></span>|<span data-ttu-id="df4fa-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df4fa-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df4fa-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="df4fa-119">issuerAddress</span></span>|<span data-ttu-id="df4fa-120">İle iletişim kurmak için güvenlik belirteci verenin URI'si.</span><span class="sxs-lookup"><span data-stu-id="df4fa-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="df4fa-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="df4fa-121">behaviorConfiguration</span></span>|<span data-ttu-id="df4fa-122">Aynı yapılandırma dosyasında tanımlanan bir uç noktası davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="df4fa-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df4fa-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df4fa-123">Child Elements</span></span>  
 <span data-ttu-id="df4fa-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="df4fa-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df4fa-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df4fa-125">Parent Elements</span></span>  
  
|<span data-ttu-id="df4fa-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="df4fa-126">Element</span></span>|<span data-ttu-id="df4fa-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df4fa-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df4fa-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="df4fa-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="df4fa-129">Belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak Windows Communication Foundation (WCF) istemci uç nokta davranışları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="df4fa-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df4fa-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df4fa-130">Remarks</span></span>  
 <span data-ttu-id="df4fa-131">`issuerAddress` istemci ile iletişim kurmak istediği güvenlik belirteci hizmeti URI içeriyor.</span><span class="sxs-lookup"><span data-stu-id="df4fa-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="df4fa-132">`behaviorConfiguration` verilen belirteçler güvenlik belirteci hizmetlerinden almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanaldaki uygulama kullanan bir uç noktası davranışı noktalarına.</span><span class="sxs-lookup"><span data-stu-id="df4fa-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4fa-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df4fa-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="df4fa-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="df4fa-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="df4fa-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="df4fa-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="df4fa-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="df4fa-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="df4fa-137">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="df4fa-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="df4fa-138">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="df4fa-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="df4fa-139">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="df4fa-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="df4fa-140">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="df4fa-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="df4fa-141">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="df4fa-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="df4fa-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="df4fa-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
