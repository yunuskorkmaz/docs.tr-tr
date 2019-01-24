---
title: '&lt;issuerChannelBehaviors&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: b77d0ce79557dff4b5a243da4d24703ed45fde07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677114"
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="6b469-102">&lt;issuerChannelBehaviors&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="6b469-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="6b469-103">Belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak Windows Communication Foundation (WCF) istemci uç nokta davranışları (yapılandırmasında tanımlı) bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6b469-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="6b469-104">Tanımlı davranışları herhangi içeremez [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6b469-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="6b469-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b469-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b469-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6b469-106">\<behaviors></span></span>  
<span data-ttu-id="6b469-107">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="6b469-107">endpointBehaviors section</span></span>  
<span data-ttu-id="6b469-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6b469-108">\<behavior></span></span>  
<span data-ttu-id="6b469-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="6b469-109">\<clientCredentials></span></span>  
<span data-ttu-id="6b469-110">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="6b469-110">\<issuedToken></span></span>  
<span data-ttu-id="6b469-111">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="6b469-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b469-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b469-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>
  <add behaviorConfiguraton="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b469-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b469-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6b469-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b469-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b469-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b469-115">Attributes</span></span>  
 <span data-ttu-id="6b469-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b469-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b469-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b469-117">Child Elements</span></span>  
  
|<span data-ttu-id="6b469-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b469-118">Element</span></span>|<span data-ttu-id="6b469-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b469-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b469-120">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="6b469-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="6b469-121">Bir davranış koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="6b469-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b469-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b469-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6b469-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b469-123">Element</span></span>|<span data-ttu-id="6b469-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b469-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b469-125">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="6b469-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="6b469-126">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b469-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b469-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b469-127">Remarks</span></span>  
 <span data-ttu-id="6b469-128">Bu herhangi bir öğesinin kullanımına davranışları (içeren davranışlar dışında `<clientCredentials>` öğeleri) bir hizmetle iletişim kurmak için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b469-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="6b469-129">Örneğin, bir [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) davranış öğesi dahil edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b469-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b469-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b469-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="6b469-131">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="6b469-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6b469-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="6b469-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6b469-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="6b469-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6b469-134">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6b469-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6b469-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6b469-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="6b469-136">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b469-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="6b469-137">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6b469-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="6b469-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="6b469-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
