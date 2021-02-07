---
description: 'Daha fazla bilgi edinin: <appDomainManagerAssembly> öğesi'
title: <appDomainManagerAssembly> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: fcd461a8c8727679df3974028ddbc4b689c73e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719311"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="d1fa9-103">\<appDomainManagerAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="d1fa9-103">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="d1fa9-104">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-104">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="d1fa9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1fa9-105">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1fa9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1fa9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d1fa9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1fa9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1fa9-108">Attributes</span></span>  
  
|<span data-ttu-id="d1fa9-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d1fa9-109">Attribute</span></span>|<span data-ttu-id="d1fa9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1fa9-110">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="d1fa9-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-111">Required attribute.</span></span> <span data-ttu-id="d1fa9-112">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemenin görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-112">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1fa9-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1fa9-113">Child Elements</span></span>  

 <span data-ttu-id="d1fa9-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1fa9-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1fa9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d1fa9-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1fa9-116">Element</span></span>|<span data-ttu-id="d1fa9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1fa9-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1fa9-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d1fa9-119">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-119">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1fa9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1fa9-120">Remarks</span></span>  

 <span data-ttu-id="d1fa9-121">Uygulama etki alanı yöneticisinin türünü belirtmek için, hem bu öğeyi hem de öğesini belirtmeniz gerekir [\<appDomainManagerType>](appdomainmanagertype-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d1fa9-121">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="d1fa9-122">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-122">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="d1fa9-123">Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen derleme yoksa veya derleme öğe tarafından belirtilen türü içermiyorsa [\<appDomainManagerType>](appdomainmanagertype-element.md) ve işlem başlatılamazsa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-123">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="d1fa9-124">Derleme bulunursa ancak sürüm bilgileri eşleşmiyorsa, bir oluşturulur <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="d1fa9-124">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="d1fa9-125">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-125">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="d1fa9-126"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Yeni bir uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-126">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="d1fa9-127">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-127">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="d1fa9-128">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir oluşturulur <xref:System.TypeLoadException> .</span><span class="sxs-lookup"><span data-stu-id="d1fa9-128">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="d1fa9-129">Derleme görünen adının biçimi için bkz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> . özelliği.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-129">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="d1fa9-130">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-130">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1fa9-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1fa9-131">Example</span></span>  

 <span data-ttu-id="d1fa9-132">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` derlemedeki tür olduğunu gösterir `AdMgrExample` .</span><span class="sxs-lookup"><span data-stu-id="d1fa9-132">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1fa9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1fa9-133">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d1fa9-134">\<appDomainManagerType> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d1fa9-134">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="d1fa9-135">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="d1fa9-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d1fa9-136">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d1fa9-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d1fa9-137">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1fa9-137">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
