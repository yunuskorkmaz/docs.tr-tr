---
title: <issuer> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397939"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="7250e-102">\<\<IssuedTokenParameters > veren ></span><span class="sxs-lookup"><span data-stu-id="7250e-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="7250e-103">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="7250e-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="7250e-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7250e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7250e-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7250e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7250e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7250e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7250e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7250e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7250e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="7250e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7250e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7250e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="7250e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="7250e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="7250e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<veren >**</span><span class="sxs-lookup"><span data-stu-id="7250e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7250e-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7250e-112">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7250e-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7250e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7250e-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="7250e-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7250e-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7250e-115">Attributes</span></span>  
  
|<span data-ttu-id="7250e-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7250e-116">Attribute</span></span>|<span data-ttu-id="7250e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7250e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7250e-118">adres</span><span class="sxs-lookup"><span data-stu-id="7250e-118">address</span></span>|<span data-ttu-id="7250e-119">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="7250e-119">Required string.</span></span> <span data-ttu-id="7250e-120">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="7250e-120">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7250e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7250e-121">Child Elements</span></span>  
  
|<span data-ttu-id="7250e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="7250e-122">Element</span></span>|<span data-ttu-id="7250e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7250e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7250e-124">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="7250e-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="7250e-125">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7250e-125">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="7250e-126">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="7250e-126">\<identity></span></span>](identity.md)|<span data-ttu-id="7250e-127">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="7250e-127">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7250e-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7250e-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7250e-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="7250e-129">Element</span></span>|<span data-ttu-id="7250e-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7250e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7250e-131">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="7250e-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="7250e-132">Geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="7250e-132">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7250e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7250e-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7250e-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="7250e-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7250e-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="7250e-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7250e-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="7250e-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7250e-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="7250e-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7250e-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7250e-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7250e-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="7250e-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7250e-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7250e-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7250e-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7250e-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="7250e-142">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="7250e-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7250e-143">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7250e-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
