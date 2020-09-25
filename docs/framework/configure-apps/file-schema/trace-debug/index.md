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
ms.openlocfilehash: ae089e941d75df7ba1cd87b5b92a514a33bfbf85
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195200"
---
# <a name="trace-and-debug-settings-schema"></a>İzleme ve Hata Ayıklama Ayarları Şeması

İzleme ve hata ayıklama ayarları, iletileri toplama, depolama ve yönlendiren izleme dinleyicilerini ve bir izleme anahtarının ayarlandığı düzeyi belirtir.  
  
 Aşağıdaki tabloda, her bir izleme ve hata ayıklama ayarları öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|`Listeners`İzleme kaynağı için koleksiyona bir dinleyici ekler.|  
|[\<add>](add-element-for-listeners-for-trace.md)|Koleksiyona bir dinleyici ekler `Listeners` .|  
|[\<add>](add-element-for-sharedlisteners.md)|Koleksiyona bir dinleyici ekler `sharedListeners` .|  
|[\<add>](add-element-for-switches.md)|Bir izleme anahtarının ayarlandığı düzeyi belirtir.|  
|[\<assert>](assert-element.md)|Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.|  
|[\<clear>](clear-element-for-listeners-for-source.md)|`Listeners`İzleme kaynağı için koleksiyonu temizler.|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|`Listeners`İzleme için koleksiyonu temizler.|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|İzleme kaynağı için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|İzleme için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|Koleksiyondaki bir dinleyiciye bir filtre ekler `sharedListeners` .|  
|[\<listeners>](listeners-element-for-source.md)|`Listeners`İzleme kaynağı için koleksiyon dinleyicileri belirtir.|  
|[\<listeners>](listeners-element-for-trace.md)|İzleme koleksiyonu için dinleyicileri belirtir `Listeners` .|  
|[\<performanceCounters>](performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|`Listeners`İzleme için koleksiyondan bir dinleyici kaldırır.|  
|[\<remove>](remove-element-for-listeners-for-source.md)|`Listeners`İzleme kaynağı için koleksiyondan bir dinleyiciyi kaldırır.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.|  
|[\<sources>](sources-element.md)|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|[\<source>](source-element.md)|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
|[\<switches>](switches-element.md)|İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.|  
|[\<system.diagnostics>](system-diagnostics-element.md)|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|[\<trace>](trace-element.md)|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [Yapılandırma dosyası şeması](../index.md)
