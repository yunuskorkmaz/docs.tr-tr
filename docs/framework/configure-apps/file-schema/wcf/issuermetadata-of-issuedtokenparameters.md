---
title: <issuerMetadata> , <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 2697d24a731dbf8de3d68bcce7fd52c55ff6dc68
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276984"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="86371-102">\<İssuedtokenparameters >, \<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="86371-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="86371-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="86371-103">\<system.serviceModel></span></span>  
<span data-ttu-id="86371-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="86371-104">\<bindings></span></span>  
<span data-ttu-id="86371-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86371-105">\<customBinding></span></span>  
<span data-ttu-id="86371-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="86371-106">\<binding></span></span>  
<span data-ttu-id="86371-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="86371-107">\<security></span></span>  
<span data-ttu-id="86371-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="86371-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="86371-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="86371-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86371-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86371-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86371-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86371-111">Attributes and Elements</span></span>  
 <span data-ttu-id="86371-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86371-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86371-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86371-113">Attributes</span></span>  
  
|<span data-ttu-id="86371-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86371-114">Attribute</span></span>|<span data-ttu-id="86371-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86371-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86371-116">adres</span><span class="sxs-lookup"><span data-stu-id="86371-116">address</span></span>|<span data-ttu-id="86371-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="86371-117">Required.</span></span> <span data-ttu-id="86371-118">Uç nokta adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="86371-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="86371-119">Adres mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86371-119">The address must be an absolute URI.</span></span> <span data-ttu-id="86371-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="86371-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86371-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86371-121">Child Elements</span></span>  
  
|<span data-ttu-id="86371-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="86371-122">Element</span></span>|<span data-ttu-id="86371-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86371-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86371-124">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="86371-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="86371-125">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="86371-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="86371-126">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="86371-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="86371-127">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="86371-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86371-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86371-128">Parent Elements</span></span>  
  
|<span data-ttu-id="86371-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="86371-129">Element</span></span>|<span data-ttu-id="86371-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86371-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86371-131">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="86371-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="86371-132">Bir federe güvenlik senaryosundaki bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="86371-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86371-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86371-133">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="86371-134">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="86371-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="86371-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="86371-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="86371-136">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="86371-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="86371-137">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="86371-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="86371-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86371-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="86371-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="86371-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="86371-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86371-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="86371-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86371-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="86371-142">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="86371-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="86371-143">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="86371-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
