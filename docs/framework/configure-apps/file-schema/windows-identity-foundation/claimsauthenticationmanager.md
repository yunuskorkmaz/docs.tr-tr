---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252100"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="ddd63-101">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="ddd63-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="ddd63-102">Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ddd63-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="ddd63-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ddd63-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ddd63-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ddd63-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ddd63-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ddd63-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ddd63-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="ddd63-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddd63-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddd63-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddd63-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddd63-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ddd63-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddd63-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddd63-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ddd63-110">Attributes</span></span>  
  
|<span data-ttu-id="ddd63-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ddd63-111">Attribute</span></span>|<span data-ttu-id="ddd63-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddd63-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddd63-113">türü</span><span class="sxs-lookup"><span data-stu-id="ddd63-113">type</span></span>|<span data-ttu-id="ddd63-114"><xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıfından türetilen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddd63-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="ddd63-115">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="ddd63-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddd63-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddd63-116">Child Elements</span></span>  
 <span data-ttu-id="ddd63-117">`type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Öznitelik yoksa veya öznitelik sınıfa <xref:System.Security.Claims.ClaimsAuthenticationManager> başvuruyorsa, öğesialtöğelerialmaz;ancak,öğesindentüretilmişsınıflaraltyapılandırmaöğelerinitanımlayabilir.`<claimsAuthenticationManager>` `type`</span><span class="sxs-lookup"><span data-stu-id="ddd63-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ddd63-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddd63-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ddd63-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddd63-119">Element</span></span>|<span data-ttu-id="ddd63-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddd63-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddd63-121">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ddd63-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="ddd63-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddd63-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddd63-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddd63-123">Remarks</span></span>  
 <span data-ttu-id="ddd63-124"><xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıfı aracılığıyla sunulan varsayılan davranış, gelen talepleri yankılar.</span><span class="sxs-lookup"><span data-stu-id="ddd63-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="ddd63-125">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` belirtiyorsa, öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="ddd63-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="ddd63-126">Özel davranışı uygulamak için `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddd63-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="ddd63-127">Türetilmiş sınıflar, bu öğeleri işlemek için `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ddd63-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="ddd63-128">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="ddd63-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="ddd63-129">`<claimsAuthenticationManager>` Öğesi özelliği<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ddd63-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd63-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddd63-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
