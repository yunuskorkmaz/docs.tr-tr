---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 410fef1a43f9202d56c4957b1162c53ee056ae3f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074921"
---
# <a name="ltremovegt"></a><span data-ttu-id="82ead-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="82ead-102">&lt;remove&gt;</span></span>
<span data-ttu-id="82ead-103">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="82ead-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="82ead-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="82ead-104">\<system.identityModel></span></span>  
<span data-ttu-id="82ead-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="82ead-105">\<identityConfiguration></span></span>  
<span data-ttu-id="82ead-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="82ead-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="82ead-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="82ead-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ead-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82ead-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82ead-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82ead-109">Attributes and Elements</span></span>  
 <span data-ttu-id="82ead-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82ead-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82ead-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82ead-111">Attributes</span></span>  
  
|<span data-ttu-id="82ead-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="82ead-112">Attribute</span></span>|<span data-ttu-id="82ead-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82ead-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82ead-114">türü</span><span class="sxs-lookup"><span data-stu-id="82ead-114">type</span></span>|<span data-ttu-id="82ead-115">Kaldırılacak belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="82ead-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="82ead-116">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="82ead-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="82ead-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="82ead-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82ead-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82ead-118">Child Elements</span></span>  
 <span data-ttu-id="82ead-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="82ead-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82ead-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82ead-120">Parent Elements</span></span>  
  
|<span data-ttu-id="82ead-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="82ead-121">Element</span></span>|<span data-ttu-id="82ead-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82ead-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82ead-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="82ead-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="82ead-124">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="82ead-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82ead-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="82ead-125">Example</span></span>  
 <span data-ttu-id="82ead-126">Aşağıdaki XML kullanımını gösterir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi bir özel oturum belirteci işleyicisi ile değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="82ead-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="82ead-127">XML alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="82ead-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
