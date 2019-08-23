---
title: <issuer> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 77ed9534ce872e805a6a6ea2c21a38710e6bc0fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925259"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="87678-102">\<\<IssuedTokenParameters > veren ></span><span class="sxs-lookup"><span data-stu-id="87678-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="87678-103">Güvenlik belirteçleri veren güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="87678-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="87678-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="87678-104">\<system.serviceModel></span></span>  
<span data-ttu-id="87678-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="87678-105">\<bindings></span></span>  
<span data-ttu-id="87678-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="87678-106">\<customBinding></span></span>  
<span data-ttu-id="87678-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="87678-107">\<binding></span></span>  
<span data-ttu-id="87678-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="87678-108">\<security></span></span>  
<span data-ttu-id="87678-109">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="87678-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="87678-110">\<veren ></span><span class="sxs-lookup"><span data-stu-id="87678-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87678-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87678-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87678-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87678-112">Attributes and Elements</span></span>  
 <span data-ttu-id="87678-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="87678-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87678-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87678-114">Attributes</span></span>  
  
|<span data-ttu-id="87678-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87678-115">Attribute</span></span>|<span data-ttu-id="87678-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87678-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87678-117">adres</span><span class="sxs-lookup"><span data-stu-id="87678-117">address</span></span>|<span data-ttu-id="87678-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="87678-118">Required string.</span></span> <span data-ttu-id="87678-119">STS 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="87678-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87678-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87678-120">Child Elements</span></span>  
  
|<span data-ttu-id="87678-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="87678-121">Element</span></span>|<span data-ttu-id="87678-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87678-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87678-123">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="87678-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="87678-124">Oluşturucunun oluşturabileceğiniz uç noktalar için bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="87678-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="87678-125">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="87678-125">\<identity></span></span>](identity.md)|<span data-ttu-id="87678-126">Verilen belirteci kullanırken, istemcinin sunucu kimliğini doğrulamasını etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="87678-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87678-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87678-127">Parent Elements</span></span>  
  
|<span data-ttu-id="87678-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="87678-128">Element</span></span>|<span data-ttu-id="87678-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87678-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87678-130">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="87678-130">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="87678-131">Geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="87678-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87678-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87678-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="87678-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="87678-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="87678-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="87678-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="87678-135">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="87678-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="87678-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="87678-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="87678-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="87678-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="87678-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="87678-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="87678-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="87678-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="87678-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="87678-140">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="87678-141">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="87678-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="87678-142">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="87678-142">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
