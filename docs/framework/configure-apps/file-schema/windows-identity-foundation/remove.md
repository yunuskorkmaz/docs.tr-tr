---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 596cab4494ef3ba200fd0a046d7935f648fb7c4f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422194"
---
# <a name="ltremovegt"></a><span data-ttu-id="1c96d-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="1c96d-102">&lt;remove&gt;</span></span>
<span data-ttu-id="1c96d-103">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c96d-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="1c96d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1c96d-104">\<system.identityModel></span></span>  
<span data-ttu-id="1c96d-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1c96d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1c96d-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1c96d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1c96d-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="1c96d-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c96d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c96d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c96d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c96d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1c96d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c96d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c96d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c96d-111">Attributes</span></span>  
  
|<span data-ttu-id="1c96d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c96d-112">Attribute</span></span>|<span data-ttu-id="1c96d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c96d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c96d-114">türü</span><span class="sxs-lookup"><span data-stu-id="1c96d-114">type</span></span>|<span data-ttu-id="1c96d-115">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="1c96d-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="1c96d-116">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="1c96d-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="1c96d-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1c96d-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c96d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c96d-118">Child Elements</span></span>  
 <span data-ttu-id="1c96d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c96d-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c96d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c96d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1c96d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c96d-121">Element</span></span>|<span data-ttu-id="1c96d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c96d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c96d-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1c96d-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="1c96d-124">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c96d-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1c96d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c96d-125">Example</span></span>  
 <span data-ttu-id="1c96d-126">Aşağıdaki XML kullanımını gösterir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi bir özel oturum belirteci işleyicisi ile değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="1c96d-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="1c96d-127">XML alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="1c96d-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
