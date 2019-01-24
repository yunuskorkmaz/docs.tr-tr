---
title: WCF Visual Studio Şablonları
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: a7529b14c3c83f0df7b41581ef18e5192209bc5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624944"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio Şablonları
Windows Communication Foundation (WCF) Visual Studio önceden tanımlanmış proje ve öğe şablonlarını Visual Studio'da WCF hizmetleri ve kapsayıcı uygulamaları hızlıca oluşturmak için kullanabileceğiniz şablonlardır.  
  
## <a name="using-the-wcf-templates"></a>WCF şablonlarını kullanma  
 WCF Visual Studio şablonları, hizmet geliştirme için bir temel sınıf yapısı sağlar. Özellikle, bu şablonları, hizmet sözleşmesi, veri sözleşmesi, hizmet uygulaması ve yapılandırma için temel tanımları sağlar. Daha gelişmiş hizmetler için bir yapı taşı yanı sıra, çok az kod etkileşimi ile basit bir hizmet oluşturmak için bu şablonları kullanabilirsiniz.  
  
### <a name="wcf-service-library-project-template"></a>WCF hizmet kitaplığı proje şablonu  
 Yeni Proje iletişim kutusu altında WCF hizmet kitaplığı proje şablonu kullanılabilir **Visual C# \WCF** ve **Visual Basic\WCF**.  
  
 Kullanarak yeni bir proje oluşturduğunuzda **WCF Hizmeti** yeni proje şablonu, aşağıdaki üç dosyayı otomatik olarak içerir:  
  
-   Hizmet sözleşme dosyası (Iservice1.cs veya Iservice1.vb). Hizmet sözleşme dosyası uygulanan WCF Hizmeti özniteliklere sahip bir arayüzdür. Bu dosya, hizmetlerinizi tanımlama göstermek için basit bir hizmet tanımının sağlar ve parametre tabanlı işlemler ve basit veri sözleşme örneği içerir. Bu, bir WCF Hizmeti projesini oluşturduktan sonra Kod Düzenleyicisi'nde görüntülenen varsayılan dosyasıdır.  
  
-   Hizmet uygulama dosyasını (Service1.cs veya gt;service1.vb). Hizmet uygulama dosyasını hizmet sözleşme dosyasında tanımlanan sözleşme uygular.  
  
-   Uygulama yapılandırma dosyasına (App.config). Yapılandırma dosyasını güvenli bir HTTP bağlaması ile temel bir WCF service model öğelerini sağlar. Ayrıca, hizmet için bir uç noktası içerir ve meta veri değişimi sağlar.  
  
> [!NOTE]
>  Visual Studio projesi için yapılandırma dosyası App.config dosyasını kullanarak çalıştırıldığında tanımak için yapılandırılmış [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), varsayılan yapılandırmayı olduğu. Bir yürütülebilir dosya hizmeti kitaplıkta barındırıyorsanız, DLL'ler için yapılandırma dosyalarını geçerli olmadığından yapılandırma kodu yürütülebilir yapılandırma dosyasına taşımak zorunda.  
  
### <a name="wcf-service-application-template"></a>WCF Hizmeti Uygulaması şablonu  
 Yeni Proje iletişim kutusunun altında WCF Hizmeti Uygulaması şablonu kullanılabilir **Visual C# \WCF** ve **Visual Basic\WCF**.  
  
 Kullanarak yeni bir proje oluşturduğunuzda **WCF Web uygulaması hizmeti** şablon, proje aşağıdaki dört dosyaları içerir:  
  
-   Hizmet ana bilgisayar dosyası (service1.svc'yi).  
  
-   Hizmet sözleşme dosyası (Iservice1.cs veya Iservice1.vb).  
  
-   Hizmet uygulama dosyasını (gt;service1.svc.cs veya Service1.svc.vb).  
  
-   Web yapılandırma dosyası (Web.config).  
  
 Şablon, otomatik olarak (bir sanal dizin ile dağıtılması için) bir Web sitesi oluşturur ve bir hizmette barındırır.  
  
### <a name="wcf-web-site-template"></a>WCF Web Site şablonu  
 Yeni Proje iletişim kutusunun altında WCF Web Site şablonunu kullanılabilir **Visual C# \Web Site\WCF hizmet** ve **Visual Basic\Web Site\WCF hizmeti**. Bu işlem, WCF Hizmeti Uygulaması şablonu ile aynı dosyaları oluşturur ancak bir ASP.NET web sitesi gibi göre düzenler. App_Code ve App_Data klasörünün oluşturulur.  
  
### <a name="wcf-service-item-template"></a>WCF hizmet öğe şablonu  
 WCF hizmet öğe şablonu mevcut Visual Studio projelerine WCF hizmetleri eklemek için hızlı bir yolunu sağlayan özel bir şablonudur.  
  
 Bu şablonu kullanmak için Git **Çözüm Gezgini** bölmesinde, projenizin adına sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe** başlatmak için **yeni Ekle Öğe** iletişim kutusu.  
  
 Hizmet arabirimi ve uygulama dosyalarının kök proje klasöründe yer alır.  
  
 Uyumlu türlerde olmaları durumunda şablon var olan bir yapılandırma dosyasının yeni hizmetinin yapılandırma bölümü birleştirmeye çalışıyor.  
  
 Bir Web projesi var olan proje ise bir hizmet ana bilgisayar dosyası (service1.svc'yi) da oluşturulur.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF hizmeti proje ve öğe şablonu.  
 Bu şablonlar, olduğu gibi bir web hizmeti erişilebilir bir iş akışı, bir iş akışı hizmeti barındıran WCF hizmetleri oluşturun. Ayrı şablonlar, XAML veya zorunlu programlama modelleri için mevcut. Şablonları kullanarak, sıralı veya Durum makinesi iş akışı oluşturabilirsiniz. Bu tür bir iş akışı hakkında daha fazla bilgi için bkz. [Windows Workflow Foundation öğreticiler](https://msdn.microsoft.com/library/e9705654-bd96-4b56-8d98-f1f118112d97). İş akışı projeleri oluşturma hakkında daha fazla bilgi için bkz. [eski iş akışı projeleri oluşturma](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 İş akışları kullanılan XOML türü yerine kodunu olanları temel visual Studio tasarımcısı daha değişkendir. XOML, oluşturulacak varsayılan iş akışı türü akışıdır.  
  
### <a name="wcf-syndication-service-library-template"></a>WCF dağıtım hizmet kitaplığı şablonu  
 Bu şablon akışınızı RSS veya ATOM biçimindeki bir WCF hizmeti olarak kullanıma sunmanıza olanak sağlar. Daha fazla bilgi için [WCF dağıtımı](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Akış adresini değiştirme  
 Dağıtım şablonu yürütme sırasında Internet Explorer'ı kullanır. Projenize sağ tıkladığınızda **Çözüm Gezgini** Visual Studio'da **özellikleri**, ardından **hata ayıklama** sekmesine tıkladığınızda varsayılan adresini görebilirsiniz şablonu. Internet Explorer, bu adresteki akış açmayı dener.  
  
 Akışınızı adresini değiştirirseniz, adres, ayrıca değiştirmeli **hata ayıklama** sekmesi. Bunu yaparsanız, Internet Explorer Akış varsayılan adresinde açın ve başarısız dener.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>AJAX etkin WCF Hizmeti öğe şablonu  
 Bu şablon bir AJAX denetimi bir WCF hizmeti olarak kullanıma sunar. AJAX denetimleri hakkında daha fazla bilgi için bkz. [AJAX denetim belgeleri](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Silverlight etkinleştirilmiş WCF Hizmeti öğe şablonu  
 Bu şablonu kullanarak bir Silverlight istemcisi veya ön uç verileri sağlayan bir Web hizmeti oluşturur. Hizmet kodu ve bir Silverlight istemcisi ile iletişim kurmasını destekleyen yapılandırması içeren bir WCF hizmeti oluşturmak için bir Web sitesi veya Web uygulaması projesi şablonu eklenebilir. Ardından **hizmet Başvurusu Ekle** istemciye bir hizmetin istemci proxy ekleyin ve Silverlight istemcisini Silverlight etkinleştirilmiş WCF hizmeti arasında veri değişimi.  
  
 Bu şablon erişmek için bir Web sitesi veya Web uygulama projesinde sağ **Çözüm Gezgini**, tıklayın **yeni bir öğe eklemek**, tıklatıp **Silverlight özellikli bir WCF Hizmeti**.  
  
> [!NOTE]
>  Silverlight özellikli bir WCF hizmeti sunan bir `basicHttpBinding` güvenlik ayarlarını etkinleştirmeden uç noktası. Bu nedenle, hizmeti hakkında bilgi için bu hizmeti bağlanan tüm istemciler tarafından alınabilir. Hizmet ve istemci arasında alınıp verilen iletileri imzalanmış veya şifrelenmiş da güncelleştirilmez. Uç nokta düzgün güvenliğini sağlamak için ASP.NET kimlik doğrulaması, HTTPS veya başka mekanizmalar kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
