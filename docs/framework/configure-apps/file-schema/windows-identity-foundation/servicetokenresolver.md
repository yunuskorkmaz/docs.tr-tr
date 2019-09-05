---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251843"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="12ee9-101">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="12ee9-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="12ee9-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="12ee9-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="12ee9-103">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12ee9-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="12ee9-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="12ee9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="12ee9-105">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="12ee9-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="12ee9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="12ee9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="12ee9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="12ee9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="12ee9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="12ee9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="12ee9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="12ee9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ee9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12ee9-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12ee9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12ee9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="12ee9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12ee9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12ee9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12ee9-113">Attributes</span></span>  
  
|<span data-ttu-id="12ee9-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12ee9-114">Attribute</span></span>|<span data-ttu-id="12ee9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12ee9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12ee9-116">türü</span><span class="sxs-lookup"><span data-stu-id="12ee9-116">type</span></span>|<span data-ttu-id="12ee9-117">Hizmet belirteci Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="12ee9-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="12ee9-118">Ya tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıftan türeyen bir tür. <xref:System.IdentityModel.Selectors.SecurityTokenResolver></span><span class="sxs-lookup"><span data-stu-id="12ee9-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="12ee9-119">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="12ee9-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="12ee9-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="12ee9-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12ee9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12ee9-121">Child Elements</span></span>  
 <span data-ttu-id="12ee9-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="12ee9-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12ee9-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12ee9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="12ee9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="12ee9-124">Element</span></span>|<span data-ttu-id="12ee9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12ee9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12ee9-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="12ee9-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="12ee9-127">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="12ee9-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12ee9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12ee9-128">Remarks</span></span>  
 <span data-ttu-id="12ee9-129">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12ee9-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="12ee9-130">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12ee9-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="12ee9-131">`type` Özniteliğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="12ee9-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="12ee9-132">Belirtilen tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfından türetilen özel bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="12ee9-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="12ee9-133">Bazı belirteç işleyicileri, yapılandırmada hizmet belirteci çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="12ee9-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="12ee9-134">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="12ee9-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12ee9-135">Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="12ee9-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="12ee9-136">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="12ee9-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12ee9-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="12ee9-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 