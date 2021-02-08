---
description: 'Hakkında daha fazla bilgi edinin: <securityTokenHandlers>'
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 14937f6763644f9b7f43c0f7be71ea2352b21402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782032"
---
# \<securityTokenHandlers>

<span data-ttu-id="e1987-102">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1987-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="e1987-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1987-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1987-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1987-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e1987-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1987-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1987-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1987-106">Attributes</span></span>  
  
|<span data-ttu-id="e1987-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e1987-107">Attribute</span></span>|<span data-ttu-id="e1987-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1987-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1987-109">name</span><span class="sxs-lookup"><span data-stu-id="e1987-109">name</span></span>|<span data-ttu-id="e1987-110">Belirteç işleyici koleksiyonunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1987-110">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="e1987-111">Framework tarafından tanınan tek değerler şunlardır "ActAs" ve "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="e1987-111">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="e1987-112">Belirteç işleyici koleksiyonları bu adlardan biriyle belirtilirse, sırasıyla ActAs veya OnBehalfOf belirteçleri işlenirken koleksiyon kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1987-112">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1987-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1987-113">Child Elements</span></span>  
  
|<span data-ttu-id="e1987-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1987-114">Element</span></span>|<span data-ttu-id="e1987-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1987-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="e1987-116">Belirteç işleyici koleksiyonuna bir güvenlik belirteci işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="e1987-116">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="e1987-117">Belirteç işleyici koleksiyonundan tüm güvenlik belirteci işleyicilerini temizler.</span><span class="sxs-lookup"><span data-stu-id="e1987-117">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="e1987-118">Belirteç işleyici koleksiyonundan bir güvenlik belirteci işleyicisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e1987-118">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="e1987-119">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1987-119">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1987-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1987-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1987-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1987-121">Element</span></span>|<span data-ttu-id="e1987-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1987-122">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="e1987-123">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1987-123">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1987-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1987-124">Remarks</span></span>  

 <span data-ttu-id="e1987-125">Bir hizmet yapılandırmasında bir veya daha fazla adlandırılmış güvenlik belirteci işleyici koleksiyonu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1987-125">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="e1987-126">Özniteliğini kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` .</span><span class="sxs-lookup"><span data-stu-id="e1987-126">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="e1987-127">Framework 'ün işlediği tek adlar "ActAs" ve "OnBehalfOf" dir.</span><span class="sxs-lookup"><span data-stu-id="e1987-127">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="e1987-128">Bu koleksiyonlarda işleyiciler varsa, bunlar işleme `ActAs` ve belirteçlere göre varsayılan işleyiciler yerine bir güvenlik belirteci hizmeti (STS) tarafından kullanılır `OnBehalfOf` .</span><span class="sxs-lookup"><span data-stu-id="e1987-128">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="e1987-129">Varsayılan olarak, koleksiyon aşağıdaki işleyici türleriyle doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="e1987-129">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="e1987-130">Koleksiyonunu `<add>` ,, `<remove>` ve öğelerini kullanarak değiştirebilirsiniz `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="e1987-130">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="e1987-131">Koleksiyonda yalnızca belirli bir türün tek bir işleyicisinin mevcut olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1987-131">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="e1987-132">Örneğin, sınıfından bir işleyici türetirsiniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , işleyiciniz ya da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyonda yapılandırılmış olabilir, ancak her ikisi birden değil.</span><span class="sxs-lookup"><span data-stu-id="e1987-132">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="e1987-133">`<securityTokenHandlerConfiguration>`Koleksiyondaki işleyiciler için yapılandırma ayarlarını belirtmek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1987-133">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="e1987-134">Bu öğe aracılığıyla belirtilen ayarlar, bu öğe aracılığıyla hizmette belirtilen ayarları geçersiz kılar [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="e1987-134">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="e1987-135">Bazı işleyiciler (yerleşik işleyici türlerinin birkaçı dahil), öğesinin bir alt öğesi aracılığıyla ek yapılandırmayı destekleyebilir `<add>` .</span><span class="sxs-lookup"><span data-stu-id="e1987-135">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="e1987-136">Bir işleyicide belirtilen ayarlar, koleksiyonda veya hizmette belirtilen eşdeğer ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e1987-136">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
