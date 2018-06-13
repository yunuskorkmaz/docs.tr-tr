---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806789"
---
# <a name="using-the-wcf-development-tools"></a>WCF Geliştirme Araçlarını Kullanma
Bu bölümde, WCFservice geliştirmeye yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.  
  
 Hızlı bir şekilde kendi hizmet oluşturmak için temel olarak Visual Studio şablonları kullanın, sonra WCF hizmeti otomatik ana bilgisayarı ve WCF Test İstemcisi hata ayıklama ve hizmetinizi sınamak için kullanın. Bu araçları birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsü sağlar ve barındırma modeli için erken bir aşamada yürütmek için gereken engellemek.  
  
## <a name="the-wcf-developer-tools"></a>WCF geliştirici araçları  
 [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 WCF hizmetleri ve çevresindeki uygulamaları hızlı bir şekilde oluşturmak için Visual Studio içindeki önceden tanımlanmış Visual Studio Proje ve öğe şablonları kullanabilirsiniz.  
  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 WCF hizmeti otomatik ana bilgisayarı (WcfSvcHost.exe), Visual Studio hata ayıklayıcısı (F5) otomatik olarak ana bilgisayar ve uygulamış olan bir hizmeti test başlatma olanak sağlar. Ardından hizmetini bulun ve olası hataları düzeltmek için WCF Test İstemcisi (wcfTestClient.exe) veya kendi istemci kullanarak test edebilirsiniz.  
  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test İstemcisi (WcfTestClient.exe) giriş parametreleri rastgele türler, hizmet ve hizmet yanıtı geri gönderir görünümü için giriş göndermek izin veren bir GUI aracıdır. WCF hizmet otomatik ana bilgisayarı ile birleştirildiğinde deneyimi sınama sorunsuz bir hizmet sağlar.  
  
 [XML'den Veri Türü Sınıfları Oluşturma](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 XML verileri Pano'ya depolanan bir kod sayfasına yapıştırılabilmesi için. Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Yönetici ayrıcalığı olmadan araçlarını kullanma  
 WCF hizmetlerini geliştirmek yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için bir ACL (erişim denetim listesi) ad alanı için oluşturulan "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında. ACL hangi makineye oturum açmış etkileşimli kullanıcıların tümünü içerir (UI) ayarlanır. Yöneticiler eklemek veya bu ACL'den kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL varsayılan yapılandırmalarında veri alıp göndermek WCF veya WF şablonları sağlar. Ayrıca, kullanıcıların yönetici ayrıcalıklarını verme olmadan WCF hizmeti otomatik ana bilgisayarı (wcfSvcHost.exe) kullanmasını sağlar.  
  
 Erişim Netsh.exe aracını kullanarak değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında. Netsh.exe kullanmaya ilişkin bir örnek verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe hakkında daha fazla bilgi için bkz: [Netsh.exe aracı ve komut satırı anahtarları kullanmayı](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
