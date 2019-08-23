---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 254d34149892abeaf31b9227f7567eb0a66ec0b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943673"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="b43b4-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="b43b4-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="b43b4-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b43b4-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="b43b4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b43b4-103">\<system.identityModel></span></span>  
<span data-ttu-id="b43b4-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b43b4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="b43b4-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b43b4-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b43b4-106">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="b43b4-106">\<add></span></span>  
<span data-ttu-id="b43b4-107">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="b43b4-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43b4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b43b4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b43b4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b43b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b43b4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b43b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b43b4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b43b4-111">Attributes</span></span>  
  
|<span data-ttu-id="b43b4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b43b4-112">Attribute</span></span>|<span data-ttu-id="b43b4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b43b4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b43b4-114">ömür</span><span class="sxs-lookup"><span data-stu-id="b43b4-114">lifetime</span></span>|<span data-ttu-id="b43b4-115">Oturum belirteçlerinin ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b43b4-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b43b4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b43b4-116">Child Elements</span></span>  
 <span data-ttu-id="b43b4-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="b43b4-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b43b4-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b43b4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b43b4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="b43b4-119">Element</span></span>|<span data-ttu-id="b43b4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b43b4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b43b4-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="b43b4-121">\<add></span></span>](add.md)|<span data-ttu-id="b43b4-122">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="b43b4-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b43b4-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b43b4-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
