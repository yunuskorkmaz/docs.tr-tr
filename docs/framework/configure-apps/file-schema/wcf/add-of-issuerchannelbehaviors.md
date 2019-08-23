---
title: <add> / <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920121"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="16a98-102">\<\<ıssuerchanneldavranışların > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="16a98-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="16a98-103">STS ile iletişim kurulurken kullanılacak bir uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="16a98-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="16a98-104">Herhangi bir uç nokta davranışı bir [ \<ClientCredentials >](clientcredentials.md) öğesi içeriyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="16a98-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="16a98-105">\<sistemin. ServiceModel > </span><span class="sxs-lookup"><span data-stu-id="16a98-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="16a98-106">\<davranışlar > </span><span class="sxs-lookup"><span data-stu-id="16a98-106">\<behaviors></span></span>\
<span data-ttu-id="16a98-107">EndpointBehavior bölüm \<davranışı > </span><span class="sxs-lookup"><span data-stu-id="16a98-107">endpointBehaviors section \<behavior></span></span>\
<span data-ttu-id="16a98-108">\<clientCredentials > </span><span class="sxs-lookup"><span data-stu-id="16a98-108">\<clientCredentials></span></span>\
<span data-ttu-id="16a98-109">\<IssuedToken > </span><span class="sxs-lookup"><span data-stu-id="16a98-109">\<issuedToken></span></span>\
<span data-ttu-id="16a98-110">\<ıssuerchanneldavranışlar > öğesi </span><span class="sxs-lookup"><span data-stu-id="16a98-110">\<issuerChannelBehaviors> Element</span></span>\
<span data-ttu-id="16a98-111">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="16a98-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="16a98-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16a98-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16a98-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16a98-113">Attributes and Elements</span></span>

<span data-ttu-id="16a98-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="16a98-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="16a98-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16a98-115">Attributes</span></span>

|<span data-ttu-id="16a98-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16a98-116">Attribute</span></span>|<span data-ttu-id="16a98-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16a98-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="16a98-118">IssuerAddress</span><span class="sxs-lookup"><span data-stu-id="16a98-118">issuerAddress</span></span>|<span data-ttu-id="16a98-119">İletişim kuracak güvenlik belirteci verenin URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="16a98-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="16a98-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="16a98-120">behaviorConfiguration</span></span>|<span data-ttu-id="16a98-121">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="16a98-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="16a98-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16a98-122">Child Elements</span></span>

<span data-ttu-id="16a98-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="16a98-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16a98-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16a98-124">Parent Elements</span></span>

|<span data-ttu-id="16a98-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="16a98-125">Element</span></span>|<span data-ttu-id="16a98-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16a98-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16a98-127">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="16a98-127">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="16a98-128">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak bir Windows Communication Foundation (WCF) istemci uç nokta davranışı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="16a98-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="16a98-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16a98-129">Remarks</span></span>

<span data-ttu-id="16a98-130">`issuerAddress`istemcinin iletişim kurmak istediği güvenlik belirteci hizmetinin URI 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="16a98-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="16a98-131">`behaviorConfiguration`uygulamanın, güvenlik belirteci hizmetlerinden verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallarda kullandığı bir uç nokta davranışına işaret eder.</span><span class="sxs-lookup"><span data-stu-id="16a98-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="16a98-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16a98-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="16a98-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="16a98-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="16a98-134">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="16a98-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="16a98-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="16a98-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="16a98-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="16a98-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="16a98-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="16a98-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="16a98-138">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="16a98-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="16a98-139">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="16a98-139">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="16a98-140">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="16a98-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="16a98-141">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="16a98-141">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
