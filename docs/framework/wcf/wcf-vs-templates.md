---
title: WCF Visual Studio Şablonları
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 6c37974f93f10870b238617bc196b37c6dbb6dd5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio Şablonları
Windows Communication Foundation (WCF) Visual Studio şablonları önceden tanımlanmış proje ve öğe şablonlarını Visual Studio'da WCF hizmetleri ve çevresindeki uygulamaları hızlı bir şekilde oluşturmak için kullanabileceğiniz ' dir.  
  
## <a name="using-the-wcf-templates"></a>WCF şablonlarını kullanma  
 WCF Visual Studio şablonları, hizmet geliştirme için bir temel sınıf yapısı sağlar. Özellikle, bu şablonları, hizmet sözleşmesi, veri sözleşmesi, hizmet uygulaması ve yapılandırma için temel tanımları sağlar. Bu şablonlar, çok az kod etkileşim gibi daha gelişmiş Hizmetleri için bir yapı bloğu ile basit bir hizmet oluşturmak için kullanabilirsiniz.  
  
### <a name="wcf-service-library-project-template"></a>WCF hizmet kitaplığı proje şablonu  
 Yeni Proje iletişim kutusu altında WCF Hizmeti kitaplığı proje şablonu kullanılabilir **Visual C# \WCF** ve **Visual Basic\WCF**.  
  
 Kullanarak yeni bir proje oluşturduğunuzda **WCF Hizmeti** şablonu, yeni proje otomatik olarak aşağıdaki üç dosyaları içerir:  
  
-   Hizmet sözleşmesi dosyası (IService1.cs veya IService1.vb). Hizmet sözleşmesi dosyası uygulanan WCF Hizmeti özniteliklere sahip bir arabirimdir. Bu dosya hizmetlerinizi tanımlamak nasıl göstermek için basit bir hizmet tanımını sağlar ve parametre tabanlı işlemler ve basit veri sözleşmesi örnek içerir. Bu, bir WCF Hizmeti projesi oluşturduktan sonra Kod Düzenleyicisi'nde görüntülenen varsayılan dosyasıdır.  
  
-   Hizmet uygulama dosyasını (service1.cs dosyasını veya Service1.vb). Hizmet uygulama dosyasını hizmet sözleşmesi dosyasında tanımlanan sözleşme uygular.  
  
-   Uygulama yapılandırma dosyasına (App.config). Yapılandırma dosyası bir WCF Hizmeti modeli temel öğelerini Güvenli HTTP bağlama ile sağlar. Ayrıca, hizmet için bir uç nokta içerir ve meta veri değişimi sağlar.  
  
> [!NOTE]
>  Visual Studio projesi için yapılandırma dosyası olarak App.config dosyasını kullanarak çalıştırıldığında tanımaya yapılandırılmış [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), varsayılan yapılandırmadır. Yürütülebilir bir dosya hizmeti kitaplıkta barındırıyorsanız, yapılandırma dosyalarını DLL'ler için geçerli olmadığından, yapılandırma kodu yürütülebilir yapılandırma dosyasına taşıyın gerekir.  
  
### <a name="wcf-service-application-template"></a>WCF hizmet uygulama şablonu  
 Yeni Proje iletişim kutusunun altında WCF Hizmeti Uygulaması şablonu kullanılabilir **Visual C# \WCF** ve **Visual Basic\WCF**.  
  
 Kullanarak yeni bir proje oluşturduğunuzda **WCF Web uygulaması hizmeti** şablonu, proje aşağıdaki dört dosyaları içerir:  
  
-   Hizmet ana bilgisayar dosyası (service1.svc).  
  
-   Hizmet sözleşmesi dosyası (IService1.cs veya IService1.vb).  
  
-   Hizmet uygulama dosyasını (Service1.svc.cs veya Service1.svc.vb).  
  
-   Web yapılandırma dosyasında (Web.config).  
  
 Şablon otomatik olarak (bir sanal dizin ile dağıtılması için) bir Web sitesi oluşturur ve bir hizmeti barındırır.  
  
### <a name="wcf-web-site-template"></a>WCF Web sitesi şablonu  
 Yeni Proje iletişim kutusunun altında WCF Web sitesi şablonu kullanılabilir **Visual C# \Web Site\WCF hizmet** ve **Visual Basic\Web Site\WCF hizmet**. Bu WCF hizmeti uygulaması şablon olarak aynı dosyaları oluşturur ama bir ASP.NET web sitesi değilmiş gibi düzenler. App_Code ve App_Data klasör oluşturulur.  
  
### <a name="wcf-service-item-template"></a>WCF hizmet öğesi şablonu  
 WCF hizmet öğesi, WCF hizmetlerini var olan Visual Studio projelerinizi eklemek için bir hızlı yol sağlayan özel bir şablon şablonudur.  
  
 Bu şablonu kullanmak için Git **Çözüm Gezgini** bölmesinde, proje adına sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe** başlatmak için **yeni Ekle Öğe** iletişim kutusu.  
  
 Hizmet arabirimi ve uygulama dosyalarını kök proje klasöründe yer alır.  
  
 Uyumlu türleri olan şablon var olan yapılandırma dosyasının yeni hizmet yapılandırma bölümünü birleştirme çalışır.  
  
 Var olan bir Web projesi projesiyse hizmet ana bilgisayar dosyası (service1.svc) da oluşturulur.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF hizmet proje ve öğe şablonu.  
 Bu şablonlar gibi bir web hizmeti erişilebilen bir iş akışı olduğu WCF hizmetleri barındıran bir iş akışı hizmeti oluşturun. Ayrı şablonları XAML veya kesinlik temelli programlama modelleri için mevcut. Şablonları kullanarak sıralı ya da Durum makinesi iş akışı oluşturabilirsiniz. Bu tür bir iş akışı hakkında daha fazla bilgi için bkz: [Windows Workflow Foundation öğreticileri](http://msdn.microsoft.com/library/e9705654-bd96-4b56-8d98-f1f118112d97). İş akışı projeleri oluşturma hakkında daha fazla bilgi için bkz: [eski iş akışı projeleri oluşturma](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 İş akışları kullanılan XOML türü yerine kodunu olanları temel visual Studio tasarımcısı daha iyi yanıt. XOML iş akışı oluşturulması için varsayılan iş akışı türüdür.  
  
### <a name="wcf-syndication-service-library-template"></a>WCF dağıtım hizmet kitaplığı şablonu  
 Bu şablon, bir WCF Hizmeti RSS veya ATOM biçimindeki akışınıza kullanıma olanak sağlar. Daha fazla bilgi için bkz: [WCF dağıtımı](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Akış adresini değiştirme  
 Dağıtım şablonu, Internet Explorer yürütme sırasında kullanır. Projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hata ayıklama** sekmesine tıkladığınızda, varsayılan adres görebilirsiniz Şablon. Internet Explorer bu adresinde akış açmaya çalışır.  
  
 Akışınıza adresini değiştirirseniz, adres, aynı zamanda değiştirmeniz gerekir **hata ayıklama** sekmesi. Bunu yaparsanız, Internet Explorer varsayılan adresindeki akış açın ve başarısız dener.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>WCF hizmet öğesi şablonu AJAX etkin  
 Bu şablon bir AJAX denetim bir WCF hizmeti olarak kullanıma sunar. AJAX denetimleri hakkında daha fazla bilgi için bkz: [AJAX denetim belgelerine](http://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Silverlight etkin bir WCF Hizmeti öğe şablonu  
 Bu şablon, Silverlight istemci veya ön uç verileri sağlayan bir Web hizmeti oluşturur. Şablon servis kodu ve Silverlight istemci ile iletişim kurmasını desteği yapılandırma içeren bir WCF hizmeti oluşturmak için bir Web sitesi veya Web uygulaması projesi eklenebilir. Daha sonra **hizmet Başvurusu Ekle** istemci proxy hizmetinin istemciye eklemek ve Silverlight istemcisini Silverlight etkin bir WCF hizmeti arasında veri değişimi için.  
  
 Bu şablon erişmek için bir Web sitesi veya Web uygulaması projesi sağ tıklatın **Çözüm Gezgini**, tıklatın **Yeni Öğe Ekle**, tıklatıp **Silverlight özellikli WCF Hizmeti**.  
  
> [!NOTE]
>  Silverlight özellikli WCF hizmeti sunan bir `basicHttpBinding` güvenlik ayarlarını etkinleştirmeden uç noktası. Bu nedenle, bu hizmete bağlanan tüm istemciler tarafından hizmeti hakkında bilgi alınamıyor. Hizmet ve istemci arasında alınıp iletileri imzalanmış veya şifrelenmiş de güncelleştirilmez. Uç nokta güvenliğini düzgün şekilde sağlamak için ASP.NET kimlik doğrulaması, HTTPS veya diğer mekanizmaları kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
