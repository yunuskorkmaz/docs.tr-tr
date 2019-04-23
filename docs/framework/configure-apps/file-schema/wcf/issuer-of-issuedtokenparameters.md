---
title: <issuer> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113548"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="79242-102">\<veren >, \<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="79242-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="79242-103">Güvenlik belirteci hizmeti (güvenlik belirteçlerini çıkartan STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="79242-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="79242-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="79242-104">\<system.serviceModel></span></span>  
<span data-ttu-id="79242-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="79242-105">\<bindings></span></span>  
<span data-ttu-id="79242-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="79242-106">\<customBinding></span></span>  
<span data-ttu-id="79242-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="79242-107">\<binding></span></span>  
<span data-ttu-id="79242-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="79242-108">\<security></span></span>  
<span data-ttu-id="79242-109">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="79242-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="79242-110">\<veren ></span><span class="sxs-lookup"><span data-stu-id="79242-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79242-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79242-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79242-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79242-112">Attributes and Elements</span></span>  
 <span data-ttu-id="79242-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79242-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79242-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79242-114">Attributes</span></span>  
  
|<span data-ttu-id="79242-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79242-115">Attribute</span></span>|<span data-ttu-id="79242-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79242-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79242-117">adres</span><span class="sxs-lookup"><span data-stu-id="79242-117">address</span></span>|<span data-ttu-id="79242-118">Zorunlu dize.</span><span class="sxs-lookup"><span data-stu-id="79242-118">Required string.</span></span> <span data-ttu-id="79242-119">STS URL'si.</span><span class="sxs-lookup"><span data-stu-id="79242-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79242-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79242-120">Child Elements</span></span>  
  
|<span data-ttu-id="79242-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="79242-121">Element</span></span>|<span data-ttu-id="79242-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79242-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79242-123">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="79242-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="79242-124">Adres üstbilgileri Oluşturucu oluşturabilirsiniz uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="79242-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="79242-125">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="79242-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="79242-126">Verilen bir belirteç kullanırken, sunucu kimlik doğrulaması istemci etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="79242-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79242-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79242-127">Parent Elements</span></span>  
  
|<span data-ttu-id="79242-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="79242-128">Element</span></span>|<span data-ttu-id="79242-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79242-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79242-130">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="79242-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="79242-131">Geçerli verilen belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="79242-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79242-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79242-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="79242-133">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="79242-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="79242-134">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="79242-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="79242-135">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="79242-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="79242-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="79242-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="79242-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="79242-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="79242-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="79242-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="79242-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="79242-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="79242-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="79242-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="79242-141">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="79242-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="79242-142">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="79242-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
