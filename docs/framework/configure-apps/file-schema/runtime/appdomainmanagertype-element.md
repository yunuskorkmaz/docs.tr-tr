---
title: '&lt;appDomainManagerType&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fb771d58a99e42ad53a465008e8848cff0a87fd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltappdomainmanagertypegt-element"></a><span data-ttu-id="cb18f-102">&lt;appDomainManagerType&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="cb18f-102">&lt;appDomainManagerType&gt; Element</span></span>
<span data-ttu-id="cb18f-103">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak görev yapar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="cb18f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="cb18f-104">\<configuration></span></span>  
<span data-ttu-id="cb18f-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="cb18f-105">\<runtime></span></span>  
<span data-ttu-id="cb18f-106">\<appDomainManagerType ></span><span class="sxs-lookup"><span data-stu-id="cb18f-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb18f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb18f-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb18f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb18f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cb18f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb18f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb18f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb18f-110">Attributes</span></span>  
  
|<span data-ttu-id="cb18f-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb18f-111">Attribute</span></span>|<span data-ttu-id="cb18f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb18f-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="cb18f-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb18f-113">Required attribute.</span></span> <span data-ttu-id="cb18f-114">İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren ad alanı dahil türünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb18f-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb18f-115">Child Elements</span></span>  
 <span data-ttu-id="cb18f-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb18f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb18f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb18f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cb18f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb18f-118">Element</span></span>|<span data-ttu-id="cb18f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb18f-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cb18f-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cb18f-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cb18f-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb18f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb18f-122">Remarks</span></span>  
 <span data-ttu-id="cb18f-123">Uygulama etki alanı yöneticisi türünü belirtmek için bu iki öğe belirtin ve [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb18f-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="cb18f-124">Bu öğelerden birini belirtilmedi, diğer göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="cb18f-125">Varsayılan uygulama etki alanı yüklendiğinde <xref:System.TypeLoadException> tarafından belirtilen derleme belirtilen türü yoksa, durum [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) öğesi; ve işlem başarısız başlatın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="cb18f-126">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları uygulama etki alanı yöneticisi türü devralır.</span><span class="sxs-lookup"><span data-stu-id="cb18f-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="cb18f-127">Kullanım <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> ve <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> yeni bir uygulama etki alanı için farklı uygulama etki alanı yöneticisi türünü belirtmek için özellikler.</span><span class="sxs-lookup"><span data-stu-id="cb18f-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="cb18f-128">Uygulama etki alanı yöneticisi türünü belirtme, uygulama tam güven gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="cb18f-129">(Örneğin, tam güven masaüstünde çalışan bir uygulama vardır.) Uygulama tam güven, yoksa bir <xref:System.TypeLoadException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cb18f-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="cb18f-130">Tür ve ad alanı için kullanılan aynı biçimdir <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cb18f-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="cb18f-131">Bu yapılandırma öğesi yalnızca kullanılabilir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="cb18f-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb18f-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb18f-132">Example</span></span>  
 <span data-ttu-id="cb18f-133">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olduğunu belirtmek gösterilmiştir `MyMgr` yazın `AdMgrExample` derleme.</span><span class="sxs-lookup"><span data-stu-id="cb18f-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb18f-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb18f-134">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="cb18f-135">\<appDomainManagerAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb18f-135">\<appDomainManagerAssembly> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
 [<span data-ttu-id="cb18f-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cb18f-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="cb18f-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="cb18f-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="cb18f-138">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb18f-138">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
