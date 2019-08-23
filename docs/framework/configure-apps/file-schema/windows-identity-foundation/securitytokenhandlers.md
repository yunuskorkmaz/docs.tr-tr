---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942467"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="6e270-101">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6e270-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="6e270-102">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e270-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="6e270-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6e270-103">\<system.identityModel></span></span>  
<span data-ttu-id="6e270-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6e270-104">\<identityConfiguration></span></span>  
<span data-ttu-id="6e270-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6e270-105">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e270-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e270-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e270-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e270-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6e270-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e270-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e270-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e270-109">Attributes</span></span>  
  
|<span data-ttu-id="6e270-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e270-110">Attribute</span></span>|<span data-ttu-id="6e270-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e270-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e270-112">name</span><span class="sxs-lookup"><span data-stu-id="6e270-112">name</span></span>|<span data-ttu-id="6e270-113">Belirteç işleyici koleksiyonunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e270-113">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="6e270-114">Framework tarafından tanınan tek değerler şunlardır "ActAs" ve "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="6e270-114">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="6e270-115">Belirteç işleyici koleksiyonları bu adlardan biriyle belirtilirse, sırasıyla ActAs veya OnBehalfOf belirteçleri işlenirken koleksiyon kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="6e270-115">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e270-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e270-116">Child Elements</span></span>  
  
|<span data-ttu-id="6e270-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e270-117">Element</span></span>|<span data-ttu-id="6e270-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e270-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e270-119">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="6e270-119">\<add></span></span>](add.md)|<span data-ttu-id="6e270-120">Belirteç işleyici koleksiyonuna bir güvenlik belirteci işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="6e270-120">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="6e270-121">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="6e270-121">\<clear></span></span>](clear.md)|<span data-ttu-id="6e270-122">Belirteç işleyici koleksiyonundan tüm güvenlik belirteci işleyicilerini temizler.</span><span class="sxs-lookup"><span data-stu-id="6e270-122">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="6e270-123">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="6e270-123">\<remove></span></span>](remove.md)|<span data-ttu-id="6e270-124">Belirteç işleyici koleksiyonundan bir güvenlik belirteci işleyicisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6e270-124">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="6e270-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6e270-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="6e270-126">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e270-126">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e270-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e270-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6e270-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e270-128">Element</span></span>|<span data-ttu-id="6e270-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e270-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e270-130">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6e270-130">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="6e270-131">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e270-131">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e270-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e270-132">Remarks</span></span>  
 <span data-ttu-id="6e270-133">Bir hizmet yapılandırmasında bir veya daha fazla adlandırılmış güvenlik belirteci işleyici koleksiyonu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e270-133">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="6e270-134">`name` Özniteliğini kullanarak bir koleksiyon için bir ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e270-134">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="6e270-135">Framework 'ün işlediği tek adlar "ActAs" ve "OnBehalfOf" dir.</span><span class="sxs-lookup"><span data-stu-id="6e270-135">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="6e270-136">Bu koleksiyonlarda işleyiciler varsa, bunlar işleme `ActAs` ve `OnBehalfOf` belirteçlere göre varsayılan işleyiciler yerine bir güvenlik belirteci hizmeti (STS) tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e270-136">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="6e270-137">Varsayılan olarak, koleksiyon aşağıdaki işleyici <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>türleriyle doldurulur:, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>,, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="6e270-137">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="6e270-138">Koleksiyonunu `<add>`, `<remove>`, ve`<clear>` öğelerini kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e270-138">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="6e270-139">Koleksiyonda yalnızca belirli bir türün tek bir işleyicisinin mevcut olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e270-139">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="6e270-140">Örneğin, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından bir işleyici türetirsiniz, işleyiciniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ya da tek bir koleksiyonda yapılandırılmış olabilir, ancak her ikisi birden değil.</span><span class="sxs-lookup"><span data-stu-id="6e270-140">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="6e270-141">Koleksiyondaki işleyiciler için yapılandırma ayarlarını belirtmek için öğesinikullanın.`<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="6e270-141">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="6e270-142">Bu öğe aracılığıyla belirtilen ayarlar, [ \<IdentityConfiguration >](identityconfiguration.md) öğesi aracılığıyla hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6e270-142">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="6e270-143">Bazı işleyiciler (yerleşik işleyici türlerinin birkaçı dahil), `<add>` öğesinin bir alt öğesi aracılığıyla ek yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6e270-143">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="6e270-144">Bir işleyicide belirtilen ayarlar, koleksiyonda veya hizmette belirtilen eşdeğer ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6e270-144">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
