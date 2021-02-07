---
description: 'Hakkında daha fazla bilgi edinin: <issuerMetadata>'
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 86671b6b704f5753cf4bd45c2dfd90a368070b22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725538"
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
  
## <a name="syntax"></a><span data-ttu-id="aa5e7-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa5e7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa5e7-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa5e7-103">Attributes and Elements</span></span>  

 <span data-ttu-id="aa5e7-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa5e7-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa5e7-105">Attributes</span></span>  
  
|<span data-ttu-id="aa5e7-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa5e7-106">Attribute</span></span>|<span data-ttu-id="aa5e7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa5e7-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa5e7-108">adres</span><span class="sxs-lookup"><span data-stu-id="aa5e7-108">address</span></span>|<span data-ttu-id="aa5e7-109">Gerekli `string` öznitelik.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-109">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="aa5e7-110">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-110">Specifies the address of the endpoint.</span></span> <span data-ttu-id="aa5e7-111">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-111">The address must be an absolute URI.</span></span> <span data-ttu-id="aa5e7-112">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-112">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa5e7-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa5e7-113">Child Elements</span></span>  
  
|<span data-ttu-id="aa5e7-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa5e7-114">Element</span></span>|<span data-ttu-id="aa5e7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa5e7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="aa5e7-116">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-116">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="aa5e7-117">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-117">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa5e7-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa5e7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="aa5e7-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa5e7-119">Element</span></span>|<span data-ttu-id="aa5e7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa5e7-120">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="aa5e7-121">Öğesi için ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="aa5e7-121">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa5e7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa5e7-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="aa5e7-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="aa5e7-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="aa5e7-124">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="aa5e7-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="aa5e7-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="aa5e7-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="aa5e7-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="aa5e7-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
