---
title: <appDomainManagerType> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154438"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="5d213-102">\<appDomainManagerType> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5d213-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="5d213-103">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d213-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="5d213-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d213-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d213-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d213-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5d213-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d213-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d213-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d213-107">Attributes</span></span>  
  
|<span data-ttu-id="5d213-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5d213-108">Attribute</span></span>|<span data-ttu-id="5d213-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d213-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="5d213-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5d213-110">Required attribute.</span></span> <span data-ttu-id="5d213-111">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi görevi gören ad alanı da dahil olmak üzere türün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d213-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d213-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d213-112">Child Elements</span></span>  
 <span data-ttu-id="5d213-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d213-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d213-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d213-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5d213-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d213-115">Element</span></span>|<span data-ttu-id="5d213-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d213-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5d213-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5d213-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5d213-118">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5d213-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d213-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d213-119">Remarks</span></span>  
 <span data-ttu-id="5d213-120">Uygulama etki alanı yöneticisinin türünü belirtmek için, hem bu öğeyi hem de öğesini belirtmeniz gerekir [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5d213-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="5d213-121">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5d213-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="5d213-122">Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen tür öğesi tarafından belirtilen derlemede yoksa [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) ve işlem başlatılamazsa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d213-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="5d213-123">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="5d213-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="5d213-124"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Yeni bir uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d213-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="5d213-125">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d213-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="5d213-126">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir oluşturulur <xref:System.TypeLoadException> .</span><span class="sxs-lookup"><span data-stu-id="5d213-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5d213-127">Türünün ve ad alanının biçimi, özelliği için kullanılan biçim <xref:System.Type.FullName%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5d213-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5d213-128">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d213-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d213-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d213-129">Example</span></span>  
 <span data-ttu-id="5d213-130">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` derlemedeki tür olduğunu gösterir `AdMgrExample` .</span><span class="sxs-lookup"><span data-stu-id="5d213-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d213-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d213-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d213-132">\<appDomainManagerAssembly>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5d213-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="5d213-133">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="5d213-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d213-134">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5d213-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5d213-135">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d213-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
