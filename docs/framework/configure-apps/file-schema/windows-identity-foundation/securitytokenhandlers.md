---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: d892fbd802ed366ca7af9b85fbf5c23d4d27e0f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157011"
---
# \<securityTokenHandlers>

<span data-ttu-id="b6b77-101">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6b77-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="b6b77-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6b77-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6b77-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6b77-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b6b77-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6b77-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6b77-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6b77-105">Attributes</span></span>  
  
|<span data-ttu-id="b6b77-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b6b77-106">Attribute</span></span>|<span data-ttu-id="b6b77-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6b77-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6b77-108">name</span><span class="sxs-lookup"><span data-stu-id="b6b77-108">name</span></span>|<span data-ttu-id="b6b77-109">Belirteç işleyici koleksiyonunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6b77-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="b6b77-110">Framework tarafından tanınan tek değerler şunlardır "ActAs" ve "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="b6b77-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="b6b77-111">Belirteç işleyici koleksiyonları bu adlardan biriyle belirtilirse, sırasıyla ActAs veya OnBehalfOf belirteçleri işlenirken koleksiyon kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b6b77-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6b77-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6b77-112">Child Elements</span></span>  
  
|<span data-ttu-id="b6b77-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6b77-113">Element</span></span>|<span data-ttu-id="b6b77-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6b77-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="b6b77-115">Belirteç işleyici koleksiyonuna bir güvenlik belirteci işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="b6b77-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="b6b77-116">Belirteç işleyici koleksiyonundan tüm güvenlik belirteci işleyicilerini temizler.</span><span class="sxs-lookup"><span data-stu-id="b6b77-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="b6b77-117">Belirteç işleyici koleksiyonundan bir güvenlik belirteci işleyicisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b6b77-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b6b77-118">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6b77-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6b77-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6b77-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b6b77-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6b77-120">Element</span></span>|<span data-ttu-id="b6b77-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6b77-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="b6b77-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6b77-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6b77-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6b77-123">Remarks</span></span>  

 <span data-ttu-id="b6b77-124">Bir hizmet yapılandırmasında bir veya daha fazla adlandırılmış güvenlik belirteci işleyici koleksiyonu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6b77-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="b6b77-125">Özniteliğini kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` .</span><span class="sxs-lookup"><span data-stu-id="b6b77-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="b6b77-126">Framework 'ün işlediği tek adlar "ActAs" ve "OnBehalfOf" dir.</span><span class="sxs-lookup"><span data-stu-id="b6b77-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="b6b77-127">Bu koleksiyonlarda işleyiciler varsa, bunlar işleme `ActAs` ve belirteçlere göre varsayılan işleyiciler yerine bir güvenlik belirteci hizmeti (STS) tarafından kullanılır `OnBehalfOf` .</span><span class="sxs-lookup"><span data-stu-id="b6b77-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="b6b77-128">Varsayılan olarak, koleksiyon aşağıdaki işleyici türleriyle doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="b6b77-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="b6b77-129">Koleksiyonunu `<add>` ,, `<remove>` ve öğelerini kullanarak değiştirebilirsiniz `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="b6b77-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="b6b77-130">Koleksiyonda yalnızca belirli bir türün tek bir işleyicisinin mevcut olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6b77-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="b6b77-131">Örneğin, sınıfından bir işleyici türetirsiniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , işleyiciniz ya da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyonda yapılandırılmış olabilir, ancak her ikisi birden değil.</span><span class="sxs-lookup"><span data-stu-id="b6b77-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="b6b77-132">`<securityTokenHandlerConfiguration>`Koleksiyondaki işleyiciler için yapılandırma ayarlarını belirtmek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6b77-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="b6b77-133">Bu öğe aracılığıyla belirtilen ayarlar, bu öğe aracılığıyla hizmette belirtilen ayarları geçersiz kılar [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="b6b77-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="b6b77-134">Bazı işleyiciler (yerleşik işleyici türlerinin birkaçı dahil), öğesinin bir alt öğesi aracılığıyla ek yapılandırmayı destekleyebilir `<add>` .</span><span class="sxs-lookup"><span data-stu-id="b6b77-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="b6b77-135">Bir işleyicide belirtilen ayarlar, koleksiyonda veya hizmette belirtilen eşdeğer ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b6b77-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
