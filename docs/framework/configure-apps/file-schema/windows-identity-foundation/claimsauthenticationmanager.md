---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 0ec7e44363f87e54eae97b70352f520fe87540be
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032298"
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="221bf-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="221bf-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="221bf-103">Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="221bf-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="221bf-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="221bf-104">\<system.identityModel></span></span>  
<span data-ttu-id="221bf-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="221bf-105">\<identityConfiguration></span></span>  
<span data-ttu-id="221bf-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="221bf-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221bf-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="221bf-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="221bf-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="221bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="221bf-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="221bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="221bf-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="221bf-110">Attributes</span></span>  
  
|<span data-ttu-id="221bf-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="221bf-111">Attribute</span></span>|<span data-ttu-id="221bf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="221bf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="221bf-113">türü</span><span class="sxs-lookup"><span data-stu-id="221bf-113">type</span></span>|<span data-ttu-id="221bf-114">Öğesinden türetilen özel bir türü belirtiyor <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="221bf-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="221bf-115">Belirtme hakkında daha fazla bilgi için `type` [özel tür başvurularını] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="221bf-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="221bf-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="221bf-116">Child Elements</span></span>  
 <span data-ttu-id="221bf-117">Yoksa hiçbir `type` özniteliği veya `type` başvuruları öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` öğenin alt öğeleri almaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="221bf-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="221bf-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="221bf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="221bf-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="221bf-119">Element</span></span>|<span data-ttu-id="221bf-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="221bf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="221bf-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="221bf-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="221bf-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="221bf-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="221bf-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="221bf-123">Remarks</span></span>  
 <span data-ttu-id="221bf-124">Sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="221bf-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="221bf-125">Hayır ise `type` özniteliği veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` öğenin alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="221bf-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="221bf-126">Belirtebileceğiniz `type` sınıfından türetilen bir tür kaydetmek için öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="221bf-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="221bf-127">Türetilen sınıflar, alt öğelerinin konfigürasyonuyla destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğelerini işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="221bf-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="221bf-128">Sınıf Tasarımcısı kadar alt öğeleri için tanımlanan şema var.</span><span class="sxs-lookup"><span data-stu-id="221bf-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="221bf-129">`<claimsAuthenticationManager>` Öğe kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="221bf-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="221bf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="221bf-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
