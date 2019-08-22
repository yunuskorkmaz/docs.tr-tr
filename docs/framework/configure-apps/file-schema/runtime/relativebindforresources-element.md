---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 859e8a12421ea92aa48c54317e052683eb8e83f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663492"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="2cd61-102">\<relativeBindForResources > öğesi</span><span class="sxs-lookup"><span data-stu-id="2cd61-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="2cd61-103">Uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="2cd61-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="2cd61-104">\<configuration> Element</span></span>  
<span data-ttu-id="2cd61-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="2cd61-105">\<runtime> Element</span></span>  
<span data-ttu-id="2cd61-106">\<relativeBindForResources > öğesi</span><span class="sxs-lookup"><span data-stu-id="2cd61-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd61-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cd61-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cd61-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cd61-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2cd61-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2cd61-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cd61-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2cd61-110">Attributes</span></span>  
  
|<span data-ttu-id="2cd61-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2cd61-111">Attribute</span></span>|<span data-ttu-id="2cd61-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cd61-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2cd61-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cd61-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2cd61-114">Ortak dil çalışma zamanının uydu derlemeleri için araştırmayı iyileştirip iyileştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2cd61-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2cd61-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2cd61-116">Değer</span><span class="sxs-lookup"><span data-stu-id="2cd61-116">Value</span></span>|<span data-ttu-id="2cd61-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cd61-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2cd61-118">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirmez.</span><span class="sxs-lookup"><span data-stu-id="2cd61-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="2cd61-119">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="2cd61-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="2cd61-120">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cd61-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cd61-121">Child Elements</span></span>  
 <span data-ttu-id="2cd61-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="2cd61-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cd61-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cd61-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2cd61-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2cd61-124">Element</span></span>|<span data-ttu-id="2cd61-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cd61-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2cd61-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2cd61-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2cd61-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd61-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cd61-128">Remarks</span></span>  
 <span data-ttu-id="2cd61-129">Genel olarak, kaynakları [paketleme ve dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelendiği gibi, kaynakların araştırmalarını Kaynak Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="2cd61-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="2cd61-130">Yani, bir kaynağın belirli bir yerelleştirilmiş sürümü için Kaynak Yöneticisi yokladığınızda, genel derleme önbelleğine bakabilir, uygulamanın kod tabanında kültüre özgü bir klasöre bakabilir, uydu Derlemeleriyle ilgili sorgu Windows Installer ve <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="2cd61-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="2cd61-131">`<relativeBindForResources>` Öğesi, uydu derlemeleri için Kaynak Yöneticisi araştırma biçimini iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="2cd61-132">Aşağıdaki koşullarda kaynakları yokladığınızda performansı iyileştirebilir:</span><span class="sxs-lookup"><span data-stu-id="2cd61-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="2cd61-133">Uydu derlemesi, kod derlemesiyle aynı konumda dağıtıldığında.</span><span class="sxs-lookup"><span data-stu-id="2cd61-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="2cd61-134">Diğer bir deyişle, kod derlemesi genel derleme önbelleğinde yüklüyse, uydu derlemelerinin de de yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="2cd61-135">Kod derlemesi uygulamanın kod tabanında yüklüyse, uydu derlemelerinin de kod tabanında kültüre özgü bir klasöre yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cd61-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="2cd61-136">Windows Installer kullanılmazsa veya yalnızca, uydu derlemelerinin isteğe bağlı yüklemesi için nadiren kullanılırsa.</span><span class="sxs-lookup"><span data-stu-id="2cd61-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="2cd61-137">Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı işlemez.</span><span class="sxs-lookup"><span data-stu-id="2cd61-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="2cd61-138">Öğesinin, uydu derlemeleri için Kaynak Yöneticisi araştırmasını `true` `enabled` en iyi duruma getirmek için öğesi özniteliği aşağıdaki `<relativeBindForResources>` gibi ayarlanıyor:</span><span class="sxs-lookup"><span data-stu-id="2cd61-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="2cd61-139">Uydu derlemesini yoklamanız için üst kod derlemesinin konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cd61-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="2cd61-140">Uydu derlemeleri için Windows Installer sorgulamaz.</span><span class="sxs-lookup"><span data-stu-id="2cd61-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="2cd61-141"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="2cd61-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd61-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd61-142">See also</span></span>

- [<span data-ttu-id="2cd61-143">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="2cd61-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="2cd61-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2cd61-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2cd61-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="2cd61-145">Configuration File Schema</span></span>](../index.md)
