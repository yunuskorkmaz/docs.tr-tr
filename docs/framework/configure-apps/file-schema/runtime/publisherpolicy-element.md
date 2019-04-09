---
title: <publisherPolicy> Öğe
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
ms.openlocfilehash: 29932eb27bcd13876ea6982982e67341edb8e0de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076295"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="21290-102">\<publisherPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="21290-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="21290-103">Çalışma zamanı Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21290-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="21290-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="21290-104">\<configuration></span></span>  
<span data-ttu-id="21290-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="21290-105">\<runtime></span></span>  
<span data-ttu-id="21290-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="21290-106">\<assemblyBinding></span></span>  
<span data-ttu-id="21290-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="21290-107">\<dependentAssembly></span></span>  
<span data-ttu-id="21290-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="21290-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21290-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21290-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21290-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21290-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21290-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21290-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21290-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21290-112">Attributes</span></span>  
  
|<span data-ttu-id="21290-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21290-113">Attribute</span></span>|<span data-ttu-id="21290-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21290-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="21290-115">Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21290-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="21290-116">bir öznitelik uygulama</span><span class="sxs-lookup"><span data-stu-id="21290-116">apply Attribute</span></span>  
  
|<span data-ttu-id="21290-117">Değer</span><span class="sxs-lookup"><span data-stu-id="21290-117">Value</span></span>|<span data-ttu-id="21290-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21290-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="21290-119">Yayımcı ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="21290-119">Applies publisher policy.</span></span> <span data-ttu-id="21290-120">Varsayılan ayar budur.</span><span class="sxs-lookup"><span data-stu-id="21290-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="21290-121">Yayımcı ilkesi uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="21290-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21290-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21290-122">Child Elements</span></span>  
 <span data-ttu-id="21290-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="21290-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21290-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21290-124">Parent Elements</span></span>  
  
|<span data-ttu-id="21290-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="21290-125">Element</span></span>|<span data-ttu-id="21290-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21290-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="21290-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="21290-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="21290-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="21290-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21290-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21290-129">Remarks</span></span>  
 <span data-ttu-id="21290-130">Bir bileşen Satıcı bir derlemenin yeni bir sürümü yayımlandığında yeni sürümü artık eski sürümü kullanan uygulamaları kullanmak için satıcı Yayımcı ilkesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="21290-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="21290-131">Belirli bir derleme için yayımcı ilkesi uygulanıp uygulanmayacağını belirtmek için put  **\<publisherPolicy >** öğesinde  **\<dependentAssembly >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="21290-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="21290-132">Varsayılan ayarı **uygulamak** özniteliği **Evet**.</span><span class="sxs-lookup"><span data-stu-id="21290-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="21290-133">Ayarlama **uygulamak** özniteliğini **hiçbir** önceki tüm geçersiz kılmaları **Evet** bir derleme için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="21290-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="21290-134">Yayımcı ilkesi kullanarak açıkça yoksaymak bir uygulama için gerekli izni [ \<publisherPolicy uygulama = "Hayır" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) öğesi uygulama yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="21290-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="21290-135">İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="21290-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="21290-136">Daha fazla bilgi için [bütünleştirilmiş kod bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="21290-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21290-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="21290-137">Example</span></span>  
 <span data-ttu-id="21290-138">Aşağıdaki örnek derleme için yayımcı ilkesini devre dışı bırakır `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="21290-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21290-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21290-139">See also</span></span>

- [<span data-ttu-id="21290-140">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="21290-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="21290-141">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="21290-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="21290-142">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="21290-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="21290-143">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="21290-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
