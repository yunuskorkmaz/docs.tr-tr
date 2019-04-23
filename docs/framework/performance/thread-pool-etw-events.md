---
title: İş Parçacığı Havuzu ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caacee591c4df8389cea241916618f50da56b22b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119138"
---
# <a name="thread-pool-etw-events"></a>İş Parçacığı Havuzu ETW Olayları
<a name="top"></a> Bu olaylar, çalışan ve g/ç iş parçacıkları hakkında bilgi toplayın.  
  
 İş parçacığı havuzu olayları iki tür vardır:  
  
-   [Çalışan iş parçacığı havuzu olayları](#worker), uygulama iş parçacığı havuzu ve iş yüklerini etkisini eşzamanlılık denetimi kullanımı hakkında bilgi sağlar.  
  
-   [G/ç iş parçacığı havuzu olayları](#io), oluşturulan, kullanımdan, g/ç iş parçacıkları hakkında bilgi sağlayan unretired veya iş parçacığı havuzundaki sonlandırıldı.  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>Çalışan iş parçacığı havuzu olayları  
 Bu olaylar, çalışma zamanının çalışan iş parçacığı havuzuna ilgilidir ve iş parçacığı olayları için bildirimleri (örneğin bir iş parçacığı oluşturulduğunda veya durduruldu) sağlayın. Çalışan iş parçacığı havuzu, burada iş parçacığı sayısı hesaplanır eşzamanlılık denetimi, ölçülen aktarım hızına göre uyarlanabilir bir algoritma kullanır. Çalışan iş parçacığı havuzu olayları, uygulama iş parçacığı havuzu ve bazı iş yüklerinin eşzamanlılık denetimi olabilecek etkisi nasıl kullandığını anlamak için kullanılabilir.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart ve ThreadPoolWorkerThreadStop  
 Aşağıdaki tabloda, bu olaylar için düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|İş parçacığı oluşturulur.|  
|`ThreadPoolWorkerThreadStop`|51|İş parçacığı durduruldu.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|İş parçacığı devre dışı bırakır.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Devre dışı bırakılan iş parçacığı yeniden etkin hale gelir.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|Kazanma: UInt32|İş zaten işleyebildiğini olanlar dahil olmak üzere iş, yürütmek için çalışan iş parçacığı sayısı.|  
|RetiredWorkerThreadCount|Kazanma: UInt32|İşleri işlemek kullanılabilir değildir, ancak daha fazla iş parçacığı daha sonra gerekli durumunda, yedekte tutulmakta çalışan iş parçacığı sayısı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Bu iş parçacığı havuzu olayları anlama ve iş parçacığı ekleme (eşzamanlılık denetimi) algoritması davranışını hata ayıklama için bilgileri sağlayın. Bilgiler, çalışan iş parçacığı havuzu tarafından dahili olarak kullanılır.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Bir örnek olarak bilgi toplamayı gösterir; diğer bir deyişle, bir ölçüm belirli bir eşzamanlılık ile üretilen iş düzeyi, anında süre.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Aktarım hızı|Kazanma: Double|Birim başına tamamlamaları zaman sayısı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|İş parçacığı ekleme (hill tırmanma) algoritması eşzamanlılık düzeyi değişikliği yerinde olduğunu belirlediğinde denetiminde bir değişikliği kaydeder.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AverageThroughput|Kazanma: Double|Ortalama aktarım hızı ölçümlerin bir örnek.|  
|NewWorkerThreadCount|Kazanma: UInt32|Yeni etkin bir çalışan iş parçacığı sayısı.|  
|Neden|Kazanma: UInt32|Nedeni ayarlama.<br /><br /> 0x00 - Isınma.<br /><br /> 0x01 - başlatılıyor.<br /><br /> 0x02 - rastgele taşıma.<br /><br /> 0x03 - dağcılık taşıma.<br /><br /> 0x04 - noktasını değiştirin.<br /><br /> 0x05 - sabitleniyor.<br /><br /> 0x06 - starvation'i tıklatın.<br /><br /> iş parçacığı 0x07 - zaman aşımına uğradı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|İş parçacığı havuzunda verileri toplar.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Süresi|Kazanma: Double|Bu sırada Bu istatistikler toplanan saniye cinsinden süre miktarı.|  
|Aktarım hızı|Kazanma: Double|Bu aralık sırasında saniyede tamamlamaları ortalama sayısı.|  
|ThreadWave|Kazanma: Double|İç kullanım için ayrılmıştır.|  
|ThroughputWave|Kazanma: Double|İç kullanım için ayrılmıştır.|  
|ThroughputErrorEstimate|Kazanma: Double|İç kullanım için ayrılmıştır.|  
|AverageThroughputErrorEstimate|Kazanma: Double|İç kullanım için ayrılmıştır.|  
|ThroughputRatio|Kazanma: Double|Bu zaman aralığında etkin bir çalışan iş parçacığı sayısı farklılığı kaynaklanan aktarım hızı göreli geliştirme.|  
|Güven|Kazanma: Double|Geçerlilik ThroughputRatio alan ölçüsü.|  
|NewcontrolSetting|Kazanma: Double|Etkin iş parçacığı sayısı gelecekteki çeşitleri için temel olarak hizmet verecek etkin bir çalışan iş parçacığı sayısı.|  
|NewThreadWaveMagnitude|Win:UInt16|Etkin iş parçacığı sayısı gelecekteki farklılığı büyüklüğünü.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>G/ç iş parçacığı olayları  
 Bu iş parçacığı havuzu olayları zaman uyumsuz g/ç iş parçacığı havuzunda (tamamlama bağlantı noktaları), iş parçacıkları için oluşur.  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Bir g/ç iş parçacığının iş parçacığı havuzunda oluşturulur.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt64|Yeni oluşturulan iş parçacığı gibi g/ç iş parçacığı sayısı.|  
|NumRetired|Kazanma: UInt64|Devre dışı bırakılan çalışan iş parçacığı sayısı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Bir g/ç iş parçacığı emeklilik aday haline gelir.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt64|Kalan iş parçacığı havuzunda g/ç iş parçacığı sayısı.|  
|NumRetired|Kazanma: UInt64|Devre dışı bırakılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Bir g/ç iş parçacığı unretired emeklilik aday iş parçacığı olduktan sonra bir bekleme dönemi içinde ulaşan g/ç nedeniyle.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt64|Bu da dahil olmak üzere iş parçacığı havuzundaki g/ç iş parçacığı sayısı.|  
|NumRetired|Kazanma: UInt64|Devre dışı bırakılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Bir g/ç iş parçacığının iş parçacığı havuzunda oluşturulur.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt64|Kalan iş parçacığı havuzunda g/ç iş parçacığı sayısı.|  
|NumRetired|Kazanma: UInt64|Devre dışı bırakılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
