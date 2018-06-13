---
title: '&lt;İssuedtokenparameters&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 5f6b8d2f861c4d64a3b81407de4ce13b42d9b864
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752939"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="ecbcc-102">&lt;İssuedtokenparameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ecbcc-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="ecbcc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ecbcc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ecbcc-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-104">\<bindings></span></span>  
<span data-ttu-id="ecbcc-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="ecbcc-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-106">\<binding></span></span>  
<span data-ttu-id="ecbcc-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-107">\<security></span></span>  
<span data-ttu-id="ecbcc-108">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-108">\<message></span></span>  
<span data-ttu-id="ecbcc-109">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbcc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecbcc-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address=String" >  
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
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecbcc-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecbcc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ecbcc-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecbcc-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ecbcc-113">Attributes</span></span>  
  
|<span data-ttu-id="ecbcc-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ecbcc-114">Attribute</span></span>|<span data-ttu-id="ecbcc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecbcc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecbcc-116">adres</span><span class="sxs-lookup"><span data-stu-id="ecbcc-116">address</span></span>|<span data-ttu-id="ecbcc-117">Gerekli `string` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="ecbcc-118">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="ecbcc-119">Adres bir mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-119">The address must be an absolute URI.</span></span> <span data-ttu-id="ecbcc-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecbcc-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecbcc-121">Child Elements</span></span>  
  
|<span data-ttu-id="ecbcc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecbcc-122">Element</span></span>|<span data-ttu-id="ecbcc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecbcc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecbcc-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="ecbcc-125">Adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ecbcc-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ecbcc-127">Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecbcc-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecbcc-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ecbcc-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecbcc-129">Element</span></span>|<span data-ttu-id="ecbcc-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecbcc-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecbcc-131">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="ecbcc-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="ecbcc-132">İleti düzeyi güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecbcc-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecbcc-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="ecbcc-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ecbcc-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="ecbcc-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ecbcc-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="ecbcc-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ecbcc-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="ecbcc-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ecbcc-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
