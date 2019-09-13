---
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
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893152"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="5a044-102">\<ıssuerchanneldavranışlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="5a044-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="5a044-103">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak Windows Communication Foundation (WCF) istemci uç noktası davranışları (yapılandırmada tanımlanır) koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5a044-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="5a044-104">Tanımlı davranışlar herhangi bir [ \<ClientCredentials >](clientcredentials.md) öğesi içeremez.</span><span class="sxs-lookup"><span data-stu-id="5a044-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="5a044-105">[\<Yapılandırma >](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-105">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="5a044-106">&nbsp;&nbsp;[\<System. serviceModel >](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a044-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<davranışlar >](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="5a044-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Endpointdavranışlar >](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5a044-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<davranış >](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5a044-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials >](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="5a044-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<IssuedToken >](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="5a044-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="5a044-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="5a044-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="5a044-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a044-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a044-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5a044-114">Attributes and elements</span></span>

<span data-ttu-id="5a044-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a044-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a044-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a044-116">Attributes</span></span>

<span data-ttu-id="5a044-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="5a044-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a044-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5a044-118">Child elements</span></span>

|<span data-ttu-id="5a044-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a044-119">Element</span></span>|<span data-ttu-id="5a044-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a044-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a044-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="5a044-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="5a044-122">Koleksiyona bir davranış ekler.</span><span class="sxs-lookup"><span data-stu-id="5a044-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5a044-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5a044-123">Parent elements</span></span>

|<span data-ttu-id="5a044-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a044-124">Element</span></span>|<span data-ttu-id="5a044-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a044-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a044-126">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="5a044-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="5a044-127">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a044-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5a044-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a044-128">Remarks</span></span>

<span data-ttu-id="5a044-129">Bir hizmet ile iletişim kurmak için herhangi bir davranış ( `<clientCredentials>` öğeler içeren davranışlar dışında) kullanılması gereken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a044-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="5a044-130">Örneğin, bir [ \<DataContractSerializer >](datacontractserializer-element.md) Behavior öğesi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="5a044-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a044-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a044-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="5a044-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="5a044-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5a044-133">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="5a044-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5a044-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="5a044-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5a044-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5a044-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5a044-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5a044-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5a044-137">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a044-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="5a044-138">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a044-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="5a044-139">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="5a044-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
