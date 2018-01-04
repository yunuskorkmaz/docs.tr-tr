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
ms.workload: dotnet
ms.openlocfilehash: de19fffdeae801163ec991ecf08d00b1286781d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="ce343-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="ce343-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="ce343-103">Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce343-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="ce343-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="ce343-104">\<system.identityModel></span></span>  
<span data-ttu-id="ce343-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ce343-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ce343-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="ce343-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce343-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce343-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce343-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce343-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce343-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce343-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce343-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce343-110">Attributes</span></span>  
  
|<span data-ttu-id="ce343-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce343-111">Attribute</span></span>|<span data-ttu-id="ce343-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce343-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce343-113">name</span><span class="sxs-lookup"><span data-stu-id="ce343-113">name</span></span>|<span data-ttu-id="ce343-114">Bir belirteci işleyicisi koleksiyonunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce343-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="ce343-115">Çerçevesi tarafından kabul edilen değerler yalnızca "ActAs" ve "OnBehalfOf" dir.</span><span class="sxs-lookup"><span data-stu-id="ce343-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="ce343-116">Belirteci işleyicisi koleksiyonları şu adlardan birini kullanarak belirtilirse, koleksiyon ActAs veya OnBehalfOf işleme sırasıyla belirteçler olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce343-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce343-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce343-117">Child Elements</span></span>  
  
|<span data-ttu-id="ce343-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce343-118">Element</span></span>|<span data-ttu-id="ce343-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce343-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce343-120">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="ce343-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="ce343-121">Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="ce343-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="ce343-122">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="ce343-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="ce343-123">Tüm güvenlik belirteci işleyicileri belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ce343-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="ce343-124">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="ce343-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="ce343-125">Bir güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ce343-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="ce343-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ce343-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="ce343-127">Belirteç işleyicileri koleksiyonunu yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce343-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce343-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce343-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ce343-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce343-129">Element</span></span>|<span data-ttu-id="ce343-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce343-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce343-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ce343-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="ce343-132">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce343-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce343-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce343-133">Remarks</span></span>  
 <span data-ttu-id="ce343-134">Hizmet yapılandırmasında güvenlik belirteci işleyicileri bir veya daha fazla adlandırılmış koleksiyonları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce343-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="ce343-135">Kullanarak bir koleksiyon için bir ad belirtebilirsiniz `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ce343-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="ce343-136">Çerçeve işleme yalnızca "ActAs" ve "OnBehalfOf" adlardır.</span><span class="sxs-lookup"><span data-stu-id="ce343-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="ce343-137">İşleyicileri bu koleksiyonları yoksa, bir güvenlik belirteci hizmeti (STS) yerine varsayılan işleyicileri işlerken kullanıldıkları `ActAs` ve `OnBehalfOf` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="ce343-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="ce343-138">Varsayılan olarak, koleksiyon şu işleyici türlerini ile doldurulur: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="ce343-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="ce343-139">Koleksiyon kullanarak değiştirebileceğiniz `<add>`, `<remove>`, ve `<clear>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ce343-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="ce343-140">Herhangi bir tür için tek bir işleyici koleksiyonunda var olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="ce343-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="ce343-141">Örneğin, bir işleyicisinden türetirseniz <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı, ya da işleyicinizi veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> tek bir koleksiyon, ancak ikisini yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce343-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="ce343-142">Kullanım `<securityTokenHandlerConfiguration>` öğe koleksiyonda işleyicileri için yapılandırma ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ce343-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="ce343-143">Hizmet aracılığıyla belirtilen bu öğe belirtilen ayarları geçersiz kılar [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="ce343-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="ce343-144">Bazı işleyicileri (birkaç yerleşik işleyici türlerini dahil) bir alt öğesi aracılığıyla ek yapılandırma destekleyebilir `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ce343-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="ce343-145">Üzerinde bir işleyici için belirtilen ayarları koleksiyon veya hizmeti belirtilen eşdeğer ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ce343-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
