---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b535ba67ab05dabd7e0a23e79692bbf69e25b55
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663916"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="530d3-102">\<appDomainManagerType > öğesi</span><span class="sxs-lookup"><span data-stu-id="530d3-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="530d3-103">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="530d3-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="530d3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="530d3-104">\<configuration></span></span>  
<span data-ttu-id="530d3-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="530d3-105">\<runtime></span></span>  
<span data-ttu-id="530d3-106">\<appDomainManagerType ></span><span class="sxs-lookup"><span data-stu-id="530d3-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="530d3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="530d3-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="530d3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="530d3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="530d3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="530d3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="530d3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="530d3-110">Attributes</span></span>  
  
|<span data-ttu-id="530d3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="530d3-111">Attribute</span></span>|<span data-ttu-id="530d3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="530d3-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="530d3-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="530d3-113">Required attribute.</span></span> <span data-ttu-id="530d3-114">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi görevi gören ad alanı da dahil olmak üzere türün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="530d3-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="530d3-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="530d3-115">Child Elements</span></span>  
 <span data-ttu-id="530d3-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="530d3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="530d3-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="530d3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="530d3-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="530d3-118">Element</span></span>|<span data-ttu-id="530d3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="530d3-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="530d3-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="530d3-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="530d3-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="530d3-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="530d3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="530d3-122">Remarks</span></span>  
 <span data-ttu-id="530d3-123">Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi [ \<hem de AppDomainManagerAssembly >](appdomainmanagerassembly-element.md) öğesini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="530d3-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="530d3-124">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="530d3-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="530d3-125">Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen tür [ \<AppDomainManagerAssembly >](appdomainmanagerassembly-element.md) öğesi tarafından belirtilen derlemede yoksa ve işlem başlatılamazsa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="530d3-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="530d3-126">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="530d3-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="530d3-127">Yeni bir uygulama <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için veözelliklerinikullanın.<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="530d3-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="530d3-128">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="530d3-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="530d3-129">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="530d3-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="530d3-130">Türünün ve ad alanının biçimi, <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği için kullanılan biçim.</span><span class="sxs-lookup"><span data-stu-id="530d3-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="530d3-131">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="530d3-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="530d3-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="530d3-132">Example</span></span>  
 <span data-ttu-id="530d3-133">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` `AdMgrExample` derlemedeki tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="530d3-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="530d3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="530d3-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="530d3-135">\<appDomainManagerAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="530d3-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="530d3-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="530d3-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="530d3-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="530d3-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="530d3-138">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="530d3-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
