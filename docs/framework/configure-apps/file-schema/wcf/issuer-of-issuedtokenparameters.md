---
title: <issuer> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397939"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="4b9a9-102">\<issuer> / \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="4b9a9-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="4b9a9-103">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="4b9a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b9a9-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b9a9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b9a9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4b9a9-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="4b9a9-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b9a9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b9a9-107">Attributes</span></span>  
  
|<span data-ttu-id="4b9a9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b9a9-108">Attribute</span></span>|<span data-ttu-id="4b9a9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b9a9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b9a9-110">adres</span><span class="sxs-lookup"><span data-stu-id="4b9a9-110">address</span></span>|<span data-ttu-id="4b9a9-111">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-111">Required string.</span></span> <span data-ttu-id="4b9a9-112">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b9a9-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b9a9-113">Child Elements</span></span>  
  
|<span data-ttu-id="4b9a9-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b9a9-114">Element</span></span>|<span data-ttu-id="4b9a9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b9a9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="4b9a9-116">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="4b9a9-117">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b9a9-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b9a9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4b9a9-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b9a9-119">Element</span></span>|<span data-ttu-id="4b9a9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b9a9-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="4b9a9-121">Geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b9a9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b9a9-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4b9a9-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="4b9a9-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4b9a9-124">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4b9a9-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4b9a9-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4b9a9-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4b9a9-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4b9a9-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4b9a9-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4b9a9-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4b9a9-128">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4b9a9-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4b9a9-129">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4b9a9-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="4b9a9-130">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4b9a9-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="4b9a9-131">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4b9a9-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
