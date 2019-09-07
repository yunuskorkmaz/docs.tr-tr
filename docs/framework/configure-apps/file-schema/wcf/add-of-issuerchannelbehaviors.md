---
title: <add> / <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398327"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="e3024-102">\<\<ıssuerchanneldavranışların > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="e3024-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="e3024-103">STS ile iletişim kurulurken kullanılacak bir uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="e3024-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="e3024-104">Herhangi bir uç nokta davranışı bir [ \<ClientCredentials >](clientcredentials.md) öğesi içeriyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e3024-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="e3024-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3024-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e3024-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e3024-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e3024-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e3024-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="e3024-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="e3024-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ıssuerchanneldavranışlar >** ](issuerchannelbehaviors-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3024-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)</span></span>\
<span data-ttu-id="e3024-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="e3024-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="e3024-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3024-114">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3024-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3024-115">Attributes and Elements</span></span>

<span data-ttu-id="e3024-116">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="e3024-116">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="e3024-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3024-117">Attributes</span></span>

|<span data-ttu-id="e3024-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3024-118">Attribute</span></span>|<span data-ttu-id="e3024-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3024-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e3024-120">IssuerAddress</span><span class="sxs-lookup"><span data-stu-id="e3024-120">issuerAddress</span></span>|<span data-ttu-id="e3024-121">İletişim kuracak güvenlik belirteci verenin URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="e3024-121">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="e3024-122">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e3024-122">behaviorConfiguration</span></span>|<span data-ttu-id="e3024-123">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="e3024-123">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e3024-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3024-124">Child Elements</span></span>

<span data-ttu-id="e3024-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3024-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3024-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3024-126">Parent Elements</span></span>

|<span data-ttu-id="e3024-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3024-127">Element</span></span>|<span data-ttu-id="e3024-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3024-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3024-129">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="e3024-129">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="e3024-130">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak bir Windows Communication Foundation (WCF) istemci uç nokta davranışı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="e3024-130">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3024-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3024-131">Remarks</span></span>

<span data-ttu-id="e3024-132">`issuerAddress`istemcinin iletişim kurmak istediği güvenlik belirteci hizmetinin URI 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="e3024-132">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="e3024-133">`behaviorConfiguration`uygulamanın, güvenlik belirteci hizmetlerinden verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallarda kullandığı bir uç nokta davranışına işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e3024-133">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3024-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3024-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="e3024-135">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="e3024-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e3024-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="e3024-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e3024-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="e3024-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e3024-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e3024-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e3024-139">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e3024-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e3024-140">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3024-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e3024-141">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3024-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="e3024-142">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="e3024-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e3024-143">\<ıssuerchanneldavranışlar ></span><span class="sxs-lookup"><span data-stu-id="e3024-143">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
