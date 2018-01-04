---
title: "&lt;bindingRedirect&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f8cd497871d8a58504cf790f84cc7e5a1d4e39b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingredirectgt-element"></a><span data-ttu-id="12608-102">&lt;bindingRedirect&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="12608-102">&lt;bindingRedirect&gt; Element</span></span>
<span data-ttu-id="12608-103">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="12608-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="12608-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="12608-104">\<configuration></span></span>  
<span data-ttu-id="12608-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="12608-105">\<runtime></span></span>  
<span data-ttu-id="12608-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="12608-106">\<assemblyBinding></span></span>  
<span data-ttu-id="12608-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="12608-107">\<dependentAssembly></span></span>  
<span data-ttu-id="12608-108">\<bindingRedirect ></span><span class="sxs-lookup"><span data-stu-id="12608-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12608-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12608-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12608-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12608-110">Attributes and Elements</span></span>  
 <span data-ttu-id="12608-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12608-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12608-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12608-112">Attributes</span></span>  
  
|<span data-ttu-id="12608-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12608-113">Attribute</span></span>|<span data-ttu-id="12608-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12608-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="12608-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="12608-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="12608-116">Başlangıçta istenen derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="12608-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="12608-117">Bir derleme sürüm numarası biçimi *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="12608-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="12608-118">Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="12608-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="12608-119">Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="12608-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="12608-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="12608-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="12608-121">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="12608-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="12608-122">İlk olarak istenen sürüm biçimde yerine kullanılacak derlemesinin sürümü belirtir: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="12608-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="12608-123">Bu değeri daha önceki bir sürümü belirtebilirsiniz `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="12608-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12608-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12608-124">Child Elements</span></span>  
  
|<span data-ttu-id="12608-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="12608-125">Element</span></span>|<span data-ttu-id="12608-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12608-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12608-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="12608-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="12608-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12608-128">Parent Elements</span></span>  
  
|<span data-ttu-id="12608-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="12608-129">Element</span></span>|<span data-ttu-id="12608-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12608-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="12608-131">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="12608-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="12608-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="12608-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="12608-133">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="12608-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="12608-134">Her bir derleme için bir bağımlı Derleme öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="12608-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="12608-135">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="12608-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12608-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12608-136">Remarks</span></span>  
 <span data-ttu-id="12608-137">Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="12608-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="12608-138">Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12608-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="12608-139">Bu dosyaları çalışma zamanı kullanmak için hangi derleme sürümünü belirlemek için nasıl kullandığı hakkında daha fazla bilgi için bkz [nasıl çalışma zamanı bulur derlemeleri](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="12608-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="12608-140">Birden çok ekleyerek birden fazla derleme sürümünü yeniden yönlendirebilirsiniz `bindingRedirect` öğelerinde bir `dependentAssembly` öğesi.</span><span class="sxs-lookup"><span data-stu-id="12608-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="12608-141">Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12608-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="12608-142">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="12608-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="12608-143">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="12608-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="12608-144">Ayarlayarak iznine sahip <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="12608-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="12608-145">Daha fazla bilgi için bkz: [derleme bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="12608-145">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12608-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="12608-146">Example</span></span>  
 <span data-ttu-id="12608-147">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12608-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12608-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12608-148">See Also</span></span>  
 [<span data-ttu-id="12608-149">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="12608-149">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="12608-150">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="12608-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="12608-151">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="12608-151">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
