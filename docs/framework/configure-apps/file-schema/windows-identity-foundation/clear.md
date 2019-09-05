---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252038"
---
# <a name="clear"></a><span data-ttu-id="395de-101">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="395de-101">\<clear></span></span>
<span data-ttu-id="395de-102">Tüm güvenlik belirteci işleyicilerini geçerli belirteç işleyici koleksiyonundan temizler.</span><span class="sxs-lookup"><span data-stu-id="395de-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
<span data-ttu-id="395de-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="395de-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="395de-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="395de-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="395de-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="395de-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="395de-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="395de-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="395de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Temizle**</span><span class="sxs-lookup"><span data-stu-id="395de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="395de-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="395de-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="395de-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="395de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="395de-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="395de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="395de-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="395de-111">Attributes</span></span>  
 <span data-ttu-id="395de-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="395de-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="395de-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="395de-113">Child Elements</span></span>  
 <span data-ttu-id="395de-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="395de-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="395de-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="395de-115">Parent Elements</span></span>  
  
|<span data-ttu-id="395de-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="395de-116">Element</span></span>|<span data-ttu-id="395de-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="395de-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="395de-118">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="395de-118">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="395de-119">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="395de-119">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
