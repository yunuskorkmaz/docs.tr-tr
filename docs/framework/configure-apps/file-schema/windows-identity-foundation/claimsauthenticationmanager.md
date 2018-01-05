---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b7d68c2fe89b5ca56319df2f24fadd51f329f5ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="6c1a1-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="6c1a1-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="6c1a1-103">Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="6c1a1-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="6c1a1-104">\<system.identityModel></span></span>  
<span data-ttu-id="6c1a1-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6c1a1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="6c1a1-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="6c1a1-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c1a1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c1a1-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c1a1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1a1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6c1a1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c1a1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c1a1-110">Attributes</span></span>  
  
|<span data-ttu-id="6c1a1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c1a1-111">Attribute</span></span>|<span data-ttu-id="6c1a1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1a1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c1a1-113">türü</span><span class="sxs-lookup"><span data-stu-id="6c1a1-113">type</span></span>|<span data-ttu-id="6c1a1-114">Türetilen bir özel tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="6c1a1-115">Nasıl belirleneceği hakkında daha fazla bilgi için `type` [özel tür başvuruları] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c1a1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1a1-116">Child Elements</span></span>  
 <span data-ttu-id="6c1a1-117">Varsa hiçbir `type` özniteliği veya `type` özniteliği başvuruları <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c1a1-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c1a1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6c1a1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c1a1-119">Element</span></span>|<span data-ttu-id="6c1a1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1a1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c1a1-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6c1a1-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="6c1a1-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c1a1-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c1a1-123">Remarks</span></span>  
 <span data-ttu-id="6c1a1-124">Üzerinden sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="6c1a1-125">Öyle değilse `type` özniteliği belirtilmediyse veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="6c1a1-126">Belirleyebileceğiniz `type` türü kaydetmek için öznitelik türetilen <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="6c1a1-127">Türetilen sınıflar, alt öğelerinin üzerinden yapılandırmayı destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğeleri işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="6c1a1-128">Alt öğeler için tanımlanan şema Sınıf Tasarımcısı kadar olur.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="6c1a1-129">`<claimsAuthenticationManager>` Öğesi kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6c1a1-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c1a1-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c1a1-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
