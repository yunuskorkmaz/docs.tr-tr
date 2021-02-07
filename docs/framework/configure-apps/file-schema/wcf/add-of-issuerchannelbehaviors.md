---
description: 'Hakkında daha fazla bilgi <add> edinin: <issuerChannelBehaviors>'
title: <add> / <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: ccd8ba015b7a6837c74ce2c051a794d36ce8ceaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750305"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="2a499-103">\<add> / \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="2a499-103">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="2a499-104">STS ile iletişim kurulurken kullanılacak bir uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="2a499-104">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="2a499-105">Herhangi bir uç nokta davranışı bir [\<clientCredentials>](clientcredentials.md) öğesi içeriyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a499-105">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="2a499-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a499-106">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a499-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a499-107">Attributes and Elements</span></span>

<span data-ttu-id="2a499-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2a499-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="2a499-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a499-109">Attributes</span></span>

|<span data-ttu-id="2a499-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a499-110">Attribute</span></span>|<span data-ttu-id="2a499-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a499-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2a499-112">IssuerAddress</span><span class="sxs-lookup"><span data-stu-id="2a499-112">issuerAddress</span></span>|<span data-ttu-id="2a499-113">İletişim kuracak güvenlik belirteci verenin URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="2a499-113">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="2a499-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a499-114">behaviorConfiguration</span></span>|<span data-ttu-id="2a499-115">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="2a499-115">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2a499-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a499-116">Child Elements</span></span>

<span data-ttu-id="2a499-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a499-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a499-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a499-118">Parent Elements</span></span>

|<span data-ttu-id="2a499-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a499-119">Element</span></span>|<span data-ttu-id="2a499-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a499-120">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="2a499-121">Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak bir Windows Communication Foundation (WCF) istemci uç nokta davranışı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="2a499-121">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2a499-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a499-122">Remarks</span></span>

<span data-ttu-id="2a499-123">`issuerAddress` istemcinin iletişim kurmak istediği güvenlik belirteci hizmetinin URI 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="2a499-123">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="2a499-124">`behaviorConfiguration` uygulamanın, güvenlik belirteci hizmetlerinden verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallarda kullandığı bir uç nokta davranışına işaret eder.</span><span class="sxs-lookup"><span data-stu-id="2a499-124">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a499-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a499-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="2a499-126">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="2a499-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2a499-127">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="2a499-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2a499-128">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="2a499-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2a499-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2a499-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2a499-130">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2a499-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="2a499-131">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a499-131">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2a499-132">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2a499-132">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2a499-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="2a499-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
