---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98914f57c24dc51625564e266157731ff173337
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157385"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="ea79d-102">\<relativeBindForResources > öğesi</span><span class="sxs-lookup"><span data-stu-id="ea79d-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="ea79d-103">Araştırma için uydu derlemelerini en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="ea79d-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="ea79d-104">\<configuration> Element</span></span>  
<span data-ttu-id="ea79d-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="ea79d-105">\<runtime> Element</span></span>  
<span data-ttu-id="ea79d-106">\<relativeBindForResources > öğesi</span><span class="sxs-lookup"><span data-stu-id="ea79d-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea79d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea79d-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea79d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea79d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea79d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea79d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea79d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea79d-110">Attributes</span></span>  
  
|<span data-ttu-id="ea79d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea79d-111">Attribute</span></span>|<span data-ttu-id="ea79d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea79d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ea79d-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ea79d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea79d-114">Ortak dil çalışma zamanı uydu derlemeler için araştırma iyileştirir olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ea79d-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea79d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ea79d-116">Değer</span><span class="sxs-lookup"><span data-stu-id="ea79d-116">Value</span></span>|<span data-ttu-id="ea79d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea79d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ea79d-118">Çalışma zamanı uydu derlemeler için araştırma iyileştirmez.</span><span class="sxs-lookup"><span data-stu-id="ea79d-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="ea79d-119">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="ea79d-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="ea79d-120">Çalışma zamanı araştırma uydu derlemeler için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea79d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea79d-121">Child Elements</span></span>  
 <span data-ttu-id="ea79d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea79d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea79d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea79d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ea79d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea79d-124">Element</span></span>|<span data-ttu-id="ea79d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea79d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ea79d-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ea79d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ea79d-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea79d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea79d-128">Remarks</span></span>  
 <span data-ttu-id="ea79d-129">Genel olarak, Resource Manager açıklandığı gibi kaynaklar için araştırmaları [kaynakları paketleme ve dağıtma](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ea79d-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="ea79d-130">Bu belirli bir yerelleştirilmiş sürümünün bir kaynak için Resource Manager araştırmaları, genel derleme önbelleğinde arayın, uygulamanın kodu temel, sorgu Windows Installer kültüre özgü bir klasörde için uydu derlemeleri bakın ve yükseltmek, anlamına gelir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="ea79d-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="ea79d-131">`<relativeBindForResources>` Öğesi Resource Manager için uydu derlemeleri araştırmaları şekilde iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="ea79d-132">Aşağıdaki koşullarda kaynaklar için yoklama zaman, performansı geliştirebilir:</span><span class="sxs-lookup"><span data-stu-id="ea79d-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="ea79d-133">Ne zaman uydu derlemesini, kod derleme ile aynı konumda dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="ea79d-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="ea79d-134">Bir kod derlemesi genel derleme önbelleğinde yüklü ise diğer bir deyişle, uydu derlemeleri de vardır yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="ea79d-135">Kod bütünleştirilmiş kodu uygulamanın temel yüklü değilse, uydu derlemeleri de kod tabanının bir kültüre özgü klasöre yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ea79d-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="ea79d-136">Windows Installer ne zaman kullanılmaz veya nadiren kullanılan isteğe bağlı yükleme uydu derlemeleri için.</span><span class="sxs-lookup"><span data-stu-id="ea79d-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="ea79d-137">Ne zaman uygulama kodunun işlemez <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="ea79d-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="ea79d-138">Ayarı `enabled` özniteliği `<relativeBindForResources>` öğesine `true` Resource Manager'ın araştırma için yardımcı derlemeler gibi en iyi duruma getirir:</span><span class="sxs-lookup"><span data-stu-id="ea79d-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="ea79d-139">Uydu derlemesi için araştırmaya üst kod derleme konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea79d-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="ea79d-140">Uydu derlemeleri için Windows Installer sorgulamaz.</span><span class="sxs-lookup"><span data-stu-id="ea79d-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="ea79d-141">Bunu yükseltmez <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="ea79d-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea79d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea79d-142">See also</span></span>

- [<span data-ttu-id="ea79d-143">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea79d-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="ea79d-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ea79d-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ea79d-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ea79d-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
