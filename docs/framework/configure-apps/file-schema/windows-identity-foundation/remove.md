---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 17c4d4289cf90b66d52986c054d4807ecff2b3d8
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758423"
---
# <a name="remove"></a><span data-ttu-id="83e3c-101">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="83e3c-101">\<remove></span></span>
<span data-ttu-id="83e3c-102">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="83e3c-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="83e3c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="83e3c-103">\<system.identityModel></span></span>  
<span data-ttu-id="83e3c-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="83e3c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="83e3c-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="83e3c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="83e3c-106">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="83e3c-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e3c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83e3c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83e3c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83e3c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="83e3c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83e3c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83e3c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83e3c-110">Attributes</span></span>  
  
|<span data-ttu-id="83e3c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83e3c-111">Attribute</span></span>|<span data-ttu-id="83e3c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83e3c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83e3c-113">türü</span><span class="sxs-lookup"><span data-stu-id="83e3c-113">type</span></span>|<span data-ttu-id="83e3c-114">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="83e3c-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="83e3c-115">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="83e3c-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="83e3c-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="83e3c-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83e3c-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83e3c-117">Child Elements</span></span>  
 <span data-ttu-id="83e3c-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="83e3c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83e3c-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83e3c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="83e3c-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="83e3c-120">Element</span></span>|<span data-ttu-id="83e3c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83e3c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83e3c-122">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="83e3c-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="83e3c-123">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="83e3c-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="83e3c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="83e3c-124">Example</span></span>  
 <span data-ttu-id="83e3c-125">Aşağıdaki XML kullanımını gösterir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi bir özel oturum belirteci işleyicisi ile değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="83e3c-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="83e3c-126">XML alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="83e3c-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
