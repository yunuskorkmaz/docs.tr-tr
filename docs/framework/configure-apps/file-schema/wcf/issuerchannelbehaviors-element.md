---
title: <issuerChannelBehaviors> Öğesi
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929935"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="cc7ea-102">\<ıssuerchanneldavranışlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="cc7ea-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="cc7ea-103">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak Windows Communication Foundation (WCF) istemci uç noktası davranışları (yapılandırmada tanımlanır) koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="cc7ea-104">Tanımlı davranışlar herhangi bir [ \<ClientCredentials >](clientcredentials.md) öğesi içeremez.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="cc7ea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc7ea-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc7ea-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc7ea-106">Attributes and Elements</span></span>

<span data-ttu-id="cc7ea-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc7ea-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc7ea-108">Attributes</span></span>

<span data-ttu-id="cc7ea-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc7ea-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc7ea-110">Child Elements</span></span>

|<span data-ttu-id="cc7ea-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc7ea-111">Element</span></span>|<span data-ttu-id="cc7ea-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc7ea-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc7ea-113">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="cc7ea-113">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="cc7ea-114">Koleksiyona bir davranış ekler.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc7ea-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc7ea-115">Parent Elements</span></span>

|<span data-ttu-id="cc7ea-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc7ea-116">Element</span></span>|<span data-ttu-id="cc7ea-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc7ea-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc7ea-118">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="cc7ea-118">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="cc7ea-119">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc7ea-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc7ea-120">Remarks</span></span>

<span data-ttu-id="cc7ea-121">Bir hizmet ile iletişim kurmak için herhangi bir davranış ( `<clientCredentials>` öğeler içeren davranışlar dışında) kullanılması gereken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="cc7ea-122">Örneğin, bir [ \<DataContractSerializer >](datacontractserializer-element.md) Behavior öğesi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-122">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc7ea-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc7ea-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="cc7ea-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="cc7ea-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cc7ea-125">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="cc7ea-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="cc7ea-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="cc7ea-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="cc7ea-127">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cc7ea-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cc7ea-128">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cc7ea-128">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="cc7ea-129">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc7ea-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="cc7ea-130">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc7ea-130">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="cc7ea-131">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="cc7ea-131">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
