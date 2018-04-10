---
title: İzleme ve Hata Ayıklama Ayarları Şeması
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6d9e5ca97e4d5940dd9de3f3ffbd4db4183196c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="trace-and-debug-settings-schema"></a>İzleme ve Hata Ayıklama Ayarları Şeması
İzleme ve hata ayıklama ayarları toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicileri belirtin.  
  
 Aşağıdaki tabloda her izleme ve hata ayıklama ayarları öğesi işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Bir dinleyici ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Bir dinleyici ekler `Listeners` koleksiyonu.|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|Bir dinleyici ekler `sharedListeners` koleksiyonu.|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|İzleme anahtarı ayarlandığı düzeyini belirtir.|  
|[\<Assert >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi; ayrıca iletileri yazmak için dosya adını belirtir.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Temizler `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Temizler `Listeners` izleme için koleksiyonu.|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Bir dinleyici için bir filtre ekler `Listeners` izleme için koleksiyonu.|  
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Bir dinleyici için bir filtre ekler `sharedListeners` koleksiyonu.|  
|[\<dinleyicileri >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Dinleyicileri için belirtir `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<dinleyicileri >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Dinleyicileri için belirtir `Listeners` izleme için koleksiyonu.|  
|[\<performans sayaçları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel bellek boyutunu belirtir.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Gelen bir dinleyici kaldırır `Listeners` izleme için koleksiyonu.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Gelen bir dinleyici kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.|  
|[\<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri içerir.|  
|[\<Kaynakları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|İzleme iletileri başlatmak izleme kaynaklarını içerir.|  
|[\<Kaynak >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|İzleme iletileri başlatan bir izleme kaynağını belirtir.|  
|[\<anahtarları >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|İzleme anahtarları ve izleme anahtarları belirlendiği düzeyi içerir.|  
|[\<System.Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
|[\<İzleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
