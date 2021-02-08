---
description: 'Daha fazla bilgi edinin: <appDomainManagerType> öğesi'
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 633dcce2e370bda96efc61447611519d0ed04a3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787142"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="1507c-103">\<appDomainManagerType> Öğesi</span><span class="sxs-lookup"><span data-stu-id="1507c-103">\<appDomainManagerType> Element</span></span>

<span data-ttu-id="1507c-104">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1507c-104">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="1507c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1507c-105">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1507c-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1507c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1507c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1507c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1507c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1507c-108">Attributes</span></span>  
  
|<span data-ttu-id="1507c-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1507c-109">Attribute</span></span>|<span data-ttu-id="1507c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1507c-110">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="1507c-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1507c-111">Required attribute.</span></span> <span data-ttu-id="1507c-112">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi görevi gören ad alanı da dahil olmak üzere türün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1507c-112">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1507c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1507c-113">Child Elements</span></span>  

 <span data-ttu-id="1507c-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="1507c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1507c-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1507c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1507c-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="1507c-116">Element</span></span>|<span data-ttu-id="1507c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1507c-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1507c-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1507c-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1507c-119">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1507c-119">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1507c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1507c-120">Remarks</span></span>  

 <span data-ttu-id="1507c-121">Uygulama etki alanı yöneticisinin türünü belirtmek için, hem bu öğeyi hem de öğesini belirtmeniz gerekir [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) .</span><span class="sxs-lookup"><span data-stu-id="1507c-121">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="1507c-122">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="1507c-122">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="1507c-123">Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen tür öğesi tarafından belirtilen derlemede yoksa [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) ve işlem başlatılamazsa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1507c-123">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="1507c-124">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="1507c-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="1507c-125"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Yeni bir uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1507c-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="1507c-126">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1507c-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="1507c-127">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir oluşturulur <xref:System.TypeLoadException> .</span><span class="sxs-lookup"><span data-stu-id="1507c-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="1507c-128">Türünün ve ad alanının biçimi, özelliği için kullanılan biçim <xref:System.Type.FullName%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1507c-128">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="1507c-129">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1507c-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1507c-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="1507c-130">Example</span></span>  

 <span data-ttu-id="1507c-131">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` derlemedeki tür olduğunu gösterir `AdMgrExample` .</span><span class="sxs-lookup"><span data-stu-id="1507c-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1507c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1507c-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1507c-133">\<appDomainManagerAssembly> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="1507c-133">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="1507c-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="1507c-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1507c-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1507c-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1507c-136">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1507c-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
