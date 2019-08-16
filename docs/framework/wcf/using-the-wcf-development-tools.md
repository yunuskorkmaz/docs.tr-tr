---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: ef20d13ade41992e6babc0ebb3a985aabb686ed3
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040417"
---
# <a name="using-the-wcf-development-tools"></a>WCF Geliştirme Araçlarını Kullanma
Bu bölümde, WCFservice 'nizi geliştirirken size yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.  
  
 Kendi hizmetinizi hızlı bir şekilde oluşturmak için Visual Studio şablonlarını temel olarak kullanabilir, sonra da hizmetinize hata ayıklamak ve test etmek için WCF hizmeti otomatik ana bilgisayarı ve WCF test Istemcisi kullanabilirsiniz. Bu araçlar birlikte hızlı ve sorunsuz bir hata ayıklama ve test çevrimi sağlar ve bir barındırma modeline erken bir aşamada yürütülmesi gereksinimini ortadan kaldırın.  
 
 > [!NOTE]
 > Visual Studio 2017 ' den itibaren, WCF geliştirme araçları varsayılan olarak yüklenmez. Bu özellikleri kullanabilmeniz için, Visual Studio yükleyicisinde Windows Communication Foundation bileşeninin seçili olduğundan emin olmanız gerekir.
  
## <a name="the-wcf-developer-tools"></a>WCF Geliştirici Araçları  
 [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Visual Studio 'da önceden tanımlanmış Visual Studio projesi ve öğe şablonlarını kullanarak WCF Hizmetleri ve çevreleyen uygulamalar oluşturabilirsiniz.  
  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 WCF hizmeti otomatik ana makinesi (WcfSvcHost. exe), uyguladık bir hizmeti otomatik olarak barındırmak ve test etmek için Visual Studio hata ayıklayıcısını (F5) başlatmanıza olanak tanır. Ardından, olası hataları bulmak ve onarmak için WCF test Istemcisi (wcfTestClient. exe) veya kendi istemcinizi kullanarak hizmeti test edebilirsiniz.  
  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 WCF test Istemcisi (WcfTestClient. exe), rastgele türlerin parametrelerini girmenize, bu girişi hizmete göndermenize ve hizmetin geri gönderdiği yanıtı görüntülemenize olanak tanıyan bir GUI aracıdır. WCF hizmeti otomatik ana bilgisayarı ile birleştirildiğinde sorunsuz bir hizmet testi deneyimi sağlar.  
  
 [XML'den Veri Türü Sınıfları Oluşturma](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Panoda depolanan XML verileri, bir kod sayfasına yapıştırılabilir. Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Araçları yönetici olmadan kullanma ayrıcalığı  
 Yönetici ayrıcalıkları olmayan kullanıcıların WCF Hizmetleri geliştirmesine olanak tanımak için, Visual Studio yüklemesi sırasında "http://+:8731/Design_Time_Addresses" ad alanı için bir ACL (Access Control listesi) oluşturulur. ACL, makinede oturum açmış tüm etkileşimli kullanıcıları içeren (UI) olarak ayarlanır. Yöneticiler bu ACL 'ye kullanıcı ekleyebilir veya kaldırabilir veya ek bağlantı noktaları açabilir. Bu ACL, WCF veya WF şablonlarının varsayılan yapılandırmasında veri göndermesini ve almasını sağlar. Ayrıca, kullanıcıların, yönetici ayrıcalıkları vermeden WCF hizmeti otomatik ana bilgisayarını (wcfSvcHost. exe) kullanmasına de olanak sağlar.  
  
 Erişimi, yükseltilmiş yönetici hesabı altında bulunan [!INCLUDE[wv](../../../includes/wv-md.md)] Netsh. exe aracını kullanarak değiştirebilirsiniz. Netsh. exe ' nin kullanılmasına bir örnek aşağıda verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh. exe hakkında daha fazla bilgi için bkz. [netsh. exe aracını ve komut satırı anahtarlarını kullanma](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)
- [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
