---
title: CLR ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7d1f7ba1a0384ed93932733f12aa3306e16b790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="clr-etw-events"></a>CLR ETW Olayları
Bu bölümdeki konular Windows (ETW) olayları için olay izleme açıklar. Her olay bir ilişkili anahtar sözcüğü ve düzeyi, hangi açıklanan [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) konu. CLR olayları için iki sağlayıcı sahiptir:  
  
-   Çalışma zamanı sağlayıcı bağlı olarak anahtar sözcükler (olayların kategorilerini) etkinleştirildiği olayları başlatır. CLR çalışma zamanı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 sağlayıcıdır.  
  
-   Özel amaçlı sahip özeti sağlayıcısını kullanır. CLR özeti GUID a669021c-c450-4609-a035-5af59af4df18 sağlayıcıdır.  
  
 Sağlayıcılar hakkında daha fazla bilgi için bkz: [CLR ETW sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Çalışma Zamanı Bilgileri Olayları](../../../docs/framework/performance/runtime-information-etw-events.md)  
 SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde de dahil olmak üzere çalışma zamanı, GUID ile (varsa), başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri yakalar.  
  
 [Özel Durum Thrown_V1 Olayı](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Oluşturulan özel durumlar hakkında bilgi yakalar.  
  
 [Çekişme Olayları](../../../docs/framework/performance/contention-etw-events.md)  
 Çalışma zamanı kullanır İzleyici kilitleri veya yerel kilit çakışması hakkındaki bilgileri yakalar.  
  
 [İş Parçacığı Havuzu Olayları](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.  
  
 [Yükleyici Olayları](../../../docs/framework/performance/loader-etw-events.md)  
 Yükleme ve kaldırma uygulama etki alanları, derlemeler ve modüller hakkında bilgi yakalar.  
  
 [Yöntem Olayları](../../../docs/framework/performance/method-etw-events.md)  
 Simge çözünürlüğü için CLR yöntemleri hakkında bilgi yakalar.  
  
 [Atık Toplama Olayları](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Çöp toplama, tanılama ve hata ayıklama yardımcı olmak için ilgili bilgiler yakalar.  
  
 [Olayları Tam Zamanında İzleme](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Tam zamanında (JIT) satır içi kullanım ve kuyruk çağrıları hakkında bilgi yakalar.  
  
 [Birlikte Çalışma Olayları](../../../docs/framework/performance/interop-etw-events.md)  
 Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.  
  
 [ARM Olayları](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi yakalar.  
  
 [Güvenlik Olayları](../../../docs/framework/performance/security-etw-events.md)  
 Güçlü ad ve Authenticode doğrulama bilgilerini yakalar.  
  
 [Yığın Olayı](../../../docs/framework/performance/stack-etw-event.md)  
 Bir olay tetiklenir sonra Yığın izlemeleri oluşturmak için kullanılan diğer olaylarla bilgilerini yakalar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama geliştirmek ve performans ile ETW ayarlama](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [Windows Performans blogu](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [.NET Framework Günlük Kaydını Denetleme](../../../docs/framework/performance/controlling-logging.md)  
 [CLR ETW Sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md)  
 [CLR ETW Anahtar Sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
