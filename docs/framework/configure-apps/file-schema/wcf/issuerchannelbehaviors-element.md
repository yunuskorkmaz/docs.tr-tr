---
description: 'Daha fazla bilgi edinin: <issuerChannelBehaviors> öğesi'
title: <issuerChannelBehaviors> Öğesi
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: 6be79f2ee6afb442a7a399ce49df4ad59dff2db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725551"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="d1636-103">\::: No-Loc ( <issuerChannelBehaviors> )::: öğesi</span><span class="sxs-lookup"><span data-stu-id="d1636-103">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="d1636-104">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak Windows Communication Foundation (WCF) istemci uç noktası davranışları (yapılandırmada tanımlanır) koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d1636-104">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="d1636-105">Tanımlı davranışlar şunları içeremez [ \: :: No-Loc ( <clientCredentials> ):::](clientcredentials.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d1636-105">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
<span data-ttu-id="d1636-106">&nbsp;&nbsp;[\::: No-Loc (<System. serviceModel>):::](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d1636-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="d1636-107">&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <behaviors> ):::](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d1636-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="d1636-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <endpointBehaviors> ):::](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d1636-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="d1636-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <behavior> ):::](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d1636-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="d1636-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <clientCredentials> ):::](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d1636-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="d1636-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <issuedToken> ):::](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="d1636-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="d1636-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\::: No-Loc ( <issuerChannelBehaviors> ):::</span><span class="sxs-lookup"><span data-stu-id="d1636-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="d1636-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1636-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1636-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d1636-114">Attributes and elements</span></span>

<span data-ttu-id="d1636-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1636-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1636-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1636-116">Attributes</span></span>

<span data-ttu-id="d1636-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d1636-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1636-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d1636-118">Child elements</span></span>

|<span data-ttu-id="d1636-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1636-119">Element</span></span>|<span data-ttu-id="d1636-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1636-120">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="d1636-121">Koleksiyona bir davranış ekler.</span><span class="sxs-lookup"><span data-stu-id="d1636-121">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d1636-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d1636-122">Parent elements</span></span>

|<span data-ttu-id="d1636-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1636-123">Element</span></span>|<span data-ttu-id="d1636-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1636-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1636-125">\::: No-Loc ( <issuedToken> ):::</span><span class="sxs-lookup"><span data-stu-id="d1636-125">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="d1636-126">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1636-126">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d1636-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1636-127">Remarks</span></span>

<span data-ttu-id="d1636-128">`<clientCredentials>`Bir hizmet ile iletişim kurmak için herhangi bir davranış (öğeler içeren davranışlar dışında) kullanılması gereken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1636-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="d1636-129">Örneğin [ \: :: No-Loc ( <dataContractSerializer> ):::](datacontractserializer-element.md) Behavior öğesi dahil edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d1636-129">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1636-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1636-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="d1636-131">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="d1636-131">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d1636-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="d1636-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d1636-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d1636-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d1636-134">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d1636-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d1636-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d1636-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d1636-136">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1636-136">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d1636-137">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d1636-137">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d1636-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d1636-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
