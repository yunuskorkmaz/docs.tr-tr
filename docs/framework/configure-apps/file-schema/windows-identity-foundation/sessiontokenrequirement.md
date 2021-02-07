---
description: 'Hakkında daha fazla bilgi edinin: <sessionTokenRequirement>'
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 8f2868df4939dc0dc7c779eb9ca5a35a6b996fc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698277"
---
# \<sessionTokenRequirement>

<span data-ttu-id="25718-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="25718-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="25718-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="25718-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25718-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25718-104">Attributes and Elements</span></span>  

 <span data-ttu-id="25718-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25718-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25718-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25718-106">Attributes</span></span>  
  
|<span data-ttu-id="25718-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="25718-107">Attribute</span></span>|<span data-ttu-id="25718-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25718-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25718-109">ömür</span><span class="sxs-lookup"><span data-stu-id="25718-109">lifetime</span></span>|<span data-ttu-id="25718-110">Oturum belirteçlerinin ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="25718-110">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25718-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25718-111">Child Elements</span></span>  

 <span data-ttu-id="25718-112">Yok</span><span class="sxs-lookup"><span data-stu-id="25718-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25718-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25718-113">Parent Elements</span></span>  
  
|<span data-ttu-id="25718-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="25718-114">Element</span></span>|<span data-ttu-id="25718-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25718-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="25718-116">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="25718-116">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="25718-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="25718-117">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
