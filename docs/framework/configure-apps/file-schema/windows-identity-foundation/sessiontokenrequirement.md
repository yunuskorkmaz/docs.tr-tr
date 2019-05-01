---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793776"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="d4240-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d4240-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="d4240-102">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="d4240-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d4240-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d4240-103">\<system.identityModel></span></span>  
<span data-ttu-id="d4240-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d4240-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d4240-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d4240-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d4240-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d4240-106">\<add></span></span>  
<span data-ttu-id="d4240-107">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d4240-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4240-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4240-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4240-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4240-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d4240-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4240-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4240-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4240-111">Attributes</span></span>  
  
|<span data-ttu-id="d4240-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4240-112">Attribute</span></span>|<span data-ttu-id="d4240-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4240-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4240-114">ömür</span><span class="sxs-lookup"><span data-stu-id="d4240-114">lifetime</span></span>|<span data-ttu-id="d4240-115">Oturum belirteç ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4240-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4240-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4240-116">Child Elements</span></span>  
 <span data-ttu-id="d4240-117">None</span><span class="sxs-lookup"><span data-stu-id="d4240-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4240-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4240-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d4240-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4240-119">Element</span></span>|<span data-ttu-id="d4240-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4240-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4240-121">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d4240-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="d4240-122">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="d4240-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4240-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4240-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
