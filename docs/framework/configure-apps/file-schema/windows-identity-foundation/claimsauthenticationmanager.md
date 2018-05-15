---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="88cf2-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="88cf2-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="88cf2-103">Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="88cf2-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="88cf2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="88cf2-104">\<system.identityModel></span></span>  
<span data-ttu-id="88cf2-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="88cf2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="88cf2-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="88cf2-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cf2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88cf2-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88cf2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="88cf2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="88cf2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88cf2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88cf2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="88cf2-110">Attributes</span></span>  
  
|<span data-ttu-id="88cf2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="88cf2-111">Attribute</span></span>|<span data-ttu-id="88cf2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88cf2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88cf2-113">türü</span><span class="sxs-lookup"><span data-stu-id="88cf2-113">type</span></span>|<span data-ttu-id="88cf2-114">Türetilen bir özel tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88cf2-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="88cf2-115">Nasıl belirleneceği hakkında daha fazla bilgi için `type` [özel tür başvuruları] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="88cf2-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88cf2-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="88cf2-116">Child Elements</span></span>  
 <span data-ttu-id="88cf2-117">Varsa hiçbir `type` özniteliği veya `type` özniteliği başvuruları <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88cf2-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88cf2-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="88cf2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="88cf2-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="88cf2-119">Element</span></span>|<span data-ttu-id="88cf2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88cf2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88cf2-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="88cf2-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="88cf2-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="88cf2-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88cf2-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88cf2-123">Remarks</span></span>  
 <span data-ttu-id="88cf2-124">Üzerinden sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="88cf2-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="88cf2-125">Öyle değilse `type` özniteliği belirtilmediyse veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz.</span><span class="sxs-lookup"><span data-stu-id="88cf2-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="88cf2-126">Belirleyebileceğiniz `type` türü kaydetmek için öznitelik türetilen <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="88cf2-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="88cf2-127">Türetilen sınıflar, alt öğelerinin üzerinden yapılandırmayı destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğeleri işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="88cf2-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="88cf2-128">Alt öğeler için tanımlanan şema Sınıf Tasarımcısı kadar olur.</span><span class="sxs-lookup"><span data-stu-id="88cf2-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="88cf2-129">`<claimsAuthenticationManager>` Öğesi kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="88cf2-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88cf2-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="88cf2-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
