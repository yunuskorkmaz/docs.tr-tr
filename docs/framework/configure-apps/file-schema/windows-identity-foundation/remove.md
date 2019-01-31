---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: a54957458311e2d5941d1aa1c2486a2f66994d9b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288138"
---
# <a name="remove"></a><span data-ttu-id="32add-101">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="32add-101">\<remove></span></span>
<span data-ttu-id="32add-102">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="32add-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="32add-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="32add-103">\<system.identityModel></span></span>  
<span data-ttu-id="32add-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="32add-104">\<identityConfiguration></span></span>  
<span data-ttu-id="32add-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="32add-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="32add-106">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="32add-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32add-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32add-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32add-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32add-108">Attributes and Elements</span></span>  
 <span data-ttu-id="32add-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32add-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32add-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32add-110">Attributes</span></span>  
  
|<span data-ttu-id="32add-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="32add-111">Attribute</span></span>|<span data-ttu-id="32add-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32add-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32add-113">türü</span><span class="sxs-lookup"><span data-stu-id="32add-113">type</span></span>|<span data-ttu-id="32add-114">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="32add-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="32add-115">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="32add-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="32add-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32add-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32add-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32add-117">Child Elements</span></span>  
 <span data-ttu-id="32add-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="32add-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32add-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32add-119">Parent Elements</span></span>  
  
|<span data-ttu-id="32add-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="32add-120">Element</span></span>|<span data-ttu-id="32add-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32add-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32add-122">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="32add-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="32add-123">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="32add-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="32add-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="32add-124">Example</span></span>  
 <span data-ttu-id="32add-125">Aşağıdaki XML kullanımını gösterir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi bir özel oturum belirteci işleyicisi ile değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="32add-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="32add-126">XML alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="32add-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
