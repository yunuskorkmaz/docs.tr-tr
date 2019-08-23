---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923105"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="f71b5-101">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="f71b5-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="f71b5-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f71b5-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f71b5-103">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f71b5-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="f71b5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f71b5-104">\<system.identityModel></span></span>  
<span data-ttu-id="f71b5-105">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f71b5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f71b5-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="f71b5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f71b5-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f71b5-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="f71b5-108">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="f71b5-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f71b5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f71b5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f71b5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f71b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f71b5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f71b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f71b5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f71b5-112">Attributes</span></span>  
  
|<span data-ttu-id="f71b5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f71b5-113">Attribute</span></span>|<span data-ttu-id="f71b5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f71b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f71b5-115">türü</span><span class="sxs-lookup"><span data-stu-id="f71b5-115">type</span></span>|<span data-ttu-id="f71b5-116">Hizmet belirteci Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f71b5-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="f71b5-117">Ya tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıftan türeyen bir tür. <xref:System.IdentityModel.Selectors.SecurityTokenResolver></span><span class="sxs-lookup"><span data-stu-id="f71b5-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="f71b5-118">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="f71b5-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="f71b5-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f71b5-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f71b5-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f71b5-120">Child Elements</span></span>  
 <span data-ttu-id="f71b5-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="f71b5-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f71b5-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f71b5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f71b5-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f71b5-123">Element</span></span>|<span data-ttu-id="f71b5-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f71b5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f71b5-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f71b5-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f71b5-126">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f71b5-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f71b5-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f71b5-127">Remarks</span></span>  
 <span data-ttu-id="f71b5-128">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f71b5-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="f71b5-129">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f71b5-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="f71b5-130">`type` Özniteliğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f71b5-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="f71b5-131">Belirtilen tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfından türetilen özel bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="f71b5-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="f71b5-132">Bazı belirteç işleyicileri, yapılandırmada hizmet belirteci çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f71b5-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="f71b5-133">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f71b5-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f71b5-134">Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="f71b5-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="f71b5-135">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="f71b5-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f71b5-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="f71b5-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
