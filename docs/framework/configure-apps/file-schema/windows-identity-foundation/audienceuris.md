---
title: '&lt;AudienceUri&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034486"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="20ed7-102">&lt;AudienceUri&gt;</span><span class="sxs-lookup"><span data-stu-id="20ed7-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="20ed7-103">Bağlı olan taraf (RP) kabul edilebilir tanımlayıcılardır bir URI'leri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="20ed7-104">Bunlar bir URI'leri izin verilen kitle için kapsamlı sürece belirteçleri kabul edilmedi.</span><span class="sxs-lookup"><span data-stu-id="20ed7-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="20ed7-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="20ed7-105">\<system.identityModel></span></span>  
<span data-ttu-id="20ed7-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="20ed7-106">\<identityConfiguration></span></span>  
<span data-ttu-id="20ed7-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="20ed7-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="20ed7-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="20ed7-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="20ed7-109">\<AudienceUri ></span><span class="sxs-lookup"><span data-stu-id="20ed7-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ed7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20ed7-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20ed7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20ed7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="20ed7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20ed7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20ed7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20ed7-113">Attributes</span></span>  
  
|<span data-ttu-id="20ed7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20ed7-114">Attribute</span></span>|<span data-ttu-id="20ed7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ed7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20ed7-116">mod</span><span class="sxs-lookup"><span data-stu-id="20ed7-116">mode</span></span>|<span data-ttu-id="20ed7-117">Bir <xref:System.IdentityModel.Selectors.AudienceUriMode> İzleyici kısıtlama için gelen bir belirteci uygulanmış olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="20ed7-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="20ed7-118">Olası değerler şunlardır: "Her zaman", "Hiçbir zaman" ve "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="20ed7-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="20ed7-119">Varsayılan değer "Her zaman" dir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-119">The default is "Always".</span></span> <span data-ttu-id="20ed7-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="20ed7-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20ed7-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20ed7-121">Child Elements</span></span>  
  
|<span data-ttu-id="20ed7-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="20ed7-122">Element</span></span>|<span data-ttu-id="20ed7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ed7-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="20ed7-124">Tarafından belirtilen URI ekler `value` özniteliği için AudienceUri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20ed7-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="20ed7-125">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-125">The `value` attribute is required.</span></span> <span data-ttu-id="20ed7-126">URI, büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="20ed7-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="20ed7-127">AudienceUri koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="20ed7-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="20ed7-128">Tüm tanımlayıcılar koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="20ed7-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="20ed7-129">Tarafından belirtilen URI kaldırır `value` AudienceUri koleksiyondan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="20ed7-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="20ed7-130">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-130">The `value` attribute is required.</span></span> <span data-ttu-id="20ed7-131">URI, büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="20ed7-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20ed7-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20ed7-132">Parent Elements</span></span>  
  
|<span data-ttu-id="20ed7-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="20ed7-133">Element</span></span>|<span data-ttu-id="20ed7-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ed7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20ed7-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="20ed7-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="20ed7-136">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="20ed7-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20ed7-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20ed7-137">Remarks</span></span>  
 <span data-ttu-id="20ed7-138">Varsayılan olarak, boş bir koleksiyon oluşturulur; kullanma `<add>`, `<clear>`, ve `<remove>` öğeleri koleksiyonu değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="20ed7-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="20ed7-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> yapılandırmak için hedef kitleyi URI toplama değerleri hedef kitle URİ'si kısıtlamaları kullanılabilir nesneleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="20ed7-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="20ed7-140">`<audienceUris>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="20ed7-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="20ed7-141">Koleksiyona eklenmesini tek bir URI tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="20ed7-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20ed7-142">Kullanımını `<audienceUris>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="20ed7-143">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="20ed7-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20ed7-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="20ed7-144">Example</span></span>  
 <span data-ttu-id="20ed7-145">Aşağıdaki XML, bir uygulama için kabul edilebilir İzleyici URI'ler yapılandırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="20ed7-146">Bu örnek, tek bir URI yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="20ed7-146">This example configures a single URI.</span></span> <span data-ttu-id="20ed7-147">Bu URI için kapsamlı belirteçleri kabul edilir, diğer tüm reddedilir.</span><span class="sxs-lookup"><span data-stu-id="20ed7-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
