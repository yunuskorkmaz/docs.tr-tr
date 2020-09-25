---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: daf576488e38bed28c7c0e5222bc053659372ff0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184007"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="f9919-102">\<relativeBindForResources> Öğesi</span><span class="sxs-lookup"><span data-stu-id="f9919-102">\<relativeBindForResources> Element</span></span>

<span data-ttu-id="f9919-103">Uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="f9919-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="f9919-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9919-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9919-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9919-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f9919-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9919-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9919-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9919-107">Attributes</span></span>  
  
|<span data-ttu-id="f9919-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9919-108">Attribute</span></span>|<span data-ttu-id="f9919-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9919-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f9919-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f9919-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f9919-111">Ortak dil çalışma zamanının uydu derlemeleri için araştırmayı iyileştirip iyileştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9919-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f9919-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9919-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="f9919-113">Değer</span><span class="sxs-lookup"><span data-stu-id="f9919-113">Value</span></span>|<span data-ttu-id="f9919-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9919-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f9919-115">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirmez.</span><span class="sxs-lookup"><span data-stu-id="f9919-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="f9919-116">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="f9919-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="f9919-117">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="f9919-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9919-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9919-118">Child Elements</span></span>  

 <span data-ttu-id="f9919-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9919-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9919-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9919-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f9919-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9919-121">Element</span></span>|<span data-ttu-id="f9919-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9919-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f9919-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f9919-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f9919-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f9919-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9919-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9919-125">Remarks</span></span>  

 <span data-ttu-id="f9919-126">Genel olarak, kaynakları [paketleme ve dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelendiği gibi, kaynakların araştırmalarını Kaynak Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="f9919-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="f9919-127">Yani, bir kaynağın belirli bir yerelleştirilmiş sürümü için Kaynak Yöneticisi araştırdığınızda, genel derleme önbelleğine bakabilir, uygulamanın kod tabanında kültüre özgü bir klasöre bakabilir, uydu Derlemeleriyle ilgili sorgu Windows Installer ve <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f9919-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="f9919-128">`<relativeBindForResources>`Öğesi, uydu derlemeleri için Kaynak Yöneticisi araştırma biçimini iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="f9919-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="f9919-129">Aşağıdaki koşullarda kaynakları yokladığınızda performansı iyileştirebilir:</span><span class="sxs-lookup"><span data-stu-id="f9919-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="f9919-130">Uydu derlemesi, kod derlemesiyle aynı konumda dağıtıldığında.</span><span class="sxs-lookup"><span data-stu-id="f9919-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="f9919-131">Diğer bir deyişle, kod derlemesi genel derleme önbelleğinde yüklüyse, uydu derlemelerinin de de yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9919-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="f9919-132">Kod derlemesi uygulamanın kod tabanında yüklüyse, uydu derlemelerinin de kod tabanında kültüre özgü bir klasöre yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9919-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="f9919-133">Windows Installer kullanılmazsa veya yalnızca, uydu derlemelerinin isteğe bağlı yüklemesi için nadiren kullanılırsa.</span><span class="sxs-lookup"><span data-stu-id="f9919-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="f9919-134">Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı işlemez.</span><span class="sxs-lookup"><span data-stu-id="f9919-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="f9919-135">Öğesinin, `enabled` `<relativeBindForResources>` `true` uydu derlemeleri için Kaynak Yöneticisi araştırmasını en iyi duruma getirmek için öğesi özniteliği aşağıdaki gibi ayarlanıyor:</span><span class="sxs-lookup"><span data-stu-id="f9919-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="f9919-136">Uydu derlemesini yoklamanız için üst kod derlemesinin konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f9919-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="f9919-137">Uydu derlemeleri için Windows Installer sorgulamaz.</span><span class="sxs-lookup"><span data-stu-id="f9919-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="f9919-138"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>Olayı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="f9919-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9919-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9919-139">See also</span></span>

- [<span data-ttu-id="f9919-140">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="f9919-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="f9919-141">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f9919-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f9919-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f9919-142">Configuration File Schema</span></span>](../index.md)
