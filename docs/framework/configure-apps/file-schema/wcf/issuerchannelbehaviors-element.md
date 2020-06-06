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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893152"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="43d3b-102">\<issuerChannelBehaviors> Öğesi</span><span class="sxs-lookup"><span data-stu-id="43d3b-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="43d3b-103">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak Windows Communication Foundation (WCF) istemci uç noktası davranışları (yapılandırmada tanımlanır) koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="43d3b-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="43d3b-104">Tanımlı davranışlar herhangi bir öğe içeremez [\<clientCredentials>](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="43d3b-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="43d3b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43d3b-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43d3b-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="43d3b-106">Attributes and elements</span></span>

<span data-ttu-id="43d3b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43d3b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="43d3b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43d3b-108">Attributes</span></span>

<span data-ttu-id="43d3b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="43d3b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43d3b-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="43d3b-110">Child elements</span></span>

|<span data-ttu-id="43d3b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="43d3b-111">Element</span></span>|<span data-ttu-id="43d3b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43d3b-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="43d3b-113">Koleksiyona bir davranış ekler.</span><span class="sxs-lookup"><span data-stu-id="43d3b-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="43d3b-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="43d3b-114">Parent elements</span></span>

|<span data-ttu-id="43d3b-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="43d3b-115">Element</span></span>|<span data-ttu-id="43d3b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43d3b-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="43d3b-117">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="43d3b-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43d3b-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43d3b-118">Remarks</span></span>

<span data-ttu-id="43d3b-119">`<clientCredentials>`Bir hizmet ile iletişim kurmak için herhangi bir davranış (öğeler içeren davranışlar dışında) kullanılması gereken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="43d3b-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="43d3b-120">Örneğin, bir [\<dataContractSerializer>](datacontractserializer-element.md) davranış öğesi dahil edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="43d3b-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="43d3b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43d3b-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="43d3b-122">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="43d3b-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="43d3b-123">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="43d3b-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="43d3b-124">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="43d3b-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="43d3b-125">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="43d3b-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="43d3b-126">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="43d3b-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="43d3b-127">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="43d3b-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="43d3b-128">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="43d3b-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="43d3b-129">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="43d3b-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
