---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 51ca91de5c77727f5f5506118461d19354f12c14
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237039"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="2718e-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="2718e-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="2718e-103">Özel bir tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2718e-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="2718e-104">Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` "Özel" bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="2718e-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="2718e-105">Özel tür nesnesinden türetilmesi <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2718e-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="2718e-106">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="2718e-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="2718e-107">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="2718e-107">\<federationConfiguration></span></span>  
<span data-ttu-id="2718e-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2718e-108">\<cookieHandler></span></span>  
<span data-ttu-id="2718e-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2718e-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2718e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2718e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2718e-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2718e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2718e-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2718e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2718e-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2718e-113">Attributes</span></span>  
  
|<span data-ttu-id="2718e-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2718e-114">Attribute</span></span>|<span data-ttu-id="2718e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2718e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2718e-116">türü</span><span class="sxs-lookup"><span data-stu-id="2718e-116">type</span></span>|<span data-ttu-id="2718e-117">Öğesinden türetilen özel bir türü belirtiyor <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2718e-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="2718e-118">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="2718e-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2718e-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2718e-119">Child Elements</span></span>  
 <span data-ttu-id="2718e-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="2718e-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2718e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2718e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2718e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="2718e-122">Element</span></span>|<span data-ttu-id="2718e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2718e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2718e-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="2718e-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="2718e-125">Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2718e-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2718e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2718e-126">Remarks</span></span>  
 <span data-ttu-id="2718e-127">Ayarlayarak özel bir tanımlama bilgisi işleyici belirttiğinizde `mode` özniteliği `<cookieHandler>` öğesi "Özel" dahil ederek özel tanımlama bilgisi işleyicisinin türü belirtmelisiniz bir `<customCookieHandler>` tanımlama bilgisi işleyici türe başvuran alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="2718e-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="2718e-128">Bu öğe olamaz belirtilen `mode` "Öbekli" veya "Varsayılan" özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2718e-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="2718e-129">Özel bir tanımlama bilgisi işleyicileri türetilmesi gereken <xref:System.IdentityModel.Services.CookieHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2718e-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="2718e-130">`<customCookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.CustomTypeElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2718e-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2718e-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="2718e-131">Example</span></span>  
 <span data-ttu-id="2718e-132">Aşağıdaki örnek bir özel tanımlama bilgisi işleyicisi türü kullanacak şekilde SAM yapılandırır `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="2718e-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2718e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2718e-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
