---
title: "Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b19e111e11097cbb4b4af60ae0b28956a4a381
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma
Geliştirme ve dağıtma bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Internet Information Services (IIS) barındırılan hizmeti, aşağıdaki görevleri içerir:  
  
-   Sağlamak bu IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] etkinleştirme bileşen doğru yüklendiğinden ve kayıtlı.  
  
-   Yeni bir IIS uygulaması oluşturun veya varolan bir yeniden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
-   İçin bir .svc dosyası oluşturmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
-   Hizmet uygulaması için IIS uygulama dağıtın.  
  
-   Yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Bir IIS tarafından barındırılan oluşturma ayrıntılı kılavuz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet için bkz: [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS, ASP.NET ve WCF doğru olduğundan emin olun yüklü ve kayıtlı  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], IIS ve ASP.NET yüklü olmalıdır için IIS tarafından barındırılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] düzgün çalışması için hizmetleri. Yükleme yordamlarına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (bir parçası olarak [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), ASP.NET ve IIS kullanılan işletim sistemi sürümüne bağlı olarak farklılık gösterir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Yükleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], bkz: [Microsoft .NET Framework 4 Web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=201185). IIS yüklemek için yönergeleri bulunabilir [IIS yükleme](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Yükleme işlemi [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] otomatik olarak kaydeder [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS makinede zaten varsa, IIS ile. Sonra IIS yüklü değilse [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ek bir adım kaydetmek için gerekli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS ile ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Aşağıdaki gibi işletim sistemine bağlı olarak bunu yapabilirsiniz:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7 ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: kullanmak [ServiceModel Kayıt Aracı (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) kaydetmek için aracı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS ile: Bu aracı kullanmak için yazın **ServiceModelReg.exe /i /x** içinde Visual Studio komut istemi. Bu komut istemi Başlat düğmesine tıkladığınızda, seçerek açabilirsiniz **tüm programlar**, **Microsoft Visual Studio 2012**, **Visual Studio Araçları**, ve  **Visual Studio komut istemi**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Windows Communication Foundation etkinleştirme bileşenleri alt bileşeni yüklemek [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Bu, Denetim Masası'nda yapmak için **Program Ekle veya Kaldır** ve ardından **Ekle\/Windows bileşenleri Kaldır**. Bu etkinleştirir **Windows Bileşen Sihirbazı**.  
  
-   Windows 7:  
  
 Son olarak ASP.NET, .NET Framework sürüm 4 kullanmak için yapılandırıldığını doğrulamanız gerekir. – İ ASPNET_Regiis Aracı'nı çalıştırarak bunu seçeneği. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ASP.NET IIS Kayıt Aracı](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Yeni bir IIS uygulama oluşturmak veya mevcut bir ASP.NET uygulamasını kullanın  
 IIS barındırılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, bir IIS uygulamasının içinde bulunmalıdır. Ana bilgisayar için yeni bir IIS uygulama oluşturabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel olarak Hizmetleri. Alternatif olarak, dağıtabileceğiniz bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mevcut uygulamaya zaten barındırma hizmet [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] içerik (örneğin, .aspx sayfaları ve ASP.NET Web Hizmetleri [ASMX]). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz. Bu seçenekleri "barındırma WCF yan yana ASP.NET ile" ve "Barındırma WCF hizmetleri, ASP.NET uyumluluk modu" bölümlerde [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Unutmayın [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ve sonraki sürümleri düzenli aralıklarla yalıtılmış bir nesne odaklı programlama uygulamayı yeniden başlatın. Varsayılan değer 1740 dakikadır. Desteklenen en yüksek değer 71,582 dakikadır. Bu yeniden başlatma devre dışı bırakılabilir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu özellik, bkz: [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Bir .svc dosyası için WCF hizmeti oluşturma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS barındırılan hizmetleri özel içerik dosyalarını (.svc dosyalarını) IIS uygulama olarak temsil edilir. Bu model, ASMX sayfaları içinde bir IIS uygulama .asmx dosyalarını olarak temsil edilir şekilde benzerdir. .Svc dosyasını içeren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-özel işleme yönergesi ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) izin veren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] barındırılan hizmetler gelen iletilere yanıt olarak etkinleştirmek için barındırma altyapı. En yaygın sözdizimi .svc dosyası için aşağıdaki deyimi şeklindedir.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Oluşur [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ve tek bir öznitelik `Service`. Değeri `Service` özniteliktir hizmet uygulaması ortak dil çalışma zamanı (CLR) türünün adı. Bu yönerge kullanarak, aşağıdaki kodu kullanarak hizmet ana bilgisayarını oluşturmak için temel olarak eşdeğerdir.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Hizmet için temel adres listesi oluşturma gibi ek barındırma yapılandırma de yapılabilir. Özel bir de kullanabilirsiniz <xref:System.ServiceModel.Activation.ServiceHostFactory> yönergesi barındırma özel çözümler ile kullanılmak üzere genişletmek için. Barındıran IIS uygulamalar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri oluşturulmasını ve yaşam süresini yönetmekten sorumlu olmayan <xref:System.ServiceModel.ServiceHost> örnekleri. Yönetilen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur gerekli altyapı barındırma <xref:System.ServiceModel.ServiceHost> .svc dosya için yapılan ilk istek alındığında dinamik olarak örneği. Ya da açıkça kod veya uygulamanın ne zaman dönüştürülmeden kapatılana kadar örnek serbest bırakılmaz.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)].svc dosyalarını sözdizimi bkz [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Hizmet uygulaması için IIS uygulama dağıtma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS barındırılan hizmetleri aynı dinamik derleme model olarak kullanmak [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. İle olarak yalnızca [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], uygulama kodunu dağıtabilirsiniz IIS tarafından barındırılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çeşitli konumlara çeşitli şekillerde gibi hizmetleri:  
  
-   Genel Derleme Önbelleği (GAC) veya uygulamanın \bin dizinine önceden derlenmiş .dll dosyasını yer gibi. Sınıf kitaplığı yeni bir sürümü dağıtılana kadar önceden derlenmiş ikili dosyaları güncelleştirilmez.  
  
-   Uygulamanın \App_Code dizininde derlenmemiş kaynak dosyaları gibi. Bu dizinde bulunan kaynak dosyaları uygulamanın ilk isteği işleme sırasında dinamik olarak gereklidir. Herhangi bir değişiklik \App_Code dizindeki dosyaların silinmesini ve bir sonraki istekte alındığında yeniden derlenmesi tüm uygulama neden.  
  
-   Doğrudan .svc dosyasında derlenmemiş kod yerleştirilmiş olarak. Uygulama kodu da olabilir hizmetin .svc dosyasında bulunan satır içi sonra @ServiceHost yönergesi. Satır içi kod yapılan değişikliklerin geri dönüşüm ve bir sonraki istekte alındığında yeniden derlenmesi uygulamanın neden.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] derleme modeli bkz [ASP.NET derleme genel bakış](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>WCF hizmetini yapılandırma  
 IIS barındırılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri uygulamaları Web.config dosyasında yapılandırmalarını depolar. IIS barındırılan hizmetleri kullanmak aynı yapılandırma öğeleri ve söz dizimine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS dışında barındırılan hizmetleri. Ancak, aşağıdaki kısıtlamalar IIS barındırma ortamı benzersiz şunlardır:  
  
-   IIS barındırılan hizmetler için temel adres.  
  
-   Barındırma uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS dışında hizmetlerini barındıran bir dizi temel adres için URI geçirerek services temel adresini denetleyebilir <xref:System.ServiceModel.ServiceHost> Oluşturucusu veya sağlayarak bir [ \<ana bilgisayar >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) hizmetin yapılandırma öğesi. IIS barındırılan hizmetleri, kendi taban adresi denetleme olanağı yoktur; IIS barındırılan hizmetin taban adresi .svc dosya adresidir.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS barındırılan hizmetleri için uç nokta adresleri  
 IIS içinde barındırıldığında, uç nokta adresleri her zaman hizmeti temsil .svc dosya adres göreli olarak kabul edilir. Örneğin, varsa taban adresini bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] http://localhost/Application1/MyService.svc şu uç nokta yapılandırması ile bir hizmettir.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Bu, "http://localhost/Application1/MyService.svc/anotherEndpoint" ulaşılabilen bir uç nokta sağlar.  
  
 Benzer şekilde, boş bir dize göreli adresini kullanan uç nokta yapılandırma öğesi bir uç nokta http://localhost/Application1/MyService.svc erişilebilir olan taban adresi sağlar.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Ayrıca, IIS tarafından barındırılan hizmet uç noktaları için her zaman göreli uç nokta adresleri kullanmanız gerekir. Uç nokta adresi IIS bitiş noktası gösterme hizmeti barındıran uygulamasını işaret etmiyorsa tam uç noktası adresi (örneğin, http://localhost/MyService.svc) biri hizmet dağıtımı hatalara yol açabilir. Barındırılan hizmetleri göreli uç nokta adresleri kullanarak, bu olası çakışmaları ortadan kaldırır.  
  
### <a name="available-transports"></a>Kullanılabilir taşımalar  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS 5.1, barındırılan hizmetleri ve [!INCLUDE[iis601](../../../../includes/iis601-md.md)] HTTP tabanlı iletişim kullanmak için kısıtlanır. Bu IIS platformlarda HTTP olmayan bağlama kullanmak için bir barındırılan hizmet yapılandırma hatayla hizmeti etkinleştirme sırasında sonuçlanır. İçin [!INCLUDE[iisver](../../../../includes/iisver-md.md)], desteklenen aktarmalar HTTP Net.TCP, Net.Pipe, Net.MSMQ ve msmq.formatname için geriye doğru uyumluluk mevcut MSMQ uygulamalarla yer alır.  
  
### <a name="http-transport-security"></a>HTTP Taşıma Güvenliği  
 IIS barındırılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri HTTP kullanan yapabilir hizmeti içeren IIS sanal dizininde desteklediği sürece aktarım güvenliği (örneğin, HTTPS ve HTTP kimlik doğrulama şemasını temel, Özet ve Windows tümleşik kimlik doğrulaması gibi) Bu ayarlar. HTTP taşıma güvenliği ayarları üzerinde barındırılan bir uç noktanın bağlama taşıma güvenlik ayarları içerdiği IIS sanal dizininde eşleşmelidir.  
  
 Örneğin, bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP digest kimlik doğrulaması kullanmak üzere yapılandırılmış uç noktası, HTTP digest kimlik doğrulaması izin vermek için yapılandırılmış bir IIS sanal dizininde bulunmalıdır. IIS ayarları eşleşmeyen birleşimlerini ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası ayarları hizmeti etkinleştirme sırasında bir hata sonuçlanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Services'te barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internet Information Services barındırma en iyi uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
