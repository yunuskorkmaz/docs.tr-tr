---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: bae4aa39f9c43480ac2ef984f78834b68646742d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118238"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="b730c-102">\<appDomainManagerType > öğesi</span><span class="sxs-lookup"><span data-stu-id="b730c-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="b730c-103">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b730c-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="b730c-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b730c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b730c-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="b730c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b730c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType >**</span><span class="sxs-lookup"><span data-stu-id="b730c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b730c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b730c-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b730c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b730c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b730c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b730c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b730c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b730c-110">Attributes</span></span>  
  
|<span data-ttu-id="b730c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b730c-111">Attribute</span></span>|<span data-ttu-id="b730c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b730c-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="b730c-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b730c-113">Required attribute.</span></span> <span data-ttu-id="b730c-114">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi görevi gören ad alanı da dahil olmak üzere türün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b730c-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b730c-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b730c-115">Child Elements</span></span>  
 <span data-ttu-id="b730c-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="b730c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b730c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b730c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b730c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b730c-118">Element</span></span>|<span data-ttu-id="b730c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b730c-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b730c-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b730c-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b730c-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b730c-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b730c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b730c-122">Remarks</span></span>  
 <span data-ttu-id="b730c-123">Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi hem de [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) öğesini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b730c-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="b730c-124">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b730c-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="b730c-125">Varsayılan uygulama etki alanı yüklendiğinde <xref:System.TypeLoadException>, belirtilen tür [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) öğesi tarafından belirtilen derlemede yoksa oluşturulur. ve işlem başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b730c-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="b730c-126">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="b730c-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="b730c-127">Yeni bir uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek üzere <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b730c-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="b730c-128">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b730c-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="b730c-129">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b730c-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="b730c-130">Tür ve ad alanı biçimi <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği için kullanılan biçim.</span><span class="sxs-lookup"><span data-stu-id="b730c-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b730c-131">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b730c-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b730c-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="b730c-132">Example</span></span>  
 <span data-ttu-id="b730c-133">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `AdMgrExample` derlemesinde `MyMgr` türüdür.</span><span class="sxs-lookup"><span data-stu-id="b730c-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b730c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b730c-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b730c-135">\<appDomainManagerAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="b730c-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="b730c-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b730c-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b730c-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="b730c-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b730c-138">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b730c-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
