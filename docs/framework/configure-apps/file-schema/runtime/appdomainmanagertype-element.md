---
title: '&lt;appDomainManagerType&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e7f37fd652ce98e24d2e2e99edcd3d59a0e597b
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610439"
---
# <a name="ltappdomainmanagertypegt-element"></a><span data-ttu-id="1d12e-102">&lt;appDomainManagerType&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="1d12e-102">&lt;appDomainManagerType&gt; Element</span></span>
<span data-ttu-id="1d12e-103">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak görev yapan türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d12e-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="1d12e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1d12e-104">\<configuration></span></span>  
<span data-ttu-id="1d12e-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="1d12e-105">\<runtime></span></span>  
<span data-ttu-id="1d12e-106">\<appDomainManagerType ></span><span class="sxs-lookup"><span data-stu-id="1d12e-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d12e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d12e-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d12e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d12e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d12e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d12e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d12e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d12e-110">Attributes</span></span>  
  
|<span data-ttu-id="1d12e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d12e-111">Attribute</span></span>|<span data-ttu-id="1d12e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d12e-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="1d12e-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1d12e-113">Required attribute.</span></span> <span data-ttu-id="1d12e-114">İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak görev yapan ad alanı dahil türünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d12e-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d12e-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d12e-115">Child Elements</span></span>  
 <span data-ttu-id="1d12e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d12e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d12e-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d12e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1d12e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d12e-118">Element</span></span>|<span data-ttu-id="1d12e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d12e-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d12e-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1d12e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1d12e-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1d12e-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d12e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d12e-122">Remarks</span></span>  
 <span data-ttu-id="1d12e-123">Uygulama etki alanı yöneticisi türünü belirtmek için bu iki öğe belirtmeniz gerekir ve [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d12e-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="1d12e-124">Diğer, bu öğelerden herhangi birini belirtilmezse, yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="1d12e-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="1d12e-125">Varsayılan uygulama etki alanına yüklendiğinde <xref:System.TypeLoadException> belirtilen türü tarafından belirtilen derlemede mevcut değilse oluşturulur [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) öğesi; ve için işlem başarısız başlatın.</span><span class="sxs-lookup"><span data-stu-id="1d12e-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="1d12e-126">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türü belirttiğinizde, uygulama etki alanı yöneticisi türü oluşturulan varsayılan uygulama etki alanından diğer uygulama etki alanları devralır.</span><span class="sxs-lookup"><span data-stu-id="1d12e-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="1d12e-127">Kullanım <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> özellikler farklı uygulama etki alanı yöneticisi türü için yeni bir uygulama etki alanı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1d12e-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="1d12e-128">Uygulama etki alanı yöneticisi türünü belirtme, uygulama tam güven gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d12e-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="1d12e-129">(Örneğin, masaüstünde çalışan bir uygulama tam güven yok.) Uygulama tam güven yoksa bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d12e-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="1d12e-130">Tür ve ad alanı için kullanılan aynı biçimdir <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1d12e-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="1d12e-131">Bu yapılandırma öğesi yalnızca [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="1d12e-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d12e-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d12e-132">Example</span></span>  
 <span data-ttu-id="1d12e-133">Aşağıdaki örnek, uygulama etki alanı yöneticisi varsayılan uygulama etki alanı için bir işlem olduğunu belirtmek gösterilmektedir `MyMgr` yazın `AdMgrExample` derleme.</span><span class="sxs-lookup"><span data-stu-id="1d12e-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d12e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d12e-134">See Also</span></span>  
- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="1d12e-135">\<appDomainManagerAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="1d12e-135">\<appDomainManagerAssembly> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
- [<span data-ttu-id="1d12e-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1d12e-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="1d12e-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="1d12e-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="1d12e-138">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d12e-138">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
