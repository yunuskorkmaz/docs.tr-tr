---
title: "wsatConfig.exe Tarafından Döndürülen Hata Kodlarını Yorumlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8bd70d22b7088a936d3243f050a4ee077d0f5c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>wsatConfig.exe Tarafından Döndürülen Hata Kodlarını Yorumlama
Bu konuda tüm hata kodları WS-AtomicTransaction yapılandırma yardımcı programı tarafından (wsatConfig.exe) oluşturulur ve önerilen gerçekleştirilecek eylemleri listeler.  
  
## <a name="list-of-error-codes"></a>Hata kodları listesi  
  
|Hata Kodu|Açıklama|Gerçekleştirilecek önerilen eylem|  
|----------------|-----------------|------------------------------------|  
|0|İşlem başarılı oldu|Yok.|  
|1.|Beklenmeyen hata|Microsoft'a başvurun|  
|2|MSDTC Güvenlik ayarlarını almak için iletişim kurmaya çalışılırken beklenmeyen bir hata oluştu.|MSDTC hizmeti devre dışı ve döndürülen özel durum listelenen tüm sorunları çözün emin olun.|  
|3|WsatConfig.exe altında çalıştırıldığı hesabı ağ güvenlik ayarlarını okumak için yeterli izinlere sahip değil.|WsatConfig.exe bir yönetici kullanıcı hesabı altında çalıştırın.|  
|4|"Ağ DTC erişimi" WS-AT desteğini etkinleştirmek denemeden önce MSDTC için etkinleştirin.|"Ağ DTC erişimi" MSDTC için etkinleştirip yardımcı programı yeniden çalıştırın.|  
|5|Girilen bağlantı noktası aralığının dışında oluştu. Değer 1 ile 65535 aralığında olmalıdır.|Düzeltin`-port:<portNum>`<br /><br /> hata iletisinde belirtildiği gibi komut satırı seçeneği.|  
|6|Geçersiz uç nokta sertifikası komut satırında belirtildi.  Sertifika bulunamadı veya doğrulamayı geçemedi.|Düzeltmek `-endpointCert` komut satırı seçeneği. Sertifika bir özel anahtara sahip, ClientAuthentication ve ServerAuthentication için kullanılmak üzere tasarlanmıştır, LocalMachine\MY sertifika deposunda yüklü ve tam güvenilir olduğundan emin olun.|  
|7|Geçersiz hesap sertifikası komut satırında belirtildi.|Düzeltmek `-accountsCerts` komut satırı seçeneği. Belirtilen sertifika yanlış belirtildi ya da bulunamadı.|  
|8|Varsayılan zaman aşımı 1-3600 saniye aralığın dışında belirtildi.|Belirtildiği gibi bir doğru varsayılan zaman aşımı değeri girin.|  
|10|Kayıt defterine erişim çalışılırken beklenmeyen bir hata oluştu.|Hata iletisi ve tıklatılabilir öğeleri için hata kodunu kontrol edin|  
|11|Kayıt defterine yazılamıyor.|Hata iletisinde listelenen anahtar kayıt defteri erişimi WsatConfig.exe altında yürütüldüğü hesabından destekleme kapasitesine sahip olduğundan emin olun.|  
|12|Sertifika deposuna erişim çalışılırken beklenmeyen bir hata oluştu.|İçin uygun sistem hatası eşlemek için döndürülen hata kodu kullanın.|  
|13|Http.sys yapılandırması başarısız oldu. Yeni bir HTTPS bağlantı noktası ayırma MSDTC için oluşturulamıyor.|İçin uygun sistem hatası eşlemek için döndürülen hata kodu kullanın.|  
|14|Http.sys yapılandırması başarısız oldu. MSDTC için önceki HTTPS bağlantı noktası ayırma kaldıramazsınız.|İçin uygun sistem hatası eşlemek için döndürülen hata kodu kullanın.|  
|15|Http.sys yapılandırması başarısız oldu. Belirtilen bağlantı noktası için bir önceki HTTPS bağlantı noktası ayırma zaten var.|Başka bir uygulama zaten belirli bağlantı noktası sahipliğini sürdü. Farklı bir bağlantı noktasına değiştirin veya kaldırın veya geçerli uygulama yeniden yapılandırın.|  
|16|Http.sys yapılandırması başarısız oldu. Belirtilen sertifika bağlantı noktasına bağlanılamıyor.|Hata iletisinde döndürülen hata kodu için uygun sistem hatası eşlemek için kullanın|  
|17|Http.sys yapılandırması başarısız oldu. Önceki bağlantı noktasından SSL sertifikası ile olan bağlantı kesilemiyor.|Hata iletisinde döndürülen hata kodu için uygun sistem hatası eşlemek için kullanın. Gerekirse, httpcfg.exe veya netsh.exe hatalı bağlantı noktası ayırmaları kaldırmak için kullanın.|  
|18|Http.sys yapılandırması başarısız oldu. Belirtilen sertifika çünkü bağlantı noktasına bağlanılamıyor önceki bir SSL bağlaması zaten mevcut.|Başka bir uygulama zaten belirli bağlantı noktası sahipliğini sürdü. Farklı bir bağlantı noktasına değiştirin veya kaldırın veya geçerli uygulama yeniden yapılandırın.|  
|19|MSDTC yeniden başlatma başarısız oldu|Gerekirse MSDTC el ile yeniden başlatın. Sorun devam ederse, Microsoft ile iletişime geçin.|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]uzak makinede yüklü değil veya düzgün şekilde yüklenmemiş.|Yükleme [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] makinedeki.|  
|21|Uzaktan yapılandırma işlemi zaman aşımına uğramadan nedeniyle başarısız oldu.|WS-AT uzak makinede yapılandırmak için çağrı 90 saniyeden daha uzun sürer.|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]uzak makinede yüklü değil veya düzgün şekilde yüklenmemiş.|Yükleme [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] makinedeki.|  
|23|Uzaktan yapılandırma uzak makinede bir özel durum nedeniyle başarısız oldu.|Kullanılabilir öğeleri için hata iletisini kontrol edin|  
|26|WsatConfig.exe için geçersiz bağımsız değişken geçirildi.|Komut satırı hataları denetleyin.|  
|27|`-accounts` Komut satırı seçeneği geçersiz.|Düzeltmek`accounts` doğru bir kullanıcı hesabı belirtmek için komut satırı seçeneği.|  
|28|`-network` Komut satırı seçeneği geçersiz.|Düzeltmek `-network` doğru "etkinleştir" belirtmek için komut satırı seçeneği veya "devre dışı bırak".|  
|29|`-maxTimeout` Komut satırı seçeneği geçersiz.|Düzeltmek `-maxTimeout` belirtildiği gibi komut satırı seçeneği.|  
|30|`-timeout` Komut satırı seçeneği geçersiz.|Düzeltmek `-timeout` belirtildiği gibi komut satırı seçeneği.|  
|31|`-traceLevel` Komut satırı seçeneği geçersiz.|Düzeltmek `-traceLevel` aşağıdakilere arasında geçerli bir değer belirtmek için komut satırı seçeneği<br /><br /> -Kapalı<br />-Hata<br />-Kritik<br />-Uyarı<br />-Bilgileri<br />-Verbose<br />-Tüm|  
|32|`-traceActivity` Komut satırı seçeneği geçersiz.|Düzeltmek `-traceActivity` "etkinleştir" veya "devre dışı bırak" belirterek komut satırı seçeneği.|  
|33|`-traceProp` Komut satırı seçeneği geçersiz.|Düzeltmek `-traceProp` "etkinleştir" veya "devre dışı bırak" belirterek komut satırı seçeneği.|  
|34|`-tracePII` Komut satırı seçeneği geçersiz.|Düzeltmek `-tracePII` "etkinleştir" veya "devre dışı bırak" belirterek komut satırı seçeneği.|  
|37|WsatConfig.exe tam makine sertifikası belirlemek mümkün değildi. Birden fazla aday olduğunda ya da hiçbiri mevcut olduğunda gerçekleşebilir.|Bir sertifika parmak izi veya doğru şekilde yapılandırmak için tam sertifikayı belirlemek için Issuer\SubjectName çifti belirtin.|  
|38|İşlemin veya kullanıcı güvenlik duvarı yapılandırmasını değiştirmek için yeterli izinlere sahip değil.|WsatConfig.exe bir yönetici kullanıcı hesabı altında çalıştırın.|  
|39|WsatConfig.exe güvenlik duvarı yapılandırması güncelleştirilirken bir hatayla karşılaştı.|Kullanılabilir öğeleri için hata iletisini kontrol edin.|  
|40|WsatConfig.exe sertifikanın özel anahtarı dosyasına MSDTC okuma erişimi verin mümkün değil|WsatConfig.exe bir yönetici kullanıcı hesabı altında çalıştırın.|  
|41|Yok ya da yüklemesi [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] bulunamadı veya bulunan sürüm aracı yapılandırmayı özellikli nedir eşleşmiyor.|Olun [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] doğru şekilde yüklendiğinden ve yalnızca kullanılır, bu sürümü ile gelen WsatConfig.exe aracı [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] WS-AT yapılandırmak için.|  
|42|Bağımsız değişken, komut satırında birden çok kez belirtildi.|Yalnızca her bir bağımsız değişkeni bir kez WsatConfig.exe yürütülürken belirtin.|  
|43|WS-AT etkin değilse WsatConfig.exe WS-AT ayarları güncelleştirilemiyor.|Belirtin `-network:enable` ek komut satırı bağımsız değişken olarak.|  
|44|Gerekli düzeltme eksik ve WS-AT düzeltme yüklenene kadar yapılandırılamaz.|Bkz: [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] gerekli düzeltme yükleme yönergeleri için sürüm notları.|  
|45|`-virtualServer` Komut satırı seçeneği geçersiz.|Düzeltmek `-virtualServer` küme kaynağı yapılandırmak üzere ağ adını belirterek komut satırı seçeneği.|  
|46|ETW izleme oturumunu Başlat çalışılırken beklenmeyen bir hata oluştu|İçin uygun sistem hatası eşlemek için döndürülen hata kodu kullanın.|  
|47|İşlemin veya kullanıcı ETW izleme oturumunu etkinleştirmek için yeterli izinlere sahip değil.|WsatConfig.exe bir yönetici kullanıcı hesabı altında çalıştırın.|  
|48|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|49|% Systemdrive % üzerinde yeterli alan nedeniyle yeni bir günlük dosyası oluşturulamıyor|% SYSTEMDRIVE % günlük dosyası için yeterli alana sahip olduğundan emin olun.|  
|51|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|52|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|53|Önceki ETW oturum günlük dosyasının yedekleme başarısız oldu.|% SYSTEMDRIVE % (varsa) günlük dosyası ve bir önceki günlük dosyası yedekleme için yeterli alana sahip olduğundan emin olun. Önceki günlük dosyası, gerekirse el ile kaldırın.|  
|55|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
|56|ETW izleme oturumunu başlatılmaya çalışılırken beklenmeyen bir hata oluştu.|Microsoft ile iletişime geçin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
