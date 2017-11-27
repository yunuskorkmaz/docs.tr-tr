---
title: '&lt;AudienceUri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3ce884c19d205df4727dcce96ffdf34144ff1dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="886b3-102">&lt;AudienceUri&gt;</span><span class="sxs-lookup"><span data-stu-id="886b3-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="886b3-103">Bağlı olan taraf (RP) kabul edilebilir tanımlayıcılardır URI'ler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="886b3-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="886b3-104">İzin verilen kitle URI'ler biri için kapsamındaki sürece belirteçleri kabul edilmedi.</span><span class="sxs-lookup"><span data-stu-id="886b3-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="886b3-105">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="886b3-105">\<system.identityModel></span></span>  
<span data-ttu-id="886b3-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="886b3-106">\<identityConfiguration></span></span>  
<span data-ttu-id="886b3-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="886b3-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="886b3-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="886b3-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="886b3-109">\<AudienceUri ></span><span class="sxs-lookup"><span data-stu-id="886b3-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="886b3-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="886b3-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="886b3-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="886b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="886b3-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="886b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="886b3-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="886b3-113">Attributes</span></span>  
  
|<span data-ttu-id="886b3-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="886b3-114">Attribute</span></span>|<span data-ttu-id="886b3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="886b3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="886b3-116">mod</span><span class="sxs-lookup"><span data-stu-id="886b3-116">mode</span></span>|<span data-ttu-id="886b3-117">Bir <xref:System.IdentityModel.Selectors.AudienceUriMode> İzleyici kısıtlama için gelen belirteci uygulanmış olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="886b3-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="886b3-118">Olası değerler şunlardır: "Her zaman", "Hiçbir zaman"'i ve "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="886b3-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="886b3-119">"Her zaman" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="886b3-119">The default is "Always".</span></span> <span data-ttu-id="886b3-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="886b3-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="886b3-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="886b3-121">Child Elements</span></span>  
  
|<span data-ttu-id="886b3-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="886b3-122">Element</span></span>|<span data-ttu-id="886b3-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="886b3-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="886b3-124">Belirtilen URI ekler `value` özniteliği için AudienceUri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="886b3-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="886b3-125">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="886b3-125">The `value` attribute is required.</span></span> <span data-ttu-id="886b3-126">URI büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="886b3-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="886b3-127">AudienceUri koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="886b3-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="886b3-128">Tüm kimliklerin koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="886b3-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="886b3-129">Belirtilen URI kaldırır `value` AudienceUri koleksiyonundan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="886b3-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="886b3-130">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="886b3-130">The `value` attribute is required.</span></span> <span data-ttu-id="886b3-131">URI büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="886b3-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="886b3-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="886b3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="886b3-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="886b3-133">Element</span></span>|<span data-ttu-id="886b3-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="886b3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="886b3-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="886b3-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="886b3-136">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="886b3-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="886b3-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="886b3-137">Remarks</span></span>  
 <span data-ttu-id="886b3-138">Varsayılan olarak, koleksiyon boştur; kullanmak `<add>`, `<clear>`, ve `<remove>` öğe koleksiyonunu Değiştir.</span><span class="sxs-lookup"><span data-stu-id="886b3-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="886b3-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> herhangi yapılandırmak için hedef kitleye URI koleksiyonu izin verilen değerler İzleyici URI kısıtlamaları kullanım nesneleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="886b3-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="886b3-140">`<audienceUris>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="886b3-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="886b3-141">Koleksiyona eklenen ayrı bir URI tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="886b3-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="886b3-142">Kullanımını `<audienceUris>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="886b3-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="886b3-143">Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="886b3-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="886b3-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="886b3-144">Example</span></span>  
 <span data-ttu-id="886b3-145">Aşağıdaki XML, bir uygulama için kabul edilebilir İzleyici URI'ler yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="886b3-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="886b3-146">Bu örnek, tek bir URI yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="886b3-146">This example configures a single URI.</span></span> <span data-ttu-id="886b3-147">Bu URI için kapsamlı belirteçleri kabul eder, diğerlerini reddedilir.</span><span class="sxs-lookup"><span data-stu-id="886b3-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
