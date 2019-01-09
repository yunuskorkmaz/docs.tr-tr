---
title: '&lt;İssuedtokenparameters&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 38fa373212464a7dc919c2f364524a391db17d43
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149364"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="827d1-102">&lt;İssuedtokenparameters&gt;</span><span class="sxs-lookup"><span data-stu-id="827d1-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="827d1-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="827d1-103">\<system.serviceModel></span></span>  
<span data-ttu-id="827d1-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="827d1-104">\<bindings></span></span>  
<span data-ttu-id="827d1-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="827d1-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="827d1-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="827d1-106">\<binding></span></span>  
<span data-ttu-id="827d1-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="827d1-107">\<security></span></span>  
<span data-ttu-id="827d1-108">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="827d1-108">\<message></span></span>  
<span data-ttu-id="827d1-109">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="827d1-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="827d1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="827d1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="827d1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="827d1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="827d1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="827d1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="827d1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="827d1-113">Attributes</span></span>  
  
|<span data-ttu-id="827d1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="827d1-114">Attribute</span></span>|<span data-ttu-id="827d1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="827d1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="827d1-116">adres</span><span class="sxs-lookup"><span data-stu-id="827d1-116">address</span></span>|<span data-ttu-id="827d1-117">Gerekli `string` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="827d1-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="827d1-118">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="827d1-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="827d1-119">Adres mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="827d1-119">The address must be an absolute URI.</span></span> <span data-ttu-id="827d1-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="827d1-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="827d1-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="827d1-121">Child Elements</span></span>  
  
|<span data-ttu-id="827d1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="827d1-122">Element</span></span>|<span data-ttu-id="827d1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="827d1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="827d1-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="827d1-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="827d1-125">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="827d1-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="827d1-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="827d1-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="827d1-127">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="827d1-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="827d1-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="827d1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="827d1-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="827d1-129">Element</span></span>|<span data-ttu-id="827d1-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="827d1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="827d1-131">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="827d1-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="827d1-132">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="827d1-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="827d1-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="827d1-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="827d1-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="827d1-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="827d1-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="827d1-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="827d1-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="827d1-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="827d1-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="827d1-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
