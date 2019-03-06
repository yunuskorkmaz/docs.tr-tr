---
title: <add> , <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377761"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="dbd96-102">\<Ekle >, \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dbd96-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="dbd96-103">Bir STS ile iletişim kurarken kullanılacak uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="dbd96-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="dbd96-104">Herhangi bir uç nokta davranışı içeriyorsa bir [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dbd96-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="dbd96-105">\<sistemi. ServiceModel > \\</span><span class="sxs-lookup"><span data-stu-id="dbd96-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="dbd96-106">\<davranışlar > \\</span><span class="sxs-lookup"><span data-stu-id="dbd96-106">\<behaviors>\\</span></span>
<span data-ttu-id="dbd96-107">endpointBehaviors bölümü \<davranışı > \\</span><span class="sxs-lookup"><span data-stu-id="dbd96-107">endpointBehaviors section \<behavior>\\</span></span>
<span data-ttu-id="dbd96-108">\<clientCredentials > \\</span><span class="sxs-lookup"><span data-stu-id="dbd96-108">\<clientCredentials>\\</span></span>
<span data-ttu-id="dbd96-109">\<IssuedToken > \\</span><span class="sxs-lookup"><span data-stu-id="dbd96-109">\<issuedToken>\\</span></span>
<span data-ttu-id="dbd96-110">\<issuerChannelBehaviors > Element\\</span><span class="sxs-lookup"><span data-stu-id="dbd96-110">\<issuerChannelBehaviors> Element\\</span></span>
<span data-ttu-id="dbd96-111">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="dbd96-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="dbd96-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbd96-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbd96-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbd96-113">Attributes and Elements</span></span>

<span data-ttu-id="dbd96-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbd96-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="dbd96-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbd96-115">Attributes</span></span>

|<span data-ttu-id="dbd96-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbd96-116">Attribute</span></span>|<span data-ttu-id="dbd96-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbd96-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="dbd96-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="dbd96-118">issuerAddress</span></span>|<span data-ttu-id="dbd96-119">İle iletişim kurmak için güvenlik belirteci vericisinin URI.</span><span class="sxs-lookup"><span data-stu-id="dbd96-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="dbd96-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="dbd96-120">behaviorConfiguration</span></span>|<span data-ttu-id="dbd96-121">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="dbd96-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="dbd96-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbd96-122">Child Elements</span></span>

<span data-ttu-id="dbd96-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbd96-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbd96-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbd96-124">Parent Elements</span></span>

|<span data-ttu-id="dbd96-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbd96-125">Element</span></span>|<span data-ttu-id="dbd96-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbd96-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbd96-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="dbd96-127">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="dbd96-128">Windows Communication Foundation (WCF) hizmeti belirtilen belirteci Hizmetleri ile iletişim kurarken kullanılacak uç nokta davranışları istemci koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="dbd96-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dbd96-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbd96-129">Remarks</span></span>

<span data-ttu-id="dbd96-130">`issuerAddress` istemci ile iletişim kurmak istediği güvenlik belirteci hizmeti URI'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="dbd96-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="dbd96-131">`behaviorConfiguration` Güvenlik belirteci hizmetlerine verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallar uygulamanın kullandığı bir uç nokta davranışı işaret eder.</span><span class="sxs-lookup"><span data-stu-id="dbd96-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbd96-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbd96-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="dbd96-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="dbd96-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="dbd96-134">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="dbd96-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dbd96-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="dbd96-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dbd96-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dbd96-136">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dbd96-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dbd96-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="dbd96-138">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbd96-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="dbd96-139">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dbd96-139">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="dbd96-140">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="dbd96-140">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dbd96-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="dbd96-141">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
