---
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400349"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="57134-102">\<IssuedTokenParameters > \<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="57134-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

<span data-ttu-id="57134-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57134-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57134-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="57134-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="57134-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="57134-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="57134-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="57134-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="57134-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="57134-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="57134-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="57134-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="57134-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="57134-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="57134-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="57134-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57134-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57134-111">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57134-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57134-112">Attributes and Elements</span></span>  
 <span data-ttu-id="57134-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57134-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57134-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57134-114">Attributes</span></span>  
  
|<span data-ttu-id="57134-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57134-115">Attribute</span></span>|<span data-ttu-id="57134-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57134-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57134-117">adres</span><span class="sxs-lookup"><span data-stu-id="57134-117">address</span></span>|<span data-ttu-id="57134-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="57134-118">Required.</span></span> <span data-ttu-id="57134-119">Uç noktanın adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="57134-119">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="57134-120">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57134-120">The address must be an absolute URI.</span></span> <span data-ttu-id="57134-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="57134-121">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57134-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57134-122">Child Elements</span></span>  
  
|<span data-ttu-id="57134-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="57134-123">Element</span></span>|<span data-ttu-id="57134-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57134-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57134-125">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="57134-125">\<headers></span></span>](headers-element.md)|<span data-ttu-id="57134-126">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="57134-126">A collection of address headers.</span></span>|  
|[<span data-ttu-id="57134-127">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="57134-127">\<identity></span></span>](identity.md)|<span data-ttu-id="57134-128">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="57134-128">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57134-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57134-129">Parent Elements</span></span>  
  
|<span data-ttu-id="57134-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="57134-130">Element</span></span>|<span data-ttu-id="57134-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57134-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57134-132">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="57134-132">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="57134-133">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="57134-133">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57134-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57134-134">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="57134-135">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="57134-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="57134-136">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="57134-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="57134-137">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="57134-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="57134-138">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="57134-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="57134-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="57134-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="57134-140">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="57134-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="57134-141">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="57134-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="57134-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="57134-142">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="57134-143">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="57134-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="57134-144">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="57134-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
