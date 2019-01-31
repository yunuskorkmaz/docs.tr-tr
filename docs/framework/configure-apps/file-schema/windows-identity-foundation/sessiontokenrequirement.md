---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271908"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="f69c0-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f69c0-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="f69c0-102">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="f69c0-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="f69c0-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f69c0-103">\<system.identityModel></span></span>  
<span data-ttu-id="f69c0-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f69c0-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f69c0-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="f69c0-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f69c0-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="f69c0-106">\<add></span></span>  
<span data-ttu-id="f69c0-107">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f69c0-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69c0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f69c0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f69c0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f69c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f69c0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f69c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f69c0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f69c0-111">Attributes</span></span>  
  
|<span data-ttu-id="f69c0-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f69c0-112">Attribute</span></span>|<span data-ttu-id="f69c0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f69c0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f69c0-114">ömür</span><span class="sxs-lookup"><span data-stu-id="f69c0-114">lifetime</span></span>|<span data-ttu-id="f69c0-115">Oturum belirteç ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f69c0-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f69c0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f69c0-116">Child Elements</span></span>  
 <span data-ttu-id="f69c0-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f69c0-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f69c0-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f69c0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f69c0-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="f69c0-119">Element</span></span>|<span data-ttu-id="f69c0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f69c0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f69c0-121">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="f69c0-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="f69c0-122">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="f69c0-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f69c0-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="f69c0-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
