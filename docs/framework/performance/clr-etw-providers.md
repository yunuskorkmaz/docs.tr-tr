---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 33ef7491c2bffeda4ef737ed8f826cdfbfbb119d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400080"
---
# <a name="clr-etw-providers"></a>CLR ETW Sağlayıcılar
Ortak dil çalışma süresi (CLR) iki sağlayıcıdan sahiptir: çalışma zamanı sağlayıcısı ve genel kaçıp sağlayıcı.  
  
 Çalışma zamanı sağlayıcısı, hangi anahtar kelimelerin (etkinlik kategorileri) etkin olduğuna bağlı olarak olayları yükseltir. Örneğin, `LoaderKeyword` anahtar kelimeyi etkinleştirerek yükleyici olaylarını toplayabilirsiniz.  
  
 Windows (ETW) olayları için Olay İzleme, daha sonra virgülle ayrılmış değer (.csv) dosyalarında gerektiğinde sonradan işlenebilecek .etl uzantısı olan bir dosyaya kaydedilir. .etl dosyasının .csv dosyasına nasıl dönüştürüldüğü hakkında bilgi için [bkz.](controlling-logging.md)  
  
## <a name="the-runtime-provider"></a>Çalışma Zamanı Sağlayıcısı  
 Çalışma zamanı sağlayıcısı ana CLR ETW sağlayıcısıdır.  
  
 CLR çalışma zamanı sağlayıcısı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 olduğunu.  
  
 Yaygın olarak kullanılan araçları kullanarak CLR ETW olaylarını nasıl günlüğe kaydedip görüntüleyebilirsiniz, [bkz.](controlling-logging.md)  
  
 Gibi anahtar kelimeler kullanmanın yanı `LoaderKeyword`sıra, çok sık gündeme getirilebilir olayları günlüğe kaydetme için anahtar kelimeleri etkinleştirmek zorunda kalabilir. Ve `EndEnumerationKeyword` anahtar kelimeler bu olayları etkinleştirmek ve [CLR ETW Anahtar Kelimeler ve Düzeyleri](clr-etw-keywords-and-levels.md)özetlenir. `StartEnumerationKeyword`  
  
## <a name="the-rundown-provider"></a>Rundown Sağlayıcı  
 Bazı özel amaçlı kullanımlar için rundown sağlayıcısının açık olması gerekir. Ancak, kullanıcıların çoğunluğu için, çalışma zamanı sağlayıcısı yeterli olmalıdır.  
  
 CLR tükenme sağlayıcısı GUID A669021C-C450-4609-A035-5AF59AF4DF18 olduğunu.  
  
 Normalde, bir işlem başlatılmadan önce ETW günlüğü etkinleştirilir ve işlem çıktıktan sonra günlüğe kaydetme kapatılır. Ancak, işlem yürütülerken ETW günlüğe kaydetme açıksa, işlem hakkında ek bilgiler gerekir. Örneğin, sembol çözünürlüğü için günlüğe kaydetmeden önce zaten yüklenen yöntemler için yöntem olaylarını günlüğe kaydetmeniz gerekir.  
  
 Ve `DCStart` `DCEnd` olaylar, veri toplama başlatıldığında ve durdurulduğunda işlemin durumunu yakalar. (Devlet zaten sadece-in-time (JIT) derlenmiş ve yüklenen derlemeler yöntemleri de dahil olmak üzere, yüksek düzeyde bilgi anlamına gelir.) Bu iki olay, süreç içinde zaten neler olduğu hakkında bilgi sağlayabilir; örneğin, hangi yöntemler JIT-derlenmiş ve benzeri.  
  
 Yalnızca `DC`, , `DCStart` `DCEnd`, `DCInit` veya adlarındaki olaylar, rundown sağlayıcısı altında yükseltilir. Ayrıca, bu olaylar yalnızca rundown sağlayıcısı altında yükseltilir.  
  
 Olay anahtar kelime filtreleri ek olarak, rundown `StartRundownKeyword` sağlayıcısı `EndRundownKeyword` da hedefli filtreleme sağlamak için ve anahtar kelimeler destekler.  
  
### <a name="start-rundown"></a>Özeti Başlat  
 `StartRundownKeyword` Başlangıç özeti, anahtar kelimeyle birlikte, tükenme sağlayıcısının altında günlüğe kaydedildiğinde tetiklenir. Bu, `DCStart` olayın yükseltilmesine neden olur ve sistemin durumunu yakalar. Numaralandırma başlamadan `DCStartInit` önce, olay yükseltilir. Numaralandırma sonunda, `DCStartComplete` olay, veri toplamanın normal olarak sonlandırıldığını denetleyiciye bildirmek için yükseltilir.  
  
### <a name="end-rundown"></a>Özeti Sona Erdirme  
 `EndRundownKeyword` Özet sağlayıcının altında günlüğe kaydetme anahtar kelimeyle etkinleştirildiğinde bir son özeti tetiklenir. Son özet, yürütmeye devam eden bir işlemde profil oluşturmayı durdurur. Profil `DCEnd` oluşturma durdurulduğunda olaylar sistemin durumunu yakalar.  
  
 Numaralandırma başlamadan `DCEndInit` önce, olay yükseltilir. Numaralandırma sonunda, `DCEndComplete` olay veri toplama normal sona erdirilmiş olduğunu tüketicibildirmek için yükseltilir. Başlangıç özeti ve bitiş özeti öncelikle yönetilen sembol çözümü için kullanılır. Başlangıç özeti, profil oluşturma oturumu başlamadan önce zaten JIT tarafından derlenmiş olan yöntemler için adres aralığı bilgileri sağlayabilir. Son özet, profil oluşturma kapatılmak üzereyken JIT tarafından derlenen tüm yöntemler için adres aralığı bilgileri sağlayabilir.  
  
 Profil oluşturma oturumu durdurulduğunda son özet otomatik olarak gerçekleşmez. Bunun yerine, yönetilen sembol çözümlemesi gerçekleştirmek isteyen bir araç, profil oluşturma `EndRundownKeyword` durdurulmadan hemen önce, anahtar kelime etkin leştirilmiş bir CLR özeti sağlayıcısı oturumunu açıkça çağırmak zorundadır.  
  
 Başlangıç özeti veya son özet yönetilen sembol çözümü için yöntem adresi aralığı bilgileri `EndRundownKeyword` sağlasa da, `DCEnd` `StartRundownKeyword` anahtar kelime (olayları sağlayan) yerine anahtar sözcüğü (olayları sağlayan) kullanmanızı öneririz (olayları sağlayan). `DCStart` Profil `StartRundownKeyword` oluşturma oturumu sırasında özetin gerçekleşmesine neden olan bu durum profil senaryosunu bozabilir.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Runtime ve Rundown Sağlayıcıları Kullanarak ETW Veri Toplama  
 Aşağıdaki örnek, proseslerin profilli pencerenin içinde veya dışında başlayıp bitmesine bakılmaksızın, yönetilen işlemlerin en az etkiyle çözüme kavuşturulmasını sağlayacak şekilde CLR özet sağlayıcısının nasıl kullanılacağını gösterir.  
  
1. CLR çalışma zamanı sağlayıcısını kullanarak ETW günlüğe kaydetmeyi açın:  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     Günlük clr1.etl dosyasına kaydedilir.  
  
2. İşlem yürütmeye devam ederken profil oluşturmayı durdurmak için, `DCEnd` olayları yakalamak için özeti sağlayıcıyı başlatın:  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     Bu, `DCEnd` olayların bir özeti oturumu başlatmak için bir koleksiyon sağlar. Tüm etkinliklerin toplanması için 30 ila 60 saniye beklemeniz gerekebilir. Günlük clr1.et2 dosyasına kaydedilir.  
  
3. Tüm ETW profil oluşturmayı kapatın:  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. Tek bir günlük dosyası oluşturmak için profilleri birleştirin:  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Birleştirilmiş.etl dosyası, çalışma saatindeki olayları ve özeti sağlayıcı oturumlarını içerir.  
  
 Bir araç, kullanıcı profil oluşturmanın durdurulmasını istediğinde profil oluşturmayı hemen kapatmak yerine 2 ve 3 adımlarını (bir başlangıç oturumu başlatıp profil oluşturmayı sonlandırma) yürütebilir. Bir araç da adım 4 çalıştırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Dil Çalışma Zamanında ETW Olayları](etw-events-in-the-common-language-runtime.md)
