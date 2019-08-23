---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941954"
---
# <a name="audienceuris"></a><span data-ttu-id="a9cc5-101">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="a9cc5-101">\<audienceUris></span></span>
<span data-ttu-id="a9cc5-102">Bağlı olan tarafın (RP) kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="a9cc5-103">Belirteçleri, izin verilen hedef kitle URI 'lerinden biri kapsamında olmadıkları müddetçe kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="a9cc5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a9cc5-104">\<system.identityModel></span></span>  
<span data-ttu-id="a9cc5-105">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a9cc5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a9cc5-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="a9cc5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a9cc5-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a9cc5-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="a9cc5-108">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="a9cc5-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9cc5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9cc5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9cc5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9cc5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a9cc5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9cc5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9cc5-112">Attributes</span></span>  
  
|<span data-ttu-id="a9cc5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9cc5-113">Attribute</span></span>|<span data-ttu-id="a9cc5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9cc5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9cc5-115">mod</span><span class="sxs-lookup"><span data-stu-id="a9cc5-115">mode</span></span>|<span data-ttu-id="a9cc5-116">Hedef <xref:System.IdentityModel.Selectors.AudienceUriMode> kitle kısıtlamasının bir gelen belirtece uygulanıp uygulanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="a9cc5-117">Olası değerler şunlardır "Always", "hiçbir" ve "Yataerkeyonly".</span><span class="sxs-lookup"><span data-stu-id="a9cc5-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="a9cc5-118">Varsayılan değer "Always" dır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-118">The default is "Always".</span></span> <span data-ttu-id="a9cc5-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9cc5-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9cc5-120">Child Elements</span></span>  
  
|<span data-ttu-id="a9cc5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9cc5-121">Element</span></span>|<span data-ttu-id="a9cc5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9cc5-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="a9cc5-123">`value` Öznitelik tarafından belirtilen URI 'yi AudienceUri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="a9cc5-124">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-124">The `value` attribute is required.</span></span> <span data-ttu-id="a9cc5-125">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="a9cc5-126">AudienceUris koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="a9cc5-127">Tüm tanımlayıcılar koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="a9cc5-128">AudienceUri koleksiyonundan `value` özniteliği tarafından belirtilen URI 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="a9cc5-129">`value` Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-129">The `value` attribute is required.</span></span> <span data-ttu-id="a9cc5-130">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9cc5-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9cc5-131">Parent Elements</span></span>  
  
|<span data-ttu-id="a9cc5-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9cc5-132">Element</span></span>|<span data-ttu-id="a9cc5-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9cc5-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9cc5-134">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a9cc5-134">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a9cc5-135">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9cc5-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9cc5-136">Remarks</span></span>  
 <span data-ttu-id="a9cc5-137">Varsayılan olarak, koleksiyon boştur; koleksiyonu `<add>`değiştirmek `<clear>`için, `<remove>` ve öğelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="a9cc5-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nesneler, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesnelerinde izin verilen tüm hedef kitle URI kısıtlamalarını yapılandırmak için hedef kitle URI koleksiyonundaki değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="a9cc5-139">`<audienceUris>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.AudienceUriElementCollection> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="a9cc5-140">Koleksiyona eklenen tek bir URI <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9cc5-141">`<audienceUris>` [Öğesinin \<IdentityConfiguration >](identityconfiguration.md) öğesinin bir alt öğesi olarak kullanılması kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a9cc5-142">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="a9cc5-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9cc5-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9cc5-143">Example</span></span>  
 <span data-ttu-id="a9cc5-144">Aşağıdaki XML, bir uygulama için kabul edilebilir hedef kitle URI 'Lerinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="a9cc5-145">Bu örnek, tek bir URI 'yi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-145">This example configures a single URI.</span></span> <span data-ttu-id="a9cc5-146">Bu URI için kapsamlı belirteçler kabul edilecek, diğerleri reddedilir.</span><span class="sxs-lookup"><span data-stu-id="a9cc5-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
