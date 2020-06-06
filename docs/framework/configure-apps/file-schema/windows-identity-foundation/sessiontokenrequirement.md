---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152547"
---
# \<sessionTokenRequirement>
<span data-ttu-id="c5cd3-101"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5cd3-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="c5cd3-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5cd3-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5cd3-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5cd3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5cd3-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5cd3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5cd3-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5cd3-105">Attributes</span></span>  
  
|<span data-ttu-id="c5cd3-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5cd3-106">Attribute</span></span>|<span data-ttu-id="c5cd3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5cd3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5cd3-108">ömür</span><span class="sxs-lookup"><span data-stu-id="c5cd3-108">lifetime</span></span>|<span data-ttu-id="c5cd3-109">Oturum belirteçlerinin ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5cd3-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5cd3-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5cd3-110">Child Elements</span></span>  
 <span data-ttu-id="c5cd3-111">Yok</span><span class="sxs-lookup"><span data-stu-id="c5cd3-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5cd3-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5cd3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c5cd3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5cd3-113">Element</span></span>|<span data-ttu-id="c5cd3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5cd3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="c5cd3-115">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="c5cd3-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5cd3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5cd3-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
