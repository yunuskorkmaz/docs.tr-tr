---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154438"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="6f813-102">\<appDomainManagerType> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6f813-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="6f813-103">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f813-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="6f813-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f813-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f813-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f813-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6f813-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span><span class="sxs-lookup"><span data-stu-id="6f813-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f813-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f813-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f813-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f813-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6f813-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f813-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f813-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f813-110">Attributes</span></span>  
  
|<span data-ttu-id="6f813-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f813-111">Attribute</span></span>|<span data-ttu-id="6f813-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f813-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="6f813-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6f813-113">Required attribute.</span></span> <span data-ttu-id="6f813-114">İşlemdeki varsayılan uygulama etki alanıiçin uygulama etki alanı yöneticisi olarak hizmet veren ad alanı da dahil olmak üzere, türün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f813-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f813-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f813-115">Child Elements</span></span>  
 <span data-ttu-id="6f813-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f813-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f813-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f813-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6f813-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f813-118">Element</span></span>|<span data-ttu-id="6f813-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f813-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6f813-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6f813-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6f813-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6f813-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f813-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f813-122">Remarks</span></span>  
 <span data-ttu-id="6f813-123">Uygulama etki alanı yöneticisinin türünü belirtmek için hem bu öğeyi hem de [ \<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) öğesini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f813-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="6f813-124">Bu öğelerden biri belirtilmemişse, diğer insalar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="6f813-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="6f813-125">Varsayılan uygulama etki alanı <xref:System.TypeLoadException> yüklendiğinde, [ \<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) öğesi tarafından belirtilen derlemede belirtilen tür yoksa atılır; ve işlem başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="6f813-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="6f813-126">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğiniz zaman, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları uygulama etki alanı yöneticisi türünü devralır.</span><span class="sxs-lookup"><span data-stu-id="6f813-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="6f813-127"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> Yeni bir <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f813-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="6f813-128">Uygulama etki alanı yöneticisi türünü belirtmek, uygulamanın tam güvene sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f813-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="6f813-129">(Örneğin, masaüstünde çalışan bir uygulama tam güvene sahiptir.) Uygulama tam güvene sahip değilse, bir <xref:System.TypeLoadException> atılır.</span><span class="sxs-lookup"><span data-stu-id="6f813-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="6f813-130">Tür ve ad alanı biçimi, özellik için kullanılan <xref:System.Type.FullName%2A?displayProperty=nameWithType> biçimle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6f813-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="6f813-131">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve sonraki yerlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f813-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f813-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f813-132">Example</span></span>  
 <span data-ttu-id="6f813-133">Aşağıdaki örnekte, bir işlemin varsayılan uygulama etki alanı için uygulama `MyMgr` etki alanı `AdMgrExample` yöneticisinin derlemedeki tür olduğunu nasıl belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6f813-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f813-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f813-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6f813-135">\<appDomainManagerAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6f813-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="6f813-136">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6f813-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6f813-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="6f813-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f813-138">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f813-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
