---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: c4ba7b6f2a9b9092c5f24d424c6de2b0f510ac88
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165006"
---
# \<remove>

<span data-ttu-id="a4fd6-101">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="a4fd6-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4fd6-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4fd6-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4fd6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a4fd6-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4fd6-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4fd6-105">Attributes</span></span>  
  
|<span data-ttu-id="a4fd6-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4fd6-106">Attribute</span></span>|<span data-ttu-id="a4fd6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4fd6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4fd6-108">tür</span><span class="sxs-lookup"><span data-stu-id="a4fd6-108">type</span></span>|<span data-ttu-id="a4fd6-109">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="a4fd6-110">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="a4fd6-110">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="a4fd6-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4fd6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4fd6-112">Child Elements</span></span>  

 <span data-ttu-id="a4fd6-113">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="a4fd6-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4fd6-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4fd6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a4fd6-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4fd6-115">Element</span></span>|<span data-ttu-id="a4fd6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4fd6-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="a4fd6-117">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4fd6-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4fd6-118">Example</span></span>  

 <span data-ttu-id="a4fd6-119">Aşağıdaki XML, `<add>` `<remove>` varsayılan oturum belirteci işleyicisini özel bir oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="a4fd6-120">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="a4fd6-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
