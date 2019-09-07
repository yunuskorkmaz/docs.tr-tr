---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397913"
---
# <a name="issuer"></a><span data-ttu-id="bb6ea-101">\<veren ></span><span class="sxs-lookup"><span data-stu-id="bb6ea-101">\<issuer></span></span>
<span data-ttu-id="bb6ea-102">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="bb6ea-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb6ea-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bb6ea-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bb6ea-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bb6ea-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bb6ea-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bb6ea-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="bb6ea-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="bb6ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="bb6ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bb6ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="bb6ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="bb6ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ileti >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="bb6ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="bb6ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<veren >**</span><span class="sxs-lookup"><span data-stu-id="bb6ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6ea-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb6ea-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
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
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb6ea-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bb6ea-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="bb6ea-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb6ea-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-114">Attributes</span></span>  
  
|<span data-ttu-id="bb6ea-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bb6ea-115">Attribute</span></span>|<span data-ttu-id="bb6ea-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6ea-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb6ea-117">adres</span><span class="sxs-lookup"><span data-stu-id="bb6ea-117">address</span></span>|<span data-ttu-id="bb6ea-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-118">Required string.</span></span> <span data-ttu-id="bb6ea-119">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb6ea-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-120">Child Elements</span></span>  
  
|<span data-ttu-id="bb6ea-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb6ea-121">Element</span></span>|<span data-ttu-id="bb6ea-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6ea-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb6ea-123">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="bb6ea-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="bb6ea-124">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="bb6ea-125">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="bb6ea-125">\<identity></span></span>](identity.md)|<span data-ttu-id="bb6ea-126">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb6ea-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bb6ea-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb6ea-128">Element</span></span>|<span data-ttu-id="bb6ea-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6ea-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb6ea-130">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="bb6ea-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="bb6ea-131">WSFederationHttpBinding > öğesi için [ \<](wsfederationhttpbinding.md) ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb6ea-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb6ea-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="bb6ea-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="bb6ea-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bb6ea-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bb6ea-135">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="bb6ea-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bb6ea-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bb6ea-137">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="bb6ea-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="bb6ea-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="bb6ea-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
