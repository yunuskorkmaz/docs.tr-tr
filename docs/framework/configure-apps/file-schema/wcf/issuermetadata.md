---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397888"
---
# <a name="issuermetadata"></a><span data-ttu-id="3322a-101">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="3322a-101">\<issuerMetadata></span></span>

<span data-ttu-id="3322a-102">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3322a-102">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3322a-103">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3322a-103">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3322a-104">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3322a-104">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3322a-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3322a-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3322a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="3322a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3322a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3322a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3322a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ileti >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3322a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3322a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="3322a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3322a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3322a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3322a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3322a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3322a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3322a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3322a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3322a-113">Attributes</span></span>  
  
|<span data-ttu-id="3322a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3322a-114">Attribute</span></span>|<span data-ttu-id="3322a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3322a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3322a-116">adres</span><span class="sxs-lookup"><span data-stu-id="3322a-116">address</span></span>|<span data-ttu-id="3322a-117">Gerekli `string` öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3322a-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="3322a-118">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3322a-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="3322a-119">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3322a-119">The address must be an absolute URI.</span></span> <span data-ttu-id="3322a-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="3322a-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3322a-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3322a-121">Child Elements</span></span>  
  
|<span data-ttu-id="3322a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="3322a-122">Element</span></span>|<span data-ttu-id="3322a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3322a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3322a-124">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="3322a-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="3322a-125">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3322a-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="3322a-126">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="3322a-126">\<identity></span></span>](identity.md)|<span data-ttu-id="3322a-127">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="3322a-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3322a-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3322a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3322a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="3322a-129">Element</span></span>|<span data-ttu-id="3322a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3322a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3322a-131">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="3322a-131">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="3322a-132">WSFederationHttpBinding > öğesi için [ \<](wsfederationhttpbinding.md) ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3322a-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3322a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3322a-133">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="3322a-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="3322a-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3322a-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="3322a-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3322a-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3322a-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3322a-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="3322a-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
