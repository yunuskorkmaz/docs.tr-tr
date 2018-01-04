---
title: '&lt;serviceTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cd981c8e48f003060c74787fdd2f29557c07901d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="eae15-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="eae15-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="eae15-103">Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eae15-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="eae15-104">Hizmet belirteç Çözümleyicisi gelen belirteçleri ve iletileri şifreleme belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eae15-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="eae15-105">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="eae15-105">\<system.identityModel></span></span>  
<span data-ttu-id="eae15-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="eae15-106">\<identityConfiguration></span></span>  
<span data-ttu-id="eae15-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="eae15-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="eae15-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="eae15-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="eae15-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="eae15-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eae15-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eae15-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eae15-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eae15-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eae15-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eae15-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eae15-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eae15-113">Attributes</span></span>  
  
|<span data-ttu-id="eae15-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eae15-114">Attribute</span></span>|<span data-ttu-id="eae15-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eae15-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eae15-116">türü</span><span class="sxs-lookup"><span data-stu-id="eae15-116">type</span></span>|<span data-ttu-id="eae15-117">Hizmet belirteç Çözümleyicisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="eae15-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="eae15-118">Her iki <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tür veya türeyen bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eae15-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="eae15-119">Nasıl belirleneceği hakkında daha fazla bilgi için `type` [özel tür başvuruları] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="eae15-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="eae15-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="eae15-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eae15-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eae15-121">Child Elements</span></span>  
 <span data-ttu-id="eae15-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="eae15-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eae15-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eae15-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eae15-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="eae15-124">Element</span></span>|<span data-ttu-id="eae15-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eae15-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eae15-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="eae15-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="eae15-127">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="eae15-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eae15-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eae15-128">Remarks</span></span>  
 <span data-ttu-id="eae15-129">Hizmet belirteç Çözümleyicisi gelen belirteçleri ve iletileri şifreleme belirtecini çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eae15-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="eae15-130">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtar almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eae15-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="eae15-131">Belirtmeniz gerekir `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="eae15-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="eae15-132">Belirtilen tür ya da olabilir <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ya türetilen özel bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eae15-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="eae15-133">Bazı belirteci işleyicileri yapılandırmada hizmet belirteç Çözümleyicisi ayarları belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="eae15-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="eae15-134">Tek tek belirteç işleyicileri ayarları güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="eae15-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eae15-135">Belirtme `<serviceTokenResolver>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="eae15-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="eae15-136">Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eae15-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eae15-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="eae15-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
