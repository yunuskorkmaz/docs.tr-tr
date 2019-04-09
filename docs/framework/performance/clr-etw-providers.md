---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d7757b50eedb25247b11fced3d4f9567691c380
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188610"
---
# <a name="clr-etw-providers"></a>CLR ETW Sağlayıcılar
Ortak dil çalışma zamanı (CLR) iki sağlayıcıları vardır: çalışma zamanı sağlayıcısı ve Özet sağlayıcı.  
  
 Çalışma zamanı sağlayıcısı olayları, etkin anahtar sözcüklere (olayların kategorilerini) bağlı olarak başlatır. Örneğin, etkinleştirerek yükleyici olaylarını toplayan `LoaderKeyword` anahtar sözcüğü.  
  
 Olay izleme için Windows (ETW) olayları, daha sonra gerektiğinde virgülle ayrılmış değer (.csv) dosyalarında sonrası işlenebilecek bir .etl uzantılı bir dosyaya kaydedilir. .Etl dosyasını bir .csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz: [denetleme .NET Framework günlük](../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Çalışma zamanı sağlayıcısı  
 Çalışma zamanı sağlayıcısı ana CLR ETW sağlayıcısıdır.  
  
 CLR çalışma zamanı sağlayıcısı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 ' dir.  
  
 Oturum ve yaygın olarak kullanılabilen araçları kullanarak CLR ETW olaylarını görüntülemek örnekleri için bkz. [denetleme .NET Framework günlük](../../../docs/framework/performance/controlling-logging.md).  
  
 Anahtar sözcükler gibi kullanmanın yanı sıra `LoaderKeyword`, çok sık harekete olaylar günlüğe anahtar sözcükleri etkinleştirmek zorunda kalabilirsiniz. `StartEnumerationKeyword` Ve `EndEnumerationKeyword` anahtar sözcükleri bu olayları etkinleştirmektedir ve de özetlenmiştir [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Özet sağlayıcısı  
 Özet sağlayıcısı bazı özel amaçlı kullanımlar için açık olması gerekir. Ancak, kullanıcıların çoğu için çalışma zamanı sağlayıcısı yeterli olacaktır.  
  
 CLR özeti sağlayıcısının GUID A669021C-C450-4609-A035-5AF59AF4DF18 ' dir.  
  
 Normalde, önce bir işlem başlatır ve süreç bittikten sonra günlük kaydı kapalı ETW günlük kaydı etkindir. Ancak, işlem yürütülürken ETW günlük kaydı açıksa, işlemleri hakkında ek bilgi gerekmiyor. Örneğin, sembol çözümleme için günlük açılmadan önce zaten yüklenmiş olan yöntemler için yöntem olaylarının günlüğe gerekir.  
  
 `DCStart` Ve `DCEnd` olayları kaydetme işleminin durumunu veri toplama başlatıldığında ve durduruldu. (Durum zaten tam derlenmiş zamanında (JIT) yöntemleri ve yüklenmiş derlemeler de dahil olmak üzere, yüksek bir düzeyde bilgi ifade eder.) Bu iki olay süreçte çoktan olmuş hakkında bilgi sağlayabilir. Örneğin, hangi yöntemlerin JIT-derlenmiş ve benzeri.  
  
 Sadece olaylar `DC`, `DCStart`, `DCEnd`, veya `DCInit` adları içinde Özet sağlayıcı altında üretilir. Ayrıca, bu olaylar yalnızca Özet sağlayıcı altında üretilir.  
  
 Olay anahtar sözcük filtrelerine ek olarak, Özet sağlayıcı da destekler `StartRundownKeyword` ve `EndRundownKeyword` sağlamak için anahtar sözcükler hedeflenen filtreleme.  
  
### <a name="start-rundown"></a>Özeti Başlat  
 Özet sağlayıcı altındaki günlük ile etkinleştirilince başlangıç özeti tetiklenir `StartRundownKeyword` anahtar sözcüğü. Bu neden `DCStart` oluşturulması için olay ve sistemin durumunu yakalar. Numaralandırma başlamadan önce `DCStartInit` olayı oluşturulur. Numaralandırmanın sonunda `DCStartComplete` veri toplama normal şekilde sona ermesinin olayı oluşturulur.  
  
### <a name="end-rundown"></a>Özet sonu  
 Özet sonu, Özet sağlayıcı altındaki günlük ile etkin olduğunda tetiklenir `EndRundownKeyword` anahtar sözcüğü. Yürütülecek devam eden süreçte profil oluşturmayı son Özet durdurur. `DCEnd` Olayları, profil oluşturma durduğunda sistem durumunu yakalar.  
  
 Numaralandırma başlamadan önce `DCEndInit` olayı oluşturulur. Numaralandırmanın sonunda `DCEndComplete` olayı, veri toplama olağan biçimde sona ermesini tüketiciye bildirmek üzere oluşturulur. Özeti başlatma ve sonu temelde sembol çözümlemesi için kullanılır. Başlangıç özeti profil oluşturma oturumu başlatılmasından önce önceden derlenmiş JIT yöntemleri için adres aralığı bilgisi sağlayabilir. Özet sonu profil oluşturma hakkında devre dışı olacağı sırada, JIT olarak derlenmiş tüm yöntemleri için adres aralığı bilgisi sağlayabilir.  
  
 Profil oluşturma oturumu durdurulduğunda Özet sonu otomatik olarak gerçekleştirilmez. Bunun yerine, CLR özeti sağlayıcısı oturumunu ile açıkça çağırmak sembol isteyen bir araç olan `EndRundownKeyword` yalnızca profil oluşturma durdurulmadan önce etkin anahtar sözcüğü.  
  
 Yönetilen sembol çözme yöntemi adres aralığı bilgisi başlangıç özeti veya Sonlandır özeti sağlamasına karşın, kullanmanızı öneririz `EndRundownKeyword` anahtar sözcüğü (kaynak olan `DCEnd` olayları) yerine `StartRundownKeyword` anahtar sözcüğü (Bu Kaynakları `DCStart` olayları). Kullanarak `StartRundownKeyword` özeti profil oluşturulan senaryoyu bozabilir profil oluşturma oturumu sırasında oluşmasına neden olur.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Çalışma zamanı ve Özet sağlayıcılarını kullanarak ETW veri toplama  
 Aşağıdaki örnek CLR özeti sağlayıcısının sembol çözümleme işlemlerini başlatmak veya profil penceresinin içinde veya dışında son bağımsız olarak en az etki ile yönetilen işlemlerin izin veren bir şekilde kullanmak nasıl gösterir.  
  
1.  CLR çalışma zamanı sağlayıcısını kullanarak ETW günlüğünü açın:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Günlük clr1.etl dosyasına kaydedilir.  
  
2.  Yürütülecek işlem devam ederken profil oluşturmayı durdurmak için yakalamak için Özet sağlayıcı Başlat `DCEnd` olayları:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Bu topluluğunun `DCEnd` Özet oturumu başlatmak için olayları. Tüm olayların toplanması için 30 ila 60 saniye beklemeniz gerekebilir. Günlük clr1.et2 dosyasına kaydedilir.  
  
3.  Tüm ETW profil oluşturmalarını devre dışı bırakın:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  Tek bir günlük dosyası oluşturmak üzere profilleri birleştirme:  
  
    ```  
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Merged.etl dosyası çalışma zamanı ve özeti sağlayıcısı oturumlarından gelen olayları içerir.  
  
 Adım 2 ve 3 (bir Özet oturumunun başlatılması ve ardından profil oluşturma sonlandırma) hemen bir kullanıcı profili oluşturma devre dışı kapatmak yerine bir aracı yürütebilir durdurulması için profil oluşturma isteği. Bir aracı, 4. adım olarak ayrıca yürütebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Dil Çalışma Zamanında ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
