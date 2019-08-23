---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942793"
---
# <a name="customcookiehandler"></a><span data-ttu-id="0fb48-101">\<Custombir ıehandler ></span><span class="sxs-lookup"><span data-stu-id="0fb48-101">\<customCookieHandler></span></span>
<span data-ttu-id="0fb48-102">Özel tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0fb48-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="0fb48-103">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "Custom" ise mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fb48-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="0fb48-104">Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0fb48-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="0fb48-105">\<System. IdentityModel. Services ></span><span class="sxs-lookup"><span data-stu-id="0fb48-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="0fb48-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0fb48-106">\<federationConfiguration></span></span>  
<span data-ttu-id="0fb48-107">\<Tanımlama, ıehandler ></span><span class="sxs-lookup"><span data-stu-id="0fb48-107">\<cookieHandler></span></span>  
<span data-ttu-id="0fb48-108">\<Custombir ıehandler ></span><span class="sxs-lookup"><span data-stu-id="0fb48-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb48-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fb48-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fb48-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fb48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0fb48-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fb48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fb48-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0fb48-112">Attributes</span></span>  
  
|<span data-ttu-id="0fb48-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0fb48-113">Attribute</span></span>|<span data-ttu-id="0fb48-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fb48-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fb48-115">türü</span><span class="sxs-lookup"><span data-stu-id="0fb48-115">type</span></span>|<span data-ttu-id="0fb48-116"><xref:System.IdentityModel.Services.CookieHandler> Sınıfından türetilen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fb48-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="0fb48-117">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fb48-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fb48-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fb48-118">Child Elements</span></span>  
 <span data-ttu-id="0fb48-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="0fb48-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fb48-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fb48-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0fb48-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0fb48-121">Element</span></span>|<span data-ttu-id="0fb48-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fb48-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fb48-123">\<Tanımlama, ıehandler ></span><span class="sxs-lookup"><span data-stu-id="0fb48-123">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="0fb48-124">Tanımlama bilgilerini okumak ve yazmak için kullandığıöğesiniyapılandırır.<xref:System.IdentityModel.Services.SessionAuthenticationModule> <xref:System.IdentityModel.Services.CookieHandler></span><span class="sxs-lookup"><span data-stu-id="0fb48-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fb48-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0fb48-125">Remarks</span></span>  
 <span data-ttu-id="0fb48-126">Öğesinin özniteliğini "Custom" olarak ayarlayarak `<customCookieHandler>` özel bir tanımlama bilgisi işleyicisi belirttiğinizde, tanımlama bilgisi işleyici türüne başvuran bir alt öğe ekleyerek özel tanımlama bilgisi işleyicisinin türünü belirtmeniz gerekir. `mode` `<cookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="0fb48-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="0fb48-127">`mode` Öznitelik "öbekli" veya "default" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="0fb48-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="0fb48-128">Özel tanımlama bilgisi işleyicileri <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0fb48-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="0fb48-129">`<customCookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.CustomTypeElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="0fb48-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fb48-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fb48-130">Example</span></span>  
 <span data-ttu-id="0fb48-131">Aşağıdaki örnek, SAM türünde `MyNamespace.MyCustomCookieHandler`özel bir tanımlama bilgisi işleyicisi kullanmak için Sam 'ı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0fb48-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fb48-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fb48-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
