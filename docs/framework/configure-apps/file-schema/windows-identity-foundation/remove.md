---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251922"
---
# \<remove>
<span data-ttu-id="83ab0-101">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="83ab0-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="83ab0-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83ab0-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83ab0-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83ab0-103">Attributes and Elements</span></span>  
 <span data-ttu-id="83ab0-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83ab0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83ab0-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83ab0-105">Attributes</span></span>  
  
|<span data-ttu-id="83ab0-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83ab0-106">Attribute</span></span>|<span data-ttu-id="83ab0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83ab0-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83ab0-108">tür</span><span class="sxs-lookup"><span data-stu-id="83ab0-108">type</span></span>|<span data-ttu-id="83ab0-109">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="83ab0-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="83ab0-110">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="83ab0-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="83ab0-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="83ab0-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83ab0-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83ab0-112">Child Elements</span></span>  
 <span data-ttu-id="83ab0-113">Yok</span><span class="sxs-lookup"><span data-stu-id="83ab0-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83ab0-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83ab0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="83ab0-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="83ab0-115">Element</span></span>|<span data-ttu-id="83ab0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83ab0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="83ab0-117">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="83ab0-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="83ab0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="83ab0-118">Example</span></span>  
 <span data-ttu-id="83ab0-119">Aşağıdaki XML, `<add>` `<remove>` varsayılan oturum belirteci işleyicisini özel bir oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="83ab0-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="83ab0-120">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="83ab0-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
