---
title: <bindingRedirect> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: dda99bb4b96efbdd274e24e7cd548e4ed4df8b66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704901"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="543c3-102">\<bindingRedirect > öğesi</span><span class="sxs-lookup"><span data-stu-id="543c3-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="543c3-103">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="543c3-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="543c3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="543c3-104">\<configuration></span></span>  
<span data-ttu-id="543c3-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="543c3-105">\<runtime></span></span>  
<span data-ttu-id="543c3-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="543c3-106">\<assemblyBinding></span></span>  
<span data-ttu-id="543c3-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="543c3-107">\<dependentAssembly></span></span>  
<span data-ttu-id="543c3-108">\<bindingRedirect ></span><span class="sxs-lookup"><span data-stu-id="543c3-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543c3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="543c3-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="543c3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="543c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="543c3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="543c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="543c3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="543c3-112">Attributes</span></span>  
  
|<span data-ttu-id="543c3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="543c3-113">Attribute</span></span>|<span data-ttu-id="543c3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="543c3-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="543c3-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="543c3-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="543c3-116">Başlangıçta istenen derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="543c3-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="543c3-117">Bir derleme sürümü numarasının biçimi *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="543c3-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="543c3-118">Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="543c3-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="543c3-119">Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="543c3-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="543c3-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="543c3-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="543c3-121">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="543c3-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="543c3-122">Biçimde başlangıçta istenen sürüm yerine kullanılacak derleme sürümünü belirtir: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="543c3-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="543c3-123">' Den önceki sürümleri bu değeri belirtebilirsiniz `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="543c3-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="543c3-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="543c3-124">Child Elements</span></span>  
  
|<span data-ttu-id="543c3-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="543c3-125">Element</span></span>|<span data-ttu-id="543c3-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="543c3-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="543c3-127">None</span><span class="sxs-lookup"><span data-stu-id="543c3-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="543c3-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="543c3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="543c3-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="543c3-129">Element</span></span>|<span data-ttu-id="543c3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="543c3-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="543c3-131">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="543c3-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="543c3-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="543c3-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="543c3-133">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="543c3-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="543c3-134">Her bir derleme için bir bağımlı Derleme öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="543c3-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="543c3-135">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="543c3-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="543c3-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="543c3-136">Remarks</span></span>  
 <span data-ttu-id="543c3-137">Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="543c3-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="543c3-138">Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="543c3-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="543c3-139">Bu dosyalarını çalışma zamanının hangi derleme sürümünün kullanılacağını belirlemek için nasıl kullandığı hakkında daha fazla bilgi için bkz [çalışma zamanı derlemeleri nasıl konumlandırır](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="543c3-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="543c3-140">Ekleyerek, birden çok derleme sürümünü yeniden yönlendirebilirsiniz `bindingRedirect` öğelerinde bir `dependentAssembly` öğesi.</span><span class="sxs-lookup"><span data-stu-id="543c3-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="543c3-141">Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="543c3-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="543c3-142">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="543c3-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="543c3-143">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="543c3-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="543c3-144">İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="543c3-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="543c3-145">Daha fazla bilgi için [bütünleştirilmiş kod bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="543c3-145">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="543c3-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="543c3-146">Example</span></span>  
 <span data-ttu-id="543c3-147">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="543c3-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="543c3-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="543c3-148">See also</span></span>

- [<span data-ttu-id="543c3-149">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="543c3-149">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="543c3-150">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="543c3-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="543c3-151">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="543c3-151">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
