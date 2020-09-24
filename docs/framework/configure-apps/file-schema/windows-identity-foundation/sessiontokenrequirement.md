---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4560c55cee5caf975e83ce9d4dc0b379ab905f8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156855"
---
# \<sessionTokenRequirement>

<span data-ttu-id="8f4bc-101"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f4bc-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="8f4bc-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f4bc-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f4bc-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f4bc-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8f4bc-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f4bc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f4bc-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f4bc-105">Attributes</span></span>  
  
|<span data-ttu-id="8f4bc-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f4bc-106">Attribute</span></span>|<span data-ttu-id="8f4bc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f4bc-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f4bc-108">ömür</span><span class="sxs-lookup"><span data-stu-id="8f4bc-108">lifetime</span></span>|<span data-ttu-id="8f4bc-109">Oturum belirteçlerinin ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f4bc-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f4bc-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f4bc-110">Child Elements</span></span>  

 <span data-ttu-id="8f4bc-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="8f4bc-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f4bc-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f4bc-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8f4bc-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f4bc-113">Element</span></span>|<span data-ttu-id="8f4bc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f4bc-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="8f4bc-115">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="8f4bc-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8f4bc-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f4bc-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
