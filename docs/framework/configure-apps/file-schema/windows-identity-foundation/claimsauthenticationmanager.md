---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941822"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="21edf-101">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="21edf-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="21edf-102">Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="21edf-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="21edf-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="21edf-103">\<system.identityModel></span></span>  
<span data-ttu-id="21edf-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="21edf-104">\<identityConfiguration></span></span>  
<span data-ttu-id="21edf-105">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="21edf-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21edf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21edf-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21edf-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21edf-107">Attributes and Elements</span></span>  
 <span data-ttu-id="21edf-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21edf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21edf-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21edf-109">Attributes</span></span>  
  
|<span data-ttu-id="21edf-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21edf-110">Attribute</span></span>|<span data-ttu-id="21edf-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21edf-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21edf-112">türü</span><span class="sxs-lookup"><span data-stu-id="21edf-112">type</span></span>|<span data-ttu-id="21edf-113"><xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıfından türetilen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="21edf-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="21edf-114">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="21edf-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21edf-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21edf-115">Child Elements</span></span>  
 <span data-ttu-id="21edf-116">`type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Öznitelik yoksa veya öznitelik sınıfa <xref:System.Security.Claims.ClaimsAuthenticationManager> başvuruyorsa, öğesialtöğelerialmaz;ancak,öğesindentüretilmişsınıflaraltyapılandırmaöğelerinitanımlayabilir.`<claimsAuthenticationManager>` `type`</span><span class="sxs-lookup"><span data-stu-id="21edf-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21edf-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21edf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="21edf-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="21edf-118">Element</span></span>|<span data-ttu-id="21edf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21edf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21edf-120">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="21edf-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="21edf-121">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21edf-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21edf-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21edf-122">Remarks</span></span>  
 <span data-ttu-id="21edf-123"><xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıfı aracılığıyla sunulan varsayılan davranış, gelen talepleri yankılar.</span><span class="sxs-lookup"><span data-stu-id="21edf-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="21edf-124">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` belirtiyorsa, öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="21edf-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="21edf-125">Özel davranışı uygulamak için `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21edf-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="21edf-126">Türetilmiş sınıflar, bu öğeleri işlemek için `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="21edf-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="21edf-127">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="21edf-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="21edf-128">`<claimsAuthenticationManager>` Öğesi özelliği<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ayarlar.</span><span class="sxs-lookup"><span data-stu-id="21edf-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21edf-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="21edf-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
