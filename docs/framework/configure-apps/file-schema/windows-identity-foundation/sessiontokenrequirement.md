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
ms.openlocfilehash: 8b729f588d2195992b231661f7bb718240141fdd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="5da0b-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="5da0b-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="5da0b-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="5da0b-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="5da0b-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="5da0b-104">\<system.identityModel></span></span>  
<span data-ttu-id="5da0b-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5da0b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5da0b-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5da0b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5da0b-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="5da0b-107">\<add></span></span>  
<span data-ttu-id="5da0b-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="5da0b-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da0b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5da0b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5da0b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5da0b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5da0b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5da0b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5da0b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5da0b-112">Attributes</span></span>  
  
|<span data-ttu-id="5da0b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5da0b-113">Attribute</span></span>|<span data-ttu-id="5da0b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5da0b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5da0b-115">ömür</span><span class="sxs-lookup"><span data-stu-id="5da0b-115">lifetime</span></span>|<span data-ttu-id="5da0b-116">Oturum belirteçleri ömrü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5da0b-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5da0b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5da0b-117">Child Elements</span></span>  
 <span data-ttu-id="5da0b-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="5da0b-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5da0b-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5da0b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5da0b-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5da0b-120">Element</span></span>|<span data-ttu-id="5da0b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5da0b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5da0b-122">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="5da0b-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="5da0b-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="5da0b-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5da0b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5da0b-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
