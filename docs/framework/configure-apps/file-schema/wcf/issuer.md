---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 37d935287fa7dfba640c39071295fd660f4db7c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160829"
---
# <a name="issuer"></a><span data-ttu-id="eac43-101">\<veren ></span><span class="sxs-lookup"><span data-stu-id="eac43-101">\<issuer></span></span>
<span data-ttu-id="eac43-102">Güvenlik belirteci hizmeti (güvenlik belirteçlerini çıkartan STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="eac43-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="eac43-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eac43-103">\<system.serviceModel></span></span>  
<span data-ttu-id="eac43-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="eac43-104">\<bindings></span></span>  
<span data-ttu-id="eac43-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="eac43-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="eac43-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="eac43-106">\<binding></span></span>  
<span data-ttu-id="eac43-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="eac43-107">\<security></span></span>  
<span data-ttu-id="eac43-108">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="eac43-108">\<message></span></span>  
<span data-ttu-id="eac43-109">\<veren ></span><span class="sxs-lookup"><span data-stu-id="eac43-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eac43-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eac43-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eac43-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eac43-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eac43-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eac43-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eac43-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eac43-113">Attributes</span></span>  
  
|<span data-ttu-id="eac43-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eac43-114">Attribute</span></span>|<span data-ttu-id="eac43-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eac43-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eac43-116">adres</span><span class="sxs-lookup"><span data-stu-id="eac43-116">address</span></span>|<span data-ttu-id="eac43-117">Zorunlu dize.</span><span class="sxs-lookup"><span data-stu-id="eac43-117">Required string.</span></span> <span data-ttu-id="eac43-118">STS URL'si.</span><span class="sxs-lookup"><span data-stu-id="eac43-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eac43-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eac43-119">Child Elements</span></span>  
  
|<span data-ttu-id="eac43-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="eac43-120">Element</span></span>|<span data-ttu-id="eac43-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eac43-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eac43-122">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="eac43-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="eac43-123">Adres üstbilgileri Oluşturucu oluşturabilirsiniz uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="eac43-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="eac43-124">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="eac43-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="eac43-125">Verilen bir belirteç kullanırken, sunucu kimlik doğrulaması istemci etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="eac43-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eac43-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eac43-126">Parent Elements</span></span>  
  
|<span data-ttu-id="eac43-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="eac43-127">Element</span></span>|<span data-ttu-id="eac43-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eac43-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eac43-129">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="eac43-129">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="eac43-130">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="eac43-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eac43-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eac43-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="eac43-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="eac43-132">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="eac43-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="eac43-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="eac43-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="eac43-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="eac43-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="eac43-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="eac43-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="eac43-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="eac43-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="eac43-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
