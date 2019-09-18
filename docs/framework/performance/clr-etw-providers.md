---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93a0271c521de6e390e323d92e93a5e7bf94444f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046730"
---
# <a name="clr-etw-providers"></a>CLR ETW Sağlayıcılar
Ortak dil çalışma zamanı (CLR) iki sağlayıcıya sahiptir: çalışma zamanı sağlayıcısı ve runaşağı sağlayıcısı.  
  
 Çalışma zamanı sağlayıcısı, hangi anahtar sözcüklere (olay kategorileri) etkin olarak olaylar oluşturur. Örneğin, `LoaderKeyword` anahtar sözcüğünü etkinleştirerek yükleyici olaylarını toplayabilirsiniz.  
  
 Windows için olay Izleme (ETW) olayları, daha sonra gerektiğinde virgülle ayrılmış değer (. csv) dosyalarında işlenmek üzere bir. etl uzantısı olan bir dosyada günlüğe kaydedilir. . Etl dosyasını. csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz. [.NET Framework günlüğünü denetleme](controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Çalışma zamanı sağlayıcısı  
 Çalışma zamanı sağlayıcısı, ana CLR ETW sağlayıcısıdır.  
  
 CLR çalışma zamanı sağlayıcısı GUID 'SI e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.  
  
 CLR ETW olaylarını yaygın olarak kullanılabilen araçları kullanarak günlüğe kaydetme ve görüntüleme örnekleri için bkz. [.NET Framework günlüğünü denetleme](controlling-logging.md).  
  
 Gibi anahtar sözcüklerin `LoaderKeyword`kullanılmasına ek olarak, çok sık ortaya çıkarılan olayları günlüğe kaydetmek için anahtar kelimeleri etkinleştirmeniz gerekebilir. Ve anahtar sözcükleri bu olayları etkinleştirir ve [CLR ETW anahtar sözcükleri ve düzeylerinde](clr-etw-keywords-and-levels.md)özetlenmektedir. `EndEnumerationKeyword` `StartEnumerationKeyword`  
  
## <a name="the-rundown-provider"></a>Özet sağlayıcı  
 Özet sağlayıcının belirli özel amaçlı kullanımlar için açık olması gerekir. Ancak, çoğu kullanıcı için çalışma zamanı sağlayıcısı yeterli olacaktır.  
  
 CLR özeti sağlayıcısı GUID 'SI A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Normalde, bir işlem başlatılmadan önce ETW günlüğü etkinleştirilir ve işlem çıktıktan sonra günlüğe kaydetme kapalıdır. Ancak, işlem yürütülürken ETW günlüğü açıksa, işlem hakkında ek bilgiler gereklidir. Örneğin, sembol çözümlemesi için, günlük kaydı açılmadan önce zaten yüklenmiş olan yöntemler için yöntem olaylarını günlüğe yazmanız gerekir.  
  
 `DCStart` Ve`DCEnd` olayları, veri toplama başlatıldığında ve durdurulduğunda işlemin durumunu yakalar. (Durum, zaten tam zamanında (JıT) derlenmiş Yöntemler ve yüklenmiş derlemeler dahil olmak üzere yüksek düzeyde bilgi anlamına gelir.) Bu iki olay, işlemde zaten ne olduğunu hakkında bilgi sağlayabilir; Örneğin, JıT olarak derlenen Yöntemler ve bu şekilde devam eder.  
  
 Yalnızca `DC` ,`DCStart`,, veya`DCInit` adlarında bulunan olaylar, Özet sağlayıcının altında oluşturulur. `DCEnd` Ayrıca, bu olaylar yalnızca Özet sağlayıcının altında oluşturulur.  
  
 Olay anahtar sözcük filtrelerine ek olarak, runaşağı sağlayıcı hedeflenen filtreleme sağlamak için `StartRundownKeyword` ve `EndRundownKeyword` anahtar kelimelerini de destekler.  
  
### <a name="start-rundown"></a>Özeti Başlat  
 Bir başlangıç Özeti, runaşağı sağlayıcısı altında günlüğe kaydetme `StartRundownKeyword` anahtar sözcüğüyle etkinleştirildiğinde tetiklenir. Bu, `DCStart` etkinliğin oluşturulmasına neden olur ve sistemin durumunu yakalar. Numaralandırma başlamadan önce `DCStartInit` olay tetiklenir. Numaralandırmanın sonunda, `DCStartComplete` olay, veri toplamanın normal olarak sonlandırıldığı denetleyiciye bildirmek için oluşturulur.  
  
### <a name="end-rundown"></a>Özeti Sonlandır  
 Özet oluşturma sağlayıcısı altında günlüğe kaydetme, `EndRundownKeyword` anahtar sözcüğüyle etkinleştirildiği zaman bir bitiş Özeti tetiklenir. Özeti Sonlandır, yürütülmeye devam eden bir işlemde profil oluşturmayı durduruyor. `DCEnd` Olaylar, profil oluşturma durdurulduğunda sistemin durumunu yakalar.  
  
 Numaralandırma başlamadan önce `DCEndInit` olay tetiklenir. Sabit listesinin sonunda, `DCEndComplete` bu olay, tüketiciye veri toplamanın normal şekilde sonlandırıldığını bildirmek için oluşturulur. Başlangıç özeti ve bitiş Özeti öncelikle yönetilen sembol çözümlemesi için kullanılır. Özeti Başlat, profil oluşturma oturumu başlatılmadan önce zaten JıT olarak derlenen yöntemler için adres aralığı bilgisi sağlayabilir. Özet sonu, profil oluşturma işlemi kapalı olduğunda JıT derlenen tüm yöntemler için adres aralığı bilgisi sağlayabilir.  
  
 Bir profil oluşturma oturumu durdurulduğunda, Özeti Sonlandır işlemi otomatik olarak gerçekleşmez. Bunun yerine, yönetilen sembol çözünürlüğünü gerçekleştirmeye yönelik bir aracın, profil oluşturma durdurulmadan hemen önce, `EndRundownKeyword` anahtar sözcüğü etkin bir clr özet sağlayıcısı oturumunu açıkça çağırması gerekir.  
  
 Başlangıç Özeti veya bitiş Özeti, yönetilen sembol çözümlemesi için yöntem adres aralığı bilgilerini sağlayabilse de, `EndRundownKeyword` `StartRundownKeyword` anahtar sözcüğü yerine anahtar sözcüğü (olayları temin `DCEnd` eder) kullanmanızı öneririz ( etkinlikleri `DCStart` sağlar). Kullanmak `StartRundownKeyword` , profil oluşturma oturumu sırasında Özet 'in profili oluşturulan senaryoyu rahatsız eden bir şekilde oluşmasına neden olur.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Çalışma zamanı ve Özet sağlayıcıları kullanılarak ETW veri toplama  
 Aşağıdaki örnek, CLR özet sağlayıcısının, işlemlerin profil oluşturulmuş pencerenin içinde mi yoksa dışında mı başlayıp bitmediğine bakılmaksızın, en az etkiyle yönetilen işlemlerin sembol çözümüne izin veren bir şekilde nasıl kullanılacağını göstermektedir.  
  
1. CLR Runtime sağlayıcısını kullanarak ETW günlüğünü açın:  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Günlük, clr1. etl dosyasına kaydedilir.  
  
2. İşlem yürütülmeye devam ederken profil oluşturmayı durdurmak için, `DCEnd` olay yakalamak üzere runaşağı sağlayıcısını başlatın:  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Bu, `DCEnd` olay koleksiyonunun bir Özet oturum başlatmasını sağlar. Tüm olayların toplanması için 30 ila 60 saniye beklemeniz gerekebilir. Günlük, clr1. ET2 dosyasına kaydedilir.  
  
3. Tüm ETW profil oluşturmayı kapat:  
  
    ```console
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. Tek bir günlük dosyası oluşturmak için profilleri birleştirin:  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Birleştirilmiş. etl dosyası çalışma zamanı ve özet sağlayıcı oturumlarından olayları içerecektir.  
  
 Bir araç, bir Kullanıcı profil oluşturmayı istemesi durumunda profil oluşturmayı hemen kapatmak yerine 2 ve 3. adımları (bir Özet oturumu başlatıp profil oluşturmayı sonlandırıp) yürütebilir. Bir araç, 4. adımı da yürütebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](etw-events-in-the-common-language-runtime.md)
