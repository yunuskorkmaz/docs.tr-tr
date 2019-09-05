---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 968c48df9e92a1dfbfb6e248b06cf4f97cece8b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251825"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="bce6a-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="bce6a-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="bce6a-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bce6a-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="bce6a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bce6a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bce6a-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="bce6a-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="bce6a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="bce6a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="bce6a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="bce6a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="bce6a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add.md)</span><span class="sxs-lookup"><span data-stu-id="bce6a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="bce6a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="bce6a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bce6a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bce6a-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bce6a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bce6a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bce6a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bce6a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bce6a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bce6a-112">Attributes</span></span>  
  
|<span data-ttu-id="bce6a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bce6a-113">Attribute</span></span>|<span data-ttu-id="bce6a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bce6a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bce6a-115">ömür</span><span class="sxs-lookup"><span data-stu-id="bce6a-115">lifetime</span></span>|<span data-ttu-id="bce6a-116">Oturum belirteçlerinin ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bce6a-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bce6a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bce6a-117">Child Elements</span></span>  
 <span data-ttu-id="bce6a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="bce6a-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bce6a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bce6a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bce6a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="bce6a-120">Element</span></span>|<span data-ttu-id="bce6a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bce6a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bce6a-122">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="bce6a-122">\<add></span></span>](add.md)|<span data-ttu-id="bce6a-123">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="bce6a-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bce6a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="bce6a-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
