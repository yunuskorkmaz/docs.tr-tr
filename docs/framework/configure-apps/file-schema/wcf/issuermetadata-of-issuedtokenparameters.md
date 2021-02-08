---
description: 'Hakkında daha fazla bilgi <issuerMetadata> edinin: <issuedTokenParameters>'
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 6b0b5064254caf1c6bcf72c2e6d3449402853b98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802248"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="c59f1-103">\<issuerMetadata> / \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="c59f1-103">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="c59f1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c59f1-104">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c59f1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c59f1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c59f1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c59f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c59f1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c59f1-107">Attributes</span></span>  
  
|<span data-ttu-id="c59f1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c59f1-108">Attribute</span></span>|<span data-ttu-id="c59f1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c59f1-110">adres</span><span class="sxs-lookup"><span data-stu-id="c59f1-110">address</span></span>|<span data-ttu-id="c59f1-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c59f1-111">Required.</span></span> <span data-ttu-id="c59f1-112">Uç noktanın adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c59f1-112">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="c59f1-113">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c59f1-113">The address must be an absolute URI.</span></span> <span data-ttu-id="c59f1-114">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c59f1-114">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c59f1-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c59f1-115">Child Elements</span></span>  
  
|<span data-ttu-id="c59f1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c59f1-116">Element</span></span>|<span data-ttu-id="c59f1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59f1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c59f1-118">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c59f1-118">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="c59f1-119">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="c59f1-119">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c59f1-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c59f1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c59f1-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c59f1-121">Element</span></span>|<span data-ttu-id="c59f1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59f1-122">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="c59f1-123">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c59f1-123">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c59f1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c59f1-124">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c59f1-125">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c59f1-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c59f1-126">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c59f1-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c59f1-127">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c59f1-127">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c59f1-128">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c59f1-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c59f1-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c59f1-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c59f1-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c59f1-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c59f1-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c59f1-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="c59f1-132">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c59f1-132">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c59f1-133">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c59f1-133">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
