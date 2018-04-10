---
title: '&lt;remove&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: 5
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: fb62bbe8b52032708dddd62dd895e61ba8c1c5e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltremovegt"></a><span data-ttu-id="eb418-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="eb418-102">&lt;remove&gt;</span></span>
<span data-ttu-id="eb418-103">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="eb418-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="eb418-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="eb418-104">\<system.identityModel></span></span>  
<span data-ttu-id="eb418-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="eb418-105">\<identityConfiguration></span></span>  
<span data-ttu-id="eb418-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="eb418-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="eb418-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="eb418-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb418-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb418-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb418-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb418-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eb418-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb418-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb418-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eb418-111">Attributes</span></span>  
  
|<span data-ttu-id="eb418-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eb418-112">Attribute</span></span>|<span data-ttu-id="eb418-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb418-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb418-114">türü</span><span class="sxs-lookup"><span data-stu-id="eb418-114">type</span></span>|<span data-ttu-id="eb418-115">Kaldırılacak belirteç işleyici CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="eb418-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="eb418-116">Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="eb418-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="eb418-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="eb418-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb418-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb418-118">Child Elements</span></span>  
 <span data-ttu-id="eb418-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="eb418-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb418-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb418-120">Parent Elements</span></span>  
  
|<span data-ttu-id="eb418-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb418-121">Element</span></span>|<span data-ttu-id="eb418-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb418-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb418-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="eb418-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="eb418-124">Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb418-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eb418-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb418-125">Example</span></span>  
 <span data-ttu-id="eb418-126">Aşağıdaki XML kullanımı gösterilmiştir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi özel oturum belirteci işleyicisi ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eb418-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="eb418-127">XML alınırlar `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="eb418-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
