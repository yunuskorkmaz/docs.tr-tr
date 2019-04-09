---
title: <appDomainManagerAssembly> Öğe
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe1dfbd62a6967ae51031fa12f80e9c5563dc44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182357"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="7eaec-102">\<appDomainManagerAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="7eaec-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="7eaec-103">Varsayılan uygulama etki alanı işlemde uygulama etki alanı yöneticisi sağlayan derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7eaec-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="7eaec-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7eaec-104">\<configuration></span></span>  
<span data-ttu-id="7eaec-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="7eaec-105">\<runtime></span></span>  
<span data-ttu-id="7eaec-106">\<appDomainManagerAssembly ></span><span class="sxs-lookup"><span data-stu-id="7eaec-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eaec-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7eaec-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eaec-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7eaec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7eaec-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7eaec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eaec-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7eaec-110">Attributes</span></span>  
  
|<span data-ttu-id="7eaec-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7eaec-111">Attribute</span></span>|<span data-ttu-id="7eaec-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7eaec-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="7eaec-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7eaec-113">Required attribute.</span></span> <span data-ttu-id="7eaec-114">İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlayan derlemenin görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7eaec-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eaec-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7eaec-115">Child Elements</span></span>  
 <span data-ttu-id="7eaec-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="7eaec-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7eaec-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7eaec-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7eaec-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="7eaec-118">Element</span></span>|<span data-ttu-id="7eaec-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7eaec-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7eaec-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7eaec-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7eaec-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7eaec-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eaec-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7eaec-122">Remarks</span></span>  
 <span data-ttu-id="7eaec-123">Uygulama etki alanı yöneticisi türünü belirtmek için bu iki öğe belirtmeniz gerekir ve [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="7eaec-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="7eaec-124">Diğer, bu öğelerden herhangi birini belirtilmezse, yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7eaec-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="7eaec-125">Varsayılan uygulama etki alanına yüklendiğinde <xref:System.TypeLoadException> belirtilen bütünleştirilmiş kodu yok veya derleme tarafından belirtilen türü içermiyor durum [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi; ve işlem başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7eaec-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="7eaec-126">Derleme bulundu, ancak sürüm bilgisi eşleşmiyor, bir <xref:System.IO.FileLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7eaec-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="7eaec-127">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türü belirttiğinizde, uygulama etki alanı yöneticisi türü oluşturulan varsayılan uygulama etki alanından diğer uygulama etki alanları devralır.</span><span class="sxs-lookup"><span data-stu-id="7eaec-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="7eaec-128">Kullanım <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> özellikler farklı uygulama etki alanı yöneticisi türü için yeni bir uygulama etki alanı belirtin.</span><span class="sxs-lookup"><span data-stu-id="7eaec-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="7eaec-129">Uygulama etki alanı yöneticisi türünü belirtme, uygulama tam güven gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7eaec-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="7eaec-130">(Örneğin, masaüstünde çalışan bir uygulama tam güven yok.) Uygulama tam güven yoksa bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7eaec-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="7eaec-131">Derlemenin görünen adı biçimi için bkz. <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7eaec-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="7eaec-132">Bu yapılandırma öğesi yalnızca [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="7eaec-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eaec-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="7eaec-133">Example</span></span>  
 <span data-ttu-id="7eaec-134">Aşağıdaki örnek, uygulama etki alanı yöneticisi varsayılan uygulama etki alanı için bir işlem olduğunu belirtmek gösterilmektedir `MyMgr` yazın `AdMgrExample` derleme.</span><span class="sxs-lookup"><span data-stu-id="7eaec-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7eaec-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7eaec-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7eaec-136">\<appDomainManagerType > öğesi</span><span class="sxs-lookup"><span data-stu-id="7eaec-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [<span data-ttu-id="7eaec-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7eaec-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="7eaec-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="7eaec-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="7eaec-139">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7eaec-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
