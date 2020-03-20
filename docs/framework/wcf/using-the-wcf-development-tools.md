---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183074"
---
# <a name="using-the-wcf-development-tools"></a>WCF Geliştirme Araçlarını Kullanma
Bu bölümde, WCFservice geliştirmede size yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.  
  
 Kendi hizmetinizi hızlı bir şekilde oluşturmak için Visual Studio şablonlarını temel olarak kullanabilir, ardından servisinizi hata ayıklamak ve test etmek için WCF Service Auto Host ve WCF Test İstemci'yi kullanabilirsiniz. Bu araçlar birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsü sağlar ve erken bir aşamada bir barındırma modeline bağlanma gereksinimini önler.  

 > [!NOTE]
 > Visual Studio 2017 ile başlayarak, WCF geliştirme araçları varsayılan olarak yüklenmez. Bu özellikleri kullanabilmek için Visual Studio yükleyicisinde Windows Communication Foundation bileşeninin seçildiğinden emin olmalısınız.
  
## <a name="the-wcf-developer-tools"></a>WCF Geliştirici Araçları  
 [WCF Visual Studio Şablonları](wcf-vs-templates.md)  
  
 WCF hizmetleri ve çevresindeki uygulamaları hızla oluşturmak için Visual Studio'daki önceden tanımlanmış Visual Studio projesini ve öğe şablonlarını kullanabilirsiniz.  
  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 WCF Service Auto Host (WcfSvcHost.exe), uyguladığınız bir hizmeti otomatik olarak barındırmak ve test etmek için Visual Studio hata ayıklama (F5) başlatmanızı sağlar. Daha sonra olası hataları bulmak ve düzeltmek için WCF Test İstemcisini (wcfTestClient.exe) veya kendi istemcinizi kullanarak hizmeti test edebilirsiniz.  
  
 [WCF Test İstemcisi (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test İstemci (WcfTestClient.exe), rasgele türlerin parametrelerini gireyapmanızı, bu girişi hizmete göndermenizi ve hizmetin geri gönderdiği yanıtı görüntülemenizi sağlayan bir GUI aracıdır. WCF Service Auto Host ile birleştirildiğinde sorunsuz bir hizmet testi deneyimi sağlar.  
  
 [XML'den Veri Türü Sınıfları Oluşturma](generating-data-type-classes-from-xml.md)  
  
 Panoda depolanan XML verileri bir kod sayfasına yapıştırılabilir. Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Yönetici ayrıcalığı olmadan Araçları Kullanma  
 Yönetici ayrıcalığına sahip olmayan kullanıcıların WCF hizmetlerini geliştirmesini sağlamak için Visual Studio'nun kurulumu sırasında " "http://+:8731/Design_Time_Addressesad alanı için bir ACL (Erişim Denetim Listesi) oluşturulur. ACL, makinede oturum açan tüm etkileşimli kullanıcıları içeren (UI) olarak ayarlanır. Yöneticiler kullanıcıları bu ACL'den ekleyebilir veya kaldırabilir veya ek bağlantı noktaları açabilir. Bu ACL, WCF veya WF şablonlarının varsayılan yapılandırmalarında veri gönderip almalarını sağlar. Ayrıca, kullanıcıların WCF Service Auto Host'u (wcfSvcHost.exe) yönetici ayrıcalıkları vermeden kullanmalarına olanak tanır.  
  
 Windows Vista'daki Netsh.exe aracını kullanarak erişimi yükseltilmiş yönetici hesabı altında değiştirebilirsiniz. Aşağıda Netsh.exe kullanarak bir örnektir.  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe hakkında daha fazla bilgi için [Netsh.exe Aracı ve Komut Satırı Anahtarları Nasıl Kullanılır'](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))a bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Visual Studio Şablonları](wcf-vs-templates.md)
- [WCF Hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
