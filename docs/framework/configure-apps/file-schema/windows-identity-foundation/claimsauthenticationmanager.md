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
ms.openlocfilehash: 48e5be23b196a24a9d3e2a1dc4639d8ca9823660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="001bb-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="001bb-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="001bb-103">Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="001bb-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="001bb-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="001bb-104">\<system.identityModel></span></span>  
<span data-ttu-id="001bb-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="001bb-105">\<identityConfiguration></span></span>  
<span data-ttu-id="001bb-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="001bb-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001bb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="001bb-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="001bb-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="001bb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="001bb-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="001bb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="001bb-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="001bb-110">Attributes</span></span>  
  
|<span data-ttu-id="001bb-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="001bb-111">Attribute</span></span>|<span data-ttu-id="001bb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="001bb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="001bb-113">türü</span><span class="sxs-lookup"><span data-stu-id="001bb-113">type</span></span>|<span data-ttu-id="001bb-114">Türetilen bir özel tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="001bb-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="001bb-115">Nasıl belirleneceği hakkında daha fazla bilgi için `type` [özel tür başvuruları] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="001bb-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="001bb-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="001bb-116">Child Elements</span></span>  
 <span data-ttu-id="001bb-117">Varsa hiçbir `type` özniteliği veya `type` özniteliği başvuruları <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="001bb-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="001bb-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="001bb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="001bb-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="001bb-119">Element</span></span>|<span data-ttu-id="001bb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="001bb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="001bb-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="001bb-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="001bb-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="001bb-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="001bb-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="001bb-123">Remarks</span></span>  
 <span data-ttu-id="001bb-124">Üzerinden sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="001bb-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="001bb-125">Öyle değilse `type` özniteliği belirtilmediyse veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz.</span><span class="sxs-lookup"><span data-stu-id="001bb-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="001bb-126">Belirleyebileceğiniz `type` türü kaydetmek için öznitelik türetilen <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="001bb-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="001bb-127">Türetilen sınıflar, alt öğelerinin üzerinden yapılandırmayı destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğeleri işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="001bb-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="001bb-128">Alt öğeler için tanımlanan şema Sınıf Tasarımcısı kadar olur.</span><span class="sxs-lookup"><span data-stu-id="001bb-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="001bb-129">`<claimsAuthenticationManager>` Öğesi kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="001bb-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="001bb-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="001bb-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
