---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252176"
---
# \<audienceUris>
<span data-ttu-id="bb3a0-101">Bağlı olan tarafın (RP) kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-101">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="bb3a0-102">Belirteçleri, izin verilen hedef kitle URI 'lerinden biri kapsamında olmadıkları müddetçe kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-102">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="bb3a0-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb3a0-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb3a0-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb3a0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="bb3a0-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb3a0-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb3a0-106">Attributes</span></span>  
  
|<span data-ttu-id="bb3a0-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bb3a0-107">Attribute</span></span>|<span data-ttu-id="bb3a0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb3a0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb3a0-109">mod</span><span class="sxs-lookup"><span data-stu-id="bb3a0-109">mode</span></span>|<span data-ttu-id="bb3a0-110"><xref:System.IdentityModel.Selectors.AudienceUriMode>Hedef kitle kısıtlamasının bir gelen belirtece uygulanıp uygulanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-110">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="bb3a0-111">Olası değerler şunlardır "Always", "hiçbir" ve "Yataerkeyonly".</span><span class="sxs-lookup"><span data-stu-id="bb3a0-111">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="bb3a0-112">Varsayılan değer "Always" dır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-112">The default is "Always".</span></span> <span data-ttu-id="bb3a0-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb3a0-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb3a0-114">Child Elements</span></span>  
  
|<span data-ttu-id="bb3a0-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb3a0-115">Element</span></span>|<span data-ttu-id="bb3a0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb3a0-116">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="bb3a0-117">Öznitelik tarafından belirtilen URI `value` 'Yi AudienceUri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-117">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="bb3a0-118">`value`Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-118">The `value` attribute is required.</span></span> <span data-ttu-id="bb3a0-119">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-119">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="bb3a0-120">AudienceUris koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-120">Clears the audienceUris collection.</span></span> <span data-ttu-id="bb3a0-121">Tüm tanımlayıcılar koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-121">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="bb3a0-122">`value`AudienceUri koleksiyonundan özniteliği tarafından BELIRTILEN URI 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-122">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="bb3a0-123">`value`Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-123">The `value` attribute is required.</span></span> <span data-ttu-id="bb3a0-124">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-124">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb3a0-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb3a0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bb3a0-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb3a0-126">Element</span></span>|<span data-ttu-id="bb3a0-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb3a0-127">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="bb3a0-128">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb3a0-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb3a0-129">Remarks</span></span>  
 <span data-ttu-id="bb3a0-130">Varsayılan olarak, koleksiyon boştur; `<add>` `<clear>` `<remove>` koleksiyonu değiştirmek için, ve öğelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-130">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="bb3a0-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nesneler, nesnelerinde izin verilen tüm hedef KITLE URI kısıtlamalarını yapılandırmak için hedef KITLE URI koleksiyonundaki değerleri kullanır <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="bb3a0-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="bb3a0-132">`<audienceUris>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> .</span><span class="sxs-lookup"><span data-stu-id="bb3a0-132">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="bb3a0-133">Koleksiyona eklenen tek bir URI sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElement> .</span><span class="sxs-lookup"><span data-stu-id="bb3a0-133">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb3a0-134">Öğenin `<audienceUris>` bir alt öğesi olarak kullanılması [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-134">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="bb3a0-135">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="bb3a0-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb3a0-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb3a0-136">Example</span></span>  
 <span data-ttu-id="bb3a0-137">Aşağıdaki XML, bir uygulama için kabul edilebilir hedef kitle URI 'Lerinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-137">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="bb3a0-138">Bu örnek, tek bir URI 'yi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-138">This example configures a single URI.</span></span> <span data-ttu-id="bb3a0-139">Bu URI için kapsamlı belirteçler kabul edilecek, diğerleri reddedilir.</span><span class="sxs-lookup"><span data-stu-id="bb3a0-139">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
