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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154302"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="1a074-102">\<bindingRedirect> Öğesi</span><span class="sxs-lookup"><span data-stu-id="1a074-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="1a074-103">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="1a074-103">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="1a074-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a074-104">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a074-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a074-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1a074-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a074-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a074-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a074-107">Attributes</span></span>  
  
|<span data-ttu-id="1a074-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a074-108">Attribute</span></span>|<span data-ttu-id="1a074-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a074-109">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="1a074-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1a074-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a074-111">Başlangıçta istenen derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a074-111">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="1a074-112">Bütünleştirilmiş kod sürümü numarası, *birincil. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="1a074-112">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="1a074-113">Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="1a074-113">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="1a074-114">Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a074-114">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="1a074-115">*n. n. n. n-n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="1a074-115">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="1a074-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1a074-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a074-117">Özgün olarak istenen sürüm yerine kullanılacak derlemenin sürümünü belirtir: *n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="1a074-117">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="1a074-118">Bu değer, sürümünden önceki bir sürümü belirtebilir `oldVersion` .</span><span class="sxs-lookup"><span data-stu-id="1a074-118">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a074-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a074-119">Child Elements</span></span>  
  
|<span data-ttu-id="1a074-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a074-120">Element</span></span>|<span data-ttu-id="1a074-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a074-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a074-122">Yok</span><span class="sxs-lookup"><span data-stu-id="1a074-122">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="1a074-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a074-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1a074-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a074-124">Element</span></span>|<span data-ttu-id="1a074-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a074-125">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="1a074-126">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1a074-126">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="1a074-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1a074-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="1a074-128">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="1a074-128">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="1a074-129">Her bir derleme için bir bağımlı Derleme öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a074-129">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="1a074-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1a074-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a074-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a074-131">Remarks</span></span>  
 <span data-ttu-id="1a074-132">Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="1a074-132">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="1a074-133">Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a074-133">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="1a074-134">Çalışma zamanının hangi derleme sürümünün kullanılacağını belirleme hakkında daha fazla bilgi için, bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1a074-134">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="1a074-135">Bir öğeye birden fazla öğe ekleyerek birden çok derleme sürümünü yeniden yönlendirebilirsiniz `bindingRedirect` `dependentAssembly` .</span><span class="sxs-lookup"><span data-stu-id="1a074-135">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="1a074-136">Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a074-136">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="1a074-137">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a074-137">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="1a074-138">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1a074-138">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="1a074-139"><xref:System.Security.Permissions.SecurityPermissionFlag>' De bayrak ayarlanarak izin verilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="1a074-139">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="1a074-140">Daha fazla bilgi için bkz. [derleme bağlama yeniden yönlendirme güvenlik izni](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="1a074-140">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a074-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a074-141">Example</span></span>  
 <span data-ttu-id="1a074-142">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1a074-142">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a074-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a074-143">See also</span></span>

- [<span data-ttu-id="1a074-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="1a074-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1a074-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1a074-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1a074-146">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="1a074-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
