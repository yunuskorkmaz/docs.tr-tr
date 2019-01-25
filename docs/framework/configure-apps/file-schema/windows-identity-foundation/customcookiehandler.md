---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a3d032279d0b568d7072dbbe020344365c341c1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724024"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="bea27-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="bea27-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="bea27-103">Özel bir tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bea27-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="bea27-104">Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` "Özel" bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="bea27-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="bea27-105">Özel tür nesnesinden türetilmesi <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bea27-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="bea27-106">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="bea27-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="bea27-107">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="bea27-107">\<federationConfiguration></span></span>  
<span data-ttu-id="bea27-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bea27-108">\<cookieHandler></span></span>  
<span data-ttu-id="bea27-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bea27-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea27-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bea27-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bea27-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bea27-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bea27-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bea27-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bea27-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bea27-113">Attributes</span></span>  
  
|<span data-ttu-id="bea27-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bea27-114">Attribute</span></span>|<span data-ttu-id="bea27-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bea27-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bea27-116">türü</span><span class="sxs-lookup"><span data-stu-id="bea27-116">type</span></span>|<span data-ttu-id="bea27-117">Öğesinden türetilen özel bir türü belirtiyor <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bea27-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="bea27-118">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="bea27-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bea27-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bea27-119">Child Elements</span></span>  
 <span data-ttu-id="bea27-120">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="bea27-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bea27-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bea27-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bea27-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bea27-122">Element</span></span>|<span data-ttu-id="bea27-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bea27-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bea27-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="bea27-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="bea27-125">Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bea27-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bea27-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bea27-126">Remarks</span></span>  
 <span data-ttu-id="bea27-127">Ayarlayarak özel bir tanımlama bilgisi işleyici belirttiğinizde `mode` özniteliği `<cookieHandler>` öğesi "Özel" dahil ederek özel tanımlama bilgisi işleyicisinin türü belirtmelisiniz bir `<customCookieHandler>` tanımlama bilgisi işleyici türe başvuran alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="bea27-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="bea27-128">Bu öğe olamaz belirtilen `mode` "Öbekli" veya "Varsayılan" özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bea27-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="bea27-129">Özel bir tanımlama bilgisi işleyicileri türetilmesi gereken <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bea27-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="bea27-130">`<customCookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.CustomTypeElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bea27-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bea27-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="bea27-131">Example</span></span>  
 <span data-ttu-id="bea27-132">Aşağıdaki örnek bir özel tanımlama bilgisi işleyicisi türü kullanacak şekilde SAM yapılandırır `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="bea27-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bea27-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bea27-133">See also</span></span>
- <xref:System.IdentityModel.Services.CookieHandler>
