---
title: İzleme ve Hata Ayıklama Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9927ad0e853577abb19750d54ba9e852a4e7ec51
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397952"
---
# <a name="trace-and-debug-settings-schema"></a>İzleme ve Hata Ayıklama Ayarları Şeması
İzleme ve hata ayıklama ayarları toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.  
  
 Aşağıdaki tabloda her izleme ve hata ayıklama ayarları öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Bir ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Bir ekler `Listeners` koleksiyonu.|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|Bir ekler `sharedListeners` koleksiyonu.|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Bir izleme anahtarı ayarlandığı düzeyini belirtir.|  
|[\<Assert >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi de ileti yazmak için dosya adını belirtir.|  
|[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Temizler `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Temizler `Listeners` izleme için koleksiyon.|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Bir dinleyicisi için bir filtre ekler `Listeners` izleme için koleksiyon.|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Bir dinleyicisi için bir filtre ekler `sharedListeners` koleksiyonu.|  
|[\<dinleyicileri >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Dinleyicileri için belirtir `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<dinleyicileri >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Dinleyicileri için belirtir `Listeners` izleme için koleksiyon.|  
|[\<performanceCounters >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Performans sayaçlarını birer paylaşılan genel bellek boyutunu belirtir.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Bir dinleyicisinden kaldırır `Listeners` izleme için koleksiyon.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Bir dinleyicisinden kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Herhangi bir kaynak veya trace ögesi başvurabilirsiniz dinleyicileri içerir.|  
|[\<Kaynakları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|İzleme iletileri başlatmak iz kaynakları içerir.|  
|[\<Kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|İzleme iletileri başlatan bir izleme kaynağı belirtir.|  
|[\<anahtarlar >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|İzleme anahtarları ve izleme anahtarları ayarlandığı düzeyi içerir.|  
|[\<System.Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|[\<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
