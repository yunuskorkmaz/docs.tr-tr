---
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400349"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="a635a-102">\<issuerMetadata> / \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="a635a-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="a635a-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a635a-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a635a-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a635a-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a635a-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a635a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a635a-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a635a-106">Attributes</span></span>  
  
|<span data-ttu-id="a635a-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a635a-107">Attribute</span></span>|<span data-ttu-id="a635a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a635a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a635a-109">adres</span><span class="sxs-lookup"><span data-stu-id="a635a-109">address</span></span>|<span data-ttu-id="a635a-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a635a-110">Required.</span></span> <span data-ttu-id="a635a-111">Uç noktanın adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a635a-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="a635a-112">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a635a-112">The address must be an absolute URI.</span></span> <span data-ttu-id="a635a-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a635a-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a635a-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a635a-114">Child Elements</span></span>  
  
|<span data-ttu-id="a635a-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a635a-115">Element</span></span>|<span data-ttu-id="a635a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a635a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="a635a-117">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a635a-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="a635a-118">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="a635a-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a635a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a635a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a635a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a635a-120">Element</span></span>|<span data-ttu-id="a635a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a635a-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="a635a-122">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a635a-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a635a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a635a-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a635a-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a635a-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a635a-125">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a635a-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a635a-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a635a-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a635a-127">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a635a-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a635a-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a635a-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a635a-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a635a-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a635a-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a635a-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="a635a-131">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a635a-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="a635a-132">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a635a-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
