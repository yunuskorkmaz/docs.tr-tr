---
description: 'Hakkında daha fazla bilgi edinin: <claimsAuthenticationManager>'
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 5a94861d6b2684b9f66c7d5e14f72aa419a0c66f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664255"
---
# \<claimsAuthenticationManager>

<span data-ttu-id="20b66-102">Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="20b66-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="20b66-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="20b66-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20b66-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20b66-104">Attributes and Elements</span></span>  

 <span data-ttu-id="20b66-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20b66-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20b66-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20b66-106">Attributes</span></span>  
  
|<span data-ttu-id="20b66-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20b66-107">Attribute</span></span>|<span data-ttu-id="20b66-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20b66-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20b66-109">tür</span><span class="sxs-lookup"><span data-stu-id="20b66-109">type</span></span>|<span data-ttu-id="20b66-110">Sınıfından türetilen özel bir tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> .</span><span class="sxs-lookup"><span data-stu-id="20b66-110">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="20b66-111">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="20b66-111">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20b66-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20b66-112">Child Elements</span></span>  

 <span data-ttu-id="20b66-113">`type`Öznitelik yoksa veya `type` öznitelik sınıfa başvuruyorsa, <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` öğesi alt öğeleri almaz; ancak, öğesinden türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="20b66-113">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20b66-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20b66-114">Parent Elements</span></span>  
  
|<span data-ttu-id="20b66-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="20b66-115">Element</span></span>|<span data-ttu-id="20b66-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20b66-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="20b66-117">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="20b66-117">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20b66-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20b66-118">Remarks</span></span>  

 <span data-ttu-id="20b66-119">Sınıfı aracılığıyla sunulan varsayılan davranış, <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen talepleri yankılar.</span><span class="sxs-lookup"><span data-stu-id="20b66-119">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="20b66-120">Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı belirtiyorsa, `<claimsAuthenticationManager>` öğesi alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="20b66-120">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="20b66-121">`type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Özel davranışı uygulamak için sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20b66-121">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="20b66-122">Türetilmiş sınıflar, `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> Bu öğeleri işlemek için yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="20b66-122">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="20b66-123">Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="20b66-123">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="20b66-124">`<claimsAuthenticationManager>`Öğesi <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="20b66-124">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20b66-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="20b66-125">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
