---
title: "CLR ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d0619388b429bd1824a62bc29ccb222eea1ffde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-etw-events"></a>CLR ETW Olayları
Bu bölümdeki konular Windows (ETW) olayları için olay izleme açıklar. Her olay bir ilişkili anahtar sözcüğü ve düzeyi, hangi açıklanan [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) konu. CLR olayları için iki sağlayıcı sahiptir:  
  
-   Çalışma zamanı sağlayıcı bağlı olarak anahtar sözcükler (olayların kategorilerini) etkinleştirildiği olayları başlatır. CLR çalışma zamanı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 sağlayıcıdır.  
  
-   Özel amaçlı sahip özeti sağlayıcısını kullanır. CLR özeti GUID a669021c-c450-4609-a035-5af59af4df18 sağlayıcıdır.  
  
 Sağlayıcılar hakkında daha fazla bilgi için bkz: [CLR ETW sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Çalışma zamanı bilgileri olayları](../../../docs/framework/performance/runtime-information-etw-events.md)  
 SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde de dahil olmak üzere çalışma zamanı, GUID ile (varsa), başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri yakalar.  
  
 [Özel durum Thrown_V1 olayı](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Oluşturulan özel durumlar hakkında bilgi yakalar.  
  
 [Çekişme olayları](../../../docs/framework/performance/contention-etw-events.md)  
 Çalışma zamanı kullanır İzleyici kilitleri veya yerel kilit çakışması hakkındaki bilgileri yakalar.  
  
 [İş parçacığı havuzu olayları](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.  
  
 [Yükleyici olayları](../../../docs/framework/performance/loader-etw-events.md)  
 Yükleme ve kaldırma uygulama etki alanları, derlemeler ve modüller hakkında bilgi yakalar.  
  
 [Yöntem olayları](../../../docs/framework/performance/method-etw-events.md)  
 Simge çözünürlüğü için CLR yöntemleri hakkında bilgi yakalar.  
  
 [Çöp toplama olayları](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Çöp toplama, tanılama ve hata ayıklama yardımcı olmak için ilgili bilgiler yakalar.  
  
 [JIT izleme olayları](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Tam zamanında (JIT) satır içi kullanım ve kuyruk çağrıları hakkında bilgi yakalar.  
  
 [Birlikte çalışma olayları](../../../docs/framework/performance/interop-etw-events.md)  
 Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.  
  
 [ARM olayları](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi yakalar.  
  
 [Güvenlik olayları](../../../docs/framework/performance/security-etw-events.md)  
 Güçlü ad ve Authenticode doğrulama bilgilerini yakalar.  
  
 [Yığın olayı](../../../docs/framework/performance/stack-etw-event.md)  
 Bir olay tetiklenir sonra Yığın izlemeleri oluşturmak için kullanılan diğer olaylarla bilgilerini yakalar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama geliştirmek ve performans ile ETW ayarlama](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [Windows Performans blogu](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [.NET Framework günlük kaydını denetleme](../../../docs/framework/performance/controlling-logging.md)  
 [CLR ETW sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md)  
 [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Ortak dil çalışma zamanında ETW olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
