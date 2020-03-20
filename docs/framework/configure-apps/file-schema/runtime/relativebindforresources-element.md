---
title: <relativeBindForResources> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153912"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="4b22d-102">\<relativeBindForResources> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4b22d-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="4b22d-103">Sondayı uydu montajları için optimize eder.</span><span class="sxs-lookup"><span data-stu-id="4b22d-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="4b22d-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b22d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b22d-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b22d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="4b22d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span><span class="sxs-lookup"><span data-stu-id="4b22d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b22d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b22d-107">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b22d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b22d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b22d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b22d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b22d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b22d-110">Attributes</span></span>  
  
|<span data-ttu-id="4b22d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b22d-111">Attribute</span></span>|<span data-ttu-id="4b22d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b22d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4b22d-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4b22d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b22d-114">Ortak dil çalışma süresinin uydu derlemeleri için sondayı optimize edip etmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b22d-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4b22d-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b22d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4b22d-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4b22d-116">Value</span></span>|<span data-ttu-id="4b22d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b22d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4b22d-118">Çalışma süresi, sondayı uydu derlemeleri için optimize etmez.</span><span class="sxs-lookup"><span data-stu-id="4b22d-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="4b22d-119">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="4b22d-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="4b22d-120">Çalışma süresi uydu meclisleri için sonda optimize eder.</span><span class="sxs-lookup"><span data-stu-id="4b22d-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b22d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b22d-121">Child Elements</span></span>  
 <span data-ttu-id="4b22d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b22d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b22d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b22d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4b22d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b22d-124">Element</span></span>|<span data-ttu-id="4b22d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b22d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4b22d-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4b22d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4b22d-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b22d-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b22d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b22d-128">Remarks</span></span>  
 <span data-ttu-id="4b22d-129">Genel olarak, Kaynak Yöneticisi, [Kaynakları Paketleme ve Dağıtma](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) konusunda belgelenen kaynaklar için sondalar.</span><span class="sxs-lookup"><span data-stu-id="4b22d-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="4b22d-130">Bu, Kaynak Yöneticisi bir kaynağın belirli bir yerelleştirilmiş sürümünü incelediğinde, genel derleme önbelleğine bakabileceği, uygulamanın kod tabanında kültüre özgü bir klasöre <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> bakabileceği, uydu derlemeleri için Windows Yükleyici'yi sorgulayabileceği ve olayı yükseltebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4b22d-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="4b22d-131">Öğe, `<relativeBindForResources>` Kaynak Yöneticisi'nin uydu derlemeleri için araştırma şeklini optimize eder.</span><span class="sxs-lookup"><span data-stu-id="4b22d-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="4b22d-132">Aşağıdaki koşullar altında kaynaklar için sondalama performansı artırabilir:</span><span class="sxs-lookup"><span data-stu-id="4b22d-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="4b22d-133">Uydu derlemesi kod derlemesi ile aynı konumda dağıtıldığında.</span><span class="sxs-lookup"><span data-stu-id="4b22d-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="4b22d-134">Başka bir deyişle, kod derlemesi genel montaj önbelleğine yüklenmişse, uydu derlemeleri de burada yüklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b22d-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="4b22d-135">Kod derlemesi uygulamanın kod tabanına yüklenmişse, uydu derlemelerinin kod tabanında kültüre özgü bir klasöre de yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b22d-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="4b22d-136">Windows Installer kullanılmadığında veya uydu derlemelerinin isteğe bağlı olarak yüklenmesi için nadiren kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="4b22d-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="4b22d-137">Uygulama kodu olayı işlemiyorsa. <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4b22d-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="4b22d-138">Kaynak Yöneticisi'nin `<relativeBindForResources>` uydu `true` derlemeleri için sondasını en iyi duruma getirmek için öğenin özniteliğini aşağıdaki gibi ayarlar: `enabled`</span><span class="sxs-lookup"><span data-stu-id="4b22d-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="4b22d-139">Uydu derlemesini araştırmak için ana kod derlemesinin konumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b22d-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="4b22d-140">Uydu derlemeleri için Windows Installer sorgusu yapmaz.</span><span class="sxs-lookup"><span data-stu-id="4b22d-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="4b22d-141"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayı yükseltmez.</span><span class="sxs-lookup"><span data-stu-id="4b22d-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b22d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b22d-142">See also</span></span>

- [<span data-ttu-id="4b22d-143">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="4b22d-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="4b22d-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4b22d-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4b22d-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4b22d-145">Configuration File Schema</span></span>](../index.md)
