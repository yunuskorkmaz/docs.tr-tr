---
title: <issuerMetadata> / <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 389ac9e96c1462f59bc42b2e20cb511acdefda00
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185671"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="20cee-102">\<issuerMetadata> / \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="20cee-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="20cee-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="20cee-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20cee-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20cee-104">Attributes and Elements</span></span>  

 <span data-ttu-id="20cee-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20cee-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20cee-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20cee-106">Attributes</span></span>  
  
|<span data-ttu-id="20cee-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20cee-107">Attribute</span></span>|<span data-ttu-id="20cee-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20cee-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20cee-109">adres</span><span class="sxs-lookup"><span data-stu-id="20cee-109">address</span></span>|<span data-ttu-id="20cee-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20cee-110">Required.</span></span> <span data-ttu-id="20cee-111">Uç noktanın adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="20cee-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="20cee-112">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20cee-112">The address must be an absolute URI.</span></span> <span data-ttu-id="20cee-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="20cee-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20cee-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20cee-114">Child Elements</span></span>  
  
|<span data-ttu-id="20cee-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="20cee-115">Element</span></span>|<span data-ttu-id="20cee-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20cee-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="20cee-117">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20cee-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="20cee-118">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="20cee-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20cee-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20cee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="20cee-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="20cee-120">Element</span></span>|<span data-ttu-id="20cee-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20cee-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="20cee-122">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="20cee-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20cee-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20cee-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="20cee-124">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="20cee-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="20cee-125">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="20cee-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="20cee-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="20cee-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="20cee-127">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="20cee-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="20cee-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="20cee-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="20cee-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="20cee-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="20cee-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="20cee-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="20cee-131">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="20cee-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="20cee-132">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="20cee-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
