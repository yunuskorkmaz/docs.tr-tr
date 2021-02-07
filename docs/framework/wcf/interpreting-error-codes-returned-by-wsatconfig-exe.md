---
description: 'Hakkında daha fazla bilgi edinin: wsatConfig.exe tarafından döndürülen hata kodlarını yorumlama'
title: wsatConfig.exe Tarafından Döndürülen Hata Kodlarını Yorumlama
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 3cde6e3f38ff09ca86159e8f499ba725ec7734f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732859"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>wsatConfig.exe Tarafından Döndürülen Hata Kodlarını Yorumlama

Bu konuda WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe) tarafından oluşturulan tüm hata kodları ve gerçekleştirilecek önerilen eylemler listelenmektedir.  
  
## <a name="list-of-error-codes"></a>Hata kodlarının listesi  
  
|Hata Kodu|Description|Önerilen eylem gerçekleştirilmelidir|  
|----------------|-----------------|------------------------------------|  
|0|İşlem başarılı oldu|Yok|  
|1|Beklenmeyen hata|Microsoft 'a başvurun|  
|2|Güvenlik ayarlarını almak için MSDTC ile iletişim kurulmaya çalışılırken beklenmeyen bir hata oluştu.|MSDTC hizmetinin devre dışı olmadığından ve döndürülen özel durumda listelenen tüm sorunları ele aldığından emin olun.|  
|3|WsatConfig.exe çalıştırıldığı hesabın, ağ güvenlik ayarlarını okumak için yeterli izni yoktu.|WsatConfig.exe yönetici kullanıcı hesabı altında yürütün.|  
|4|WS-AT desteğini etkinleştirmeyi denemeden önce MSDTC için "Ağ DTC erişimi" ni etkinleştirin.|MSDTC için "Ağ DTC erişimi" ni etkinleştirin ve yardımcı programı yeniden çalıştırın.|  
|5|Girilen bağlantı noktası aralık dışındaydı. Değer 1 ile 65535 arasında olmalıdır.|Şunu düzeltin `-port:<portNum>`<br /><br /> hata iletisinde gösterildiği gibi komut satırı seçeneği.|  
|6|Komut satırında geçersiz bir uç nokta sertifikası belirtildi.  Sertifika bulunamadı veya doğrulama başarılı olmadı.|`-endpointCert`Komut satırı seçeneğini düzeltin. Sertifikanın özel anahtarı olduğundan ve hem ClientAuthentication hem de ServerAuthentication için kullanılması amaçlanan, Localmachine\certificate deposunda yüklü olduğundan ve tam güvenilir olduğundan emin olun.|  
|7|Komut satırında geçersiz bir hesap sertifikası belirtildi.|`-accountsCerts`Komut satırı seçeneğini düzeltin. Belirtilen sertifika yanlış belirtildi ya da bulunamadı.|  
|8|Varsayılan zaman aşımı değeri 1 ile 3600 saniye arasında belirtildi.|Belirtilen şekilde doğru bir varsayılan zaman aşımı değeri girin.|  
|10|Kayıt defterine erişmeye çalışırken beklenmeyen bir hata oluştu.|İşlem yapılabilir öğeler için hata iletisini ve hata kodunu denetleyin|  
|11|Kayıt defterine yazılamıyor.|Hata iletisinde listelenen anahtarın, altında yürütüldüğü WsatConfig.exe hesap için kayıt defteri erişimini destekleme yeteneğine sahip olduğundan emin olun.|  
|12|Sertifika deposuna erişmeye çalışırken beklenmeyen bir hata oluştu.|Uygun sistem hatasına eşlemek için döndürülen hata kodunu kullanın.|  
|13|http.sys yapılandırması başarısız oldu. MSDTC için yeni bir HTTPS bağlantı noktası ayırması oluşturulamıyor.|Uygun sistem hatasına eşlemek için döndürülen hata kodunu kullanın.|  
|14|http.sys yapılandırması başarısız oldu. MSDTC için önceki HTTPS bağlantı noktası ayırması kaldırılamıyor.|Uygun sistem hatasına eşlemek için döndürülen hata kodunu kullanın.|  
|15|http.sys yapılandırması başarısız oldu. Belirtilen bağlantı noktası için önceki bir HTTPS bağlantı noktası ayırması zaten var.|Başka bir uygulama, belirli bir bağlantı noktasının sahipliğini zaten aldı. Farklı bir bağlantı noktasına değiştirin veya geçerli uygulamayı kaldırın veya yeniden yapılandırın.|  
|16|http.sys yapılandırması başarısız oldu. Belirtilen sertifika, bağlantı noktasına bağlanamıyor.|Uygun sistem hatasıyla eşlemek için hata iletisinde döndürülen hata kodunu kullanın|  
|17|http.sys yapılandırması başarısız oldu. Önceki bağlantı noktasından SSL sertifikasının bağlantısı kesilemedi.|Hata iletisinde döndürülen hata kodunu kullanarak uygun sistem hatasına eşleyin. Gerekirse, hatalı bağlantı noktası ayırmalarını kaldırmak için httpcfg.exe veya netsh.exe kullanın.|  
|18|http.sys yapılandırması başarısız oldu. Önceki bir SSL bağlaması zaten mevcut olduğundan, belirtilen sertifika bağlantı noktasına bağlanamıyor.|Başka bir uygulama, belirli bir bağlantı noktasının sahipliğini zaten aldı. Farklı bir bağlantı noktasına değiştirin veya geçerli uygulamayı kaldırın veya yeniden yapılandırın.|  
|19|MSDTC yeniden başlatılamadı|Gerekirse MSDTC 'yi el ile yeniden başlatın. Sorun devam ederse, Microsoft 'a başvurun.|  
|20|WinFX, uzak makinede yüklü değil veya doğru şekilde yüklenmemiş.|Makineye WinFX 'yi yükler.|  
|21|İşlemin zaman aşımına uğraması nedeniyle uzak yapılandırma başarısız oldu.|Uzak makinede WS-AT yapılandırma çağrısı 90 saniyeden uzun sürer.|  
|22|WinFX, uzak makinede yüklü değil veya doğru şekilde yüklenmemiş.|Makineye WinFX 'yi yükler.|  
|23|Uzak makinedeki bir özel durum nedeniyle uzak yapılandırma başarısız oldu.|İşlem yapılabilir öğeler için hata iletisini denetle|  
|26|WsatConfig.exe geçersiz bir bağımsız değişken geçirildi.|Hatalar için komut satırını denetleyin.|  
|27|`-accounts`Komut satırı seçeneği geçersizdi.|`accounts`Kullanıcı hesabını doğru şekilde belirtmek için-komut satırı seçeneğini düzeltin.|  
|28|`-network`Komut satırı seçeneği geçersizdi.|`-network`"Etkinleştir" veya "devre dışı bırak" seçeneklerini doğru bir şekilde belirtmek için komut satırı seçeneğini düzeltin.|  
|29|`-maxTimeout`Komut satırı seçeneği geçersizdi.|`-maxTimeout`Komut satırı seçeneğini belirtilen şekilde düzeltin.|  
|30|`-timeout`Komut satırı seçeneği geçersizdi.|`-timeout`Komut satırı seçeneğini belirtilen şekilde düzeltin.|  
|31|`-traceLevel`Komut satırı seçeneği geçersizdi.|`-traceLevel`Komut satırı seçeneğini, ardından, ' den sonra geçerli bir değer belirtmek için düzeltin,<br /><br /> -Kapalı<br />-Hata<br />-Kritik<br />-Uyarı<br />-Bilgi<br />-Ayrıntılı<br />-Tümü|  
|32|`-traceActivity`Komut satırı seçeneği geçersizdi.|`-traceActivity`"Etkinleştir" veya "devre dışı bırak" seçeneklerini belirleyerek komut satırı seçeneğini düzeltin.|  
|33|`-traceProp`Komut satırı seçeneği geçersizdi.|`-traceProp`"Etkinleştir" veya "devre dışı bırak" seçeneklerini belirleyerek komut satırı seçeneğini düzeltin.|  
|34|`-tracePII`Komut satırı seçeneği geçersizdi.|`-tracePII`"Etkinleştir" veya "devre dışı bırak" seçeneklerini belirleyerek komut satırı seçeneğini düzeltin.|  
|37|WsatConfig.exe, tam makine sertifikasını saptayamadı. Bu, birden fazla aday olduğunda veya hiç yoksa oluşabilir.|Yapılandırılacak sertifikayı doğru şekilde belirlemek için bir sertifika parmak izi veya Issuer\SubjectName çifti belirtin.|  
|38|İşlem veya Kullanıcı güvenlik duvarı yapılandırmasını değiştirmek için yeterli izinlere sahip değil.|WsatConfig.exe yönetici kullanıcı hesabı altında yürütün.|  
|39|WsatConfig.exe, güvenlik duvarı yapılandırmasını güncelleştirirken bir hatayla karşılaştı.|İşlem yapılabilir öğeler için hata iletisini denetleyin.|  
|40|WsatConfig.exe, MSDTC 'nin sertifikanın özel anahtar dosyasına okuma erişimi veremeyebilir|WsatConfig.exe yönetici kullanıcı hesabı altında yürütün.|  
|41|Herhangi bir WinFX yüklemesi bulunamadı veya bulunan sürüm, aracın yapılandırma yeteneğine sahip olduğu ile eşleşmiyor.|WinFX 'in düzgün yüklendiğinden emin olun ve yalnızca, WinFX 'in bu sürümü ile birlikte gelen WsatConfig.exe aracını kullanarak WS-AT ' i yapılandırın.|  
|42|Komut satırında bir bağımsız değişken birden çok kez belirtildi.|WsatConfig.exe yürütürken her bir bağımsız değişkeni yalnızca bir kez belirtin.|  
|43|WS-AT etkinleştirilmemişse WsatConfig.exe WS-AT ayarları güncelleştirilemez.|`-network:enable`Ek bir komut satırı bağımsız değişkeni olarak belirtin.|  
|44|Gerekli bir düzeltme eksik ve WS-AT, düzeltme yüklenene kadar yapılandırılamaz.|Gerekli düzeltmenin yüklenmesiyle ilgili yönergeler için bkz. WinFX sürüm notları.|  
|45|`-virtualServer`Komut satırı seçeneği geçersizdi.|`-virtualServer`Yapılandırılacak küme kaynağının ağ adını belirterek komut satırı seçeneğini düzeltin.|  
|46|ETW izleme oturumu başlatılmaya çalışılırken beklenmeyen bir hata oluştu|Uygun sistem hatasına eşlemek için döndürülen hata kodunu kullanın.|  
|47|İşlem veya kullanıcı ETW izleme oturumunu etkinleştirmek için yeterli izinlere sahip değil.|WsatConfig.exe yönetici kullanıcı hesabı altında yürütün.|  
|48|ETW izleme oturumu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft 'a başvurun.|  
|49|% Systemdrive% üzerinde yeterli alan olmadığından yeni bir günlük dosyası oluşturulamıyor|% Systemdrive% ' 'nizin günlük dosyası için yeterli alana sahip olduğundan emin olun.|  
|51|ETW izleme oturumu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft 'a başvurun.|  
|52|ETW izleme oturumu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft 'a başvurun.|  
|53|Önceki ETW oturum günlük dosyası yedeklemesi başarısız oldu.|% Systemdrive% ' inizin günlük dosyası ve önceki günlük dosyasının (varsa) yedeklemesi için yeterli alana sahip olduğundan emin olun. Gerekirse, önceki günlük dosyasını el ile kaldırın.|  
|55|ETW izleme oturumu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft 'a başvurun.|  
|56|ETW izleme oturumu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft 'a başvurun.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
