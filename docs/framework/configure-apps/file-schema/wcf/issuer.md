---
title: '&lt;veren&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e034b3ed0813d621ed86c2c3e86bb901ab39e40b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="c93c9-102">&lt;veren&gt;</span><span class="sxs-lookup"><span data-stu-id="c93c9-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="c93c9-103">Güvenlik belirteci hizmeti (güvenlik belirteçleri veren STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c93c9-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="c93c9-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c93c9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c93c9-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c93c9-105">\<bindings></span></span>  
<span data-ttu-id="c93c9-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c93c9-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="c93c9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c93c9-107">\<binding></span></span>  
<span data-ttu-id="c93c9-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="c93c9-108">\<security></span></span>  
<span data-ttu-id="c93c9-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="c93c9-109">\<message></span></span>  
<span data-ttu-id="c93c9-110">\<veren ></span><span class="sxs-lookup"><span data-stu-id="c93c9-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c93c9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c93c9-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c93c9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c93c9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c93c9-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="c93c9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c93c9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c93c9-114">Attributes</span></span>  
  
|<span data-ttu-id="c93c9-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c93c9-115">Attribute</span></span>|<span data-ttu-id="c93c9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c93c9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c93c9-117">adres</span><span class="sxs-lookup"><span data-stu-id="c93c9-117">address</span></span>|<span data-ttu-id="c93c9-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="c93c9-118">Required string.</span></span> <span data-ttu-id="c93c9-119">STS URL'si.</span><span class="sxs-lookup"><span data-stu-id="c93c9-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c93c9-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c93c9-120">Child Elements</span></span>  
  
|<span data-ttu-id="c93c9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c93c9-121">Element</span></span>|<span data-ttu-id="c93c9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c93c9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c93c9-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="c93c9-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="c93c9-124">Adres üstbilgileri Oluşturucu oluşturabilirsiniz uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c93c9-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="c93c9-125">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="c93c9-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c93c9-126">Verilen bir belirteç kullanırken, sunucu kimlik doğrulaması istemci etkinleştirme ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c93c9-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c93c9-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c93c9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c93c9-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="c93c9-128">Element</span></span>|<span data-ttu-id="c93c9-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c93c9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c93c9-130">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="c93c9-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c93c9-131">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="c93c9-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c93c9-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c93c9-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="c93c9-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c93c9-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c93c9-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c93c9-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c93c9-135">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c93c9-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c93c9-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c93c9-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c93c9-137">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c93c9-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="c93c9-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c93c9-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
