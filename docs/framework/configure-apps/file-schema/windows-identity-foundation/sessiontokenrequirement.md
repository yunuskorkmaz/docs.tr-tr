---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152547"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="b7e59-101">\<oturumTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="b7e59-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="b7e59-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7e59-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="b7e59-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7e59-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7e59-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b7e59-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b7e59-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b7e59-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b7e59-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="b7e59-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="b7e59-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add.md)</span><span class="sxs-lookup"><span data-stu-id="b7e59-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="b7e59-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oturumTokenRequirement>**</span><span class="sxs-lookup"><span data-stu-id="b7e59-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e59-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7e59-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7e59-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7e59-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7e59-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7e59-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7e59-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7e59-112">Attributes</span></span>  
  
|<span data-ttu-id="b7e59-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b7e59-113">Attribute</span></span>|<span data-ttu-id="b7e59-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7e59-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7e59-115">ömür</span><span class="sxs-lookup"><span data-stu-id="b7e59-115">lifetime</span></span>|<span data-ttu-id="b7e59-116">Oturum belirteçlerinin kullanım ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7e59-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7e59-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7e59-117">Child Elements</span></span>  
 <span data-ttu-id="b7e59-118">None</span><span class="sxs-lookup"><span data-stu-id="b7e59-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7e59-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7e59-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b7e59-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7e59-120">Element</span></span>|<span data-ttu-id="b7e59-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7e59-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e59-122">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="b7e59-122">\<add></span></span>](add.md)|<span data-ttu-id="b7e59-123">Belirteç işleyicisi koleksiyonuna belirtilen güvenlik belirteci işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="b7e59-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7e59-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7e59-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
