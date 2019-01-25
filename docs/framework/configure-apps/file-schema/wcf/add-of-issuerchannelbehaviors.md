---
title: '&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: e0f49f71a3f9649492b3ad7ccf263114957ee4e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729937"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="30b73-102">&lt;issuerChannelBehaviors&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="30b73-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="30b73-103">Bir STS ile iletişim kurarken kullanılacak uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="30b73-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b73-104">Herhangi bir uç nokta davranışı içeriyorsa bir [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="30b73-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="30b73-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="30b73-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="30b73-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="30b73-106">\<behaviors></span></span>  
<span data-ttu-id="30b73-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="30b73-107">endpointBehaviors section</span></span>  
<span data-ttu-id="30b73-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="30b73-108">\<behavior></span></span>  
<span data-ttu-id="30b73-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="30b73-109">\<clientCredentials></span></span>  
<span data-ttu-id="30b73-110">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="30b73-110">\<issuedToken></span></span>  
<span data-ttu-id="30b73-111">\<issuerChannelBehaviors > öğesi</span><span class="sxs-lookup"><span data-stu-id="30b73-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="30b73-112">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="30b73-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b73-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30b73-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30b73-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30b73-114">Attributes and Elements</span></span>  
 <span data-ttu-id="30b73-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30b73-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30b73-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30b73-116">Attributes</span></span>  
  
|<span data-ttu-id="30b73-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30b73-117">Attribute</span></span>|<span data-ttu-id="30b73-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30b73-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30b73-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="30b73-119">issuerAddress</span></span>|<span data-ttu-id="30b73-120">İle iletişim kurmak için güvenlik belirteci vericisinin URI.</span><span class="sxs-lookup"><span data-stu-id="30b73-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="30b73-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="30b73-121">behaviorConfiguration</span></span>|<span data-ttu-id="30b73-122">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="30b73-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30b73-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30b73-123">Child Elements</span></span>  
 <span data-ttu-id="30b73-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="30b73-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30b73-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30b73-125">Parent Elements</span></span>  
  
|<span data-ttu-id="30b73-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="30b73-126">Element</span></span>|<span data-ttu-id="30b73-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30b73-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30b73-128">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="30b73-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="30b73-129">Windows Communication Foundation (WCF) hizmeti belirtilen belirteci Hizmetleri ile iletişim kurarken kullanılacak uç nokta davranışları istemci koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="30b73-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30b73-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30b73-130">Remarks</span></span>  
 <span data-ttu-id="30b73-131">`issuerAddress` istemci ile iletişim kurmak istediği güvenlik belirteci hizmeti URI'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="30b73-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="30b73-132">`behaviorConfiguration` Güvenlik belirteci hizmetlerine verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallar uygulamanın kullandığı bir uç nokta davranışı işaret eder.</span><span class="sxs-lookup"><span data-stu-id="30b73-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b73-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b73-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="30b73-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="30b73-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="30b73-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="30b73-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="30b73-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="30b73-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="30b73-137">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="30b73-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="30b73-138">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="30b73-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="30b73-139">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="30b73-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="30b73-140">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="30b73-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="30b73-141">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="30b73-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="30b73-142">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="30b73-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
