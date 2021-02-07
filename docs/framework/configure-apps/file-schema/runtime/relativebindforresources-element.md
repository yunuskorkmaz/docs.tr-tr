---
description: 'Daha fazla bilgi edinin: <relativeBindForResources> öğesi'
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: f08d8f8a8fc4bb14d28762254dca99788d44a858
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712928"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="dbb2d-103">\<relativeBindForResources> Öğesi</span><span class="sxs-lookup"><span data-stu-id="dbb2d-103">\<relativeBindForResources> Element</span></span>

<span data-ttu-id="dbb2d-104">Uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-104">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="dbb2d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dbb2d-105">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbb2d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbb2d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dbb2d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbb2d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbb2d-108">Attributes</span></span>  
  
|<span data-ttu-id="dbb2d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbb2d-109">Attribute</span></span>|<span data-ttu-id="dbb2d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb2d-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="dbb2d-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="dbb2d-112">Ortak dil çalışma zamanının uydu derlemeleri için araştırmayı iyileştirip iyileştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-112">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dbb2d-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbb2d-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="dbb2d-114">Değer</span><span class="sxs-lookup"><span data-stu-id="dbb2d-114">Value</span></span>|<span data-ttu-id="dbb2d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb2d-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="dbb2d-116">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirmez.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-116">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="dbb2d-117">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-117">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="dbb2d-118">Çalışma zamanı, uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-118">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbb2d-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbb2d-119">Child Elements</span></span>  

 <span data-ttu-id="dbb2d-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbb2d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbb2d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dbb2d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbb2d-122">Element</span></span>|<span data-ttu-id="dbb2d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb2d-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dbb2d-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dbb2d-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbb2d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbb2d-126">Remarks</span></span>  

 <span data-ttu-id="dbb2d-127">Genel olarak, kaynakları [paketleme ve dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelendiği gibi, kaynakların araştırmalarını Kaynak Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-127">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="dbb2d-128">Yani, bir kaynağın belirli bir yerelleştirilmiş sürümü için Kaynak Yöneticisi araştırdığınızda, genel derleme önbelleğine bakabilir, uygulamanın kod tabanında kültüre özgü bir klasöre bakabilir, uydu Derlemeleriyle ilgili sorgu Windows Installer ve <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-128">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="dbb2d-129">`<relativeBindForResources>`Öğesi, uydu derlemeleri için Kaynak Yöneticisi araştırma biçimini iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-129">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="dbb2d-130">Aşağıdaki koşullarda kaynakları yokladığınızda performansı iyileştirebilir:</span><span class="sxs-lookup"><span data-stu-id="dbb2d-130">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="dbb2d-131">Uydu derlemesi, kod derlemesiyle aynı konumda dağıtıldığında.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-131">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="dbb2d-132">Diğer bir deyişle, kod derlemesi genel derleme önbelleğinde yüklüyse, uydu derlemelerinin de de yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-132">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="dbb2d-133">Kod derlemesi uygulamanın kod tabanında yüklüyse, uydu derlemelerinin de kod tabanında kültüre özgü bir klasöre yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-133">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="dbb2d-134">Windows Installer kullanılmazsa veya yalnızca, uydu derlemelerinin isteğe bağlı yüklemesi için nadiren kullanılırsa.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-134">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="dbb2d-135">Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı işlemez.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-135">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="dbb2d-136">Öğesinin, `enabled` `<relativeBindForResources>` `true` uydu derlemeleri için Kaynak Yöneticisi araştırmasını en iyi duruma getirmek için öğesi özniteliği aşağıdaki gibi ayarlanıyor:</span><span class="sxs-lookup"><span data-stu-id="dbb2d-136">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="dbb2d-137">Uydu derlemesini yoklamanız için üst kod derlemesinin konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-137">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="dbb2d-138">Uydu derlemeleri için Windows Installer sorgulamaz.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-138">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="dbb2d-139"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>Olayı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-139">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb2d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-140">See also</span></span>

- [<span data-ttu-id="dbb2d-141">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="dbb2d-141">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="dbb2d-142">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="dbb2d-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dbb2d-143">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="dbb2d-143">Configuration File Schema</span></span>](../index.md)
