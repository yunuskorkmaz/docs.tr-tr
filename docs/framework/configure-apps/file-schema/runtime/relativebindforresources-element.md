---
title: "&lt;relativeBindForResources&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffd5b62e0759b3a4f97e105e884912a41f0117de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a><span data-ttu-id="1c774-102">&lt;relativeBindForResources&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="1c774-102">&lt;relativeBindForResources&gt; Element</span></span>
<span data-ttu-id="1c774-103">Araştırması için uydu derlemelerini en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="1c774-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="1c774-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="1c774-104">\<configuration> Element</span></span>  
<span data-ttu-id="1c774-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="1c774-105">\<runtime> Element</span></span>  
<span data-ttu-id="1c774-106">\<relativeBindForResources > öğesi</span><span class="sxs-lookup"><span data-stu-id="1c774-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c774-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c774-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c774-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c774-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1c774-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c774-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c774-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c774-110">Attributes</span></span>  
  
|<span data-ttu-id="1c774-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c774-111">Attribute</span></span>|<span data-ttu-id="1c774-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c774-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1c774-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1c774-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1c774-114">Ortak dil çalışma zamanı için uydu derlemelerini araştırma iyileştirir olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c774-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1c774-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c774-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1c774-116">Değer</span><span class="sxs-lookup"><span data-stu-id="1c774-116">Value</span></span>|<span data-ttu-id="1c774-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c774-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1c774-118">Çalışma zamanı için uydu derlemelerini araştırma iyileştirmez.</span><span class="sxs-lookup"><span data-stu-id="1c774-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="1c774-119">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="1c774-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="1c774-120">Çalışma zamanı araştırma için uydu derlemelerini en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="1c774-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c774-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c774-121">Child Elements</span></span>  
 <span data-ttu-id="1c774-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c774-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c774-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c774-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1c774-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c774-124">Element</span></span>|<span data-ttu-id="1c774-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c774-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1c774-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1c774-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1c774-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1c774-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c774-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c774-128">Remarks</span></span>  
 <span data-ttu-id="1c774-129">Genel olarak, Resource Manager açıklandığı gibi kaynaklar için yoklamaları [paketleme ve dağıtma kaynakları](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu.</span><span class="sxs-lookup"><span data-stu-id="1c774-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="1c774-130">Bu belirli yerelleştirilmiş bir sürümün bir kaynağın için Resource Manager araştırmaları, onu genel derleme önbelleğinde arayın, kültüre özgü bir klasörde sorgusunda uygulamanın kodu temel, Windows Installer'ın için uydu derlemelerini bakın ve yükseltmek anlamına gelir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="1c774-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="1c774-131">`<relativeBindForResources>` Öğesi Resource Manager için uydu derlemelerini yoklamaları şekilde iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="1c774-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="1c774-132">Aşağıdaki koşullarda kaynaklar için yoklama zaman, performansı geliştirebilir:</span><span class="sxs-lookup"><span data-stu-id="1c774-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="1c774-133">Uydu bütünleştirilmiş kod derleme ile aynı konumda dağıtıldığında.</span><span class="sxs-lookup"><span data-stu-id="1c774-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="1c774-134">Kod derleme genel derleme önbelleğinde yüklü değilse, diğer bir deyişle, uydu derlemelerini Ayrıca var. yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c774-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="1c774-135">Kod derleme temel uygulamanın kodu yüklüyse, kod temeli kültüre özgü klasöründe uydu derlemelerini ayrıca yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c774-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="1c774-136">Windows Installer zaman kullanılmaz veya nadiren kullanılan isteğe bağlı yüklemesinin uydu derlemelerini.</span><span class="sxs-lookup"><span data-stu-id="1c774-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="1c774-137">Ne zaman uygulama kodu işlemiyor <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="1c774-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="1c774-138">Ayarı `enabled` özniteliği `<relativeBindForResources>` öğesine `true` Resource Manager'ın araştırma için uydu derlemelerini gibi en iyi duruma getirir:</span><span class="sxs-lookup"><span data-stu-id="1c774-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="1c774-139">Uydu derlemesi için araştırma için üst kod derleme konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c774-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="1c774-140">Windows Installer için uydu derlemelerini sorgulamaz.</span><span class="sxs-lookup"><span data-stu-id="1c774-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="1c774-141">Değil Yükselt <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="1c774-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c774-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c774-142">See Also</span></span>  
 [<span data-ttu-id="1c774-143">Paketleme ve dağıtma kaynakları</span><span class="sxs-lookup"><span data-stu-id="1c774-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [<span data-ttu-id="1c774-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1c774-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1c774-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1c774-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
