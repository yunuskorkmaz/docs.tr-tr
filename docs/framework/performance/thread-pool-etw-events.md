---
title: İş Parçacığı Havuzu ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f1c92154fe62b1b6ba6981606680daf37d087f4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974858"
---
# <a name="thread-pool-etw-events"></a>İş Parçacığı Havuzu ETW Olayları
Bu olaylar, çalışan ve g/ç iş parçacıkları hakkında bilgi toplar.  
  
 İki iş parçacığı havuzu olayları grubu vardır:  
  
- Bir uygulamanın iş parçacığı havuzunu nasıl kullandığı hakkında bilgi sağlayan [çalışan iş parçacığı havuzu olayları](#worker-thread-pool-events)ve eşzamanlılık denetimindeki iş yüklerinin etkisi.  
  
- İş parçacığı havuzunda oluşturulan, kullanımdan kaldırılan, kullanımdan kaldırılan veya sonlandırılan g/ç iş parçacıkları hakkında bilgi sağlayan [g/ç iş parçacığı havuzu olayları](#io-thread-events).  

## <a name="worker-thread-pool-events"></a>Çalışan Iş parçacığı havuzu olayları
 Bu olaylar çalışma zamanının çalışan iş parçacığı havuzuyla ilgilidir ve iş parçacığı olayları için bildirim sağlar (örneğin, bir iş parçacığı oluşturulduğunda veya durdurulduğunda). Çalışan iş parçacığı havuzu, iş parçacığı sayısının ölçülen verimlilik temelinde hesaplandığı eşzamanlılık denetimi için uyarlamalı bir algoritma kullanır. Çalışan iş parçacığı havuzu olayları, bir uygulamanın iş parçacığı havuzunu nasıl kullandığını ve bazı iş yüklerinin eşzamanlılık denetimine sahip olabileceğini anlamak için kullanılabilir.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart ve Threadpoolworkerthreadthreadstop  
 Aşağıdaki tabloda bu olayların anahtar sözcüğü ve düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Bir çalışan iş parçacığı oluşturulur.|  
|`ThreadPoolWorkerThreadStop`|51|Çalışan iş parçacığı durduruldu.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Bir çalışan iş parçacığı yeniden oluşturma.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Kullanımdan kaldırılan bir çalışan iş parçacığı yeniden etkin hale gelir.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|Win: UInt32|İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.|  
|RetiredWorkerThreadCount|Win: UInt32|Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>Threadpoolworkerthreadadde ayarlama  
 Bu iş parçacığı havuzu olayları, iş parçacığı ekleme (eşzamanlılık denetimi) algoritmasının davranışını anlama ve hata ayıklama bilgilerini sağlar. Bilgiler, çalışan iş parçacığı havuzu tarafından dahili olarak kullanılır.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>Threadpoolworkerthreadadadatmentsample  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Bir örnek için bilgi toplamayı ifade eder; diğer bir deyişle, belirli bir eşzamanlılık düzeyi olan aktarım hızı, zaman içinde bir ölçümdür.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Trafiği|Win: Double|Zaman birimi başına tamamlama sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>Threadpoolworkerthreadadyatmentadde  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|İş parçacığı ekleme (Hill-climbing) algoritması eşzamanlılık düzeyindeki bir değişikliğin yerinde olduğunu belirlediğinde denetimdeki bir değişikliği kaydeder.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Averageüretilen Iş|Win: Double|Ölçüm örneğinin ortalama performansı.|  
|NewWorkerThreadCount|Win: UInt32|Yeni etkin çalışan iş parçacığı sayısı.|  
|Neden|Win: UInt32|Ayarlamanın nedeni.<br /><br /> 0x00-Warmup.<br /><br /> 0x01 başlatılıyor.<br /><br /> 0x02-rastgele taşı.<br /><br /> 0x03-taşıma hareketi.<br /><br /> 0x04-nokta değiştirme.<br /><br /> 0x05-sabitleniyor.<br /><br /> 0x06-başlangıça.<br /><br /> 0x07-Iş parçacığı zaman aşımına uğradı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>Threadpoolworkerthreadadadatmentstats  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|İş parçacığı havuzundaki verileri toplar.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|sürenin|Win: Double|Bu istatistiklerin toplandığı sürenin saniye cinsinden miktarı.|  
|Trafiği|Win: Double|Bu Aralık sırasında saniye başına ortalama tamamlama sayısı.|  
|ThreadWave|Win: Double|Dahili kullanım için ayrılmıştır.|  
|ThroughputWave|Win: Double|Dahili kullanım için ayrılmıştır.|  
|ThroughputErrorEstimate|Win: Double|Dahili kullanım için ayrılmıştır.|  
|AverageThroughputErrorEstimate|Win: Double|Dahili kullanım için ayrılmıştır.|  
|ThroughputRatio|Win: Double|Bu zaman aralığı boyunca etkin çalışan iş parçacığı sayısında değişimler nedeniyle üretilen iş akışındaki göreli geliştirme.|  
|likli|Win: Double|ThroughputRatio alanının geçerlilik süresinin ölçüsü.|  
|NewcontrolSetting|Win: Double|Etkin iş parçacığı sayısında gelecekteki Çeşitlemeler için temel olarak görev yapacak etkin çalışan iş parçacıklarının sayısı.|  
|Newthreadwavebüyüklük|Win: UInt16|Etkin iş parçacığı sayısı ' nda gelecekteki varyasyonların büyüklüğü.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  

## <a name="io-thread-events"></a>G/ç Iş parçacığı olayları  
 Bu iş parçacığı havuzu olayları, zaman uyumsuz olan g/ç iş parçacığı havuzundaki (tamamlanma bağlantı noktaları) iş parçacıkları için oluşur.  
  
### <a name="iothreadcreate_v1"></a>IOThreadCreate_V1  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-|-|-|  
|`IOThreadCreate_V1`|44|İş parçacığı havuzunda bir g/ç iş parçacığı oluşturulur.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Biriktirme|Win: UInt64|Yeni oluşturulan iş parçacığı dahil olmak üzere g/ç iş parçacıklarının sayısı.|  
|Numemekli|Win: UInt64|Kullanımdan kaldırılan çalışan iş parçacıklarının sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
### <a name="iothreadretire_v1"></a>IOThreadRetire_V1  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Bir g/ç iş parçacığı bir kullanımdan kaldırma adayı haline gelir.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Biriktirme|Win: UInt64|İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.|  
|Numemekli|Win: UInt64|Kullanımdan kaldırılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
### <a name="iothreadunretire_v1"></a>IOThreadUnretire_V1  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Bir g/ç iş parçacığı, iş parçacığı bir kullanımdan kaldırma adayı olduktan sonra bekleme süresi içinde ulaşan g/ç nedeniyle kullanımdan kaldırıldı.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Biriktirme|Win: UInt64|Bu dahil iş parçacığı havuzundaki g/ç iş parçacıklarının sayısı.|  
|Numemekli|Win: UInt64|Kullanımdan kaldırılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
### <a name="iothreadterminate"></a>Iothreadterminate  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|İş parçacığı havuzunda bir g/ç iş parçacığı oluşturulur.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Biriktirme|Win: UInt64|İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.|  
|Numemekli|Win: UInt64|Kullanımdan kaldırılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
