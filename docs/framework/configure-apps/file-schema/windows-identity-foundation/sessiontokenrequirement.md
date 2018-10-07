---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4d5d2348f04ace7596a3a513c5106ea612dc17b7
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840894"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="3e826-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="3e826-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="3e826-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="3e826-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="3e826-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3e826-104">\<system.identityModel></span></span>  
<span data-ttu-id="3e826-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3e826-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3e826-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3e826-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3e826-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3e826-107">\<add></span></span>  
<span data-ttu-id="3e826-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="3e826-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e826-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e826-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e826-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e826-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e826-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e826-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e826-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e826-112">Attributes</span></span>  
  
|<span data-ttu-id="3e826-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e826-113">Attribute</span></span>|<span data-ttu-id="3e826-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e826-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e826-115">ömür</span><span class="sxs-lookup"><span data-stu-id="3e826-115">lifetime</span></span>|<span data-ttu-id="3e826-116">Oturum belirteç ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e826-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e826-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e826-117">Child Elements</span></span>  
 <span data-ttu-id="3e826-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e826-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e826-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e826-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3e826-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e826-120">Element</span></span>|<span data-ttu-id="3e826-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e826-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e826-122">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3e826-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="3e826-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="3e826-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e826-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e826-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
