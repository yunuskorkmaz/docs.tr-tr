---
title: WCF Visual Studio Şablonları
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 1b4a600e4ed19b967bcaeb6d880ea181b7c2d61f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197196"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio Şablonları
Windows Communication Foundation (WCF) Visual Studio şablonları, Visual Studio 'da kolayca WCF Hizmetleri ve çevreleyen uygulamalar oluşturmak için kullanabileceğiniz, önceden tanımlanmış proje ve öğe şablonlarıdır.  
  
## <a name="using-the-wcf-templates"></a>WCF şablonlarını kullanma  
 WCF Visual Studio şablonları, hizmet geliştirme için temel bir sınıf yapısı sağlar. Özellikle, bu şablonlar hizmet sözleşmesi, veri sözleşmesi, hizmet uygulama ve yapılandırma için temel tanımları sağlar. Bu şablonları, en az kod etkileşimi ile basit bir hizmet ve daha gelişmiş hizmetler için bir yapı taşı oluşturmak üzere kullanabilirsiniz.  
  
### <a name="wcf-service-library-project-template"></a>WCF hizmet kitaplığı proje şablonu  
 WCF hizmet kitaplığı proje şablonu, **Visual C#\Wcf** ve **Visual Basic\WCF**altındaki yeni proje iletişim kutusunda kullanılabilir.  
  
 **WCF hizmeti** şablonunu kullanarak yeni bir proje oluşturduğunuzda, yeni proje otomatik olarak aşağıdaki üç dosyayı içerir:  
  
- Hizmet sözleşmesi dosyası (IService1.cs veya IService1. vb). Hizmet sözleşmesi dosyası, WCF hizmeti özniteliklerinin uygulandığı bir arabirimdir. Bu dosya, hizmetlerinizi nasıl tanımlayacağınızı gösteren basit bir hizmetin tanımını sağlar ve parametre tabanlı işlemler ve basit bir veri sözleşmesi örneği içerir. Bu, bir WCF hizmeti projesi oluşturulduktan sonra kod düzenleyicisinde oluşturulan varsayılan dosyadır.  
  
- Hizmet uygulama dosyası (Service1.cs veya Service1. vb). Hizmet uygulama dosyası, hizmet sözleşmesi dosyasında tanımlanan sözleşmeyi uygular.  
  
- Uygulama yapılandırma dosyası (App. config). Yapılandırma dosyası, bir WCF hizmeti modelinin, güvenli bir HTTP bağlaması olan temel öğelerini sağlar. Ayrıca hizmet için bir uç nokta içerir ve meta veri değişimi etkinleştirilir.  
  
> [!NOTE]
> Visual Studio, varsayılan yapılandırma olan [WCF hizmet ana bilgisayarı (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md)kullanılarak çalıştırıldığında proje için yapılandırma dosyası olarak App. config dosyasını tanıyacak şekilde yapılandırılmıştır. Hizmet kitaplığını bir yürütülebilir dosyada barındırdıysanız, dll 'Ler için yapılandırma dosyaları geçerli olmadığından, yapılandırma kodunu yürütülebilir dosyanın yapılandırma dosyasına taşımanız gerekir.  
  
### <a name="wcf-service-application-template"></a>WCF hizmeti uygulama şablonu  
 WCF hizmeti uygulama şablonu, **Visual C#\Wcf** ve **Visual Basic\wcf**altındaki yeni proje iletişim kutusunda kullanılabilir.  
  
 **WCF Web uygulaması hizmet** şablonunu kullanarak yeni bir proje oluşturduğunuzda, proje aşağıdaki dört dosyayı içerir:  
  
- Hizmet ana bilgisayar dosyası (Service1. svc).  
  
- Hizmet sözleşmesi dosyası (IService1.cs veya IService1. vb).  
  
- Hizmet uygulama dosyası (Service1.svc.cs veya Service1. svc. vb).  
  
- Web yapılandırma dosyası (Web. config).  
  
 Şablon otomatik olarak bir Web sitesi oluşturur (sanal bir dizine dağıtılacak) ve içinde bir hizmet barındırır.  
  
### <a name="wcf-web-site-template"></a>WCF Web sitesi şablonu  
 WCF Web sitesi şablonu, **Visual C#\Web site\wcf hizmeti** ve **Visual basic\web Site\wcf hizmeti**altındaki yeni proje iletişim kutusunda kullanılabilir. Bu, WCF hizmeti uygulama şablonuyla aynı dosyaları oluşturur, ancak bir ASP.NET Web sitesi gibi düzenler. App_Code ve App_Data klasörleri oluşturulur.  
  
### <a name="wcf-service-item-template"></a>WCF hizmeti öğe şablonu  
 WCF hizmeti öğe şablonu, var olan Visual Studio projelerinize WCF hizmetleri eklemenin hızlı bir yolunu sağlayan özel bir şablondur.  
  
 Bu şablonu kullanmak için **Çözüm Gezgini** bölmesine gidin, proje adına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe** ' ye tıklayarak **Yeni öğe Ekle** iletişim kutusunu başlatın.  
  
 Hizmet arabirimi ve uygulama dosyaları kök proje klasörüne yerleştirilir.  
  
 Şablon, yeni hizmetin yapılandırma bölümünü, uyumlu türlerse, mevcut yapılandırma dosyası ile birleştirmeye çalışır.  
  
 Mevcut proje bir Web projem ise, bir hizmet ana bilgisayar dosyası (Service1. svc) de oluşturulur.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF hizmeti projesi ve öğe şablonu.  
 Bu şablonlar, bir Web hizmeti gibi erişilebilen bir iş akışı olan Iş akışı hizmetini barındıran WCF Hizmetleri oluşturur. XAML veya kesinlik temelli programlama modelleri için ayrı şablonlar var. Şablonları kullanarak sıralı veya eyalet makinesi iş akışı oluşturabilirsiniz. Bu iş akışı türleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışı oluşturma](../windows-workflow-foundation/how-to-create-a-workflow.md). İş akışı projeleri oluşturma hakkında daha fazla bilgi için bkz. [eski Iş akışı projeleri oluşturma](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Visual Studio Tasarımcısı, kod tabanlı olanlar yerine XOML türü iş akışları kullanıldığında daha hızlı yanıt verir. XOML iş akışı oluşturulacak varsayılan iş akışı türüdür.  
  
### <a name="wcf-syndication-service-library-template"></a>WCF dağıtım hizmeti kitaplık şablonu  
 Bu şablon, akışınızı RSS veya ATOM biçiminde bir WCF hizmeti olarak kullanıma sunmanızı sağlar. Daha fazla bilgi için bkz. [WCF dağıtımı](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Akışın adresini değiştirme  
 Dağıtım şablonu, yürütme sırasında Internet Explorer 'ı kullanır. Visual Studio 'da **Çözüm Gezgini** ' nde projenize sağ tıkladığınızda **Özellikler**' i seçin, ardından **Hata Ayıkla** sekmesini seçin ve şablonun varsayılan adresini görebilirsiniz. Internet Explorer bu adreste akışı açmaya çalışır.  
  
 Akışlarınızın adresini değiştirirseniz, **Hata Ayıkla** sekmesindeki adresi de değiştirmelisiniz. Bunu yapmazsanız, Internet Explorer akışı varsayılan adreste açmaya çalışır ve başarısız olur.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>AJAX etkin WCF hizmeti öğe şablonu  
 Bu şablon, bir AJAX denetimini WCF hizmeti olarak kullanıma sunar. AJAX denetimleri hakkında daha fazla bilgi için bkz. [AJAX denetim belgeleri](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Silverlight etkin WCF hizmeti öğe şablonu  
 Bu şablon, bir Silverlight istemcisine veya ön uca veri sağlayan bir Web hizmeti oluşturur. Şablon bir Web sitesine veya Web uygulaması projesine, bir Silverlight istemcisiyle iletişim kuran hizmet kodu ve yapılandırmasını içeren bir WCF hizmeti oluşturmak için eklenebilir. Daha sonra **hizmet başvurusu Ekle** kullanarak istemciye hizmetin istemci proxy 'sini ekleyebilir ve Silverlight Istemcisi ile SILVERLIGHT özellikli WCF hizmeti arasında veri alışverişi yapabilirsiniz.  
  
 Bu şablona erişmek için **Çözüm Gezgini**' de bir Web sitesine veya Web uygulaması projesine sağ tıklayın, **Yeni öğe Ekle**' ye tıklayın ve **Silverlight etkin WCF hizmeti**' ne tıklayın.  
  
> [!NOTE]
> Silverlight etkin WCF hizmeti herhangi bir güvenlik ayarını etkinleştirmeden bir `basicHttpBinding` uç noktası sunar. Bu nedenle, hizmet hakkındaki bilgiler, bu hizmete bağlanan tüm istemciler tarafından elde edilebilir. Hizmet ve istemci arasında değiş tokuş edilen iletiler de imzalanmamıştır veya şifrelenmez. Uç noktanın düzgün şekilde güvenliğini sağlamak için ASP.NET Authentication, HTTPS veya diğer mekanizmaların kullanılması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
