---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252014"
---
# \<customCookieHandler>
<span data-ttu-id="ce958-101">Özel tanımlama bilgisi işleyici türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ce958-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="ce958-102">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "Custom" ise mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce958-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="ce958-103">Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ce958-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="ce958-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce958-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce958-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce958-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ce958-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce958-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce958-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce958-107">Attributes</span></span>  
  
|<span data-ttu-id="ce958-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce958-108">Attribute</span></span>|<span data-ttu-id="ce958-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce958-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce958-110">tür</span><span class="sxs-lookup"><span data-stu-id="ce958-110">type</span></span>|<span data-ttu-id="ce958-111">Sınıfından türetilen özel bir tür belirtir <xref:System.IdentityModel.Services.CookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="ce958-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="ce958-112">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce958-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce958-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce958-113">Child Elements</span></span>  
 <span data-ttu-id="ce958-114">Yok</span><span class="sxs-lookup"><span data-stu-id="ce958-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce958-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce958-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ce958-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce958-116">Element</span></span>|<span data-ttu-id="ce958-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce958-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="ce958-118"><xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> Tanımlama bilgilerini okumak ve yazmak için kullandığı öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ce958-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce958-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce958-119">Remarks</span></span>  
 <span data-ttu-id="ce958-120">`mode`Öğesinin özniteliğini "Custom" olarak ayarlayarak özel bir tanımlama bilgisi işleyicisi belirttiğinizde `<cookieHandler>` , `<customCookieHandler>` tanımlama bilgisi işleyici türüne başvuran bir alt öğe ekleyerek özel tanımlama bilgisi işleyicisinin türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce958-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="ce958-121">`mode`Öznitelik "öbekli" veya "default" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="ce958-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="ce958-122">Özel tanımlama bilgisi işleyicileri <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ce958-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="ce958-123">`<customCookieHandler>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.CustomTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="ce958-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce958-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce958-124">Example</span></span>  
 <span data-ttu-id="ce958-125">Aşağıdaki örnek, SAM türünde özel bir tanımlama bilgisi işleyicisi kullanmak için SAM 'ı yapılandırır `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="ce958-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce958-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce958-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
