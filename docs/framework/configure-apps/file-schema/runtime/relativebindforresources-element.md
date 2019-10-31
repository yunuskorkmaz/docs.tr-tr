---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: 6a418fc546313b74bb965a0b223eca9c2e5acc08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115796"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="7e642-102">\<Relativeforresources > öğesi</span><span class="sxs-lookup"><span data-stu-id="7e642-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="7e642-103">Uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="7e642-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="7e642-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7e642-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e642-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="7e642-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7e642-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources >**</span><span class="sxs-lookup"><span data-stu-id="7e642-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e642-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e642-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e642-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e642-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7e642-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e642-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e642-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e642-110">Attributes</span></span>  
  
|<span data-ttu-id="7e642-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7e642-111">Attribute</span></span>|<span data-ttu-id="7e642-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e642-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7e642-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7e642-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7e642-114">Ortak dil çalışma zamanının uydu derlemeleri için araştırmayı iyileştirip iyileştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e642-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7e642-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7e642-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7e642-116">Değer</span><span class="sxs-lookup"><span data-stu-id="7e642-116">Value</span></span>|<span data-ttu-id="7e642-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e642-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7e642-118">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirmez.</span><span class="sxs-lookup"><span data-stu-id="7e642-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="7e642-119">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="7e642-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="7e642-120">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="7e642-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e642-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e642-121">Child Elements</span></span>  
 <span data-ttu-id="7e642-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7e642-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e642-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e642-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7e642-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e642-124">Element</span></span>|<span data-ttu-id="7e642-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e642-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7e642-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7e642-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7e642-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7e642-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e642-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e642-128">Remarks</span></span>  
 <span data-ttu-id="7e642-129">Genel olarak, kaynakları [paketleme ve dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelendiği gibi, kaynakların araştırmalarını Kaynak Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="7e642-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="7e642-130">Yani, bir kaynağın belirli bir yerelleştirilmiş sürümü için Kaynak Yöneticisi yokladığınızda, genel derleme önbelleğine bakabilir, uygulamanın kod tabanında kültüre özgü bir klasöre bakabilir, uydu Derlemeleriyle ilgili sorgu Windows Installer ve <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı.</span><span class="sxs-lookup"><span data-stu-id="7e642-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="7e642-131">`<relativeBindForResources>` öğesi, uydu derlemeleri için Kaynak Yöneticisi araştırma şeklini iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="7e642-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="7e642-132">Aşağıdaki koşullarda kaynakları yokladığınızda performansı iyileştirebilir:</span><span class="sxs-lookup"><span data-stu-id="7e642-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="7e642-133">Uydu derlemesi, kod derlemesiyle aynı konumda dağıtıldığında.</span><span class="sxs-lookup"><span data-stu-id="7e642-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="7e642-134">Diğer bir deyişle, kod derlemesi genel derleme önbelleğinde yüklüyse, uydu derlemelerinin de de yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e642-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="7e642-135">Kod derlemesi uygulamanın kod tabanında yüklüyse, uydu derlemelerinin de kod tabanında kültüre özgü bir klasöre yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e642-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="7e642-136">Windows Installer kullanılmazsa veya yalnızca, uydu derlemelerinin isteğe bağlı yüklemesi için nadiren kullanılırsa.</span><span class="sxs-lookup"><span data-stu-id="7e642-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="7e642-137">Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını işlemez.</span><span class="sxs-lookup"><span data-stu-id="7e642-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="7e642-138">`<relativeBindForResources>` öğesinin `enabled` özniteliğini `true` olarak ayarlamak, aşağıdaki gibi uydu derlemeleri için Kaynak Yöneticisi araştırmasını iyileştirir:</span><span class="sxs-lookup"><span data-stu-id="7e642-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="7e642-139">Uydu derlemesini yoklamanız için üst kod derlemesinin konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e642-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="7e642-140">Uydu derlemeleri için Windows Installer sorgulamaz.</span><span class="sxs-lookup"><span data-stu-id="7e642-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="7e642-141"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını yükseltmez.</span><span class="sxs-lookup"><span data-stu-id="7e642-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e642-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e642-142">See also</span></span>

- [<span data-ttu-id="7e642-143">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="7e642-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="7e642-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7e642-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7e642-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="7e642-145">Configuration File Schema</span></span>](../index.md)
