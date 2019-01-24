---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: e9a398ac6914582d299658e3e45d17ea5468917d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712096"
---
# <a name="using-the-wcf-development-tools"></a>WCF Geliştirme Araçlarını Kullanma
Bu bölümde, WCFservice geliştirmenize yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.  
  
 Visual Studio şablonları, kendi hizmetinizi hızla oluşturmak için bir temel kullanın. sonra hizmeti test etmek ve hata ayıklama için WCF hizmet otomatik konağı ve WCF Test İstemcisi'nı kullanın. Bu araçlar birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsünü sağlamak ve bir barındırma modeli için erken bir aşamada işleme gerek kullanımını.  
  
## <a name="the-wcf-developer-tools"></a>WCF geliştirici araçları  
 [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 WCF hizmetleri ve kapsayıcı uygulamaları hızlıca oluşturmak için Visual Studio'da önceden tanımlanmış Visual Studio'nun proje ve öğe şablonlarını kullanabilirsiniz.  
  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 WCF hizmet otomatik ana bilgisayarı (WcfSvcHost.exe), Visual Studio hata ayıklayıcıyı otomatik olarak ana bilgisayar ve uyguladıysanız bir hizmeti test etmek için (F5) başlatmak sağlar. Sonra hizmeti bulun ve olası hataları düzeltmek için WCF Test İstemcisi (wcfTestClient.exe) veya kendi istemci kullanarak test edebilirsiniz.  
  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test İstemcisi (WcfTestClient.exe) giriş parametreleri rastgele türler, hizmet ve hizmet yanıtı geri gönderir görünümü girdi gönderme olanak tanıyan bir GUI aracıdır. Bu test WCF hizmet otomatik konağı ile birleştirildiğinde deneyimi sorunsuz bir hizmet sağlar.  
  
 [XML'den Veri Türü Sınıfları Oluşturma](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 XML verileri Pano'ya depolanan bir kod sayfasına yapıştırılabilir. Verilerde tanımlanan sınıflar için kod türleri dönüştürülür.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Yönetici ayrıcalığı olmayan araçları kullanarak  
 WCF hizmetleri geliştirmek yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için bir ACL (erişim denetim listesi) için ad alanı oluşturulan "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında. ACL makinede oturum açan tüm etkileşimli kullanıcılar içerir (UI) için ayarlanır. Yöneticiler ekleyin veya bu ACL'SİNDEN kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL, varsayılan yapılandırmasında veri alıp göndermek WCF veya WF şablonları sağlar. Ayrıca, kullanıcıların yönetici ayrıcalıkları vermeden WCF hizmet otomatik ana bilgisayarı (wcfSvcHost.exe) kullanmasını sağlar.  
  
 İçinde Netsh.exe aracını kullanarak erişimi değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında. Netsh.exe kullanmaya bir örnek verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe hakkında daha fazla bilgi için bkz: [Netsh.exe aracı ve komut satırı anahtarları nasıl kullanılacağını](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)
- [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
