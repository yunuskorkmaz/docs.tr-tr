---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267283"
---
# <a name="audienceuris"></a><span data-ttu-id="3b661-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="3b661-101">\<audienceUris></span></span>
<span data-ttu-id="3b661-102">Bağlı olan taraf (RP) kabul edilebilir tanımlayıcılardır bir URI'leri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b661-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="3b661-103">Bunlar bir URI'leri izin verilen kitle için kapsamlı sürece belirteçleri kabul edilmedi.</span><span class="sxs-lookup"><span data-stu-id="3b661-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="3b661-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3b661-104">\<system.identityModel></span></span>  
<span data-ttu-id="3b661-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3b661-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3b661-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3b661-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3b661-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3b661-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="3b661-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="3b661-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b661-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b661-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b661-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b661-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b661-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b661-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b661-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b661-112">Attributes</span></span>  
  
|<span data-ttu-id="3b661-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3b661-113">Attribute</span></span>|<span data-ttu-id="3b661-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b661-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b661-115">mod</span><span class="sxs-lookup"><span data-stu-id="3b661-115">mode</span></span>|<span data-ttu-id="3b661-116">Bir <xref:System.IdentityModel.Selectors.AudienceUriMode> İzleyici kısıtlama için gelen bir belirteci uygulanmış olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3b661-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="3b661-117">Olası değerler şunlardır: "Her zaman", "Hiçbir zaman" ve "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="3b661-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="3b661-118">Varsayılan değer "Her zaman" dir.</span><span class="sxs-lookup"><span data-stu-id="3b661-118">The default is "Always".</span></span> <span data-ttu-id="3b661-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3b661-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b661-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b661-120">Child Elements</span></span>  
  
|<span data-ttu-id="3b661-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b661-121">Element</span></span>|<span data-ttu-id="3b661-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b661-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="3b661-123">Tarafından belirtilen URI ekler `value` özniteliği için AudienceUri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3b661-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="3b661-124">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3b661-124">The `value` attribute is required.</span></span> <span data-ttu-id="3b661-125">URI, büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b661-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="3b661-126">AudienceUri koleksiyonu temizler.</span><span class="sxs-lookup"><span data-stu-id="3b661-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="3b661-127">Tüm tanımlayıcılar koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3b661-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="3b661-128">Tarafından belirtilen URI kaldırır `value` AudienceUri koleksiyondan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3b661-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="3b661-129">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3b661-129">The `value` attribute is required.</span></span> <span data-ttu-id="3b661-130">URI, büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b661-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b661-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b661-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3b661-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b661-132">Element</span></span>|<span data-ttu-id="3b661-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b661-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b661-134">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3b661-134">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="3b661-135">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b661-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b661-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b661-136">Remarks</span></span>  
 <span data-ttu-id="3b661-137">Varsayılan olarak, boş bir koleksiyon oluşturulur; kullanma `<add>`, `<clear>`, ve `<remove>` öğeleri koleksiyonu değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="3b661-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="3b661-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> yapılandırmak için hedef kitleyi URI toplama değerleri hedef kitle URİ'si kısıtlamaları kullanılabilir nesneleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3b661-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="3b661-139">`<audienceUris>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3b661-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="3b661-140">Koleksiyona eklenmesini tek bir URI tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3b661-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b661-141">Kullanımını `<audienceUris>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3b661-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="3b661-142">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b661-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b661-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b661-143">Example</span></span>  
 <span data-ttu-id="3b661-144">Aşağıdaki XML, bir uygulama için kabul edilebilir İzleyici URI'ler yapılandırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b661-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="3b661-145">Bu örnek, tek bir URI yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3b661-145">This example configures a single URI.</span></span> <span data-ttu-id="3b661-146">Bu URI için kapsamlı belirteçleri kabul edilir, diğer tüm reddedilir.</span><span class="sxs-lookup"><span data-stu-id="3b661-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
