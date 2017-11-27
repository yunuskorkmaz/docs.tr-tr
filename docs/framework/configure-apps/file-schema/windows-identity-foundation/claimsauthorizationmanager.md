---
title: '&lt;claimsAuthorizationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4b4d86204d5f7225f167be125ce017488c851e98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthorizationmanagergt"></a><span data-ttu-id="29cf4-102">&lt;claimsAuthorizationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="29cf4-102">&lt;claimsAuthorizationManager&gt;</span></span>
<span data-ttu-id="29cf4-103">Bir gelen talep için talep Yetkilendirme Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="29cf4-103">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="29cf4-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="29cf4-104">\<system.identityModel></span></span>  
<span data-ttu-id="29cf4-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="29cf4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="29cf4-106">\<claimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="29cf4-106">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29cf4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29cf4-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29cf4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29cf4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29cf4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29cf4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29cf4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29cf4-110">Attributes</span></span>  
  
|<span data-ttu-id="29cf4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29cf4-111">Attribute</span></span>|<span data-ttu-id="29cf4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29cf4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29cf4-113">türü</span><span class="sxs-lookup"><span data-stu-id="29cf4-113">type</span></span>|<span data-ttu-id="29cf4-114">Türetilen bir özel tür <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="29cf4-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="29cf4-115">Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="29cf4-115">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29cf4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29cf4-116">Child Elements</span></span>  
 <span data-ttu-id="29cf4-117">Varsa hiçbir `type` özniteliği veya `type` özniteliği başvuruları <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthorizationManager>` öğesi alt öğe olmaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthorizationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29cf4-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29cf4-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29cf4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="29cf4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="29cf4-119">Element</span></span>|<span data-ttu-id="29cf4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29cf4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29cf4-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="29cf4-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="29cf4-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29cf4-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29cf4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29cf4-123">Remarks</span></span>  
 <span data-ttu-id="29cf4-124">Üzerinden sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı, gelen talepleri her zaman yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="29cf4-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="29cf4-125">Öyle değilse `type` özniteliği belirtilmediyse veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı, `<claimsAuthorizationManager>` öğesi alt öğe olmaz.</span><span class="sxs-lookup"><span data-stu-id="29cf4-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="29cf4-126">Belirleyebileceğiniz `type` türü kaydetmek için öznitelik türetilen <xref:System.Security.Claims.ClaimsAuthorizationManager> özel davranışı uygulamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="29cf4-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="29cf4-127">Türetilen sınıflar, alt öğelerinin üzerinden yapılandırmayı destekleyebilir `<claimsAuthorizationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> bu öğeleri işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="29cf4-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="29cf4-128">Alt öğeler için tanımlanan şema Sınıf Tasarımcısı kadar olur.</span><span class="sxs-lookup"><span data-stu-id="29cf4-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29cf4-129">Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> tarafından başvurulan kimlik yapılandırması kodunuzda talep tabanlı erişim denetimi sağlamak için sınıf `<federationConfiguration>` öğesi yapılandırır talep Yetkilendirme Yöneticisi'ni ve yapmak için kullanılan İlkesi yetkilendirme kararları.</span><span class="sxs-lookup"><span data-stu-id="29cf4-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="29cf4-130">Bu durum bile pasif Web senaryoları, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama değildir senaryolarda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29cf4-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="29cf4-131">Uygulama Pasif bir Web uygulaması değilse `<claimsAuthorizationManager>` öğesi (ve alt ilke öğeleri, varsa) başvurulan kimlik yapılandırması olan uygulanan ayarlar.</span><span class="sxs-lookup"><span data-stu-id="29cf4-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="29cf4-132">Tüm diğer ayarlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="29cf4-132">All other settings are ignored.</span></span> <span data-ttu-id="29cf4-133">Daha fazla bilgi için bkz: [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="29cf4-133">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="29cf4-134">Bu öğe ayarlar <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="29cf4-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29cf4-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="29cf4-135">Example</span></span>  
 <span data-ttu-id="29cf4-136">Aşağıdaki XML her biri kaynak eylemi gerçekleştirmek için bir istek sahibi sahip olması gerekir talepleri boolean birleşimleri belirtir kaynak eylem çiftlerinden oluşan ilke uyguluyor Yöneticisi talep yetkilendirme için yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="29cf4-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="29cf4-137">Bu ilke kullanma yeteneği talep Yetkilendirme Yöneticisi uygulayan kod bulunabilir `ClaimsBasedAuthorization` örnek.</span><span class="sxs-lookup"><span data-stu-id="29cf4-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
