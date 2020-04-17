---
title: WCF Visual Studio Şablonları
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 13183ad5f05350c34eebd025eca3faa7d97644f8
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608029"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio Şablonları
Windows Communication Foundation (WCF) Visual Studio şablonları, Visual Studio'da WCF hizmetlerini ve çevresindeki uygulamaları hızla oluşturmak için kullanabileceğiniz önceden tanımlanmış proje ve öğe şablonlarıdır.  
  
## <a name="using-the-wcf-templates"></a>WCF Şablonlarını Kullanma  
 WCF Visual Studio şablonları, hizmet geliştirme için temel bir sınıf yapısı sağlar. Özellikle, bu şablonlar hizmet sözleşmesi, veri sözleşmesi, hizmet uygulaması ve yapılandırma için temel tanımları sağlar. Bu şablonları, en az kod etkileşimi içeren basit bir hizmetin yanı sıra daha gelişmiş hizmetler için bir yapı taşı oluşturmak için kullanabilirsiniz.  
  
### <a name="wcf-service-library-project-template"></a>WCF Hizmet Kütüphanesi Proje Şablonu  
 WCF Hizmet Kitaplığı proje şablonu **Visual C#\WCF** ve **Visual Basic\WCF**altındaki yeni proje iletişim kutusunda kullanılabilir.  
  
 **WCF Hizmeti** şablonu kullanarak yeni bir proje oluşturduğunuzda, yeni proje otomatik olarak aşağıdaki üç dosyayı içerir:  
  
- Hizmet sözleşmesi dosyası (IService1.cs veya IService1.vb). Hizmet sözleşmesi dosyası, WCF hizmet öznitelikleriuygulanan bir arabirimdir. Bu dosya, hizmetlerinizi nasıl tanımlayabileceğinizi göstermek için basit bir hizmetin tanımını sağlar ve parametre tabanlı işlemler ve basit bir veri sözleşmesi örneği içerir. Bu, bir WCF hizmet projesi oluşturduktan sonra kod düzenleyicisinde görüntülenen varsayılan dosyadır.  
  
- Hizmet uygulama dosyası (Service1.cs veya Service1.vb). Hizmet uygulama dosyası, hizmet sözleşmesi dosyasında tanımlanan sözleşmeyi uygular.  
  
- Uygulama yapılandırma dosyası (App.config). Yapılandırma dosyası, güvenli bir HTTP bağlama ile bir WCF hizmet modelinin temel öğelerini sağlar. Ayrıca hizmet için bir bitiş noktası içerir ve meta veri alışverişini sağlar.  
  
> [!NOTE]
> Visual Studio, varsayılan yapılandırma olan [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)kullanılarak çalıştırıldığında App.config dosyasını proje için yapılandırma dosyası olarak tanıyacak şekilde yapılandırılmıştır. Hizmet kitaplığını yürütülebilir bir şekilde barındırıyorsanız, DL'ler için yapılandırma dosyaları geçerli olmadığı için yapılandırma kodunu yürütülebilir yapılandırma dosyasına taşımanız gerekir.  
  
### <a name="wcf-service-application-template"></a>WCF Hizmet Uygulama Şablonu  
 WCF Hizmet Uygulaması şablonu **Visual C#\WCF** ve **Visual Basic\WCF**altında Yeni Proje iletişim kutusunda kullanılabilir.  
  
 **WCF Web Uygulama Hizmeti** şablonu kullanarak yeni bir proje oluşturduğunuzda, proje aşağıdaki dört dosyayı içerir:  
  
- Servis ana bilgisayar dosyası (service1.svc).  
  
- Hizmet sözleşmesi dosyası (IService1.cs veya IService1.vb).  
  
- Hizmet uygulama dosyası (Service1.svc.cs veya Service1.svc.vb).  
  
- Web yapılandırma dosyası (Web.config).  
  
 Şablon otomatik olarak bir Web sitesi oluşturur (sanal bir dizine dağıtılacak) ve içinde bir hizmet barındırAn.  
  
### <a name="wcf-web-site-template"></a>WCF Web Sitesi Şablonu  
 WCF Web Sitesi şablonu **Visual C#\Web Sitesi\WCF Hizmeti** ve **Visual Basic\WCF Hizmeti**altında Yeni Proje iletişim kutusunda kullanılabilir. Bu, WCF Hizmet Uygulaması şablonuyla aynı dosyaları oluşturur, ancak ASP.NET bir web sitesi gibi düzenler. App_Code ve App_Data klasörleri oluşturulur.  
  
### <a name="wcf-service-item-template"></a>WCF Hizmet Öğesi Şablonu  
 WCF Hizmet Öğesi şablonu, mevcut Visual Studio projelerinize WCF hizmetleri eklemek için hızlı bir yol sağlayan özel bir şablondur.  
  
 Bu şablonu kullanmak için **Çözüm Gezgini** bölmesine gidin, proje adınızı sağ tıklatın, **Ekle'ye**işaret edin ve yeni **öğe ekle** iletişim kutusunu başlatmak için Yeni **Öğe'yi** tıklatın.  
  
 Hizmet arabirimi ve uygulama dosyaları kök proje klasörüne yerleştirilir.  
  
 Şablon, uyumlu türler varsa, yeni hizmetin yapılandırma bölümünü varolan yapılandırma dosyasıyla birleştirmeyi dener.  
  
 Varolan proje bir Web projesiyse, bir hizmet ana bilgisayar dosyası (service1.svc) de oluşturulur.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF Hizmet Projesi ve Madde Şablonu.  
 Bu şablonlar, bir web hizmeti gibi erişilebilen bir iş akışı olan bir İş Akışı Hizmeti barındıran WCF hizmetleri oluşturur. XAML veya zorunlu programlama modelleri için ayrı şablonlar vardır. Şablonları kullanarak, sıralı veya durum makine iş akışı oluşturabilirsiniz. Bu iş akışı türleri hakkında daha fazla bilgi için [bkz.](../windows-workflow-foundation/how-to-create-a-workflow.md) İş akışı projeleri oluşturma hakkında daha fazla bilgi için [bkz.](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)  
  
 Visual Studio tasarımcısı, kod tabanlı akışlar yerine XOML türü iş akışları kullanıldığında daha duyarlıdır. XOML iş akışı oluşturulacak varsayılan iş akışı türüdür.  
  
### <a name="wcf-syndication-service-library-template"></a>WCF Sendikasyon Hizmeti Kitaplığı Şablonu  
 Bu şablon, özet akışınızı Bir WCF hizmeti olarak RSS veya ATOM biçiminde ortaya çıkarmanızı sağlar. Daha fazla bilgi için [WCF Sendikasyon'a](./feature-details/wcf-syndication.md)bakın.  
  
#### <a name="changing-the-address-of-the-feed"></a>Özet Akışının Adresini Değiştirme  
 Sendikasyon şablonu yürütme sırasında Internet Explorer kullanır. Visual Studio'da Solutions **Explorer'da** projenizi sağ tıklattığınızda, **Özellikler'i**seçin ve **hata ayıklama** sekmesini seçin ve şablonun varsayılan adresini görebilirsiniz. Internet Explorer bu adresteki akışı açmaya çalışır.  
  
 Özet akışınızın adresini değiştirirseniz, **Hata Ayıklama** sekmesindeki adresi de değiştirmeniz gerekir. Bunu yapmazsanız, Internet Explorer akışı varsayılan adreste açmaya çalışır ve başarısız olur.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>AJAX etkin WCF Hizmet Öğesi Şablonu  
 Bu şablon, Bir WCF hizmeti olarak bir AJAX denetimini ortaya çıkarır. AJAX denetimleri hakkında daha fazla bilgi için [AJAX kontrol belgelerine](/aspnet/ajax/)bakın.  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Silverlight özellikli WCF Hizmet Öğesi Şablonu  
 Bu şablon, Silverlight istemcisine veya ön uça veri sağlayan bir Web hizmeti oluşturur. Şablon, bir Silverlight istemcisi ile iletişimi destekleyen hizmet kodu ve yapılandırma içeren bir WCF hizmeti oluşturmak için bir Web sitesi veya Web uygulama projesine eklenebilir. Daha sonra hizmetin istemciye bir istemci proxy'si eklemek ve Silverlight istemcisi ile Silverlight özellikli WCF hizmeti arasında veri alışverişi yapmak için **Hizmet Başvurusu Ekle'yi** kullanabilirsiniz.  
  
 Bu şablona erişmek için **Çözüm Gezgini'nde**bir Web sitesi veya Web uygulama projesine sağ tıklayın , **yeni bir öğe ekle'yi**tıklatın ve **Silverlight özellikli WCF Hizmeti'ni**tıklatın.  
  
> [!NOTE]
> Silverlight özellikli WCF Hizmeti, `basicHttpBinding` herhangi bir güvenlik ayarını etkinleştirmeden bir bitiş noktası ortaya çıkarır. Bu nedenle, hizmet hakkında bilgi bu hizmete bağlanan tüm istemciler tarafından elde edilebilir. Hizmet ve istemci arasında değiş tokuş edilen iletiler de imzalanmaz veya şifrelenmez. Bitiş noktasını doğru şekilde sabitlemek için kimlik doğrulaması, HTTPS veya diğer mekanizmaları ASP.NET kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
