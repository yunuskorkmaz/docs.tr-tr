---
title: <appDomainManagerAssembly> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 1716b11106775bed2c0d6ccb62e8d5b032b6e8be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176142"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="21dd5-102">\<appDomainManagerAssembly> Öğesi</span><span class="sxs-lookup"><span data-stu-id="21dd5-102">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="21dd5-103">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="21dd5-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="21dd5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="21dd5-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21dd5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21dd5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="21dd5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21dd5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21dd5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21dd5-107">Attributes</span></span>  
  
|<span data-ttu-id="21dd5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21dd5-108">Attribute</span></span>|<span data-ttu-id="21dd5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21dd5-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="21dd5-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="21dd5-110">Required attribute.</span></span> <span data-ttu-id="21dd5-111">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemenin görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21dd5-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21dd5-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21dd5-112">Child Elements</span></span>  

 <span data-ttu-id="21dd5-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="21dd5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21dd5-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21dd5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="21dd5-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="21dd5-115">Element</span></span>|<span data-ttu-id="21dd5-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21dd5-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="21dd5-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="21dd5-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="21dd5-118">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="21dd5-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21dd5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21dd5-119">Remarks</span></span>  

 <span data-ttu-id="21dd5-120">Uygulama etki alanı yöneticisinin türünü belirtmek için, hem bu öğeyi hem de öğesini belirtmeniz gerekir [\<appDomainManagerType>](appdomainmanagertype-element.md) .</span><span class="sxs-lookup"><span data-stu-id="21dd5-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="21dd5-121">Bu öğelerden biri belirtilmediyse, diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="21dd5-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="21dd5-122">Varsayılan uygulama etki alanı yüklendiğinde, <xref:System.TypeLoadException> belirtilen derleme yoksa veya derleme öğe tarafından belirtilen türü içermiyorsa [\<appDomainManagerType>](appdomainmanagertype-element.md) ve işlem başlatılamazsa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="21dd5-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="21dd5-123">Derleme bulunursa ancak sürüm bilgileri eşleşmiyorsa, bir oluşturulur <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="21dd5-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="21dd5-124">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi türünü belirttiğinizde, varsayılan uygulama etki alanından oluşturulan diğer uygulama etki alanları, uygulama etki alanı yöneticisi türünü alırlar.</span><span class="sxs-lookup"><span data-stu-id="21dd5-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="21dd5-125"><xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Yeni bir uygulama etki alanı için farklı bir uygulama etki alanı yöneticisi türü belirtmek için ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21dd5-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="21dd5-126">Uygulama etki alanı yöneticisi türü belirtildiğinde uygulamanın tam güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="21dd5-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="21dd5-127">(Örneğin, masaüstünde çalışan bir uygulamanın tam güveni vardır.) Uygulamanın tam güveni yoksa, bir oluşturulur <xref:System.TypeLoadException> .</span><span class="sxs-lookup"><span data-stu-id="21dd5-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="21dd5-128">Derleme görünen adının biçimi için bkz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> . özelliği.</span><span class="sxs-lookup"><span data-stu-id="21dd5-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="21dd5-129">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21dd5-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21dd5-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="21dd5-130">Example</span></span>  

 <span data-ttu-id="21dd5-131">Aşağıdaki örnek, bir işlemin varsayılan uygulama etki alanı için uygulama etki alanı yöneticisinin `MyMgr` derlemedeki tür olduğunu gösterir `AdMgrExample` .</span><span class="sxs-lookup"><span data-stu-id="21dd5-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21dd5-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21dd5-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="21dd5-133">\<appDomainManagerType> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="21dd5-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="21dd5-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="21dd5-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="21dd5-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="21dd5-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="21dd5-136">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21dd5-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
