---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252014"
---
# <a name="customcookiehandler"></a><span data-ttu-id="13395-101">\<Custombir ıehandler ></span><span class="sxs-lookup"><span data-stu-id="13395-101">\<customCookieHandler></span></span>
<span data-ttu-id="13395-102">Özel tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13395-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="13395-103">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "Custom" ise mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="13395-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="13395-104">Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="13395-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
<span data-ttu-id="13395-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="13395-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13395-106">&nbsp;&nbsp;[ **\<System. IdentityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="13395-106">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="13395-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="13395-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="13395-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Tanımlama, ıehandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="13395-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="13395-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Custombir ıehandler >**</span><span class="sxs-lookup"><span data-stu-id="13395-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13395-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13395-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13395-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13395-111">Attributes and Elements</span></span>  
 <span data-ttu-id="13395-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13395-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13395-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13395-113">Attributes</span></span>  
  
|<span data-ttu-id="13395-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="13395-114">Attribute</span></span>|<span data-ttu-id="13395-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13395-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13395-116">türü</span><span class="sxs-lookup"><span data-stu-id="13395-116">type</span></span>|<span data-ttu-id="13395-117"><xref:System.IdentityModel.Services.CookieHandler> Sınıfından türetilen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="13395-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="13395-118">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="13395-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13395-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13395-119">Child Elements</span></span>  
 <span data-ttu-id="13395-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="13395-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13395-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13395-121">Parent Elements</span></span>  
  
|<span data-ttu-id="13395-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="13395-122">Element</span></span>|<span data-ttu-id="13395-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13395-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13395-124">\<Tanımlama, ıehandler ></span><span class="sxs-lookup"><span data-stu-id="13395-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="13395-125">Tanımlama bilgilerini okumak ve yazmak için kullandığıöğesiniyapılandırır.<xref:System.IdentityModel.Services.SessionAuthenticationModule> <xref:System.IdentityModel.Services.CookieHandler></span><span class="sxs-lookup"><span data-stu-id="13395-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13395-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13395-126">Remarks</span></span>  
 <span data-ttu-id="13395-127">Öğesinin özniteliğini "Custom" olarak ayarlayarak `<customCookieHandler>` özel bir tanımlama bilgisi işleyicisi belirttiğinizde, tanımlama bilgisi işleyici türüne başvuran bir alt öğe ekleyerek özel tanımlama bilgisi işleyicisinin türünü belirtmeniz gerekir. `mode` `<cookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="13395-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="13395-128">`mode` Öznitelik "öbekli" veya "default" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="13395-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="13395-129">Özel tanımlama bilgisi işleyicileri <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="13395-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="13395-130">`<customCookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.CustomTypeElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="13395-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13395-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="13395-131">Example</span></span>  
 <span data-ttu-id="13395-132">Aşağıdaki örnek, SAM türünde `MyNamespace.MyCustomCookieHandler`özel bir tanımlama bilgisi işleyicisi kullanmak için Sam 'ı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="13395-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13395-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13395-133">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
