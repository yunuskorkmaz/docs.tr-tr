---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 9e92bbcacf529a97e1ae936e93e38c98eab19cab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157271"
---
# \<issuer>

<span data-ttu-id="ac915-101">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac915-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="ac915-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac915-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac915-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac915-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ac915-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="ac915-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac915-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac915-105">Attributes</span></span>  
  
|<span data-ttu-id="ac915-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ac915-106">Attribute</span></span>|<span data-ttu-id="ac915-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac915-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac915-108">adres</span><span class="sxs-lookup"><span data-stu-id="ac915-108">address</span></span>|<span data-ttu-id="ac915-109">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="ac915-109">Required string.</span></span> <span data-ttu-id="ac915-110">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="ac915-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac915-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac915-111">Child Elements</span></span>  
  
|<span data-ttu-id="ac915-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac915-112">Element</span></span>|<span data-ttu-id="ac915-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac915-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="ac915-114">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ac915-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="ac915-115">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac915-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac915-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac915-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ac915-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac915-117">Element</span></span>|<span data-ttu-id="ac915-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac915-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="ac915-119">Öğesi için ileti düzeyi güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ac915-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac915-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac915-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="ac915-121">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ac915-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ac915-122">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ac915-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ac915-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ac915-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ac915-124">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ac915-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ac915-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ac915-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ac915-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ac915-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
