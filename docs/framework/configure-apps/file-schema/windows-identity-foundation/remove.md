---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 11aeed0277fc13cbd9a65232311bd575a4a81ff7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942579"
---
# <a name="remove"></a><span data-ttu-id="315c9-101">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="315c9-101">\<remove></span></span>
<span data-ttu-id="315c9-102">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="315c9-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="315c9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="315c9-103">\<system.identityModel></span></span>  
<span data-ttu-id="315c9-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="315c9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="315c9-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="315c9-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="315c9-106">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="315c9-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315c9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="315c9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="315c9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="315c9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="315c9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="315c9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="315c9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="315c9-110">Attributes</span></span>  
  
|<span data-ttu-id="315c9-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="315c9-111">Attribute</span></span>|<span data-ttu-id="315c9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="315c9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="315c9-113">türü</span><span class="sxs-lookup"><span data-stu-id="315c9-113">type</span></span>|<span data-ttu-id="315c9-114">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="315c9-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="315c9-115">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="315c9-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="315c9-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="315c9-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="315c9-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="315c9-117">Child Elements</span></span>  
 <span data-ttu-id="315c9-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="315c9-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="315c9-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="315c9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="315c9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="315c9-120">Element</span></span>|<span data-ttu-id="315c9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="315c9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="315c9-122">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="315c9-122">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="315c9-123">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="315c9-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="315c9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="315c9-124">Example</span></span>  
 <span data-ttu-id="315c9-125">Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel `<add>` bir `<remove>` oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="315c9-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="315c9-126">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="315c9-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
