---
title: '&lt;publisherPolicy&gt; öğesi'
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
ms.openlocfilehash: 4c81b403fa4d633428946d36960d5df32df76d21
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613784"
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="08b8b-102">&lt;publisherPolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="08b8b-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="08b8b-103">Çalışma zamanı Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08b8b-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="08b8b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="08b8b-104">\<configuration></span></span>  
<span data-ttu-id="08b8b-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="08b8b-105">\<runtime></span></span>  
<span data-ttu-id="08b8b-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="08b8b-106">\<assemblyBinding></span></span>  
<span data-ttu-id="08b8b-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="08b8b-107">\<dependentAssembly></span></span>  
<span data-ttu-id="08b8b-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="08b8b-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b8b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08b8b-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08b8b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="08b8b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="08b8b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08b8b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08b8b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08b8b-112">Attributes</span></span>  
  
|<span data-ttu-id="08b8b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="08b8b-113">Attribute</span></span>|<span data-ttu-id="08b8b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08b8b-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="08b8b-115">Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08b8b-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="08b8b-116">bir öznitelik uygulama</span><span class="sxs-lookup"><span data-stu-id="08b8b-116">apply Attribute</span></span>  
  
|<span data-ttu-id="08b8b-117">Değer</span><span class="sxs-lookup"><span data-stu-id="08b8b-117">Value</span></span>|<span data-ttu-id="08b8b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08b8b-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="08b8b-119">Yayımcı ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="08b8b-119">Applies publisher policy.</span></span> <span data-ttu-id="08b8b-120">Varsayılan ayar budur.</span><span class="sxs-lookup"><span data-stu-id="08b8b-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="08b8b-121">Yayımcı ilkesi uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="08b8b-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08b8b-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="08b8b-122">Child Elements</span></span>  
 <span data-ttu-id="08b8b-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="08b8b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08b8b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="08b8b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="08b8b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="08b8b-125">Element</span></span>|<span data-ttu-id="08b8b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08b8b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="08b8b-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="08b8b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="08b8b-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="08b8b-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08b8b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08b8b-129">Remarks</span></span>  
 <span data-ttu-id="08b8b-130">Bir bileşen Satıcı bir derlemenin yeni bir sürümü yayımlandığında yeni sürümü artık eski sürümü kullanan uygulamaları kullanmak için satıcı Yayımcı ilkesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="08b8b-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="08b8b-131">Belirli bir derleme için yayımcı ilkesi uygulanıp uygulanmayacağını belirtmek için put  **\<publisherPolicy >** öğesinde  **\<dependentAssembly >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="08b8b-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="08b8b-132">Varsayılan ayarı **uygulamak** özniteliği **Evet**.</span><span class="sxs-lookup"><span data-stu-id="08b8b-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="08b8b-133">Ayarlama **uygulamak** özniteliğini **hiçbir** önceki tüm geçersiz kılmaları **Evet** bir derleme için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08b8b-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="08b8b-134">Yayımcı ilkesi kullanarak açıkça yoksaymak bir uygulama için gerekli izni [ \<publisherPolicy uygulama = "Hayır" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) öğesi uygulama yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="08b8b-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="08b8b-135">İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="08b8b-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="08b8b-136">Daha fazla bilgi için [bütünleştirilmiş kod bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="08b8b-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08b8b-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="08b8b-137">Example</span></span>  
 <span data-ttu-id="08b8b-138">Aşağıdaki örnek derleme için yayımcı ilkesini devre dışı bırakır `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="08b8b-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08b8b-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08b8b-139">See Also</span></span>  
- [<span data-ttu-id="08b8b-140">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="08b8b-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="08b8b-141">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="08b8b-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="08b8b-142">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="08b8b-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="08b8b-143">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="08b8b-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
