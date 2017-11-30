---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="be526-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="be526-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="be526-103">Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="be526-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="be526-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="be526-104">\<system.identityModel></span></span>  
<span data-ttu-id="be526-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="be526-105">\<identityConfiguration></span></span>  
<span data-ttu-id="be526-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="be526-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be526-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be526-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be526-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be526-108">Attributes and Elements</span></span>  
 <span data-ttu-id="be526-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be526-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be526-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be526-110">Attributes</span></span>  
  
|<span data-ttu-id="be526-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="be526-111">Attribute</span></span>|<span data-ttu-id="be526-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be526-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be526-113">name</span><span class="sxs-lookup"><span data-stu-id="be526-113">name</span></span>|<span data-ttu-id="be526-114">Bir belirteci işleyicisi koleksiyonunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be526-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="be526-115">Çerçevesi tarafından kabul edilen değerler yalnızca "ActAs" ve "OnBehalfOf" dir.</span><span class="sxs-lookup"><span data-stu-id="be526-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="be526-116">Belirteci işleyicisi koleksiyonları şu adlardan birini kullanarak belirtilirse, koleksiyon ActAs veya OnBehalfOf işleme sırasıyla belirteçler olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be526-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be526-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be526-117">Child Elements</span></span>  
  
|<span data-ttu-id="be526-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="be526-118">Element</span></span>|<span data-ttu-id="be526-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be526-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be526-120">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="be526-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="be526-121">Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="be526-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="be526-122">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="be526-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="be526-123">Tüm güvenlik belirteci işleyicileri belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be526-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="be526-124">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="be526-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="be526-125">Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be526-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="be526-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="be526-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="be526-127">Belirteç işleyicileri koleksiyonunu yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="be526-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be526-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be526-128">Parent Elements</span></span>  
  
|<span data-ttu-id="be526-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="be526-129">Element</span></span>|<span data-ttu-id="be526-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be526-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be526-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="be526-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="be526-132">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be526-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be526-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be526-133">Remarks</span></span>  
 <span data-ttu-id="be526-134">Hizmet yapılandırmasında güvenlik belirteci işleyicileri bir veya daha fazla adlandırılmış koleksiyonları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be526-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="be526-135">Kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="be526-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="be526-136">Çerçeve işleme yalnızca "ActAs" ve "OnBehalfOf" adlardır.</span><span class="sxs-lookup"><span data-stu-id="be526-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="be526-137">İşleyicileri bu koleksiyonları yoksa, bir güvenlik belirteci hizmeti (STS) yerine varsayılan işleyicileri işlerken kullanıldıkları `ActAs` ve `OnBehalfOf` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="be526-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="be526-138">Varsayılan olarak, koleksiyon şu işleyici türlerini ile doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="be526-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="be526-139">Koleksiyon kullanarak değiştirebileceğiniz `<add>`, `<remove>`, ve `<clear>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="be526-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="be526-140">Herhangi bir tür için tek bir işleyici koleksiyonunda var olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="be526-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="be526-141">Örneğin, bir işleyicisinden türetirseniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı, ya da işleyicinizi veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyon, ancak ikisini yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="be526-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="be526-142">Kullanım `<securityTokenHandlerConfiguration>` öğe koleksiyonda işleyicileri için yapılandırma ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="be526-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="be526-143">Hizmet aracılığıyla belirtilen bu öğe belirtilen ayarları geçersiz kılar [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="be526-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="be526-144">Bazı işleyicileri (birkaç yerleşik işleyici türlerini dahil) bir alt öğesi aracılığıyla ek yapılandırma destekleyebilir `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="be526-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="be526-145">Üzerinde bir işleyici için belirtilen ayarları koleksiyon veya hizmeti belirtilen eşdeğer ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="be526-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
