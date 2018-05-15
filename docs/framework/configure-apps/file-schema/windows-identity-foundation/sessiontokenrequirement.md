---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6c40948633eaf892db06e9bba756158dfc3c4a2e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="be7ae-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="be7ae-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="be7ae-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="be7ae-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="be7ae-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="be7ae-104">\<system.identityModel></span></span>  
<span data-ttu-id="be7ae-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="be7ae-105">\<identityConfiguration></span></span>  
<span data-ttu-id="be7ae-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="be7ae-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="be7ae-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="be7ae-107">\<add></span></span>  
<span data-ttu-id="be7ae-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="be7ae-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7ae-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be7ae-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be7ae-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be7ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="be7ae-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be7ae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be7ae-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be7ae-112">Attributes</span></span>  
  
|<span data-ttu-id="be7ae-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="be7ae-113">Attribute</span></span>|<span data-ttu-id="be7ae-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be7ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be7ae-115">ömür</span><span class="sxs-lookup"><span data-stu-id="be7ae-115">lifetime</span></span>|<span data-ttu-id="be7ae-116">Oturum belirteçleri ömrü belirtir.</span><span class="sxs-lookup"><span data-stu-id="be7ae-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be7ae-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be7ae-117">Child Elements</span></span>  
 <span data-ttu-id="be7ae-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="be7ae-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be7ae-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be7ae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="be7ae-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="be7ae-120">Element</span></span>|<span data-ttu-id="be7ae-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be7ae-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be7ae-122">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="be7ae-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="be7ae-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="be7ae-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="be7ae-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="be7ae-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
