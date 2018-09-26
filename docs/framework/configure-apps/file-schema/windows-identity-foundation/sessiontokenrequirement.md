---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4d5d2348f04ace7596a3a513c5106ea612dc17b7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070098"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="881d6-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="881d6-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="881d6-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="881d6-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="881d6-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="881d6-104">\<system.identityModel></span></span>  
<span data-ttu-id="881d6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="881d6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="881d6-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="881d6-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="881d6-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="881d6-107">\<add></span></span>  
<span data-ttu-id="881d6-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="881d6-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="881d6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="881d6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="881d6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="881d6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="881d6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="881d6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="881d6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="881d6-112">Attributes</span></span>  
  
|<span data-ttu-id="881d6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="881d6-113">Attribute</span></span>|<span data-ttu-id="881d6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="881d6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="881d6-115">ömür</span><span class="sxs-lookup"><span data-stu-id="881d6-115">lifetime</span></span>|<span data-ttu-id="881d6-116">Oturum belirteç ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="881d6-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="881d6-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="881d6-117">Child Elements</span></span>  
 <span data-ttu-id="881d6-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="881d6-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="881d6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="881d6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="881d6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="881d6-120">Element</span></span>|<span data-ttu-id="881d6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="881d6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="881d6-122">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="881d6-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="881d6-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="881d6-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="881d6-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="881d6-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
