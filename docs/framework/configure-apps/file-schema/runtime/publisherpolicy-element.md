---
title: "&lt;publisherPolicy&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5f629dd347f63c8fb8e624c475bfb0ecf658f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="c2c41-102">&lt;publisherPolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="c2c41-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="c2c41-103">Çalışma zamanı Yayımcı ilkesi geçerli olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2c41-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="c2c41-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c2c41-104">\<configuration></span></span>  
<span data-ttu-id="c2c41-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="c2c41-105">\<runtime></span></span>  
<span data-ttu-id="c2c41-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="c2c41-106">\<assemblyBinding></span></span>  
<span data-ttu-id="c2c41-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="c2c41-107">\<dependentAssembly></span></span>  
<span data-ttu-id="c2c41-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="c2c41-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c41-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2c41-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2c41-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2c41-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c2c41-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2c41-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2c41-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2c41-112">Attributes</span></span>  
  
|<span data-ttu-id="c2c41-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c2c41-113">Attribute</span></span>|<span data-ttu-id="c2c41-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2c41-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="c2c41-115">Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2c41-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="c2c41-116">Özniteliğini uygulayın</span><span class="sxs-lookup"><span data-stu-id="c2c41-116">apply Attribute</span></span>  
  
|<span data-ttu-id="c2c41-117">Değer</span><span class="sxs-lookup"><span data-stu-id="c2c41-117">Value</span></span>|<span data-ttu-id="c2c41-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2c41-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="c2c41-119">Yayımcı ilkesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c2c41-119">Applies publisher policy.</span></span> <span data-ttu-id="c2c41-120">Varsayılan ayar budur.</span><span class="sxs-lookup"><span data-stu-id="c2c41-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="c2c41-121">Yayımcı ilkesi uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="c2c41-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2c41-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2c41-122">Child Elements</span></span>  
 <span data-ttu-id="c2c41-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c2c41-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2c41-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2c41-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c2c41-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c2c41-125">Element</span></span>|<span data-ttu-id="c2c41-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2c41-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c2c41-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c2c41-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c2c41-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c2c41-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2c41-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2c41-129">Remarks</span></span>  
 <span data-ttu-id="c2c41-130">Bir bileşen satıcısı bütünleştirilmiş yeni bir sürümü yayımlandığında, yeni sürümü şimdi eski sürümünü kullanan uygulamaları kullanmak için satıcı Yayımcı ilkesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c2c41-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="c2c41-131">Yayımcı ilkesi için belirli bir derleme uygulanıp uygulanmayacağını belirtin, put  **\<publisherPolicy >** öğesinde  **\<dependentAssembly >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="c2c41-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="c2c41-132">İçin varsayılan ayar **uygulamak** özniteliği **Evet**.</span><span class="sxs-lookup"><span data-stu-id="c2c41-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="c2c41-133">Ayarı **uygulamak** özniteliğini **hiçbir** geçersiz kılmaları herhangi önceki **Evet** derleme için ayarları.</span><span class="sxs-lookup"><span data-stu-id="c2c41-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="c2c41-134">Bir uygulama ilkesi publisher'ı kullanarak açıkça yoksaymak izni gereklidir [ \<publisherPolicy uygulamak = "Hayır" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="c2c41-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="c2c41-135">Ayarlayarak iznine sahip <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="c2c41-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="c2c41-136">Daha fazla bilgi için bkz: [derleme bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="c2c41-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c41-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2c41-137">Example</span></span>  
 <span data-ttu-id="c2c41-138">Aşağıdaki örnek derleme için yayımcı ilkesi devre dışı bırakır `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="c2c41-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2c41-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2c41-139">See Also</span></span>  
 [<span data-ttu-id="c2c41-140">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c2c41-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c2c41-141">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c2c41-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c2c41-142">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c2c41-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="c2c41-143">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c2c41-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
