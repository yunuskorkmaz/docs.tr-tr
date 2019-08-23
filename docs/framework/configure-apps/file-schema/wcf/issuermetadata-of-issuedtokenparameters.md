---
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: d9d7d41277eff1de43f717816b35fdc10d52192e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928872"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="b0ad0-102">\<IssuedTokenParameters > \<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="b0ad0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b0ad0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b0ad0-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-104">\<bindings></span></span>  
<span data-ttu-id="b0ad0-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-105">\<customBinding></span></span>  
<span data-ttu-id="b0ad0-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-106">\<binding></span></span>  
<span data-ttu-id="b0ad0-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-107">\<security></span></span>  
<span data-ttu-id="b0ad0-108">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="b0ad0-109">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ad0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0ad0-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0ad0-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0ad0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0ad0-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0ad0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0ad0-113">Attributes</span></span>  
  
|<span data-ttu-id="b0ad0-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0ad0-114">Attribute</span></span>|<span data-ttu-id="b0ad0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0ad0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0ad0-116">adres</span><span class="sxs-lookup"><span data-stu-id="b0ad0-116">address</span></span>|<span data-ttu-id="b0ad0-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-117">Required.</span></span> <span data-ttu-id="b0ad0-118">Uç noktanın adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="b0ad0-119">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-119">The address must be an absolute URI.</span></span> <span data-ttu-id="b0ad0-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0ad0-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0ad0-121">Child Elements</span></span>  
  
|<span data-ttu-id="b0ad0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0ad0-122">Element</span></span>|<span data-ttu-id="b0ad0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0ad0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0ad0-124">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="b0ad0-125">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="b0ad0-126">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-126">\<identity></span></span>](identity.md)|<span data-ttu-id="b0ad0-127">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0ad0-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0ad0-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b0ad0-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0ad0-129">Element</span></span>|<span data-ttu-id="b0ad0-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0ad0-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0ad0-131">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="b0ad0-132">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0ad0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0ad0-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b0ad0-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b0ad0-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b0ad0-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b0ad0-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b0ad0-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b0ad0-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b0ad0-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b0ad0-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b0ad0-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b0ad0-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b0ad0-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b0ad0-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b0ad0-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b0ad0-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b0ad0-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b0ad0-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b0ad0-142">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="b0ad0-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b0ad0-143">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b0ad0-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
