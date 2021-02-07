---
description: 'İçin: öğesi hakkında daha fazla bilgi <assemblyBinding><runtime>'
title: <runtime> için <assemblyBinding> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: a797b541f9f13852234872f1eb2fc68a2eac727d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719233"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="590f9-103">\<runtime> için \<assemblyBinding> Öğesi</span><span class="sxs-lookup"><span data-stu-id="590f9-103">\<assemblyBinding> Element for \<runtime></span></span>

<span data-ttu-id="590f9-104">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="590f9-104">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="590f9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="590f9-105">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="590f9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="590f9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="590f9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="590f9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="590f9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="590f9-108">Attributes</span></span>  
  
|<span data-ttu-id="590f9-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="590f9-109">Attribute</span></span>|<span data-ttu-id="590f9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="590f9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="590f9-111">**özniteliði**</span><span class="sxs-lookup"><span data-stu-id="590f9-111">**xmlns**</span></span>|<span data-ttu-id="590f9-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="590f9-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="590f9-113">Derleme bağlaması için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="590f9-113">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="590f9-114">Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="590f9-114">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="590f9-115">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="590f9-115">**appliesTo**</span></span>|<span data-ttu-id="590f9-116">.NET Framework derleme yeniden yönlendirmenin uygulandığı çalışma zamanı sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="590f9-116">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="590f9-117">Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="590f9-117">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="590f9-118">Hiçbir **AppliesTo** özniteliği belirtilmemişse, **\<assemblyBinding>** öğesi .NET Framework tüm sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="590f9-118">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="590f9-119">**AppliesTo** özniteliği .NET Framework sürüm 1,1 ' de tanıtılmıştı; .NET Framework 1,0 sürümü tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="590f9-119">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="590f9-120">Bu, **\<assemblyBinding>** bir **AppliesTo** özniteliği belirtilmiş olsa bile, .NET Framework sürüm 1,0 kullanılırken tüm öğelerin uygulandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="590f9-120">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="590f9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="590f9-121">Child Elements</span></span>  
  
|<span data-ttu-id="590f9-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="590f9-122">Element</span></span>|<span data-ttu-id="590f9-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="590f9-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="590f9-124">Derleme için bağlama ilkesini ve derleme konumunu kapsüller.</span><span class="sxs-lookup"><span data-stu-id="590f9-124">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="590f9-125">**\<dependentAssembly>** Her derleme için bir etiket kullanın.</span><span class="sxs-lookup"><span data-stu-id="590f9-125">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="590f9-126">Derlemeler yüklenirken ortak dil çalışma zamanı aramalarının alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="590f9-126">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="590f9-127">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="590f9-127">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="590f9-128">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="590f9-128">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="590f9-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="590f9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="590f9-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="590f9-130">Element</span></span>|<span data-ttu-id="590f9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="590f9-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="590f9-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="590f9-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="590f9-133">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="590f9-133">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="590f9-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="590f9-134">Example</span></span>  

 <span data-ttu-id="590f9-135">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceğini ve bir kod temeli nasıl sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="590f9-135">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="590f9-136">Aşağıdaki örnek, bir .NET Framework derlemesinin bağlamasını yeniden yönlendirmek için **AppliesTo** özniteliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="590f9-136">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="590f9-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="590f9-137">See also</span></span>

- [<span data-ttu-id="590f9-138">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="590f9-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="590f9-139">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="590f9-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="590f9-140">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="590f9-140">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
