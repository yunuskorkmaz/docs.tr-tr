---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252176"
---
# <a name="audienceuris"></a><span data-ttu-id="bf9b8-101">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="bf9b8-101">\<audienceUris></span></span>
<span data-ttu-id="bf9b8-102">Bağlı olan tarafın (RP) kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="bf9b8-103">Belirteçleri, izin verilen hedef kitle URI 'lerinden biri kapsamında olmadıkları müddetçe kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
<span data-ttu-id="bf9b8-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf9b8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf9b8-105">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="bf9b8-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="bf9b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="bf9b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="bf9b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="bf9b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="bf9b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="bf9b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="bf9b8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**</span><span class="sxs-lookup"><span data-stu-id="bf9b8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9b8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf9b8-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf9b8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf9b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bf9b8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf9b8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf9b8-113">Attributes</span></span>  
  
|<span data-ttu-id="bf9b8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bf9b8-114">Attribute</span></span>|<span data-ttu-id="bf9b8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf9b8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf9b8-116">mod</span><span class="sxs-lookup"><span data-stu-id="bf9b8-116">mode</span></span>|<span data-ttu-id="bf9b8-117">Hedef <xref:System.IdentityModel.Selectors.AudienceUriMode> kitle kısıtlamasının bir gelen belirtece uygulanıp uygulanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="bf9b8-118">Olası değerler şunlardır "Always", "hiçbir" ve "Yataerkeyonly".</span><span class="sxs-lookup"><span data-stu-id="bf9b8-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="bf9b8-119">Varsayılan değer "Always" dır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-119">The default is "Always".</span></span> <span data-ttu-id="bf9b8-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf9b8-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf9b8-121">Child Elements</span></span>  
  
|<span data-ttu-id="bf9b8-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf9b8-122">Element</span></span>|<span data-ttu-id="bf9b8-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf9b8-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="bf9b8-124">`value` Öznitelik tarafından belirtilen URI 'yi AudienceUri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="bf9b8-125">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-125">The `value` attribute is required.</span></span> <span data-ttu-id="bf9b8-126">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="bf9b8-127">AudienceUris koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="bf9b8-128">Tüm tanımlayıcılar koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="bf9b8-129">AudienceUri koleksiyonundan `value` özniteliği tarafından belirtilen URI 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="bf9b8-130">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-130">The `value` attribute is required.</span></span> <span data-ttu-id="bf9b8-131">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf9b8-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf9b8-132">Parent Elements</span></span>  
  
|<span data-ttu-id="bf9b8-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf9b8-133">Element</span></span>|<span data-ttu-id="bf9b8-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf9b8-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf9b8-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf9b8-135">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="bf9b8-136">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf9b8-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf9b8-137">Remarks</span></span>  
 <span data-ttu-id="bf9b8-138">Varsayılan olarak, koleksiyon boştur; koleksiyonu `<add>`değiştirmek `<clear>`için, `<remove>` ve öğelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="bf9b8-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nesneler, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesnelerinde izin verilen tüm hedef kitle URI kısıtlamalarını yapılandırmak için hedef kitle URI koleksiyonundaki değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="bf9b8-140">`<audienceUris>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.AudienceUriElementCollection> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="bf9b8-141">Koleksiyona eklenen tek bir URI <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf9b8-142">`<audienceUris>` [Öğesinin \<IdentityConfiguration >](identityconfiguration.md) öğesinin bir alt öğesi olarak kullanılması kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="bf9b8-143">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="bf9b8-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf9b8-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf9b8-144">Example</span></span>  
 <span data-ttu-id="bf9b8-145">Aşağıdaki XML, bir uygulama için kabul edilebilir hedef kitle URI 'Lerinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="bf9b8-146">Bu örnek, tek bir URI 'yi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-146">This example configures a single URI.</span></span> <span data-ttu-id="bf9b8-147">Bu URI için kapsamlı belirteçler kabul edilecek, diğerleri reddedilir.</span><span class="sxs-lookup"><span data-stu-id="bf9b8-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
