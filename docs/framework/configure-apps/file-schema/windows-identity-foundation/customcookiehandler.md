---
description: 'Hakkında daha fazla bilgi edinin: <customCookieHandler>'
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 6b433769c429ed4149efb324d7c4b216d6042705
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664086"
---
# \<customCookieHandler>

<span data-ttu-id="e4846-102">Özel tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e4846-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="e4846-103">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "Custom" ise mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4846-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="e4846-104">Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e4846-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="e4846-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4846-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4846-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4846-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e4846-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4846-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4846-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4846-108">Attributes</span></span>  
  
|<span data-ttu-id="e4846-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e4846-109">Attribute</span></span>|<span data-ttu-id="e4846-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4846-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4846-111">tür</span><span class="sxs-lookup"><span data-stu-id="e4846-111">type</span></span>|<span data-ttu-id="e4846-112">Sınıfından türetilen özel bir tür belirtir <xref:System.IdentityModel.Services.CookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="e4846-112">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="e4846-113">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4846-113">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4846-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4846-114">Child Elements</span></span>  

 <span data-ttu-id="e4846-115">Yok</span><span class="sxs-lookup"><span data-stu-id="e4846-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4846-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4846-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e4846-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4846-117">Element</span></span>|<span data-ttu-id="e4846-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4846-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="e4846-119"><xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> Tanımlama bilgilerini okumak ve yazmak için kullandığı öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e4846-119">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4846-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4846-120">Remarks</span></span>  

 <span data-ttu-id="e4846-121">`mode`Öğesinin özniteliğini "Custom" olarak ayarlayarak özel bir tanımlama bilgisi işleyicisi belirttiğinizde `<cookieHandler>` , `<customCookieHandler>` tanımlama bilgisi işleyici türüne başvuran bir alt öğe ekleyerek özel tanımlama bilgisi işleyicisinin türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4846-121">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="e4846-122">`mode`Öznitelik "öbekli" veya "default" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="e4846-122">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="e4846-123">Özel tanımlama bilgisi işleyicileri <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e4846-123">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="e4846-124">`<customCookieHandler>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.CustomTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="e4846-124">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4846-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4846-125">Example</span></span>  

 <span data-ttu-id="e4846-126">Aşağıdaki örnek, SAM türünde özel bir tanımlama bilgisi işleyicisi kullanmak için SAM 'ı yapılandırır `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="e4846-126">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4846-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4846-127">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
