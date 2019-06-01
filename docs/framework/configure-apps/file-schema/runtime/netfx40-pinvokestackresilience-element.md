---
title: <NetFx40_PInvokeStackResilience> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60fcdd902c6acf919e68806ff65e3b8142533280
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456388"
---
# <a name="netfx40pinvokestackresilience-element"></a><span data-ttu-id="aa5f7-102">\<Netfx40_pınvokestackresilience > öğesi</span><span class="sxs-lookup"><span data-stu-id="aa5f7-102">\<NetFx40_PInvokeStackResilience> Element</span></span>
<span data-ttu-id="aa5f7-103">Olup çalışma zamanı düzeltmeleri yanlış platform çağırma bildirimler arasında yavaş geçişler, çalışma zamanında otomatik olarak yönetilen ve yönetilmeyen kod belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="aa5f7-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="aa5f7-104">\<configuration></span></span>  
<span data-ttu-id="aa5f7-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="aa5f7-105">\<runtime></span></span>  
<span data-ttu-id="aa5f7-106"><NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="aa5f7-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa5f7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa5f7-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa5f7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa5f7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa5f7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa5f7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa5f7-110">Attributes</span></span>  
  
|<span data-ttu-id="aa5f7-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa5f7-111">Attribute</span></span>|<span data-ttu-id="aa5f7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa5f7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="aa5f7-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="aa5f7-114">Çalışma zamanı yanlış platform algılayıp algılamadığını belirtir bildirimleri çağırabilir ve yığın çalışma zamanında 32-bit platformlarda otomatik olarak düzeltir.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="aa5f7-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa5f7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="aa5f7-116">Değer</span><span class="sxs-lookup"><span data-stu-id="aa5f7-116">Value</span></span>|<span data-ttu-id="aa5f7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa5f7-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="aa5f7-118">Çalışma zamanı sürümünde mimarisi hazırlama daha hızlı bir şekilde birlikte çalışma kullanır [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], hangi algılamazsa ve düzeltme yanlış platform çağırma bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="aa5f7-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="aa5f7-120">Algılayan ve yanlış platform düzeltme çalışma zamanı kullanan daha yavaş geçişleri bildirimleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa5f7-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa5f7-121">Child Elements</span></span>  
 <span data-ttu-id="aa5f7-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa5f7-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa5f7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="aa5f7-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa5f7-124">Element</span></span>|<span data-ttu-id="aa5f7-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa5f7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aa5f7-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aa5f7-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa5f7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa5f7-128">Remarks</span></span>  
 <span data-ttu-id="aa5f7-129">Bu öğe, yanlış platform karşı çalıştırma esnekliği çağırmak için bildirimleri daha hızlı bir şekilde birlikte çalışma hazırlama ticari olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="aa5f7-130">.NET Framework 4 ile başlayarak, kolaylaştırılmış bir birlikte çalışma hazırlama mimarisi yönetilen koddan yönetilmeyen koda geçişleri için önemli bir performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="aa5f7-131">.NET Framework'ün önceki sürümlerinde, sıralama algılanan katman yanlış platform, 32-bit platformlarda bildirimleri çağırın ve yığın otomatik olarak düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="aa5f7-132">Yeni sıralama mimarisi, bu adım ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="aa5f7-133">Sonuç olarak, geçiş çok hızlı, ancak yanlış bir platform çağırma bildirimi bir program hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="aa5f7-134">Geliştirme sırasında yanlış bildirimleri algılamak kolaylaştırmak için Visual Studio hata ayıklama deneyimi geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="aa5f7-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) yönetilen hata ayıklama Yardımcısı (MDA), yanlış platform çağırma bildirimleri uygulamanızı hata ayıklayıcısı ekli çalıştırırken bildirir.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="aa5f7-136">Burada, uygulamanızın kullandığı derlemeniz olamaz ve kullanabileceğiniz sahip yanlış platform çağırma, bildirimleri, bileşenlerin bir senaryoya `NetFx40_PInvokeStackResilience` öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="aa5f7-137">Bu öğe, uygulama yapılandırma dosyası ekleme `enabled="1"` daha yavaş geçişleri, .NET Framework'ün önceki sürümlerinde davranışını ile bir uyumluluk moduna kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="aa5f7-138">.NET Framework'ün önceki sürümlerinde karşı derlenen derlemeler bu uyumluluk moduna otomatik olarak tutulur ve bu öğe gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="aa5f7-139">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="aa5f7-139">Configuration File</span></span>  
 <span data-ttu-id="aa5f7-140">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa5f7-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa5f7-141">Example</span></span>  
 <span data-ttu-id="aa5f7-142">Aşağıdaki örnekte gösterildiği yanlış karşı artan dayanıklılık katılmayı için platform çağırma nasıl arasında yavaş geçişler, bir uygulama için bildirimleri yönetilen ve yönetilmeyen kod.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa5f7-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa5f7-143">See also</span></span>

- [<span data-ttu-id="aa5f7-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="aa5f7-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="aa5f7-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="aa5f7-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="aa5f7-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="aa5f7-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
