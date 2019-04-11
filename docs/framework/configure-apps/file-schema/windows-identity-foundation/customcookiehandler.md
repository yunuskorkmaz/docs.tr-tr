---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 0129c63fe17b63889a77ea1a56c0d7e657def859
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224057"
---
# <a name="customcookiehandler"></a><span data-ttu-id="2f9a9-101">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2f9a9-101">\<customCookieHandler></span></span>
<span data-ttu-id="2f9a9-102">Özel bir tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="2f9a9-103">Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` "Özel" bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="2f9a9-104">Özel tür nesnesinden türetilmesi <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="2f9a9-105">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="2f9a9-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="2f9a9-106">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="2f9a9-106">\<federationConfiguration></span></span>  
<span data-ttu-id="2f9a9-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2f9a9-107">\<cookieHandler></span></span>  
<span data-ttu-id="2f9a9-108">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2f9a9-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f9a9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f9a9-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f9a9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f9a9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2f9a9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f9a9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2f9a9-112">Attributes</span></span>  
  
|<span data-ttu-id="2f9a9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2f9a9-113">Attribute</span></span>|<span data-ttu-id="2f9a9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f9a9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f9a9-115"> türü</span><span class="sxs-lookup"><span data-stu-id="2f9a9-115">type</span></span>|<span data-ttu-id="2f9a9-116">Öğesinden türetilen özel bir türü belirtiyor <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="2f9a9-117">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="2f9a9-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f9a9-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f9a9-118">Child Elements</span></span>  
 <span data-ttu-id="2f9a9-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f9a9-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f9a9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2f9a9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2f9a9-121">Element</span></span>|<span data-ttu-id="2f9a9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f9a9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f9a9-123">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2f9a9-123">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="2f9a9-124">Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f9a9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f9a9-125">Remarks</span></span>  
 <span data-ttu-id="2f9a9-126">Ayarlayarak özel bir tanımlama bilgisi işleyici belirttiğinizde `mode` özniteliği `<cookieHandler>` öğesi "Özel" dahil ederek özel tanımlama bilgisi işleyicisinin türü belirtmelisiniz bir `<customCookieHandler>` tanımlama bilgisi işleyici türe başvuran alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="2f9a9-127">Bu öğe olamaz belirtilen `mode` "Öbekli" veya "Varsayılan" özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="2f9a9-128">Özel bir tanımlama bilgisi işleyicileri türetilmesi gereken <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="2f9a9-129">`<customCookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.CustomTypeElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f9a9-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f9a9-130">Example</span></span>  
 <span data-ttu-id="2f9a9-131">Aşağıdaki örnek bir özel tanımlama bilgisi işleyicisi türü kullanacak şekilde SAM yapılandırır `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f9a9-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f9a9-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
