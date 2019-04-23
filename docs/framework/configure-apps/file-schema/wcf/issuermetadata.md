---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 0dffad6a17720dd0506acbcd60efe4aafe24ed28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090114"
---
# <a name="issuermetadata"></a><span data-ttu-id="9338c-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="9338c-101">\<issuerMetadata></span></span>
<span data-ttu-id="9338c-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9338c-102">\<system.serviceModel></span></span>  
<span data-ttu-id="9338c-103">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9338c-103">\<bindings></span></span>  
<span data-ttu-id="9338c-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9338c-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="9338c-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9338c-105">\<binding></span></span>  
<span data-ttu-id="9338c-106">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9338c-106">\<security></span></span>  
<span data-ttu-id="9338c-107">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="9338c-107">\<message></span></span>  
<span data-ttu-id="9338c-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="9338c-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9338c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9338c-109">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9338c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9338c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9338c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9338c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9338c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9338c-112">Attributes</span></span>  
  
|<span data-ttu-id="9338c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9338c-113">Attribute</span></span>|<span data-ttu-id="9338c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9338c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9338c-115">adres</span><span class="sxs-lookup"><span data-stu-id="9338c-115">address</span></span>|<span data-ttu-id="9338c-116">Gerekli `string` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9338c-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="9338c-117">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9338c-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="9338c-118">Adres mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9338c-118">The address must be an absolute URI.</span></span> <span data-ttu-id="9338c-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9338c-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9338c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9338c-120">Child Elements</span></span>  
  
|<span data-ttu-id="9338c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9338c-121">Element</span></span>|<span data-ttu-id="9338c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9338c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9338c-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="9338c-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="9338c-124">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9338c-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="9338c-125">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="9338c-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9338c-126">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="9338c-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9338c-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9338c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9338c-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="9338c-128">Element</span></span>|<span data-ttu-id="9338c-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9338c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9338c-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="9338c-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="9338c-131">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="9338c-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9338c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9338c-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="9338c-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="9338c-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9338c-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9338c-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9338c-135">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="9338c-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9338c-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9338c-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
