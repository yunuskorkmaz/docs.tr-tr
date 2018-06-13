---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e33e93ba42ad37d6a998fc80348af551aed18a4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398163"
---
# <a name="clr-etw-providers"></a>CLR ETW Sağlayıcılar
Ortak dil çalışma zamanı (CLR) iki sağlayıcı vardır: çalışma zamanı sağlayıcısı ve özeti sağlayıcısı.  
  
 Çalışma zamanı sağlayıcısı bağlı olarak anahtar sözcükler (olayların kategorilerini) etkinleştirildiği olayları başlatır. Etkinleştirerek yükleyici olayları gibi toplayabilirsiniz `LoaderKeyword` anahtar sözcüğü.  
  
 Olay için Windows (ETW) olayları izleme, daha sonra gerektikçe virgülle ayrılmış değer (.csv) dosyalarında sonrası işlenebilir .etl uzantısına sahip bir dosyaya kaydedilir. .Etl dosyası bir .csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz: [.NET Framework günlüğü denetleme](../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Çalışma zamanı sağlayıcısı  
 Çalışma zamanı sağlayıcısı ana CLR ETW sağlayıcısıdır.  
  
 CLR çalışma zamanı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 sağlayıcıdır.  
  
 Oturum ve yaygın olarak kullanılabilen araçlar kullanarak CLR ETW olayları görüntülemek nasıl örnekleri için bkz: [.NET Framework günlüğü denetleme](../../../docs/framework/performance/controlling-logging.md).  
  
 Anahtar sözcükler gibi kullanmanın yanı sıra `LoaderKeyword`, çok sık gerçekleştirilen olaylar günlüğe için anahtar sözcükleri etkinleştirmeniz gerekebilir. `StartEnumerationKeyword` Ve `EndEnumerationKeyword` anahtar sözcükler bu olayları etkinleştirmek ve içinde özetlenen [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Özeti sağlayıcısı  
 Belirli özel amaçlı kullanımları özeti sağlayıcısı açılması gerekir. Ancak, kullanıcıların çoğunluğunun için çalışma zamanı sağlayıcısı yeterli olacaktır.  
  
 CLR özeti GUID A669021C-C450-4609-A035-5AF59AF4DF18 sağlayıcıdır.  
  
 Normalde, bir işlem başlatır ve işlem çıktıktan sonra günlüğe kaydetme kapalı önce ETW günlük kaydı etkindir. Ancak, işlem yürütülürken ETW günlük kaydı açıksa, işlemi hakkında ek bilgi gereklidir. Örneğin, simge çözünürlüğü için yöntem olayları günlüğe kaydetme açık olduğu önce zaten yüklü yöntemleri için oturum gerekir.  
  
 `DCStart` Ve `DCEnd` olayları yakalama işleminin durumunu veri toplama başlatıldığında ve durduruldu. (Durumu yüklenen derlemeler ve sadece derlenmiş zamanında (JIT) zaten olan yöntemler de dahil olmak üzere yüksek bir düzeyde bilgi ifade eder.) Bu iki olay işlemde önce olanlar hakkında bilgiler sağlayabilir; Örneğin, hangi yöntemlerin JIT-derlenmiş vb. yoktu.  
  
 Yalnızca olaylarla `DC`, `DCStart`, `DCEnd`, veya `DCInit` adlarında özeti sağlayıcısı altında oluşturulur. Ayrıca bu olaylar yalnızca özeti sağlayıcısı altında oluşturulur.  
  
 Olay anahtar sözcük filtreleri yanı sıra da özeti sağlayıcının desteklediği `StartRundownKeyword` ve `EndRundownKeyword` sağlamak için anahtar sözcükler hedeflenen filtreleme.  
  
### <a name="start-rundown"></a>Özeti Başlat  
 Günlük kaydı özeti sağlayıcısı altında ile etkinleştirildiğinde başlangıç özeti tetiklenir `StartRundownKeyword` anahtar sözcüğü. Bu neden `DCStart` oluşturulması için olay ve sistem durumunu yakalar. Numaralandırma başlamadan önce `DCStartInit` olayı oluşturulur. Numaralandırma sonunda `DCStartComplete` olayı veri toplama normal olarak sonlandı denetleyicisi bildirmek için oluşturulur.  
  
### <a name="end-rundown"></a>Son özeti  
 Günlük kaydı özeti sağlayıcısı altında ile etkinleştirildiğinde son özeti tetiklenir `EndRundownKeyword` anahtar sözcüğü. Yürütmek için devam eden bir işlem profil son özeti durdurur. `DCEnd` Profil durdurulduğunda sistem durumu olayları yakalar.  
  
 Numaralandırma başlamadan önce `DCEndInit` olayı oluşturulur. Numaralandırma sonunda `DCEndComplete` olayı veri toplama normal olarak sonlandı tüketici bildirmek için oluşturulur. Özeti başlangıç ve bitiş özeti temelde yönetilen simgesi çözümlemesi için kullanılır. Başlangıç özeti profil oluşturma oturumu başlatıldı önce zaten JIT derlenmiş yöntemleri için adres aralığı bilgilerini sağlayabilir. Son özeti profil oluşturma hakkında kapatılmasına olduğunda JIT derlenmiş tüm yöntemleri için adres aralığı bilgilerini sağlayabilir.  
  
 Profil oluşturma oturumu durdurulduğunda son özeti otomatik olarak gerçekleştirilmez. Bunun yerine, açıkça bir CLR özeti sağlayıcısı oturumla çağırmak yönetilen simgesi çözümlemesi arayan bir araç olan `EndRundownKeyword` anahtar sözcüğü yalnızca profil durdurulmadan önce etkin.  
  
 Başlangıç özeti ya da son özeti yönetilen simge çözünürlüğü için yöntemi adres aralığı bilgilerini sağlayabilir, ancak kullanmanızı öneririz `EndRundownKeyword` anahtar sözcüğü (hangi kaynakları `DCEnd` olayları) yerine `StartRundownKeyword` anahtar sözcüğü (hangi sağladığı `DCStart` olayları). Kullanarak `StartRundownKeyword` profili senaryo rahatsız profil oluşturma oturumu sırasında gerçekleşecek şekilde özeti neden olur.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Çalışma zamanı ve özeti sağlayıcılarını kullanarak ETW veri toplama  
 Aşağıdaki örnek CLR özeti sağlayıcısının işlemleri başlatın veya profili penceresinin içinde veya dışında bitiş bağımsız olarak en az etkiyle yönetilen işlemlerin simge çözünürlüğü izin veren bir şekilde nasıl kullanılacağını gösterir.  
  
1.  CLR çalışma zamanı sağlayıcısı kullanarak ETW günlük özelliğini açın:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Günlük clr1.etl dosyasına kaydedilir.  
  
2.  Yürütülecek işlem devam ederken profil oluşturmayı durdurmak için yakalamak için özeti sağlayıcı Başlat `DCEnd` olayları:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Bu koleksiyonu sağlar `DCEnd` özeti oturumu başlatmak için olaylar. Tüm olayları toplanacak 30-60 saniye beklemeniz gerekebilir. Günlük clr1.et2 dosyasına kaydedilir.  
  
3.  Tüm ETW profil oluşturmayı Kapat:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  Tek bir günlük dosyası oluşturmak için profillerini birleştirin:  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     Çalışma zamanı ve özeti sağlayıcısı oturumları olayların merged.etl dosyası içerir.  
  
 Bir aracı hemen bir kullanıcı profil oluşturmayı kapatma yerine adım 2 ve 3 (özeti bir oturum açması ve profil oluşturma sonlandırma) yürütebilir durdurulacak profil istekleri. Bir aracı ayrıca 4. adım yürütebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
