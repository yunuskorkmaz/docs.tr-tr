---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152755"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="713bd-101">\<İddialarAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="713bd-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="713bd-102">Gelen talepler için bir talep kimlik doğrulama yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="713bd-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="713bd-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="713bd-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="713bd-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="713bd-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="713bd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="713bd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="713bd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<İddialarAuthenticationManager>**</span><span class="sxs-lookup"><span data-stu-id="713bd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713bd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="713bd-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="713bd-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="713bd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="713bd-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="713bd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="713bd-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="713bd-110">Attributes</span></span>  
  
|<span data-ttu-id="713bd-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="713bd-111">Attribute</span></span>|<span data-ttu-id="713bd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="713bd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="713bd-113">type</span><span class="sxs-lookup"><span data-stu-id="713bd-113">type</span></span>|<span data-ttu-id="713bd-114"><xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıftan türeyen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="713bd-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="713bd-115">Öznitelik nasıl belirtilir `type` hakkında daha fazla bilgi için bkz: [Özel Tür Başvuruları].</span><span class="sxs-lookup"><span data-stu-id="713bd-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="713bd-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="713bd-116">Child Elements</span></span>  
 <span data-ttu-id="713bd-117">Öznitelik yoksa `type` veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfa başvuruyorsa, `<claimsAuthenticationManager>` öğe alt öğeleri almaz; ancak, türetilen <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıflar alt yapılandırma öğelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="713bd-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="713bd-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="713bd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="713bd-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="713bd-119">Element</span></span>|<span data-ttu-id="713bd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="713bd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="713bd-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="713bd-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="713bd-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="713bd-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="713bd-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="713bd-123">Remarks</span></span>  
 <span data-ttu-id="713bd-124"><xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıf aracılığıyla sağlanan varsayılan davranış, gelen talepleri yineler.</span><span class="sxs-lookup"><span data-stu-id="713bd-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="713bd-125">Öznitelik `type` belirtilmemişse veya `type` öznitelik sınıfı <xref:System.Security.Claims.ClaimsAuthenticationManager> belirtmiyorsa, `<claimsAuthenticationManager>` öğe alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="713bd-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="713bd-126">Özel davranış `type` uygulamak için <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıftan türetilen bir türü kaydetmek için özniteliği belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713bd-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="713bd-127">Türemiş sınıflar, bu öğeleri `<claimsAuthenticationManager>` işlemek için <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> yöntemi geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="713bd-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="713bd-128">Alt öğeler için tanımlanan şema sınıfın tasarımcısına kılır.</span><span class="sxs-lookup"><span data-stu-id="713bd-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="713bd-129">Öğe `<claimsAuthenticationManager>` <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="713bd-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="713bd-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="713bd-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
