---
title: Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 59f18d8487deb52f5ecb5b5c814ec9bdbc74e2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496386"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma
Geliştirme ve Internet Information Services (IIS) barındırılan bir Windows Communication Foundation (WCF) hizmetini dağıtma, aşağıdaki görevleri içerir:  
  
-   IIS, ASP.NET, WCF ve WCF etkinleştirme bileşeni düzgün yüklü ve kayıtlı olan emin olun.  
  
-   Yeni bir IIS uygulaması oluşturun veya varolan bir yeniden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
-   WCF hizmeti için .svc dosyası oluşturun.  
  
-   Hizmet uygulaması için IIS uygulama dağıtın.  
  
-   WCF hizmetini yapılandırın.  
  
 IIS barındırılan bir WCF hizmeti oluşturma ayrıntılı bilgi için bkz [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS, ASP.NET ve WCF doğru olduğundan emin olun yüklü ve kayıtlı  
 IIS barındırılan WCF hizmetleri düzgün çalışması, WCF, IIS ve ASP.NET yüklü olmalıdır. WCF yüklemek için yordamları (bir parçası olarak [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), ASP.NET ve IIS kullanılan işletim sistemi sürümüne bağlı olarak farklılık gösterir. WCF yükleme hakkında daha fazla bilgi için ve [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], bkz: [Microsoft .NET Framework 4 Web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=201185). IIS yüklemek için yönergeleri bulunabilir [IIS yükleme](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Yükleme işlemi [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] IIS makinede zaten varsa WCF IIS ile otomatik olarak kaydeder. Sonra IIS yüklü değilse [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], WCF IIS ile kaydetmek için ek bir adım gereklidir ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Aşağıdaki gibi işletim sistemine bağlı olarak bunu yapabilirsiniz:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7 ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: kullanmak [ServiceModel Kayıt Aracı (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) aracı WCF IIS ile kaydetmek için: Bu aracı kullanmak için şunu yazın **ServiceModelReg.exe /i /x** Visual Studio'da Komut İstemi. Bu komut istemi Başlat düğmesine tıkladığınızda, seçerek açabilirsiniz **tüm programlar**, **Microsoft Visual Studio 2012**, **Visual Studio Araçları**, ve  **Visual Studio komut istemi**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Windows Communication Foundation etkinleştirme bileşenleri alt bileşeni yüklemek [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Bu, Denetim Masası'nda yapmak için **Program Ekle veya Kaldır** ve ardından **Ekle\/Windows bileşenleri Kaldır**. Bu etkinleştirir **Windows Bileşen Sihirbazı**.  
  
-   Windows 7:  
  
 Son olarak ASP.NET, .NET Framework sürüm 4 kullanmak için yapılandırıldığını doğrulamanız gerekir. – İ ASPNET_Regiis Aracı'nı çalıştırarak bunu seçeneği. Daha fazla bilgi için bkz: [ASP.NET IIS Kayıt Aracı](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Yeni bir IIS uygulama oluşturmak veya mevcut bir ASP.NET uygulamasını kullanın  
 IIS barındırılan WCF hizmetleri bir IIS uygulamasının içinde bulunmalıdır. Yeni bir IIS uygulama WCF hizmetlerini barındırmak için özel olarak oluşturabilirsiniz. Alternatif olarak, bir WCF hizmeti zaten barındırma mevcut bir uygulamasına dağıtabilirsiniz [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] içerik (örneğin, .aspx sayfaları ve ASP.NET Web Hizmetleri [ASMX]). Bu seçenekler hakkında daha fazla bilgi için bkz: "barındırma WCF yan yana ASP.NET ile" ve "ASP.NET uyumluluk modunda barındırma WCF hizmetleri" bölümler [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Unutmayın [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ve sonraki sürümleri düzenli aralıklarla yalıtılmış bir nesne odaklı programlama uygulamayı yeniden başlatın. Varsayılan değer 1740 dakikadır. Desteklenen en yüksek değer 71,582 dakikadır. Bu yeniden başlatma devre dışı bırakılabilir. Bu özellik hakkında daha fazla bilgi için bkz: [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Bir .svc dosyası için WCF hizmeti oluşturma  
 IIS barındırılan WCF hizmetleri özel içerik dosyalarını (.svc dosyalarını) IIS uygulama olarak temsil edilir. Bu model, ASMX sayfaları içinde bir IIS uygulama .asmx dosyalarını olarak temsil edilir şekilde benzerdir. WCF özel işleme yönergesi .svc dosyasını içeren ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) barındırılan hizmetler gelen iletilere yanıt olarak etkinleştirmek altyapı barındırma WCF sağlar. En yaygın sözdizimi .svc dosyası için aşağıdaki deyimi şeklindedir.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Oluşur [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ve tek bir öznitelik `Service`. Değeri `Service` özniteliktir hizmet uygulaması ortak dil çalışma zamanı (CLR) türünün adı. Bu yönerge kullanarak, aşağıdaki kodu kullanarak hizmet ana bilgisayarını oluşturmak için temel olarak eşdeğerdir.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Hizmet için temel adres listesi oluşturma gibi ek barındırma yapılandırma de yapılabilir. Özel bir de kullanabilirsiniz <xref:System.ServiceModel.Activation.ServiceHostFactory> yönergesi barındırma özel çözümler ile kullanılmak üzere genişletmek için. WCF hizmetleri barındıran IIS uygulamaları oluşturulmasını ve yaşam süresini yönetmekten sorumlu olmayan <xref:System.ServiceModel.ServiceHost> örnekleri. Gerekli yönetilen WCF barındırma altyapıyı oluşturur <xref:System.ServiceModel.ServiceHost> .svc dosya için yapılan ilk istek alındığında dinamik olarak örneği. Ya da açıkça kod veya uygulamanın ne zaman dönüştürülmeden kapatılana kadar örnek serbest bırakılmaz.  
  
 .Svc dosyalarını sözdizimi hakkında daha fazla bilgi için bkz: [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Hizmet uygulaması için IIS uygulama dağıtma  
 IIS barındırılan WCF hizmetleri aynı dinamik derleme model olarak kullanmak [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. İle olarak yalnızca [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], IIS barındırılan WCF hizmetleri çeşitli konumlara çeşitli şekillerde uygulama kodunu gibi dağıtın:  
  
-   Genel Derleme Önbelleği (GAC) veya uygulamanın \bin dizinine önceden derlenmiş .dll dosyasını yer gibi. Sınıf kitaplığı yeni bir sürümü dağıtılana kadar önceden derlenmiş ikili dosyaları güncelleştirilmez.  
  
-   Uygulamanın \App_Code dizininde derlenmemiş kaynak dosyaları gibi. Bu dizinde bulunan kaynak dosyaları uygulamanın ilk isteği işleme sırasında dinamik olarak gereklidir. Herhangi bir değişiklik \App_Code dizindeki dosyaların silinmesini ve bir sonraki istekte alındığında yeniden derlenmesi tüm uygulama neden.  
  
-   Doğrudan .svc dosyasında derlenmemiş kod yerleştirilmiş olarak. Uygulama kodu da olabilir hizmetin .svc dosyasında bulunan satır içi sonra @ServiceHost yönergesi. Satır içi kod yapılan değişikliklerin geri dönüşüm ve bir sonraki istekte alındığında yeniden derlenmesi uygulamanın neden.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] derleme modeli bkz [ASP.NET derleme genel bakış](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>WCF hizmetini yapılandırma  
 IIS barındırılan WCF hizmetleri uygulamaları Web.config dosyasında yapılandırmalarını depolar. IIS barındırılan hizmetleri dışında IIS barındırılan WCF hizmetleri olarak aynı yapılandırma öğeleri ve sözdizimini kullanın. Ancak, aşağıdaki kısıtlamalar IIS barındırma ortamı benzersiz şunlardır:  
  
-   IIS barındırılan hizmetler için temel adres.  
  
-   IIS dışında barındırma WCF hizmetlerini barındırmak temel bir dizi geçirerek services temel adresini denetleyebilir uygulamalar için URI adresi <xref:System.ServiceModel.ServiceHost> Oluşturucusu veya sağlayarak bir [ \<ana bilgisayar >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) öğesinde hizmet yapılandırmasının. IIS barındırılan hizmetleri, kendi taban adresi denetleme olanağı yoktur; IIS barındırılan hizmetin taban adresi .svc dosya adresidir.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS barındırılan hizmetleri için uç nokta adresleri  
 IIS içinde barındırıldığında, uç nokta adresleri her zaman hizmeti temsil .svc dosya adres göreli olarak kabul edilir. Örneğin, bir WCF Hizmeti temel adresi ise http://localhost/Application1/MyService.svc şu uç nokta yapılandırması ile.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Bu, üzerinde erişilebilir bir uç nokta sağlar "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Göreli adresi en erişilebilir bir uç nokta sağladığından, boş bir dizeyi kullanan benzer şekilde, uç nokta yapılandırma öğesi http://localhost/Application1/MyService.svc, taban adresi değil.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Ayrıca, IIS tarafından barındırılan hizmet uç noktaları için her zaman göreli uç nokta adresleri kullanmanız gerekir. Tam uç noktası adresi (örneğin, http://localhost/MyService.svc) uç nokta adresi IIS bitiş noktası gösterme hizmeti barındıran uygulamasını işaret etmiyorsa biri hizmet dağıtımı hatalara yol açabilir. Barındırılan hizmetleri göreli uç nokta adresleri kullanarak, bu olası çakışmaları ortadan kaldırır.  
  
### <a name="available-transports"></a>Kullanılabilir taşımalar  
 IIS 5.1, barındırılan WCF hizmetleri ve [!INCLUDE[iis601](../../../../includes/iis601-md.md)] HTTP tabanlı iletişim kullanmak için kısıtlanır. Bu IIS platformlarda HTTP olmayan bağlama kullanmak için bir barındırılan hizmet yapılandırma hatayla hizmeti etkinleştirme sırasında sonuçlanır. İçin [!INCLUDE[iisver](../../../../includes/iisver-md.md)], desteklenen aktarmalar HTTP Net.TCP, Net.Pipe, Net.MSMQ ve msmq.formatname için geriye doğru uyumluluk mevcut MSMQ uygulamalarla yer alır.  
  
### <a name="http-transport-security"></a>HTTP Taşıma Güvenliği  
 IIS barındırılan WCF hizmetleri HTTP kullanmak yapabilir hizmeti içeren IIS sanal dizininde olanlar desteklediği sürece aktarım güvenliği (örneğin, HTTPS ve HTTP kimlik doğrulama şemasını temel, Özet ve Windows tümleşik kimlik doğrulaması gibi) Ayarlar. HTTP taşıma güvenliği ayarları üzerinde barındırılan bir uç noktanın bağlama taşıma güvenlik ayarları içerdiği IIS sanal dizininde eşleşmelidir.  
  
 Örneğin, HTTP digest kimlik doğrulaması kullanmak üzere yapılandırılmış bir WCF uç noktası, aynı zamanda HTTP digest kimlik doğrulaması izin vermek için yapılandırılmış bir IIS sanal dizininde bulunması gerekir. IIS ve WCF Bitiş noktası ayarlarını eşleşmeyen birleşimlerini hizmeti etkinleştirme sırasında hataya neden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Services'te Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
