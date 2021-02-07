---
description: 'Hakkında daha fazla bilgi edinin: <remove>'
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 942148f677e10bbab7b86acfba2d0fdfb1b10ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664073"
---
# \<remove>

<span data-ttu-id="542b7-102">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="542b7-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="542b7-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="542b7-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="542b7-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="542b7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="542b7-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="542b7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="542b7-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="542b7-106">Attributes</span></span>  
  
|<span data-ttu-id="542b7-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="542b7-107">Attribute</span></span>|<span data-ttu-id="542b7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="542b7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="542b7-109">tür</span><span class="sxs-lookup"><span data-stu-id="542b7-109">type</span></span>|<span data-ttu-id="542b7-110">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="542b7-110">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="542b7-111">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="542b7-111">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="542b7-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="542b7-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="542b7-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="542b7-113">Child Elements</span></span>  

 <span data-ttu-id="542b7-114">Yok</span><span class="sxs-lookup"><span data-stu-id="542b7-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="542b7-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="542b7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="542b7-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="542b7-116">Element</span></span>|<span data-ttu-id="542b7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="542b7-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="542b7-118">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="542b7-118">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="542b7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="542b7-119">Example</span></span>  

 <span data-ttu-id="542b7-120">Aşağıdaki XML, `<add>` `<remove>` varsayılan oturum belirteci işleyicisini özel bir oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="542b7-120">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="542b7-121">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="542b7-121">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
