---
title: wsatConfig.exe Tarafından Döndürülen Hata Kodlarını Yorumlama
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 26e7c40cb105ad10dac3b13b73cb33bc4fa57d69
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959849"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>wsatConfig.exe Tarafından Döndürülen Hata Kodlarını Yorumlama
Bu konuda, tüm hata kodlarını WS-AtomicTransaction yapılandırma hizmet programı (wsatConfig.exe) oluşturulan ve önerilen gerçekleştirilecek eylemler listeler.  
  
## <a name="list-of-error-codes"></a>Hata kodlarının listesi  
  
|Hata Kodu|Açıklama|Gerçekleştirilecek önerilen eylem|  
|----------------|-----------------|------------------------------------|  
|0|İşlem başarılı oldu|Yok.|  
|1.|Beklenmeyen bir hata oluştu|Microsoft ile iletişime geçin|  
|2|Güvenlik ayarlarını almak için MSDTC bağlanmaya çalışılırken beklenmeyen bir hata oluştu.|MSDTC hizmetinin devre dışı değildir ve döndürülen özel durumda listelenen tüm sorunları gidermeye emin olun.|  
|3|Ağ güvenlik ayarları okumak için yeterli izinlere WsatConfig.exe altında çalıştırıldığı hesabı yok.|WsatConfig.exe yönetici kullanıcı hesabı altında çalıştırın.|  
|4|"Ağ DTC erişimi" WS-AT desteğini etkinleştirmek denemeden önce MSDTC için etkinleştirin.|"Ağ DTC erişimi" MSDTC için etkinleştirip yardımcı programını yeniden çalıştırın.|  
|5|Girilen bağlantı noktası byl mimo platný. Değer 1 ile 65535 aralığında olmalıdır.|Düzeltin `-port:<portNum>`<br /><br /> hata iletisinde belirtildiği gibi komut satırı seçeneği.|  
|6|Komut satırında geçersiz uç nokta sertifikası belirtildi.  Sertifika bulunamadı veya doğrulamadan geçemedi.|Düzeltme `-endpointCert` komut satırı seçeneği. Sertifika bir özel anahtara sahip, ClientAuthentication ve ServerAuthentication için kullanılmak üzere tasarlanmıştır, LocalMachine\MY sertifika deposunda yüklü ve tam güvenilir olduğundan emin olun.|  
|7|Komut satırında geçersiz hesap sertifikası belirtildi.|Düzeltme `-accountsCerts` komut satırı seçeneği. Belirtilen sertifika yanlış belirtildi ya da işlemi bulunamadı.|  
|8|Varsayılan zaman aşımı 1-3600 saniye aralığı dışında belirtildi.|Belirtildiği şekilde doğru varsayılan zaman aşımı değeri girin.|  
|10|Kayıt defteri erişmeye çalışırken beklenmeyen bir hata oluştu.|Hata iletisi ve eyleme dönüştürülebilir öğeleri için hata kodunu kontrol edin|  
|11|Kayıt defterine yazılamıyor.|Hata iletisinde listelenen kayıt anahtarını kayıt defteri erişimini WsatConfig.exe altında yürütülen hesabından destekleme kapasitesine sahip olduğundan emin olun.|  
|12|Sertifika deposu erişmeye çalışırken beklenmeyen bir hata oluştu.|İçin uygun sistem hatası eşlemek döndürülen hata kodu kullanın.|  
|13|Http.sys yapılandırması başarısız oldu. Yeni bir HTTPS bağlantı noktası ayırma MSDTC için oluşturulamıyor.|İçin uygun sistem hatası eşlemek döndürülen hata kodu kullanın.|  
|14|Http.sys yapılandırması başarısız oldu. MSDTC için önceki HTTPS bağlantı noktası ayırması kaldırılamıyor.|İçin uygun sistem hatası eşlemek döndürülen hata kodu kullanın.|  
|15|Http.sys yapılandırması başarısız oldu. Belirtilen bağlantı noktası için önceki HTTPS bağlantı noktası ayırma zaten var.|Zaten başka bir uygulama belirli bir bağlantı noktasını sahipliğini duruma getirdi. Farklı bir bağlantı noktasına değiştirin veya kaldırın ya da geçerli uygulamanın yeniden yapılandırın.|  
|16|Http.sys yapılandırması başarısız oldu. Belirtilen sertifika, bağlantı noktasına bağlanamaz.|Hata iletisinde döndürülen hata kodu için uygun sistem hatası eşlemek için kullanın|  
|17|Http.sys yapılandırması başarısız oldu. Önceki bağlantı noktasından SSL sertifikası bağlamayı Kaldır olamaz.|Hata iletisinde döndürülen hata kodu için uygun sistem hatası eşlemek için kullanın. Gerekirse, httpcfg.exe veya netsh.exe hatalı bağlantı noktası ayırmaları kaldırmak için kullanın.|  
|18|Http.sys yapılandırması başarısız oldu. Belirtilen sertifika noktasına bağlanamaz, çünkü önceki bir SSL bağlaması zaten mevcut.|Zaten başka bir uygulama belirli bir bağlantı noktasını sahipliğini duruma getirdi. Farklı bir bağlantı noktasına değiştirin veya kaldırın ya da geçerli uygulamanın yeniden yapılandırın.|  
|19|MSDTC yeniden başlatılamadı|Gerekirse MSDTC el ile yeniden başlatın. Sorun devam ederse, Microsoft ile iletişime geçin.|  
|20|WinFX uzak makinede yüklü değil veya doğru şekilde yüklenmedi.|WinFX makineye yükleyin.|  
|21|Uzaktan yapılandırma işlemi zaman aşımına nedeniyle başarısız oldu.|Uzak makinede WS-AT yapılandırmak için çağrı 90 saniyeden daha uzun sürer.|  
|22|WinFX uzak makinede yüklü değil veya doğru şekilde yüklenmedi.|WinFX makineye yükleyin.|  
|23|Uzak yapılandırması, uzak makinedeki bir özel durum nedeniyle başarısız oldu.|Eyleme dönüştürülebilir öğeleri için hata iletisine bakın|  
|26|WsatConfig.exe için geçersiz bağımsız değişken geçirildi.|Komut satırı hataları denetleyin.|  
|27|`-accounts` Komut satırı seçeneği geçersiz.|Düzeltme`accounts` doğru bir kullanıcı hesabı belirtmek için komut satırı seçeneği.|  
|28|`-network` Komut satırı seçeneği geçersiz.|Düzeltme `-network` doğru "etkinleştir" belirtmek için komut satırı seçeneği veya "devre dışı bırak".|  
|29|`-maxTimeout` Komut satırı seçeneği geçersiz.|Düzeltme `-maxTimeout` belirtildiği gibi komut satırı seçeneği.|  
|30|`-timeout` Komut satırı seçeneği geçersiz.|Düzeltme `-timeout` belirtildiği gibi komut satırı seçeneği.|  
|31|`-traceLevel` Komut satırı seçeneği geçersiz.|Düzeltme `-traceLevel` aşağıdakilere arasında geçerli bir değer belirtmek için komut satırı seçeneği<br /><br /> -Kapalı<br />-Hata<br />-Kritik<br />-Uyarı<br />-Bilgiler<br />-Verbose<br />-Tümü|  
|32|`-traceActivity` Komut satırı seçeneği geçersiz.|Düzeltme `-traceActivity` "etkinleştir" veya "devre dışı bırak" belirterek komut satırı seçeneği.|  
|33|`-traceProp` Komut satırı seçeneği geçersiz.|Düzeltme `-traceProp` "etkinleştir" veya "devre dışı bırak" belirterek komut satırı seçeneği.|  
|34|`-tracePII` Komut satırı seçeneği geçersiz.|Düzeltme `-tracePII` "etkinleştir" veya "devre dışı bırak" belirterek komut satırı seçeneği.|  
|37|WsatConfig.exe tam makine sertifikası belirlemek mümkün değildi. Bu, birden fazla aday olduğunda ya da hiçbiri mevcut olduğunda meydana gelir.|Bir sertifika parmak izi veya doğru şekilde yapılandırmak için tam sertifikayı belirlemek için Issuer\SubjectName çifti belirtin.|  
|38|İşlemin veya kullanıcı güvenlik duvarı yapılandırmasını değiştirmek için yeterli izinlere sahip değil.|WsatConfig.exe yönetici kullanıcı hesabı altında çalıştırın.|  
|39|WsatConfig.exe, güvenlik duvarı yapılandırması güncelleştirilirken bir hatayla karşılaştı.|Eyleme dönüştürülebilir öğeleri için hata iletisine bakın.|  
|40|WsatConfig.exe MSDTC okuma erişimi vermek için sertifikanın özel anahtar dosyası değil|WsatConfig.exe yönetici kullanıcı hesabı altında çalıştırın.|  
|41|WinFX hiçbir yüklemesi bulunamadı veya bulunan sürüm aracı yapılandırma yeteneğine sahip nedir eşleşmiyor.|WinFX doğru şekilde yüklendiğinden emin olun ve yalnızca WinFX WS-AT yapılandırmak için bu sürümü ile birlikte gelen WsatConfig.exe aracını kullanın.|  
|42|Bağımsız değişken, komut satırında birden çok kez belirtildi.|Yalnızca her bağımsız değişken bir kez WsatConfig.exe yürütülürken belirtin.|  
|43|WS-AT etkin değilse WsatConfig.exe WS-AT ayarları güncelleştirilemiyor.|Belirtin `-network:enable` ek komut satırı bağımsız değişken olarak.|  
|44|Gerekli düzeltme eksik ve düzeltmeyi yüklenene kadar WS-AT yapılandırılamaz.|WinFX gerekli düzeltmeyi yükleme yönergeleri için sürüm notlarına bakın.|  
|45|`-virtualServer` Komut satırı seçeneği geçersiz.|Düzeltme `-virtualServer` yapılandırmak, küme kaynağının ağ adı belirterek komut satırı seçeneği.|  
|46|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu|İçin uygun sistem hatası eşlemek döndürülen hata kodu kullanın.|  
|47|İşlemin veya kullanıcı ETW izleme oturumunu etkinleştirmek için yeterli izinlere sahip değil.|WsatConfig.exe yönetici kullanıcı hesabı altında çalıştırın.|  
|48|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|49|Yetersiz alan nedeniyle yeni bir günlük dosyası % systemdrive % oluşturulamıyor|% SYSTEMDRIVE %, günlük dosyası için yeterli alan olduğundan emin olun.|  
|51|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|52|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|53|Önceki ETW oturumu günlük dosyasının yedekleme başarısız oldu.|% SYSTEMDRIVE % için günlük dosyasını ve önceki günlük dosyasının yedeği yeterli alan (varsa) olduğundan emin olun. Önceki günlük dosyası, gerekirse el ile kaldırın.|  
|55|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|56|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
