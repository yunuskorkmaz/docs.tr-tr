---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152755"
---
# \<claimsAuthenticationManager>
<span data-ttu-id="9705d-101">Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9705d-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="9705d-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9705d-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9705d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9705d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9705d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9705d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9705d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9705d-105">Attributes</span></span>  
  
|<span data-ttu-id="9705d-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9705d-106">Attribute</span></span>|<span data-ttu-id="9705d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9705d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9705d-108">tür</span><span class="sxs-lookup"><span data-stu-id="9705d-108">type</span></span>|<span data-ttu-id="9705d-109">Sınıfından türetilen özel bir tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> .</span><span class="sxs-lookup"><span data-stu-id="9705d-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="9705d-110">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="9705d-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9705d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9705d-111">Child Elements</span></span>  
 <span data-ttu-id="9705d-112">`type`Öznitelik yoksa veya `type` öznitelik sınıfa başvuruyorsa, <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` öğesi alt öğeleri almaz; ancak, öğesinden türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9705d-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9705d-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9705d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="9705d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9705d-114">Element</span></span>|<span data-ttu-id="9705d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9705d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="9705d-116">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9705d-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9705d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9705d-117">Remarks</span></span>  
 <span data-ttu-id="9705d-118">Sınıfı aracılığıyla sunulan varsayılan davranış, <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen talepleri yankılar.</span><span class="sxs-lookup"><span data-stu-id="9705d-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="9705d-119">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı belirtiyorsa, `<claimsAuthenticationManager>` öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="9705d-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="9705d-120">`type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Özel davranışı uygulamak için sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9705d-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="9705d-121">Türetilmiş sınıflar, `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> Bu öğeleri işlemek için yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9705d-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="9705d-122">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="9705d-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="9705d-123">`<claimsAuthenticationManager>`Öğesi <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9705d-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9705d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="9705d-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
