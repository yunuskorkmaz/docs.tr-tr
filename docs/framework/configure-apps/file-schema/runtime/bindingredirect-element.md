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
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154302"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="a7f43-102">\<bağlayıcıRedirect> Elemanı</span><span class="sxs-lookup"><span data-stu-id="a7f43-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="a7f43-103">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-103">Redirects one assembly version to another.</span></span>  
  
<span data-ttu-id="a7f43-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7f43-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7f43-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7f43-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a7f43-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montajBağlama>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="a7f43-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="a7f43-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bağımlıAssembly>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7f43-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="a7f43-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcıRedirect>**</span><span class="sxs-lookup"><span data-stu-id="a7f43-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f43-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7f43-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f43-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f43-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f43-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7f43-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f43-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7f43-112">Attributes</span></span>  
  
|<span data-ttu-id="a7f43-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7f43-113">Attribute</span></span>|<span data-ttu-id="a7f43-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f43-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="a7f43-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a7f43-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="a7f43-116">Başlangıçta istenen derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="a7f43-117">Bir derleme sürüm numarasının biçimi *major.minor.build.revision*' dir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="a7f43-118">Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="a7f43-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="a7f43-119">Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7f43-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="a7f43-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="a7f43-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="a7f43-121">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a7f43-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="a7f43-122">Biçimde başlangıçta istenen sürüm yerine kullanılacak derleme sürümünü belirtir: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="a7f43-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="a7f43-123">Bu değer, 'den `oldVersion`önceki bir sürümü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7f43-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f43-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f43-124">Child Elements</span></span>  
  
|<span data-ttu-id="a7f43-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7f43-125">Element</span></span>|<span data-ttu-id="a7f43-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f43-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7f43-127">None</span><span class="sxs-lookup"><span data-stu-id="a7f43-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f43-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7f43-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f43-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7f43-129">Element</span></span>|<span data-ttu-id="a7f43-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f43-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a7f43-131">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a7f43-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a7f43-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="a7f43-133">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="a7f43-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="a7f43-134">Her bir derleme için bir bağımlı Derleme öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7f43-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="a7f43-135">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f43-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7f43-136">Remarks</span></span>  
 <span data-ttu-id="a7f43-137">Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7f43-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="a7f43-138">Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7f43-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="a7f43-139">Çalışma zamanının hangi derleme sürümünü niçin kullanacağını belirlemek için bu dosyaları nasıl kullandığına ilişkin ayrıntılar [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'a](../../../deployment/how-the-runtime-locates-assemblies.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a7f43-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="a7f43-140">Bir `bindingRedirect` `dependentAssembly` öğeye birden çok öğe ekleyerek birden fazla derleme sürümünü yeniden yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7f43-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="a7f43-141">Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7f43-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="a7f43-142">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="a7f43-143">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="a7f43-144">İzin, <xref:System.Security.Permissions.SecurityPermissionFlag> bayrağın üzerinde ayarlanmasıyla <xref:System.Security.Permissions.SecurityPermission>verilir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a7f43-145">Daha fazla bilgi için, [Derleme Bağlama Yeniden Yönlendirme Güvenlik İzni'ne](../../assembly-binding-redirection-security-permission.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a7f43-145">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f43-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7f43-146">Example</span></span>  
 <span data-ttu-id="a7f43-147">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a7f43-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7f43-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f43-148">See also</span></span>

- [<span data-ttu-id="a7f43-149">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a7f43-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a7f43-150">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="a7f43-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a7f43-151">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="a7f43-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
