---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 0dffad6a17720dd0506acbcd60efe4aafe24ed28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761682"
---
# <a name="issuermetadata"></a><span data-ttu-id="0c258-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="0c258-101">\<issuerMetadata></span></span>
<span data-ttu-id="0c258-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0c258-102">\<system.serviceModel></span></span>  
<span data-ttu-id="0c258-103">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0c258-103">\<bindings></span></span>  
<span data-ttu-id="0c258-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c258-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="0c258-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0c258-105">\<binding></span></span>  
<span data-ttu-id="0c258-106">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0c258-106">\<security></span></span>  
<span data-ttu-id="0c258-107">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="0c258-107">\<message></span></span>  
<span data-ttu-id="0c258-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="0c258-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c258-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c258-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c258-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c258-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c258-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c258-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c258-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c258-112">Attributes</span></span>  
  
|<span data-ttu-id="0c258-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c258-113">Attribute</span></span>|<span data-ttu-id="0c258-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c258-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c258-115">adres</span><span class="sxs-lookup"><span data-stu-id="0c258-115">address</span></span>|<span data-ttu-id="0c258-116">Gerekli `string` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0c258-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="0c258-117">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c258-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="0c258-118">Adres mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c258-118">The address must be an absolute URI.</span></span> <span data-ttu-id="0c258-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="0c258-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c258-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c258-120">Child Elements</span></span>  
  
|<span data-ttu-id="0c258-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c258-121">Element</span></span>|<span data-ttu-id="0c258-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c258-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c258-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="0c258-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="0c258-124">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0c258-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="0c258-125">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="0c258-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="0c258-126">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="0c258-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c258-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c258-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0c258-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c258-128">Element</span></span>|<span data-ttu-id="0c258-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c258-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c258-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="0c258-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="0c258-131">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="0c258-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c258-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c258-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="0c258-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="0c258-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0c258-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0c258-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0c258-135">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="0c258-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0c258-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0c258-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
