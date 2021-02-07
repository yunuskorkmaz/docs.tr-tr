---
description: 'Hakkında daha fazla bilgi <issuer> edinin: <issuedTokenParameters>'
title: <issuer> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 7d67583eda22414750631b6dff40f6e6ea8831e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725655"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="c9389-103">\<issuer> / \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="c9389-103">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="c9389-104">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9389-104">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="c9389-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9389-105">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9389-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9389-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c9389-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c9389-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9389-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9389-108">Attributes</span></span>  
  
|<span data-ttu-id="c9389-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9389-109">Attribute</span></span>|<span data-ttu-id="c9389-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9389-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9389-111">adres</span><span class="sxs-lookup"><span data-stu-id="c9389-111">address</span></span>|<span data-ttu-id="c9389-112">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="c9389-112">Required string.</span></span> <span data-ttu-id="c9389-113">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="c9389-113">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9389-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9389-114">Child Elements</span></span>  
  
|<span data-ttu-id="c9389-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9389-115">Element</span></span>|<span data-ttu-id="c9389-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9389-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c9389-117">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c9389-117">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="c9389-118">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9389-118">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9389-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9389-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c9389-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9389-120">Element</span></span>|<span data-ttu-id="c9389-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9389-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="c9389-122">Geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9389-122">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9389-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9389-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c9389-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c9389-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c9389-125">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c9389-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c9389-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c9389-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c9389-127">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c9389-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c9389-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c9389-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c9389-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c9389-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c9389-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c9389-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="c9389-131">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9389-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c9389-132">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9389-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
