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
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115841"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="ebb3b-102">\<publisherPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ebb3b-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="ebb3b-103">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="ebb3b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebb3b-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebb3b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ebb3b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ebb3b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebb3b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ebb3b-107">Attributes</span></span>  
  
|<span data-ttu-id="ebb3b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ebb3b-108">Attribute</span></span>|<span data-ttu-id="ebb3b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebb3b-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="ebb3b-110">Yayımcı ilkesinin uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="ebb3b-111">Özniteliği Uygula</span><span class="sxs-lookup"><span data-stu-id="ebb3b-111">apply Attribute</span></span>  
  
|<span data-ttu-id="ebb3b-112">Değer</span><span class="sxs-lookup"><span data-stu-id="ebb3b-112">Value</span></span>|<span data-ttu-id="ebb3b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebb3b-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="ebb3b-114">Yayımcı ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-114">Applies publisher policy.</span></span> <span data-ttu-id="ebb3b-115">Bu varsayılan ayardır.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="ebb3b-116">Yayımcı ilkesi uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebb3b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ebb3b-117">Child Elements</span></span>  

<span data-ttu-id="ebb3b-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebb3b-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ebb3b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ebb3b-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="ebb3b-120">Element</span></span>|<span data-ttu-id="ebb3b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebb3b-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ebb3b-122">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ebb3b-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="ebb3b-124">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="ebb3b-125">`<dependentAssembly>`Her derleme için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="ebb3b-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebb3b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebb3b-127">Remarks</span></span>  
 <span data-ttu-id="ebb3b-128">Bir bileşen satıcısı bir derlemenin yeni bir sürümünü yayımlarsa, satıcı bir yayımcı ilkesi içerebilir, bu nedenle eski sürümü kullanan uygulamalar artık yeni sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="ebb3b-129">Belirli bir derleme için yayımcı ilkesinin uygulanıp uygulanmayacağını belirtmek için öğesini öğesine koyun **\<publisherPolicy>** **\<dependentAssembly>** .</span><span class="sxs-lookup"><span data-stu-id="ebb3b-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="ebb3b-130">**Apply** özniteliği için varsayılan ayar **Evet**' tir.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="ebb3b-131">**Apply** özniteliğini **Hayır** olarak ayarlamak, bir derleme için önceki tüm **Evet** ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="ebb3b-132">Uygulamanın, [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) uygulama yapılandırma dosyasındaki öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="ebb3b-133"><xref:System.Security.Permissions.SecurityPermissionFlag>' De bayrak ayarlanarak izin verilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="ebb3b-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="ebb3b-134">Daha fazla bilgi için bkz. [derleme bağlama yeniden yönlendirme güvenlik izni](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="ebb3b-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebb3b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebb3b-135">Example</span></span>  
 <span data-ttu-id="ebb3b-136">Aşağıdaki örnek, derleme için yayımcı ilkesini devre dışı bırakır `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="ebb3b-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebb3b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebb3b-137">See also</span></span>

- [<span data-ttu-id="ebb3b-138">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="ebb3b-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ebb3b-139">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ebb3b-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ebb3b-140">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="ebb3b-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ebb3b-141">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="ebb3b-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
