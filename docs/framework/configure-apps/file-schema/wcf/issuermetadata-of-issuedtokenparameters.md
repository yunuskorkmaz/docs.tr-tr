---
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: e46e56c6285af24941a550b2c4f7dec3b441db69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214812"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="0ac49-102">\<İssuedtokenparameters >, \<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="0ac49-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="0ac49-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0ac49-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0ac49-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0ac49-104">\<bindings></span></span>  
<span data-ttu-id="0ac49-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0ac49-105">\<customBinding></span></span>  
<span data-ttu-id="0ac49-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0ac49-106">\<binding></span></span>  
<span data-ttu-id="0ac49-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0ac49-107">\<security></span></span>  
<span data-ttu-id="0ac49-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="0ac49-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="0ac49-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="0ac49-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ac49-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ac49-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ac49-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ac49-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0ac49-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ac49-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ac49-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ac49-113">Attributes</span></span>  
  
|<span data-ttu-id="0ac49-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ac49-114">Attribute</span></span>|<span data-ttu-id="0ac49-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ac49-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ac49-116">adres</span><span class="sxs-lookup"><span data-stu-id="0ac49-116">address</span></span>|<span data-ttu-id="0ac49-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0ac49-117">Required.</span></span> <span data-ttu-id="0ac49-118">Uç nokta adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0ac49-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="0ac49-119">Adres mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ac49-119">The address must be an absolute URI.</span></span> <span data-ttu-id="0ac49-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="0ac49-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ac49-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ac49-121">Child Elements</span></span>  
  
|<span data-ttu-id="0ac49-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ac49-122">Element</span></span>|<span data-ttu-id="0ac49-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ac49-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ac49-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="0ac49-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="0ac49-125">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0ac49-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="0ac49-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="0ac49-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="0ac49-127">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="0ac49-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ac49-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ac49-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0ac49-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ac49-129">Element</span></span>|<span data-ttu-id="0ac49-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ac49-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ac49-131">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="0ac49-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="0ac49-132">Bir federe güvenlik senaryosundaki bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ac49-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ac49-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ac49-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0ac49-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="0ac49-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0ac49-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0ac49-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0ac49-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="0ac49-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0ac49-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0ac49-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0ac49-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0ac49-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0ac49-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="0ac49-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0ac49-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0ac49-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0ac49-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0ac49-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="0ac49-142">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ac49-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="0ac49-143">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0ac49-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
