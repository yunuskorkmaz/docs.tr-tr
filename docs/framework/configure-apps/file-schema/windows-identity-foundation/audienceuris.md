---
description: 'Hakkında daha fazla bilgi edinin: <audienceUris>'
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 98b411e73d4b9941e65daaf5d1d63285cdc90fd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681857"
---
# \<audienceUris>

<span data-ttu-id="52d26-102">Bağlı olan tarafın (RP) kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="52d26-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="52d26-103">Belirteçleri, izin verilen hedef kitle URI 'lerinden biri kapsamında olmadıkları müddetçe kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="52d26-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="52d26-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="52d26-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52d26-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52d26-105">Attributes and Elements</span></span>  

 <span data-ttu-id="52d26-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52d26-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52d26-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52d26-107">Attributes</span></span>  
  
|<span data-ttu-id="52d26-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52d26-108">Attribute</span></span>|<span data-ttu-id="52d26-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52d26-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52d26-110">mod</span><span class="sxs-lookup"><span data-stu-id="52d26-110">mode</span></span>|<span data-ttu-id="52d26-111"><xref:System.IdentityModel.Selectors.AudienceUriMode>Hedef kitle kısıtlamasının bir gelen belirtece uygulanıp uygulanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="52d26-111">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="52d26-112">Olası değerler şunlardır "Always", "hiçbir" ve "Yataerkeyonly".</span><span class="sxs-lookup"><span data-stu-id="52d26-112">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="52d26-113">Varsayılan değer "Always" dır.</span><span class="sxs-lookup"><span data-stu-id="52d26-113">The default is "Always".</span></span> <span data-ttu-id="52d26-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="52d26-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52d26-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52d26-115">Child Elements</span></span>  
  
|<span data-ttu-id="52d26-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="52d26-116">Element</span></span>|<span data-ttu-id="52d26-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52d26-117">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="52d26-118">Öznitelik tarafından belirtilen URI `value` 'Yi AudienceUri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="52d26-118">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="52d26-119">`value`Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="52d26-119">The `value` attribute is required.</span></span> <span data-ttu-id="52d26-120">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="52d26-120">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="52d26-121">AudienceUris koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="52d26-121">Clears the audienceUris collection.</span></span> <span data-ttu-id="52d26-122">Tüm tanımlayıcılar koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="52d26-122">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="52d26-123">`value`AudienceUri koleksiyonundan özniteliği tarafından BELIRTILEN URI 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="52d26-123">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="52d26-124">`value`Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="52d26-124">The `value` attribute is required.</span></span> <span data-ttu-id="52d26-125">URI, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="52d26-125">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52d26-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52d26-126">Parent Elements</span></span>  
  
|<span data-ttu-id="52d26-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="52d26-127">Element</span></span>|<span data-ttu-id="52d26-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52d26-128">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="52d26-129">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="52d26-129">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d26-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52d26-130">Remarks</span></span>  

 <span data-ttu-id="52d26-131">Varsayılan olarak, koleksiyon boştur; `<add>` `<clear>` `<remove>` koleksiyonu değiştirmek için, ve öğelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="52d26-131">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="52d26-132"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nesneler, nesnelerinde izin verilen tüm hedef KITLE URI kısıtlamalarını yapılandırmak için hedef KITLE URI koleksiyonundaki değerleri kullanır <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="52d26-132"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="52d26-133">`<audienceUris>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> .</span><span class="sxs-lookup"><span data-stu-id="52d26-133">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="52d26-134">Koleksiyona eklenen tek bir URI sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElement> .</span><span class="sxs-lookup"><span data-stu-id="52d26-134">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52d26-135">Öğenin `<audienceUris>` bir alt öğesi olarak kullanılması [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="52d26-135">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="52d26-136">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="52d26-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52d26-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="52d26-137">Example</span></span>  

 <span data-ttu-id="52d26-138">Aşağıdaki XML, bir uygulama için kabul edilebilir hedef kitle URI 'Lerinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52d26-138">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="52d26-139">Bu örnek, tek bir URI 'yi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="52d26-139">This example configures a single URI.</span></span> <span data-ttu-id="52d26-140">Bu URI için kapsamlı belirteçler kabul edilecek, diğerleri reddedilir.</span><span class="sxs-lookup"><span data-stu-id="52d26-140">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
