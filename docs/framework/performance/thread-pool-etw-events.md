---
title: "İş Parçacığı Havuzu ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3dfd8b17e4ca01802651087ff20988744a411ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="thread-pool-etw-events"></a>İş Parçacığı Havuzu ETW Olayları
<a name="top"></a>Bu olaylar çalışan ve g/ç iş parçacıkları hakkında bilgi toplayın.  
  
 İş parçacığı havuzu olayları iki grupları vardır:  
  
-   [Çalışan iş parçacığı havuzu olayları](#worker), bir uygulama iş parçacığı havuzu ve iş yükleri etkisini eşzamanlılık denetimi kullanma hakkında bilgi sağlar.  
  
-   [G/ç iş parçacığı havuzu olayları](#io), kullanımdan kaldırıldı, oluşturulduğunu, g/ç iş parçacıkları hakkında bilgi sağlayan unretired veya iş parçacığı havuzundaki sonlandırıldı.  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>Çalışan iş parçacığı havuzu olayları  
 Bu olaylar zamanının çalışan iş parçacığı havuzuna ilgili ve iş parçacığı olayları için bildirimleri (örneğin bir iş parçacığı oluşturulduğunda veya durduruldu) sağlayın. Çalışan iş parçacığı havuzu iş parçacığı sayısını burada hesaplanır eşzamanlılık denetimi ölçülen işlemeyi temel alan, Uyarlamalı bir algoritma kullanıyor. Çalışan iş parçacığı havuzu olayları, uygulama iş parçacığı havuzu ve belirli iş yükleri eşzamanlılık üzerinde denetiminiz etkisi nasıl kullandığı anlamak için kullanılabilir.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart ve ThreadPoolWorkerThreadStop  
 Aşağıdaki tabloda, bu olayların düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Bir çalışan iş parçacığı oluşturulur.|  
|`ThreadPoolWorkerThreadStop`|51|Bir çalışan iş parçacığı durduruldu.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Bir çalışan iş parçacığı kaldırdıktan.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Kullanımdan Kaldırılan çalışan iş parçacığı yeniden etkin hale gelir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|Win: UInt32|İş zaten işleme dahil olan iş işlemek için kullanılabilecek çalışan iş parçacığı sayısı.|  
|RetiredWorkerThreadCount|Win: UInt32|İş işlemek kullanılabilir değildir, ancak daha fazla iş parçacığı daha sonra gerekli durumunda, yedekte tutulan çalışan iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Bu iş parçacığı havuzu olayları anlama ve iş parçacığı ekleme (eşzamanlılık denetimi) algoritması davranışını hata ayıklama bilgilerini sağlayın. Bilgiler çalışan iş parçacığı havuzu tarafından dahili olarak kullanılır.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Bir örnek için bilgi topluluğu gösterir; diğer bir deyişle, belirli bir eşzamanlılık işlemeyle ölçü düzey, anında süre.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Üretilen iş|Win: Double|Birim başına tamamlamalar süre sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|İş parçacığı ekleme (tepe climbing) algoritması eşzamanlılık düzeyi değişikliği yerinde olduğunu belirlediğinde, bir değişiklik denetiminde kaydeder.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AverageThroughput|Win: Double|Bir örnek ölçümlerin ortalama performansıdır.|  
|NewWorkerThreadCount|Win: UInt32|Yeni etkin çalışan iş parçacığı sayısı.|  
|Neden|Win: UInt32|Değişiklik nedeni.<br /><br /> 0x00 - Isınma.<br /><br /> 0x01 - başlatılıyor.<br /><br /> 0x02 - rastgele taşıma.<br /><br /> 0x03 - dağcılık taşıma.<br /><br /> 0x04 - noktasını değiştirin.<br /><br /> 0x05 - Dengeleme.<br /><br /> 0x06 - yetersizliğine neden olabilir.<br /><br /> iş parçacığı 0x07 - zaman aşımına uğradı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|İş parçacığı havuzu verileri toplar.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Süre|Win: Double|Bu istatistikler sırasında toplanan saniye cinsinden süre miktarı.|  
|Üretilen iş|Win: Double|Tamamlamalar bu aralığı sırasında saniye başına ortalama sayısı.|  
|ThreadWave|Win: Double|İç kullanım için ayrılmıştır.|  
|ThroughputWave|Win: Double|İç kullanım için ayrılmıştır.|  
|ThroughputErrorEstimate|Win: Double|İç kullanım için ayrılmıştır.|  
|AverageThroughputErrorEstimate|Win: Double|İç kullanım için ayrılmıştır.|  
|ThroughputRatio|Win: Double|Bu zaman aralığı boyunca etkin çalışan iş parçacığı sayısı Çeşitlemeler nedeni verimlilik göreli gelişme.|  
|Güven|Win: Double|ThroughputRatio alan geçerliliğini ölçüsü.|  
|NewcontrolSetting|Win: Double|Etkin iş parçacığı sayısı gelecekteki Çeşitlemeler için temel olarak hizmet verecektir etkin çalışan iş parçacığı sayısı.|  
|NewThreadWaveMagnitude|Win: UInt16|Etkin iş parçacığı sayısı gelecekteki Çeşitlemeler büyüklüğü.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>G/ç iş parçacığı olayları  
 Zaman uyumsuz g/ç iş parçacığı havuzu (tamamlama bağlantı noktaları), iş parçacıkları için bu iş parçacığı havuzu olayları oluşur.  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Bir g/ç iş parçacığı, iş parçacığı havuzu oluşturulur.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt64|Yeni oluşturulan iş parçacığı dahil olmak üzere g/ç iş parçacığı sayısı.|  
|NumRetired|Win: UInt64|Kullanımdan Kaldırılan çalışan iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Bir g/ç iş parçacığı devre dışı bırakma aday olur.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt64|İş parçacığı havuzundaki kalan g/ç iş parçacığı sayısı.|  
|NumRetired|Win: UInt64|Kullanımdan Kaldırılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Bir g/ç iş parçacığı unretired iş parçacığı devre dışı bırakma aday hale geldikten sonra bir bekleme süresi içinde ulaşan g/ç nedeniyle.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt64|Bu da dahil olmak üzere iş parçacığı havuzundaki g/ç iş parçacığı sayısı.|  
|NumRetired|Win: UInt64|Kullanımdan Kaldırılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Bir g/ç iş parçacığı, iş parçacığı havuzu oluşturulur.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt64|İş parçacığı havuzundaki kalan g/ç iş parçacığı sayısı.|  
|NumRetired|Win: UInt64|Kullanımdan Kaldırılan g/ç iş parçacığı sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
