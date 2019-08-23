---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: bf512c427637ca65a7271ec8300a373a38632108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913516"
---
# <a name="issuermetadata"></a><span data-ttu-id="a8947-101">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="a8947-101">\<issuerMetadata></span></span>
<span data-ttu-id="a8947-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a8947-102">\<system.serviceModel></span></span>  
<span data-ttu-id="a8947-103">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a8947-103">\<bindings></span></span>  
<span data-ttu-id="a8947-104">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a8947-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="a8947-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a8947-105">\<binding></span></span>  
<span data-ttu-id="a8947-106">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a8947-106">\<security></span></span>  
<span data-ttu-id="a8947-107">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="a8947-107">\<message></span></span>  
<span data-ttu-id="a8947-108">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="a8947-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8947-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8947-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8947-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8947-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a8947-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8947-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8947-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8947-112">Attributes</span></span>  
  
|<span data-ttu-id="a8947-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8947-113">Attribute</span></span>|<span data-ttu-id="a8947-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8947-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8947-115">adres</span><span class="sxs-lookup"><span data-stu-id="a8947-115">address</span></span>|<span data-ttu-id="a8947-116">Gerekli `string` öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a8947-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="a8947-117">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8947-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="a8947-118">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8947-118">The address must be an absolute URI.</span></span> <span data-ttu-id="a8947-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a8947-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8947-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8947-120">Child Elements</span></span>  
  
|<span data-ttu-id="a8947-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8947-121">Element</span></span>|<span data-ttu-id="a8947-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8947-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8947-123">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="a8947-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="a8947-124">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a8947-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="a8947-125">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="a8947-125">\<identity></span></span>](identity.md)|<span data-ttu-id="a8947-126">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="a8947-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8947-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8947-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a8947-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8947-128">Element</span></span>|<span data-ttu-id="a8947-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8947-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8947-130">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="a8947-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a8947-131">WSFederationHttpBinding > öğesi için [ \<](wsfederationhttpbinding.md) ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8947-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8947-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8947-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="a8947-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a8947-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a8947-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a8947-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a8947-135">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a8947-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a8947-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a8947-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
