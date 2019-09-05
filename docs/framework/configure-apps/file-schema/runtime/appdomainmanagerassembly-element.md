---
title: <appDomainManagerAssembly> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 083e3ba21dcd196eacfe3d9fd649c211da9dc125
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252845"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="1e972-102">\<appDomainManagerAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="1e972-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="1e972-103">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e972-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="1e972-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e972-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e972-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e972-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1e972-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly >**</span><span class="sxs-lookup"><span data-stu-id="1e972-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e972-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e972-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e972-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e972-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e972-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1e972-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e972-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e972-110">Attributes</span></span>  
  
|<span data-ttu-id="1e972-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1e972-111">Attribute</span></span>|<span data-ttu-id="1e972-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e972-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="1e972-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1e972-113">Required attribute.</span></span> <span data-ttu-id="1e972-114">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemenin görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e972-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e972-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e972-115">Child Elements</span></span>  
 <span data-ttu-id="1e972-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="1e972-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e972-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e972-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1e972-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e972-118">Element</span></span>|<span data-ttu-id="1e972-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e972-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1e972-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1e972-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1e972-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1e972-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e972-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e972-122">Remarks</span></span>  
 <span data-ttu-id="1e972-123">Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi [ \<hem de AppDomainManagerType >](appdomainmanagertype-element.md) öğesini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e972-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="1e972-124">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="1e972-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="1e972-125">Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen derleme yoksa veya derleme [ \<AppDomainManagerType >](appdomainmanagertype-element.md) öğesi ile belirtilen türü içermiyorsa ve işlem başarısız olursa başından.</span><span class="sxs-lookup"><span data-stu-id="1e972-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="1e972-126">Derleme bulunursa ancak sürüm bilgileri eşleşmiyorsa, bir <xref:System.IO.FileLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1e972-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="1e972-127">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="1e972-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="1e972-128">Yeni bir uygulama <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için veözelliklerinikullanın.<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1e972-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="1e972-129">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e972-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="1e972-130">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1e972-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="1e972-131">Derleme görünen adının biçimi için bkz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> . özelliği.</span><span class="sxs-lookup"><span data-stu-id="1e972-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="1e972-132">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e972-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e972-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e972-133">Example</span></span>  
 <span data-ttu-id="1e972-134">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` `AdMgrExample` derlemedeki tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e972-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e972-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e972-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1e972-136">\<appDomainManagerType > öğesi</span><span class="sxs-lookup"><span data-stu-id="1e972-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="1e972-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1e972-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1e972-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="1e972-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1e972-139">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e972-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
