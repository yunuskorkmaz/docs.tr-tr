---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255191"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="df494-101">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="df494-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="df494-102">Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="df494-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="df494-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="df494-103">\<system.identityModel></span></span>  
<span data-ttu-id="df494-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="df494-104">\<identityConfiguration></span></span>  
<span data-ttu-id="df494-105">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="df494-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df494-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df494-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df494-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df494-107">Attributes and Elements</span></span>  
 <span data-ttu-id="df494-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df494-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df494-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df494-109">Attributes</span></span>  
  
|<span data-ttu-id="df494-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df494-110">Attribute</span></span>|<span data-ttu-id="df494-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df494-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df494-112">türü</span><span class="sxs-lookup"><span data-stu-id="df494-112">type</span></span>|<span data-ttu-id="df494-113">Öğesinden türetilen özel bir türü belirtiyor <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="df494-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="df494-114">Belirtme hakkında daha fazla bilgi için `type` [özel tür başvurularını] özniteliği için bkz.</span><span class="sxs-lookup"><span data-stu-id="df494-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df494-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df494-115">Child Elements</span></span>  
 <span data-ttu-id="df494-116">Yoksa hiçbir `type` özniteliği veya `type` başvuruları öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` öğenin alt öğeleri almaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df494-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df494-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df494-117">Parent Elements</span></span>  
  
|<span data-ttu-id="df494-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="df494-118">Element</span></span>|<span data-ttu-id="df494-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df494-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df494-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="df494-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="df494-121">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="df494-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df494-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df494-122">Remarks</span></span>  
 <span data-ttu-id="df494-123">Sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="df494-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="df494-124">Hayır ise `type` özniteliği veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` öğenin alt öğeleri almaz.</span><span class="sxs-lookup"><span data-stu-id="df494-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="df494-125">Belirtebileceğiniz `type` sınıfından türetilen bir tür kaydetmek için öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="df494-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="df494-126">Türetilen sınıflar, alt öğelerinin konfigürasyonuyla destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğelerini işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df494-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="df494-127">Sınıf Tasarımcısı kadar alt öğeleri için tanımlanan şema var.</span><span class="sxs-lookup"><span data-stu-id="df494-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="df494-128">`<claimsAuthenticationManager>` Öğe kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="df494-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df494-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="df494-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
