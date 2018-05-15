---
title: '&lt;appDomainManagerAssembly&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7656f4819e8ed6d8c1c87eabcbd5862929d47cdc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltappdomainmanagerassemblygt-element"></a><span data-ttu-id="5f43b-102">&lt;appDomainManagerAssembly&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="5f43b-102">&lt;appDomainManagerAssembly&gt; Element</span></span>
<span data-ttu-id="5f43b-103">İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlar derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f43b-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="5f43b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5f43b-104">\<configuration></span></span>  
<span data-ttu-id="5f43b-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="5f43b-105">\<runtime></span></span>  
<span data-ttu-id="5f43b-106">\<appDomainManagerAssembly ></span><span class="sxs-lookup"><span data-stu-id="5f43b-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f43b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f43b-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f43b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f43b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5f43b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f43b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f43b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f43b-110">Attributes</span></span>  
  
|<span data-ttu-id="5f43b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5f43b-111">Attribute</span></span>|<span data-ttu-id="5f43b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f43b-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="5f43b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5f43b-113">Required attribute.</span></span> <span data-ttu-id="5f43b-114">İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlar derleme görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f43b-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f43b-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f43b-115">Child Elements</span></span>  
 <span data-ttu-id="5f43b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f43b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f43b-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f43b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5f43b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f43b-118">Element</span></span>|<span data-ttu-id="5f43b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f43b-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5f43b-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5f43b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5f43b-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5f43b-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f43b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f43b-122">Remarks</span></span>  
 <span data-ttu-id="5f43b-123">Uygulama etki alanı yöneticisi türünü belirtmek için bu iki öğe belirtin ve [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5f43b-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="5f43b-124">Bu öğelerden birini belirtilmedi, diğer göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="5f43b-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="5f43b-125">Varsayılan uygulama etki alanı yüklendiğinde <xref:System.TypeLoadException> belirtilen derleme mevcut değilse veya derleme tarafından belirtilen tür içermiyorsa durum [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) öğesi; ve işlem başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5f43b-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="5f43b-126">Derleme bulundu, ancak sürüm bilgilerini eşleşmiyor, bir <xref:System.IO.FileLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f43b-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5f43b-127">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları uygulama etki alanı yöneticisi türü devralır.</span><span class="sxs-lookup"><span data-stu-id="5f43b-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="5f43b-128">Kullanım <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> yeni bir uygulama etki alanı için farklı uygulama etki alanı yöneticisi türünü belirtmek için özellikler.</span><span class="sxs-lookup"><span data-stu-id="5f43b-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="5f43b-129">Uygulama etki alanı yöneticisi türünü belirtme, uygulama tam güven gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f43b-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="5f43b-130">(Örneğin, tam güven masaüstünde çalışan bir uygulama vardır.) Uygulama tam güven, yoksa bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f43b-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5f43b-131">Derleme görünen adı biçimi için bkz: <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f43b-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5f43b-132">Bu yapılandırma öğesi yalnızca kullanılabilir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="5f43b-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f43b-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f43b-133">Example</span></span>  
 <span data-ttu-id="5f43b-134">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olduğunu belirtmek gösterilmiştir `MyMgr` yazın `AdMgrExample` derleme.</span><span class="sxs-lookup"><span data-stu-id="5f43b-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f43b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f43b-135">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5f43b-136">\<appDomainManagerType > öğesi</span><span class="sxs-lookup"><span data-stu-id="5f43b-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [<span data-ttu-id="5f43b-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5f43b-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5f43b-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5f43b-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5f43b-139">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f43b-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
