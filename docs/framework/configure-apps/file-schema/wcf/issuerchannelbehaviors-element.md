---
title: <issuerChannelBehaviors> Öğesi
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 3386a287d577681b67bd3ad54a75b0276e29da1f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357254"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="c4c75-102">\<issuerChannelBehaviors > öğesi</span><span class="sxs-lookup"><span data-stu-id="c4c75-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="c4c75-103">Belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak Windows Communication Foundation (WCF) istemci uç nokta davranışları (yapılandırmasında tanımlı) bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c4c75-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="c4c75-104">Tanımlı davranışları herhangi içeremez [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c4c75-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>

<span data-ttu-id="c4c75-105">\<sistemi. ServiceModel > \\</span><span class="sxs-lookup"><span data-stu-id="c4c75-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="c4c75-106">\<davranışlar > \\</span><span class="sxs-lookup"><span data-stu-id="c4c75-106">\<behaviors>\\</span></span>
<span data-ttu-id="c4c75-107">endpointBehaviors section\\</span><span class="sxs-lookup"><span data-stu-id="c4c75-107">endpointBehaviors section\\</span></span>
<span data-ttu-id="c4c75-108">\<davranış > \\</span><span class="sxs-lookup"><span data-stu-id="c4c75-108">\<behavior>\\</span></span>
<span data-ttu-id="c4c75-109">\<clientCredentials > \\</span><span class="sxs-lookup"><span data-stu-id="c4c75-109">\<clientCredentials>\\</span></span>
<span data-ttu-id="c4c75-110">\<IssuedToken > \\</span><span class="sxs-lookup"><span data-stu-id="c4c75-110">\<issuedToken>\\</span></span>
<span data-ttu-id="c4c75-111">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="c4c75-111">\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="c4c75-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4c75-112">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4c75-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4c75-113">Attributes and Elements</span></span>

<span data-ttu-id="c4c75-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4c75-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4c75-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4c75-115">Attributes</span></span>

<span data-ttu-id="c4c75-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4c75-116">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4c75-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4c75-117">Child Elements</span></span>

|<span data-ttu-id="c4c75-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4c75-118">Element</span></span>|<span data-ttu-id="c4c75-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c75-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4c75-120">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="c4c75-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="c4c75-121">Bir davranış koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="c4c75-121">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4c75-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4c75-122">Parent Elements</span></span>

|<span data-ttu-id="c4c75-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4c75-123">Element</span></span>|<span data-ttu-id="c4c75-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c75-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4c75-125">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="c4c75-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="c4c75-126">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4c75-126">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4c75-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4c75-127">Remarks</span></span>

<span data-ttu-id="c4c75-128">Bu herhangi bir öğesinin kullanımına davranışları (içeren davranışlar dışında `<clientCredentials>` öğeleri) bir hizmetle iletişim kurmak için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4c75-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="c4c75-129">Örneğin, bir [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) davranış öğesi dahil edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4c75-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c75-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4c75-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="c4c75-131">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c4c75-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c4c75-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c4c75-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c4c75-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c4c75-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c4c75-134">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c4c75-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c4c75-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c4c75-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="c4c75-136">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4c75-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c4c75-137">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4c75-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="c4c75-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c4c75-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
