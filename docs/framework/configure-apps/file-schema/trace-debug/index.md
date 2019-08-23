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
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927126"
---
# <a name="trace-and-debug-settings-schema"></a>İzleme ve Hata Ayıklama Ayarları Şeması
İzleme ve hata ayıklama ayarları, iletileri toplama, depolama ve yönlendiren izleme dinleyicilerini ve bir izleme anahtarının ayarlandığı düzeyi belirtir.  
  
 Aşağıdaki tabloda, her bir izleme ve hata ayıklama ayarları öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add-element-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyona bir dinleyici ekler.|  
|[\<> Ekle](add-element-for-listeners-for-trace.md)|`Listeners` Koleksiyona bir dinleyici ekler.|  
|[\<> Ekle](add-element-for-sharedlisteners.md)|`sharedListeners` Koleksiyona bir dinleyici ekler.|  
|[\<> Ekle](add-element-for-switches.md)|Bir izleme anahtarının ayarlandığı düzeyi belirtir.|  
|[\<onaylama >](assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.|  
|[\<> Temizle](clear-element-for-listeners-for-source.md)|İzleme kaynağı için koleksiyonu temizler. `Listeners`|  
|[\<> Temizle](clear-element-for-listeners-for-trace.md)|İzleme için `Listeners` koleksiyonu temizler.|  
|[\<Filtre >](filter-element-for-add-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.|  
|[\<Filtre >](filter-element-for-add-for-listeners-for-trace.md)|İzleme için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.|  
|[\<Filtre >](filter-element-for-add-for-sharedlisteners.md)|`sharedListeners` Koleksiyondaki bir dinleyiciye bir filtre ekler.|  
|[\<dinleyiciler >](listeners-element-for-source.md)|İzleme kaynağı için `Listeners` koleksiyon dinleyicileri belirtir.|  
|[\<dinleyiciler >](listeners-element-for-trace.md)|İzleme `Listeners` koleksiyonu için dinleyicileri belirtir.|  
|[\<performanceCounters >](performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.|  
|[\<> Kaldır](remove-element-for-listeners-for-trace.md)|İzleme için `Listeners` koleksiyondan bir dinleyici kaldırır.|  
|[\<> Kaldır](remove-element-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyondan bir dinleyiciyi kaldırır.|  
|[\<sharedListeners >](sharedlisteners-element.md)|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.|  
|[\<Kaynaklar >](sources-element.md)|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|[\<Kaynak >](source-element.md)|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
|[\<Anahtarlar >](switches-element.md)|İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.|  
|[\<System. Diagnostics >](system-diagnostics-element.md)|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|[\<İzleme >](trace-element.md)|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [Yapılandırma Dosyası Şeması](../index.md)
