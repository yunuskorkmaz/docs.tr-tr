---
title: <issuerChannelBehaviors> Öğe
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7cbd50daa82b0ca937a1bba93786545898b03c8b
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890481"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="82a00-102">\<issuerChannelBehaviors > öğesi</span><span class="sxs-lookup"><span data-stu-id="82a00-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="82a00-103">Belirtilen hizmet belirteci Hizmetleri ile iletişim kurarken kullanılacak Windows Communication Foundation (WCF) istemci uç nokta davranışları (yapılandırmasında tanımlı) bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="82a00-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="82a00-104">Tanımlı davranışları herhangi içeremez [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="82a00-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="82a00-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82a00-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82a00-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82a00-106">Attributes and Elements</span></span>

<span data-ttu-id="82a00-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82a00-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="82a00-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82a00-108">Attributes</span></span>

<span data-ttu-id="82a00-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="82a00-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82a00-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82a00-110">Child Elements</span></span>

|<span data-ttu-id="82a00-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="82a00-111">Element</span></span>|<span data-ttu-id="82a00-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82a00-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82a00-113">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="82a00-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="82a00-114">Bir davranış koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="82a00-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="82a00-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82a00-115">Parent Elements</span></span>

|<span data-ttu-id="82a00-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="82a00-116">Element</span></span>|<span data-ttu-id="82a00-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82a00-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82a00-118">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="82a00-118">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="82a00-119">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="82a00-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82a00-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82a00-120">Remarks</span></span>

<span data-ttu-id="82a00-121">Bu herhangi bir öğesinin kullanımına davranışları (içeren davranışlar dışında `<clientCredentials>` öğeleri) bir hizmetle iletişim kurmak için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a00-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="82a00-122">Örneğin, bir [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) davranış öğesi dahil edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a00-122">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="82a00-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82a00-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="82a00-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="82a00-124">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="82a00-125">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="82a00-125">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="82a00-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="82a00-126">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="82a00-127">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="82a00-127">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="82a00-128">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="82a00-128">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="82a00-129">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="82a00-129">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="82a00-130">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82a00-130">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="82a00-131">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="82a00-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
