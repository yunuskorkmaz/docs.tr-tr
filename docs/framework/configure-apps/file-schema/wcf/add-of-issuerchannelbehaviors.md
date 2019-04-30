---
title: <add> / <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673621"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="a3ec1-102">\<Ekle >, \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a3ec1-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="a3ec1-103">Bir STS ile iletişim kurarken kullanılacak uç nokta davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="a3ec1-104">Herhangi bir uç nokta davranışı içeriyorsa bir [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="a3ec1-105">\<sistemi. ServiceModel > \\</span><span class="sxs-lookup"><span data-stu-id="a3ec1-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="a3ec1-106">\<davranışlar > \\</span><span class="sxs-lookup"><span data-stu-id="a3ec1-106">\<behaviors>\\</span></span>
<span data-ttu-id="a3ec1-107">endpointBehaviors bölümü \<davranışı > \\</span><span class="sxs-lookup"><span data-stu-id="a3ec1-107">endpointBehaviors section \<behavior>\\</span></span>
<span data-ttu-id="a3ec1-108">\<clientCredentials > \\</span><span class="sxs-lookup"><span data-stu-id="a3ec1-108">\<clientCredentials>\\</span></span>
<span data-ttu-id="a3ec1-109">\<IssuedToken > \\</span><span class="sxs-lookup"><span data-stu-id="a3ec1-109">\<issuedToken>\\</span></span>
<span data-ttu-id="a3ec1-110">\<issuerChannelBehaviors > Element\\</span><span class="sxs-lookup"><span data-stu-id="a3ec1-110">\<issuerChannelBehaviors> Element\\</span></span>
<span data-ttu-id="a3ec1-111">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="a3ec1-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="a3ec1-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3ec1-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3ec1-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3ec1-113">Attributes and Elements</span></span>

<span data-ttu-id="a3ec1-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="a3ec1-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3ec1-115">Attributes</span></span>

|<span data-ttu-id="a3ec1-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a3ec1-116">Attribute</span></span>|<span data-ttu-id="a3ec1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3ec1-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a3ec1-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="a3ec1-118">issuerAddress</span></span>|<span data-ttu-id="a3ec1-119">İle iletişim kurmak için güvenlik belirteci vericisinin URI.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="a3ec1-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3ec1-120">behaviorConfiguration</span></span>|<span data-ttu-id="a3ec1-121">Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a3ec1-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3ec1-122">Child Elements</span></span>

<span data-ttu-id="a3ec1-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a3ec1-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3ec1-124">Parent Elements</span></span>

|<span data-ttu-id="a3ec1-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3ec1-125">Element</span></span>|<span data-ttu-id="a3ec1-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3ec1-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3ec1-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="a3ec1-127">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="a3ec1-128">Windows Communication Foundation (WCF) hizmeti belirtilen belirteci Hizmetleri ile iletişim kurarken kullanılacak uç nokta davranışları istemci koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3ec1-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3ec1-129">Remarks</span></span>

<span data-ttu-id="a3ec1-130">`issuerAddress` istemci ile iletişim kurmak istediği güvenlik belirteci hizmeti URI'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="a3ec1-131">`behaviorConfiguration` Güvenlik belirteci hizmetlerine verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallar uygulamanın kullandığı bir uç nokta davranışı işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3ec1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3ec1-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="a3ec1-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a3ec1-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a3ec1-134">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a3ec1-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a3ec1-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a3ec1-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a3ec1-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a3ec1-136">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a3ec1-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a3ec1-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="a3ec1-138">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3ec1-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a3ec1-139">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a3ec1-139">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a3ec1-140">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a3ec1-140">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a3ec1-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="a3ec1-141">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
