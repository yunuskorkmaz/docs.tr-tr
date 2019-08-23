---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929369"
---
# <a name="issuer"></a><span data-ttu-id="32750-101">\<veren ></span><span class="sxs-lookup"><span data-stu-id="32750-101">\<issuer></span></span>
<span data-ttu-id="32750-102">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="32750-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="32750-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32750-103">\<system.serviceModel></span></span>  
<span data-ttu-id="32750-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="32750-104">\<bindings></span></span>  
<span data-ttu-id="32750-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="32750-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="32750-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="32750-106">\<binding></span></span>  
<span data-ttu-id="32750-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="32750-107">\<security></span></span>  
<span data-ttu-id="32750-108">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="32750-108">\<message></span></span>  
<span data-ttu-id="32750-109">\<veren ></span><span class="sxs-lookup"><span data-stu-id="32750-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32750-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32750-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32750-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32750-111">Attributes and Elements</span></span>  
 <span data-ttu-id="32750-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="32750-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32750-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32750-113">Attributes</span></span>  
  
|<span data-ttu-id="32750-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="32750-114">Attribute</span></span>|<span data-ttu-id="32750-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32750-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32750-116">adres</span><span class="sxs-lookup"><span data-stu-id="32750-116">address</span></span>|<span data-ttu-id="32750-117">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="32750-117">Required string.</span></span> <span data-ttu-id="32750-118">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="32750-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32750-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32750-119">Child Elements</span></span>  
  
|<span data-ttu-id="32750-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="32750-120">Element</span></span>|<span data-ttu-id="32750-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32750-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32750-122">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="32750-122">\<headers></span></span>](headers-element.md)|<span data-ttu-id="32750-123">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="32750-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="32750-124">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="32750-124">\<identity></span></span>](identity.md)|<span data-ttu-id="32750-125">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="32750-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32750-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32750-126">Parent Elements</span></span>  
  
|<span data-ttu-id="32750-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="32750-127">Element</span></span>|<span data-ttu-id="32750-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32750-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32750-129">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="32750-129">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="32750-130">WSFederationHttpBinding > öğesi için [ \<](wsfederationhttpbinding.md) ileti düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="32750-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32750-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32750-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="32750-132">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="32750-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="32750-133">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="32750-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="32750-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="32750-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="32750-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="32750-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="32750-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="32750-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="32750-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="32750-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
