---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252080"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="bc1a4-101">\<claimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="bc1a4-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="bc1a4-102">Gelen talepler için bir talep Yetkilendirme Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
<span data-ttu-id="bc1a4-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc1a4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc1a4-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc1a4-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="bc1a4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="bc1a4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="bc1a4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthorizationManager >**</span><span class="sxs-lookup"><span data-stu-id="bc1a4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1a4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc1a4-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc1a4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc1a4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bc1a4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc1a4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc1a4-110">Attributes</span></span>  
  
|<span data-ttu-id="bc1a4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc1a4-111">Attribute</span></span>|<span data-ttu-id="bc1a4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc1a4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc1a4-113">türü</span><span class="sxs-lookup"><span data-stu-id="bc1a4-113">type</span></span>|<span data-ttu-id="bc1a4-114"><xref:System.Security.Claims.ClaimsAuthorizationManager> Sınıfından türetilen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="bc1a4-115">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc1a4-115">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc1a4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc1a4-116">Child Elements</span></span>  
 <span data-ttu-id="bc1a4-117">`type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Öznitelik yoksa veya öznitelik sınıfa <xref:System.Security.Claims.ClaimsAuthorizationManager> başvuruyorsa, öğesialtöğelerialmaz;ancak,öğesindentüretilmişsınıflaraltyapılandırmaöğelerinitanımlayabilir.`<claimsAuthorizationManager>` `type`</span><span class="sxs-lookup"><span data-stu-id="bc1a4-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc1a4-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc1a4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bc1a4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc1a4-119">Element</span></span>|<span data-ttu-id="bc1a4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc1a4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc1a4-121">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bc1a4-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="bc1a4-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc1a4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc1a4-123">Remarks</span></span>  
 <span data-ttu-id="bc1a4-124"><xref:System.Security.Claims.ClaimsAuthorizationManager> Sınıfı aracılığıyla sunulan varsayılan davranış her zaman gelen talepleri yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="bc1a4-125">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı `<claimsAuthorizationManager>` belirtiyorsa, öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="bc1a4-126">Özel davranışı uygulamak için `type` <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="bc1a4-127">Türetilmiş sınıflar, bu öğeleri işlemek için `<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="bc1a4-128">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc1a4-129">Kodunuzda talep tabanlı <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> erişim denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için ya da sınıfını kullanırken, `<federationConfiguration>` öğesi tarafından başvurulan kimlik yapılandırması, bu işlemi yapmak için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandırır yetkilendirme kararları.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="bc1a4-130">Bu, pasif Web senaryoları olmayan senaryolarda bile, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="bc1a4-131">Uygulama pasif bir Web uygulaması değilse, `<claimsAuthorizationManager>` başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) uygulanan tek ayarlardır.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="bc1a4-132">Diğer tüm ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-132">All other settings are ignored.</span></span> <span data-ttu-id="bc1a4-133">Daha fazla bilgi için, bkz [ \<. FederationConfiguration >](federationconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-133">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="bc1a4-134">Bu öğe <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc1a4-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc1a4-135">Example</span></span>  
 <span data-ttu-id="bc1a4-136">Aşağıdaki XML, her biri kaynak Eylem çiftlerinden oluşan ilkeyi uygulayan, her birinin kaynak üzerinde eylemi gerçekleştirmek için sahip olması gereken taleplerin Boole birleşimlerini belirten bir talep Yetkilendirme Yöneticisi yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="bc1a4-137">Bu ilkeyi kullanan talep Yetkilendirme Yöneticisini uygulayan kod `ClaimsBasedAuthorization` örneğinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bc1a4-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
