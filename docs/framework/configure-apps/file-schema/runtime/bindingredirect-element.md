---
description: 'Daha fazla bilgi edinin: <bindingRedirect> öğesi'
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
ms.openlocfilehash: 833ee73fa11d179ac855f3ac4d2bca8d7a2226ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719181"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="a95ea-103">\<bindingRedirect> Öğesi</span><span class="sxs-lookup"><span data-stu-id="a95ea-103">\<bindingRedirect> Element</span></span>

<span data-ttu-id="a95ea-104">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-104">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="a95ea-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a95ea-105">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a95ea-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a95ea-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a95ea-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a95ea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a95ea-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a95ea-108">Attributes</span></span>  
  
|<span data-ttu-id="a95ea-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a95ea-109">Attribute</span></span>|<span data-ttu-id="a95ea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a95ea-110">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="a95ea-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a95ea-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a95ea-112">Başlangıçta istenen derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-112">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="a95ea-113">Bütünleştirilmiş kod sürümü numarası, *birincil. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="a95ea-113">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="a95ea-114">Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="a95ea-114">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="a95ea-115">Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a95ea-115">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="a95ea-116">*n. n. n. n-n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="a95ea-116">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="a95ea-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a95ea-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="a95ea-118">Özgün olarak istenen sürüm yerine kullanılacak derlemenin sürümünü belirtir: *n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="a95ea-118">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="a95ea-119">Bu değer, sürümünden önceki bir sürümü belirtebilir `oldVersion` .</span><span class="sxs-lookup"><span data-stu-id="a95ea-119">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a95ea-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a95ea-120">Child Elements</span></span>  
  
|<span data-ttu-id="a95ea-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a95ea-121">Element</span></span>|<span data-ttu-id="a95ea-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a95ea-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a95ea-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="a95ea-123">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="a95ea-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a95ea-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a95ea-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a95ea-125">Element</span></span>|<span data-ttu-id="a95ea-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a95ea-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a95ea-127">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a95ea-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a95ea-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="a95ea-129">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="a95ea-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="a95ea-130">Her bir derleme için bir bağımlı Derleme öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a95ea-130">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="a95ea-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a95ea-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a95ea-132">Remarks</span></span>  

 <span data-ttu-id="a95ea-133">Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a95ea-133">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="a95ea-134">Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a95ea-134">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="a95ea-135">Çalışma zamanının hangi derleme sürümünün kullanılacağını belirleme hakkında daha fazla bilgi için, bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a95ea-135">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="a95ea-136">Bir öğeye birden fazla öğe ekleyerek birden çok derleme sürümünü yeniden yönlendirebilirsiniz `bindingRedirect` `dependentAssembly` .</span><span class="sxs-lookup"><span data-stu-id="a95ea-136">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="a95ea-137">Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a95ea-137">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="a95ea-138">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-138">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="a95ea-139">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-139">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="a95ea-140"><xref:System.Security.Permissions.SecurityPermissionFlag>' De bayrak ayarlanarak izin verilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="a95ea-140">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a95ea-141">Daha fazla bilgi için bkz. [derleme bağlama yeniden yönlendirme güvenlik izni](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="a95ea-141">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a95ea-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="a95ea-142">Example</span></span>  

 <span data-ttu-id="a95ea-143">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a95ea-143">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a95ea-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a95ea-144">See also</span></span>

- [<span data-ttu-id="a95ea-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="a95ea-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a95ea-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a95ea-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a95ea-147">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="a95ea-147">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
