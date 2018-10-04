---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: d4b64e2c88e153834b7cf5a83bd6258b6dfd471f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780797"
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="bf249-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="bf249-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="bf249-103">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bf249-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="bf249-104">Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf249-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="bf249-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bf249-105">\<system.identityModel></span></span>  
<span data-ttu-id="bf249-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf249-106">\<identityConfiguration></span></span>  
<span data-ttu-id="bf249-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="bf249-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bf249-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf249-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="bf249-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="bf249-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf249-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf249-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf249-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf249-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bf249-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf249-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf249-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf249-113">Attributes</span></span>  
  
|<span data-ttu-id="bf249-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bf249-114">Attribute</span></span>|<span data-ttu-id="bf249-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf249-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf249-116">türü</span><span class="sxs-lookup"><span data-stu-id="bf249-116">type</span></span>|<span data-ttu-id="bf249-117">Belirteç çözümleyici hizmet türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf249-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="bf249-118">Her iki <xref:System.IdentityModel.Selectors.SecurityTokenResolver> türü veya, türetilen tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bf249-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="bf249-119">Belirtme hakkında daha fazla bilgi için `type` [özel tür başvurularını] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="bf249-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="bf249-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bf249-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf249-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf249-121">Child Elements</span></span>  
 <span data-ttu-id="bf249-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="bf249-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf249-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf249-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf249-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf249-124">Element</span></span>|<span data-ttu-id="bf249-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf249-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf249-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf249-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="bf249-127">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf249-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf249-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf249-128">Remarks</span></span>  
 <span data-ttu-id="bf249-129">Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci gidermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf249-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="bf249-130">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf249-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="bf249-131">Belirtmelisiniz `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bf249-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="bf249-132">Belirtilen türü olabilir <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ya öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bf249-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="bf249-133">Bazı belirteç işleyicileri yapılandırmada hizmet belirteç çözümleyici ayarları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf249-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="bf249-134">Ayarları tek tek belirteç işleyicileri güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bf249-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf249-135">Belirtme `<serviceTokenResolver>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bf249-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="bf249-136">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bf249-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf249-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf249-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
