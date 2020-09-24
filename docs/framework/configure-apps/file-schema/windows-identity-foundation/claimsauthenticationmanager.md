---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 9e099b8de486631702548b8a035a46a7e0f4eb30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158480"
---
# \<claimsAuthenticationManager>

<span data-ttu-id="a403c-101">Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a403c-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="a403c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a403c-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a403c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a403c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a403c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a403c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a403c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a403c-105">Attributes</span></span>  
  
|<span data-ttu-id="a403c-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a403c-106">Attribute</span></span>|<span data-ttu-id="a403c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a403c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a403c-108">tür</span><span class="sxs-lookup"><span data-stu-id="a403c-108">type</span></span>|<span data-ttu-id="a403c-109">Sınıfından türetilen özel bir tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> .</span><span class="sxs-lookup"><span data-stu-id="a403c-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="a403c-110">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="a403c-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a403c-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a403c-111">Child Elements</span></span>  

 <span data-ttu-id="a403c-112">`type`Öznitelik yoksa veya `type` öznitelik sınıfa başvuruyorsa, <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` öğesi alt öğeleri almaz; ancak, öğesinden türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a403c-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a403c-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a403c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a403c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a403c-114">Element</span></span>|<span data-ttu-id="a403c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a403c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="a403c-116">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a403c-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a403c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a403c-117">Remarks</span></span>  

 <span data-ttu-id="a403c-118">Sınıfı aracılığıyla sunulan varsayılan davranış, <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen talepleri yankılar.</span><span class="sxs-lookup"><span data-stu-id="a403c-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="a403c-119">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı belirtiyorsa, `<claimsAuthenticationManager>` öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="a403c-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="a403c-120">`type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Özel davranışı uygulamak için sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a403c-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="a403c-121">Türetilmiş sınıflar, `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> Bu öğeleri işlemek için yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a403c-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="a403c-122">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="a403c-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="a403c-123">`<claimsAuthenticationManager>`Öğesi <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a403c-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a403c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a403c-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
