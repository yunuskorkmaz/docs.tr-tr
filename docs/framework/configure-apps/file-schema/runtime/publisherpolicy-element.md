---
title: <publisherPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252376"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="b8739-102">\<publisherPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="b8739-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="b8739-103">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8739-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="b8739-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8739-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8739-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8739-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b8739-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="b8739-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="b8739-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8739-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="b8739-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy >**</span><span class="sxs-lookup"><span data-stu-id="b8739-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8739-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8739-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8739-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8739-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b8739-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8739-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8739-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8739-112">Attributes</span></span>  
  
|<span data-ttu-id="b8739-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8739-113">Attribute</span></span>|<span data-ttu-id="b8739-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8739-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="b8739-115">Yayımcı ilkesinin uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8739-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="b8739-116">Özniteliği Uygula</span><span class="sxs-lookup"><span data-stu-id="b8739-116">apply Attribute</span></span>  
  
|<span data-ttu-id="b8739-117">Değer</span><span class="sxs-lookup"><span data-stu-id="b8739-117">Value</span></span>|<span data-ttu-id="b8739-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8739-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="b8739-119">Yayımcı ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="b8739-119">Applies publisher policy.</span></span> <span data-ttu-id="b8739-120">Varsayılan ayar budur.</span><span class="sxs-lookup"><span data-stu-id="b8739-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="b8739-121">Yayımcı ilkesi uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="b8739-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8739-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8739-122">Child Elements</span></span>  

<span data-ttu-id="b8739-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8739-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8739-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8739-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b8739-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8739-125">Element</span></span>|<span data-ttu-id="b8739-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8739-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="b8739-127">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b8739-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="b8739-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b8739-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="b8739-129">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="b8739-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="b8739-130">Her derleme `<dependentAssembly>` için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8739-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="b8739-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b8739-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8739-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8739-132">Remarks</span></span>  
 <span data-ttu-id="b8739-133">Bir bileşen satıcısı bir derlemenin yeni bir sürümünü yayımlarsa, satıcı bir yayımcı ilkesi içerebilir, bu nedenle eski sürümü kullanan uygulamalar artık yeni sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8739-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="b8739-134">Belirli bir derleme için yayımcı ilkesinin uygulanıp uygulanmayacağını belirtmek için,  **\<publisherPolicy >** öğesini  **\<dependentAssembly >** öğesine koyun.</span><span class="sxs-lookup"><span data-stu-id="b8739-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="b8739-135">**Apply** özniteliği için varsayılan ayar **Evet**' tir.</span><span class="sxs-lookup"><span data-stu-id="b8739-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="b8739-136">**Apply** özniteliğini **Hayır** olarak ayarlamak, bir derleme için önceki tüm **Evet** ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b8739-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="b8739-137">Uygulamanın, uygulama yapılandırma dosyasında [ \<publisherPolicy apply = "No"/>](publisherpolicy-element.md) öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8739-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="b8739-138">' De <xref:System.Security.Permissions.SecurityPermissionFlag> bayrak ayarlanarak izin verilir. <xref:System.Security.Permissions.SecurityPermission></span><span class="sxs-lookup"><span data-stu-id="b8739-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="b8739-139">Daha fazla bilgi için bkz. [derleme bağlama yeniden yönlendirme güvenlik izni](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="b8739-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8739-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8739-140">Example</span></span>  
 <span data-ttu-id="b8739-141">Aşağıdaki örnek, derleme `myAssembly`için yayımcı ilkesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b8739-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8739-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8739-142">See also</span></span>

- [<span data-ttu-id="b8739-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b8739-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b8739-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="b8739-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b8739-145">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="b8739-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b8739-146">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="b8739-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
