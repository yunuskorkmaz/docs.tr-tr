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
ms.openlocfilehash: 7c8f8744d3ef1ca30eb05a4c8c3290d8a514714b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663509"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="9c6de-102">\<publisherPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="9c6de-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="9c6de-103">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c6de-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="9c6de-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9c6de-104">\<configuration></span></span>  
<span data-ttu-id="9c6de-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="9c6de-105">\<runtime></span></span>  
<span data-ttu-id="9c6de-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="9c6de-106">\<assemblyBinding></span></span>  
<span data-ttu-id="9c6de-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="9c6de-107">\<dependentAssembly></span></span>  
<span data-ttu-id="9c6de-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="9c6de-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6de-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c6de-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c6de-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c6de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c6de-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c6de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c6de-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9c6de-112">Attributes</span></span>  
  
|<span data-ttu-id="9c6de-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9c6de-113">Attribute</span></span>|<span data-ttu-id="9c6de-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c6de-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="9c6de-115">Yayımcı ilkesinin uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c6de-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="9c6de-116">Özniteliği Uygula</span><span class="sxs-lookup"><span data-stu-id="9c6de-116">apply Attribute</span></span>  
  
|<span data-ttu-id="9c6de-117">Değer</span><span class="sxs-lookup"><span data-stu-id="9c6de-117">Value</span></span>|<span data-ttu-id="9c6de-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c6de-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="9c6de-119">Yayımcı ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="9c6de-119">Applies publisher policy.</span></span> <span data-ttu-id="9c6de-120">Varsayılan ayar budur.</span><span class="sxs-lookup"><span data-stu-id="9c6de-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="9c6de-121">Yayımcı ilkesi uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="9c6de-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c6de-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c6de-122">Child Elements</span></span>  
 <span data-ttu-id="9c6de-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="9c6de-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c6de-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c6de-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9c6de-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c6de-125">Element</span></span>|<span data-ttu-id="9c6de-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c6de-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9c6de-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9c6de-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9c6de-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9c6de-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c6de-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c6de-129">Remarks</span></span>  
 <span data-ttu-id="9c6de-130">Bir bileşen satıcısı bir derlemenin yeni bir sürümünü yayımlarsa, satıcı bir yayımcı ilkesi içerebilir, bu nedenle eski sürümü kullanan uygulamalar artık yeni sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c6de-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="9c6de-131">Belirli bir derleme için yayımcı ilkesinin uygulanıp uygulanmayacağını belirtmek için,  **\<publisherPolicy >** öğesini  **\<dependentAssembly >** öğesine koyun.</span><span class="sxs-lookup"><span data-stu-id="9c6de-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="9c6de-132">**Apply** özniteliği için varsayılan ayar **Evet**' tir.</span><span class="sxs-lookup"><span data-stu-id="9c6de-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="9c6de-133">**Apply** özniteliğini **Hayır** olarak ayarlamak, bir derleme için önceki tüm **Evet** ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9c6de-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="9c6de-134">Uygulamanın, uygulama yapılandırma dosyasında [ \<publisherPolicy apply = "No"/>](publisherpolicy-element.md) öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c6de-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="9c6de-135">' De <xref:System.Security.Permissions.SecurityPermissionFlag> bayrak ayarlanarak izin verilir. <xref:System.Security.Permissions.SecurityPermission></span><span class="sxs-lookup"><span data-stu-id="9c6de-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="9c6de-136">Daha fazla bilgi için bkz. [derleme bağlama yeniden yönlendirme güvenlik izni](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="9c6de-136">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c6de-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c6de-137">Example</span></span>  
 <span data-ttu-id="9c6de-138">Aşağıdaki örnek, derleme `myAssembly`için yayımcı ilkesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9c6de-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c6de-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c6de-139">See also</span></span>

- [<span data-ttu-id="9c6de-140">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9c6de-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9c6de-141">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="9c6de-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9c6de-142">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="9c6de-142">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9c6de-143">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="9c6de-143">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
