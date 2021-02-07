---
description: 'Hakkında daha fazla bilgi edinin: <issuer>'
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 771fb8d0bee4e78b598bd20c4d99ec5180f9fb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725642"
---
# \<issuer>

<span data-ttu-id="0afad-102">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="0afad-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="0afad-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0afad-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0afad-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0afad-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0afad-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="0afad-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0afad-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0afad-106">Attributes</span></span>  
  
|<span data-ttu-id="0afad-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0afad-107">Attribute</span></span>|<span data-ttu-id="0afad-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0afad-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0afad-109">adres</span><span class="sxs-lookup"><span data-stu-id="0afad-109">address</span></span>|<span data-ttu-id="0afad-110">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="0afad-110">Required string.</span></span> <span data-ttu-id="0afad-111">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="0afad-111">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0afad-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0afad-112">Child Elements</span></span>  
  
|<span data-ttu-id="0afad-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0afad-113">Element</span></span>|<span data-ttu-id="0afad-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0afad-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="0afad-115">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0afad-115">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="0afad-116">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="0afad-116">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0afad-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0afad-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0afad-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0afad-118">Element</span></span>|<span data-ttu-id="0afad-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0afad-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="0afad-120">Öğesi için ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0afad-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0afad-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0afad-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="0afad-122">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="0afad-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0afad-123">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0afad-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0afad-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="0afad-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0afad-125">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0afad-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0afad-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="0afad-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0afad-127">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0afad-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
