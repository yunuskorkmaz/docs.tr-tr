---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397888"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="64ffb-101">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64ffb-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64ffb-102">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ffb-102">Attributes and Elements</span></span>  
 <span data-ttu-id="64ffb-103">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64ffb-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64ffb-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="64ffb-104">Attributes</span></span>  
  
|<span data-ttu-id="64ffb-105">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="64ffb-105">Attribute</span></span>|<span data-ttu-id="64ffb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ffb-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64ffb-107">adres</span><span class="sxs-lookup"><span data-stu-id="64ffb-107">address</span></span>|<span data-ttu-id="64ffb-108">Gerekli `string` öznitelik.</span><span class="sxs-lookup"><span data-stu-id="64ffb-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="64ffb-109">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64ffb-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="64ffb-110">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64ffb-110">The address must be an absolute URI.</span></span> <span data-ttu-id="64ffb-111">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="64ffb-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64ffb-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ffb-112">Child Elements</span></span>  
  
|<span data-ttu-id="64ffb-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="64ffb-113">Element</span></span>|<span data-ttu-id="64ffb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ffb-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="64ffb-115">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="64ffb-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="64ffb-116">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="64ffb-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64ffb-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ffb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="64ffb-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="64ffb-118">Element</span></span>|<span data-ttu-id="64ffb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ffb-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="64ffb-120">Öğesi için ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="64ffb-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64ffb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ffb-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="64ffb-122">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="64ffb-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="64ffb-123">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="64ffb-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="64ffb-124">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="64ffb-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="64ffb-125">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="64ffb-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
