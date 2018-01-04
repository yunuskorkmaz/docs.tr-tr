---
title: "&lt;bypassTrustedAppStrongNames&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="5a9d1-102">&lt;bypassTrustedAppStrongNames&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="5a9d1-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="5a9d1-103">Tanımlayıcı adlar tam güvene yüklenen tam güven derlemeleri Doğrulamayı atla belirtir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="5a9d1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5a9d1-104">\<configuration></span></span>  
<span data-ttu-id="5a9d1-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="5a9d1-105">\<runtime></span></span>  
<span data-ttu-id="5a9d1-106">\<bypassTrustedAppStrongNames ></span><span class="sxs-lookup"><span data-stu-id="5a9d1-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a9d1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a9d1-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a9d1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a9d1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a9d1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a9d1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a9d1-110">Attributes</span></span>  
  
|<span data-ttu-id="5a9d1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5a9d1-111">Attribute</span></span>|<span data-ttu-id="5a9d1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a9d1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5a9d1-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a9d1-114">Tanımlayıcı adlar tam güven derlemeler için doğrulama önler atlama özelliğini etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="5a9d1-115">Bu özellik etkinleştirildiğinde, derleme yüklendiğinde tanımlayıcı adlar doğruluğu doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="5a9d1-116">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5a9d1-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5a9d1-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="5a9d1-118">Değer</span><span class="sxs-lookup"><span data-stu-id="5a9d1-118">Value</span></span>|<span data-ttu-id="5a9d1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a9d1-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="5a9d1-120">Tam güven derlemeleri imzaları tanımlayıcı ad derlemeleri tam güvene yüklü olduğunda doğrulanmaz <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="5a9d1-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="5a9d1-122">Tam güven derlemeleri imzaları tanımlayıcı ad derlemeleri tam güvene yüklü olduğunda doğrulanma <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="5a9d1-123">Tanımlayıcı ad imzası yalnızca imza doğruluğu denetlenir; bir eşleşme için başka bir güçlü ad için karşılaştırıldığında değil.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a9d1-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a9d1-124">Child Elements</span></span>  
 <span data-ttu-id="5a9d1-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a9d1-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a9d1-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5a9d1-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a9d1-127">Element</span></span>|<span data-ttu-id="5a9d1-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a9d1-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a9d1-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a9d1-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a9d1-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a9d1-131">Remarks</span></span>  
 <span data-ttu-id="5a9d1-132">Tanımlayıcı adlı atlama özelliği tam güven derlemelerin tanımlayıcı ad imzası doğrulama yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="5a9d1-133">Atlama özelliğini tanımlayıcı bir ad ile imzalanmış ve aşağıdaki özelliklere sahip herhangi bir derlemeye geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="5a9d1-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="5a9d1-134">Tam olarak güvenilmeyen olmadan <xref:System.Security.Policy.StrongName> kanıt (örneğin, sahip `MyComputer` bölge kanıt).</span><span class="sxs-lookup"><span data-stu-id="5a9d1-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="5a9d1-135">Bir tam olarak güvenilmeyen yüklenen <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="5a9d1-136">Altında bir konumdan yüklenen <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği, <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="5a9d1-137">Gecikme imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a9d1-138">Atlama özelliği bilgisayardaki tüm uygulamalar için bir kayıt defteri anahtarını kullanarak kapatıldı, bu yapılandırma dosyası ayarı bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="5a9d1-139">Daha fazla bilgi için bkz: [nasıl yapılır: tanımlayıcı adlı atlama özelliğini devre dışı](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="5a9d1-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a9d1-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a9d1-140">Example</span></span>  
 <span data-ttu-id="5a9d1-141">Aşağıdaki örnek, tam güven derlemeleri sağlam ad imzası doğrulama davranışını belirtmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a9d1-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-142">See Also</span></span>  
 [<span data-ttu-id="5a9d1-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5a9d1-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5a9d1-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5a9d1-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5a9d1-145">Nasıl yapılır: Kesin Adlandırılmış Atlama Özelliğini Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="5a9d1-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
