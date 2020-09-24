---
title: <issuer> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bfe8163d2d6baba1d6e8053f7f6579673d8b4b21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157284"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="606b1-102">\<issuer> / \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="606b1-102">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="606b1-103">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="606b1-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="606b1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="606b1-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="606b1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="606b1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="606b1-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="606b1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="606b1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="606b1-107">Attributes</span></span>  
  
|<span data-ttu-id="606b1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="606b1-108">Attribute</span></span>|<span data-ttu-id="606b1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="606b1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="606b1-110">adres</span><span class="sxs-lookup"><span data-stu-id="606b1-110">address</span></span>|<span data-ttu-id="606b1-111">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="606b1-111">Required string.</span></span> <span data-ttu-id="606b1-112">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="606b1-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="606b1-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="606b1-113">Child Elements</span></span>  
  
|<span data-ttu-id="606b1-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="606b1-114">Element</span></span>|<span data-ttu-id="606b1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="606b1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="606b1-116">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="606b1-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="606b1-117">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="606b1-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="606b1-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="606b1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="606b1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="606b1-119">Element</span></span>|<span data-ttu-id="606b1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="606b1-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="606b1-121">Geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="606b1-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="606b1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="606b1-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="606b1-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="606b1-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="606b1-124">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="606b1-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="606b1-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="606b1-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="606b1-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="606b1-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="606b1-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="606b1-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="606b1-128">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="606b1-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="606b1-129">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="606b1-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="606b1-130">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="606b1-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="606b1-131">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="606b1-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
