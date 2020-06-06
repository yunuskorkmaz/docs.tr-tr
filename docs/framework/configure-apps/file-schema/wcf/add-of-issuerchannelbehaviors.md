---
title: <add> / <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398327"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="a7691-102">\<add> / \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="a7691-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="a7691-103">STS ile iletişim kurulurken kullanılacak bir uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="a7691-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="a7691-104">Herhangi bir uç nokta davranışı bir [\<clientCredentials>](clientcredentials.md) öğesi içeriyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7691-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="a7691-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7691-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7691-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7691-106">Attributes and Elements</span></span>

<span data-ttu-id="a7691-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="a7691-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="a7691-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7691-108">Attributes</span></span>

|<span data-ttu-id="a7691-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7691-109">Attribute</span></span>|<span data-ttu-id="a7691-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7691-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a7691-111">IssuerAddress</span><span class="sxs-lookup"><span data-stu-id="a7691-111">issuerAddress</span></span>|<span data-ttu-id="a7691-112">İletişim kuracak güvenlik belirteci verenin URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="a7691-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="a7691-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7691-113">behaviorConfiguration</span></span>|<span data-ttu-id="a7691-114">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="a7691-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a7691-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7691-115">Child Elements</span></span>

<span data-ttu-id="a7691-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7691-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a7691-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7691-117">Parent Elements</span></span>

|<span data-ttu-id="a7691-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7691-118">Element</span></span>|<span data-ttu-id="a7691-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7691-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="a7691-120">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak bir Windows Communication Foundation (WCF) istemci uç nokta davranışı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="a7691-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7691-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7691-121">Remarks</span></span>

<span data-ttu-id="a7691-122">`issuerAddress`istemcinin iletişim kurmak istediği güvenlik belirteci hizmetinin URI 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="a7691-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="a7691-123">`behaviorConfiguration`uygulamanın, güvenlik belirteci hizmetlerinden verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallarda kullandığı bir uç nokta davranışına işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a7691-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7691-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7691-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="a7691-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a7691-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a7691-126">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a7691-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a7691-127">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a7691-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a7691-128">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a7691-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a7691-129">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a7691-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a7691-130">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7691-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a7691-131">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a7691-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a7691-132">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a7691-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
