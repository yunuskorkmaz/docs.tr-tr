---
title: '&lt;sessionTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5a141dd83cb7ef1271906871097eb68da174d22f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="49c45-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="49c45-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="49c45-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="49c45-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="49c45-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="49c45-104">\<system.identityModel></span></span>  
<span data-ttu-id="49c45-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="49c45-105">\<identityConfiguration></span></span>  
<span data-ttu-id="49c45-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="49c45-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="49c45-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="49c45-107">\<add></span></span>  
<span data-ttu-id="49c45-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="49c45-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c45-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49c45-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49c45-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49c45-110">Attributes and Elements</span></span>  
 <span data-ttu-id="49c45-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49c45-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49c45-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49c45-112">Attributes</span></span>  
  
|<span data-ttu-id="49c45-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49c45-113">Attribute</span></span>|<span data-ttu-id="49c45-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49c45-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49c45-115">ömür</span><span class="sxs-lookup"><span data-stu-id="49c45-115">lifetime</span></span>|<span data-ttu-id="49c45-116">Oturum belirteçleri ömrü belirtir.</span><span class="sxs-lookup"><span data-stu-id="49c45-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49c45-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49c45-117">Child Elements</span></span>  
 <span data-ttu-id="49c45-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="49c45-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49c45-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49c45-119">Parent Elements</span></span>  
  
|<span data-ttu-id="49c45-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="49c45-120">Element</span></span>|<span data-ttu-id="49c45-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49c45-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49c45-122">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="49c45-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="49c45-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="49c45-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="49c45-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="49c45-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
