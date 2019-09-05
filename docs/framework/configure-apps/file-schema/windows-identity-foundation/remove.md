---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251922"
---
# <a name="remove"></a><span data-ttu-id="696e3-101">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="696e3-101">\<remove></span></span>
<span data-ttu-id="696e3-102">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="696e3-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
<span data-ttu-id="696e3-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="696e3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="696e3-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="696e3-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="696e3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="696e3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="696e3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="696e3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="696e3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="696e3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696e3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="696e3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="696e3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="696e3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="696e3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="696e3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="696e3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="696e3-111">Attributes</span></span>  
  
|<span data-ttu-id="696e3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="696e3-112">Attribute</span></span>|<span data-ttu-id="696e3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="696e3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="696e3-114">türü</span><span class="sxs-lookup"><span data-stu-id="696e3-114">type</span></span>|<span data-ttu-id="696e3-115">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="696e3-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="696e3-116">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="696e3-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="696e3-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="696e3-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="696e3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="696e3-118">Child Elements</span></span>  
 <span data-ttu-id="696e3-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="696e3-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="696e3-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="696e3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="696e3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="696e3-121">Element</span></span>|<span data-ttu-id="696e3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="696e3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="696e3-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="696e3-123">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="696e3-124">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="696e3-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="696e3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="696e3-125">Example</span></span>  
 <span data-ttu-id="696e3-126">Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel `<add>` bir `<remove>` oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="696e3-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="696e3-127">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="696e3-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
