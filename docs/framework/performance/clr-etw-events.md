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
ms.openlocfilehash: cb7520518497b244be8be3751ca8a3063a02717a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788017"
---
# <a name="clr-etw-events"></a>CLR ETW Olayları
Bu bölümdeki konularda, Windows (ETW) olayları için olay izleme açıklanmaktadır. İlişkili bir anahtar sözcüğü her olayda ve düzeyi, açıklanan olduğu [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) konu. CLR olayları için iki sağlayıcıları vardır:  
  
- Çalışma zamanı sağlayıcısı olayları etkin anahtar sözcüklere (olayların kategorilerini) bağlı olarak oluşturur. CLR çalışma zamanı sağlayıcısı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 ' dir.  
  
- Özel amaçlı olan Özet sağlayıcısı kullanır. CLR özeti sağlayıcısının GUID a669021c-c450-4609-a035-5af59af4df18.  
  
 Sağlayıcılar hakkında daha fazla bilgi için bkz. [CLR ETW sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Çalışma Zamanı Bilgileri Olayları](../../../docs/framework/performance/runtime-information-etw-events.md)  
 SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde dahil olmak üzere çalışma zamanı, GUID, (varsa), ile başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri yakalar.  
  
 [Özel Durum Thrown_V1 Olayı](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Oluşturulan özel durumları hakkında bilgileri yakalar.  
  
 [Çekişme Olayları](../../../docs/framework/performance/contention-etw-events.md)  
 Çalışma zamanı kullanan İzleyici kilitler veya yerel kilit çakışması bilgilerini yakalar.  
  
 [İş Parçacığı Havuzu Olayları](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkındaki bilgileri yakalar.  
  
 [Yükleyici Olayları](../../../docs/framework/performance/loader-etw-events.md)  
 Modülleri yükleme ve kaldırma uygulama etki alanları ve derlemeler hakkındaki bilgileri yakalar.  
  
 [Yöntem Olayları](../../../docs/framework/performance/method-etw-events.md)  
 Sembol çözümlemesi için CLR yöntemleri hakkında bilgi yakalar.  
  
 [Atık Toplama Olayları](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Çöp toplama, tanılama ve hata ayıklama amacıyla ilgili bilgileri yakalar.  
  
 [Olayları Tam Zamanında İzleme](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Just-in-time (JIT) satır içi kullanım ve kuyruk çağrıları hakkındaki bilgileri yakalar.  
  
 [Birlikte Çalışma Olayları](../../../docs/framework/performance/interop-etw-events.md)  
 Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.  
  
 [ARM Olayları](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgileri çalışın.  
  
 [Güvenlik Olayları](../../../docs/framework/performance/security-etw-events.md)  
 Tanımlayıcı ad hem de Authenticode doğrulama hakkındaki bilgileri yakalar.  
  
 [Yığın Olayı](../../../docs/framework/performance/stack-etw-event.md)  
 Bir olay tetiklenir sonra yığın izlemelerini oluşturmak için kullanılan diğer olaylarla bilgileri yakalar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama artırmak ve ETW ile performans ayarlama](https://go.microsoft.com/fwlink/?LinkId=179696)
- [Windows Performans blogu](https://go.microsoft.com/fwlink/?LinkId=179509)
- [.NET Framework Günlük Kaydını Denetleme](../../../docs/framework/performance/controlling-logging.md)
- [CLR ETW Sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md)
- [CLR ETW Anahtar Sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
