---
title: '&lt;issuerChannelBehaviors&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7e5b8ace06a224db3abcc6b9d0ec87ccbc1a6a77
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="f87dc-102">&lt;issuerChannelBehaviors&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="f87dc-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="f87dc-103">Belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak (yapılandırmasında tanımlanmış) Windows Communication Foundation (WCF) istemci uç nokta davranışları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f87dc-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="f87dc-104">Tanımlı davranışları herhangi içeremez [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f87dc-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="f87dc-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f87dc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f87dc-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f87dc-106">\<behaviors></span></span>  
<span data-ttu-id="f87dc-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="f87dc-107">endpointBehaviors section</span></span>  
<span data-ttu-id="f87dc-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f87dc-108">\<behavior></span></span>  
<span data-ttu-id="f87dc-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f87dc-109">\<clientCredentials></span></span>  
<span data-ttu-id="f87dc-110">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="f87dc-110">\<issuedToken></span></span>  
<span data-ttu-id="f87dc-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f87dc-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f87dc-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f87dc-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f87dc-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f87dc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f87dc-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f87dc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f87dc-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f87dc-115">Attributes</span></span>  
 <span data-ttu-id="f87dc-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="f87dc-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f87dc-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f87dc-117">Child Elements</span></span>  
  
|<span data-ttu-id="f87dc-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f87dc-118">Element</span></span>|<span data-ttu-id="f87dc-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f87dc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f87dc-120">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="f87dc-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="f87dc-121">Bir davranış koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="f87dc-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f87dc-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f87dc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f87dc-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f87dc-123">Element</span></span>|<span data-ttu-id="f87dc-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f87dc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f87dc-125">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="f87dc-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="f87dc-126">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="f87dc-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f87dc-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f87dc-127">Remarks</span></span>  
 <span data-ttu-id="f87dc-128">Herhangi bir zaman bu öğeyi kullanın davranışları (dahil davranışları dışında `<clientCredentials>` öğeleri) hizmet ile iletişim kurmak için kullanılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="f87dc-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="f87dc-129">Örneğin, bir [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) davranışı öğesi dahil edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f87dc-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87dc-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f87dc-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="f87dc-131">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="f87dc-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="f87dc-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="f87dc-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="f87dc-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="f87dc-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f87dc-134">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f87dc-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f87dc-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f87dc-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="f87dc-136">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f87dc-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="f87dc-137">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f87dc-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="f87dc-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="f87dc-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
