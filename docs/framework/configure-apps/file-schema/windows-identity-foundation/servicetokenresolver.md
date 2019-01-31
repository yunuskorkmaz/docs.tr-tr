---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 1143717882652fc8a03947327b5f1ea89dde7373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267436"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="e435e-101">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e435e-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="e435e-102">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e435e-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e435e-103">Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e435e-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="e435e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e435e-104">\<system.identityModel></span></span>  
<span data-ttu-id="e435e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e435e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e435e-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e435e-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e435e-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e435e-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="e435e-108">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e435e-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e435e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e435e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e435e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e435e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e435e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e435e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e435e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e435e-112">Attributes</span></span>  
  
|<span data-ttu-id="e435e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e435e-113">Attribute</span></span>|<span data-ttu-id="e435e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e435e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e435e-115">türü</span><span class="sxs-lookup"><span data-stu-id="e435e-115">type</span></span>|<span data-ttu-id="e435e-116">Belirteç çözümleyici hizmet türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e435e-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="e435e-117">Her iki <xref:System.IdentityModel.Selectors.SecurityTokenResolver> türü veya, türetilen tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e435e-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="e435e-118">Belirtme hakkında daha fazla bilgi için `type` [özel tür başvurularını] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="e435e-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="e435e-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e435e-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e435e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e435e-120">Child Elements</span></span>  
 <span data-ttu-id="e435e-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="e435e-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e435e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e435e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e435e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e435e-123">Element</span></span>|<span data-ttu-id="e435e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e435e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e435e-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e435e-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e435e-126">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e435e-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e435e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e435e-127">Remarks</span></span>  
 <span data-ttu-id="e435e-128">Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci gidermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e435e-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e435e-129">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e435e-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="e435e-130">Belirtmelisiniz `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e435e-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="e435e-131">Belirtilen türü olabilir <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ya öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e435e-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="e435e-132">Bazı belirteç işleyicileri yapılandırmada hizmet belirteç çözümleyici ayarları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e435e-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="e435e-133">Ayarları tek tek belirteç işleyicileri güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e435e-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e435e-134">Belirtme `<serviceTokenResolver>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e435e-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e435e-135">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e435e-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e435e-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e435e-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
