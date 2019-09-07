---
title: <issuerChannelBehaviors> Öğesi
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 2c0e0d8d041565edd25c4b2c2802bfd2a589b4f7
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397896"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="a64fb-102">\<ıssuerchanneldavranışlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="a64fb-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="a64fb-103">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak Windows Communication Foundation (WCF) istemci uç noktası davranışları (yapılandırmada tanımlanır) koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a64fb-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="a64fb-104">Tanımlı davranışlar herhangi bir [ \<ClientCredentials >](clientcredentials.md) öğesi içeremez.</span><span class="sxs-lookup"><span data-stu-id="a64fb-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="a64fb-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a64fb-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a64fb-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a64fb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a64fb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a64fb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="a64fb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="a64fb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="a64fb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ıssuerchanneldavranışlar >**</span><span class="sxs-lookup"><span data-stu-id="a64fb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerChannelBehaviors>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a64fb-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a64fb-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a64fb-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a64fb-114">Attributes and Elements</span></span>

<span data-ttu-id="a64fb-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a64fb-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a64fb-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a64fb-116">Attributes</span></span>

<span data-ttu-id="a64fb-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="a64fb-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a64fb-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a64fb-118">Child Elements</span></span>

|<span data-ttu-id="a64fb-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a64fb-119">Element</span></span>|<span data-ttu-id="a64fb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a64fb-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a64fb-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="a64fb-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="a64fb-122">Koleksiyona bir davranış ekler.</span><span class="sxs-lookup"><span data-stu-id="a64fb-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a64fb-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a64fb-123">Parent Elements</span></span>

|<span data-ttu-id="a64fb-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a64fb-124">Element</span></span>|<span data-ttu-id="a64fb-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a64fb-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a64fb-126">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="a64fb-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="a64fb-127">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="a64fb-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a64fb-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a64fb-128">Remarks</span></span>

<span data-ttu-id="a64fb-129">Bir hizmet ile iletişim kurmak için herhangi bir davranış ( `<clientCredentials>` öğeler içeren davranışlar dışında) kullanılması gereken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a64fb-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="a64fb-130">Örneğin, bir [ \<DataContractSerializer >](datacontractserializer-element.md) Behavior öğesi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a64fb-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="a64fb-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a64fb-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="a64fb-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a64fb-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a64fb-133">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a64fb-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a64fb-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a64fb-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a64fb-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a64fb-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a64fb-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a64fb-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a64fb-137">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="a64fb-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a64fb-138">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a64fb-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a64fb-139">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a64fb-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
