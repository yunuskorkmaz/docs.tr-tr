---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252080"
---
# \<claimsAuthorizationManager>
<span data-ttu-id="a30ab-101">Gelen talepler için bir talep Yetkilendirme Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a30ab-101">Registers a claims authorization manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="a30ab-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a30ab-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a30ab-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a30ab-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a30ab-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a30ab-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a30ab-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a30ab-105">Attributes</span></span>  
  
|<span data-ttu-id="a30ab-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a30ab-106">Attribute</span></span>|<span data-ttu-id="a30ab-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a30ab-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a30ab-108">tür</span><span class="sxs-lookup"><span data-stu-id="a30ab-108">type</span></span>|<span data-ttu-id="a30ab-109">Sınıfından türetilen özel bir tür <xref:System.Security.Claims.ClaimsAuthorizationManager> .</span><span class="sxs-lookup"><span data-stu-id="a30ab-109">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="a30ab-110">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="a30ab-110">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a30ab-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a30ab-111">Child Elements</span></span>  
 <span data-ttu-id="a30ab-112">`type`Öznitelik yoksa veya `type` öznitelik sınıfa başvuruyorsa, <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthorizationManager>` öğesi alt öğeleri almaz; ancak, öğesinden türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthorizationManager> alt yapılandırma öğelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a30ab-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a30ab-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a30ab-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a30ab-114">Element</span></span>|<span data-ttu-id="a30ab-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a30ab-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="a30ab-116">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a30ab-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a30ab-117">Remarks</span></span>  
 <span data-ttu-id="a30ab-118">Sınıfı aracılığıyla sunulan varsayılan davranış <xref:System.Security.Claims.ClaimsAuthorizationManager> her zaman gelen talepleri yetkilendirir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="a30ab-119">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthorizationManager> sınıfı belirtiyorsa, `<claimsAuthorizationManager>` öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="a30ab-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="a30ab-120">`type` <xref:System.Security.Claims.ClaimsAuthorizationManager> Özel davranışı uygulamak için sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a30ab-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="a30ab-121">Türetilmiş sınıflar, `<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> Bu öğeleri işlemek için yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-121">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="a30ab-122">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="a30ab-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a30ab-123"><xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, öğesinin başvurduğu kimlik yapılandırması, `<federationConfiguration>` yetkilendirme kararları vermek için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a30ab-123">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="a30ab-124">Bu, pasif Web senaryoları olmayan senaryolarda bile, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-124">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="a30ab-125">Uygulama pasif bir Web uygulaması değilse, `<claimsAuthorizationManager>` başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) uygulanan tek ayarlardır.</span><span class="sxs-lookup"><span data-stu-id="a30ab-125">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="a30ab-126">Diğer tüm ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="a30ab-126">All other settings are ignored.</span></span> <span data-ttu-id="a30ab-127">Daha fazla bilgi için, bkz [\<federationConfiguration>](federationconfiguration.md) . öğesi.</span><span class="sxs-lookup"><span data-stu-id="a30ab-127">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="a30ab-128">Bu öğe özelliği ayarlar <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a30ab-128">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a30ab-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a30ab-129">Example</span></span>  
 <span data-ttu-id="a30ab-130">Aşağıdaki XML, her biri kaynak Eylem çiftlerinden oluşan ilkeyi uygulayan, her birinin kaynak üzerinde eylemi gerçekleştirmek için sahip olması gereken taleplerin Boole birleşimlerini belirten bir talep Yetkilendirme Yöneticisi yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-130">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="a30ab-131">Bu ilkeyi kullanan talep Yetkilendirme Yöneticisini uygulayan kod `ClaimsBasedAuthorization` örneğinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a30ab-131">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
