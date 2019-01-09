---
title: '&lt;Veren&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: d2728bf3613b41ed9f0810207d27d6d67477afd2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149559"
---
# <a name="ltissuergt"></a><span data-ttu-id="4f454-102">&lt;Veren&gt;</span><span class="sxs-lookup"><span data-stu-id="4f454-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="4f454-103">Güvenlik belirteci hizmeti (güvenlik belirteçlerini çıkartan STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f454-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="4f454-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4f454-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4f454-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4f454-105">\<bindings></span></span>  
<span data-ttu-id="4f454-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="4f454-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="4f454-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4f454-107">\<binding></span></span>  
<span data-ttu-id="4f454-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4f454-108">\<security></span></span>  
<span data-ttu-id="4f454-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="4f454-109">\<message></span></span>  
<span data-ttu-id="4f454-110">\<veren ></span><span class="sxs-lookup"><span data-stu-id="4f454-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f454-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f454-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f454-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f454-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f454-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f454-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f454-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f454-114">Attributes</span></span>  
  
|<span data-ttu-id="4f454-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4f454-115">Attribute</span></span>|<span data-ttu-id="4f454-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f454-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f454-117">adres</span><span class="sxs-lookup"><span data-stu-id="4f454-117">address</span></span>|<span data-ttu-id="4f454-118">Zorunlu dize.</span><span class="sxs-lookup"><span data-stu-id="4f454-118">Required string.</span></span> <span data-ttu-id="4f454-119">STS URL'si.</span><span class="sxs-lookup"><span data-stu-id="4f454-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f454-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f454-120">Child Elements</span></span>  
  
|<span data-ttu-id="4f454-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f454-121">Element</span></span>|<span data-ttu-id="4f454-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f454-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f454-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="4f454-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="4f454-124">Adres üstbilgileri Oluşturucu oluşturabilirsiniz uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="4f454-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="4f454-125">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="4f454-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4f454-126">Verilen bir belirteç kullanırken, sunucu kimlik doğrulaması istemci etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f454-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f454-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f454-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4f454-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f454-128">Element</span></span>|<span data-ttu-id="4f454-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f454-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f454-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="4f454-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="4f454-131">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f454-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f454-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f454-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="4f454-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="4f454-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="4f454-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4f454-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="4f454-135">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="4f454-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="4f454-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4f454-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="4f454-137">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4f454-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="4f454-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4f454-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
