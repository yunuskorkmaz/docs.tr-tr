---
title: Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: fcfad4c6cd7ffb0bf1233bab842b57a10bcc7f87
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486922"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma

Geliştirme ve Internet Information Services (IIS) barındırılan Windows Communication Foundation (WCF) hizmet dağıtma aşağıdaki görevleri içerir:

- IIS, ASP.NET, WCF ve WCF etkinleştirme bileşeni düzgün yüklü ve kayıtlı olan emin olun.

- Yeni bir IIS uygulama oluşturun veya mevcut bir ASP.NET uygulamasını yeniden kullanabilirsiniz.

- Bir WCF hizmeti için .svc dosyası oluşturun.

- Hizmet uygulaması için IIS uygulama dağıtın.

- WCF hizmetini yapılandırın.

IIS barındırılan bir WCF hizmeti oluşturma ayrıntılı kılavuz için bkz. [nasıl yapılır: IIS'de WCF Hizmeti barındırma](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS, ASP.NET ve WCF doğru olduğundan emin olun yüklü ve kayıtlı

WCF, IIS ve ASP.NET için IIS barındırılan WCF hizmetleri düzgün çalışması yüklenmesi gerekir. WCF (parçası olarak .NET Framework), ASP.NET ve IIS yüklemek için yordamları, işletim sistemine bağlı olarak değişir. WCF ve .NET Framework'ü yükleme hakkında daha fazla bilgi için bkz. [geliştiriciler için .NET Framework yükleme](../../install/guide-for-developers.md). Windows 10'da IIS yüklemek için açın **programlar ve Özellikler** içinde **Denetim Masası** seçip **kapatma Windows özelliklerini aç veya Kapat**. İçinde **Windows özellikleri**seçin **Internet Information Services** seçip **Tamam**.

![Vurgulanan IIS ile Windows özellikleri](media/windows-features-iis.png)

Diğer işletim sistemlerinde IIS'yi yüklemek için yönergeler bulunabilir [Windows Vista ve Windows 7 yüklemek IIS'de](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) ve [Windows Server 2012 R2 üzerinde yükleme IIS 8.5](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Makinede IIS zaten varsa, .NET Framework yükleme işlemi ile IIS WCF otomatik olarak kaydeder. IIS sonra .NET Framework yüklü değilse, IIS ve ASP.NET ile WCF kaydetmek için ek bir adım gereklidir. Aşağıdaki gibi işletim sistemine bağlı olarak bunu yapabilirsiniz:

- Windows 7 ve Windows Server 2003 için: Kullanım [ServiceModel Kayıt Aracı (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) WCF'ı IIS ile kaydetmeniz için aracı. Bu aracı kullanmak için yazmanız **ServiceModelReg.exe /i /x** içinde [Visual Studio için geliştirici komut istemi](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Son olarak, ASP.NET .NET Framework 4 veya sonraki bir sürümü kullanmak için yapılandırıldığını doğrulamanız gerekir. İle ASPNET_Regiis aracını çalıştırarak bunu `–i` seçeneği. Daha fazla bilgi için [ASP.NET IIS Kayıt Aracı](https://go.microsoft.com/fwlink/?LinkId=201186).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Yeni bir IIS uygulama oluşturun veya mevcut bir ASP.NET uygulamasını yeniden kullanma

IIS barındırılan WCF hizmetlerini bir IIS uygulama içinde bulunmalıdır. WCF hizmetlerini barındırmak için yeni bir IIS uygulama amaçları oluşturabilirsiniz. Alternatif olarak, bir WCF hizmetini ASP.NET 2.0 içerik (örneğin, .aspx sayfaları ve ASP.NET Web Hizmetleri [ASMX]) barındırma zaten mevcut bir uygulamasına dağıtabilirsiniz. Bu seçenekler hakkında daha fazla bilgi için bkz: "barındırma WCF yan yana ASP.NET ile" ve "ASP.NET uyumluluk modunda barındırma WCF hizmetleri" bölümleri içinde [WCF hizmetleri ve ASP.NET](wcf-services-and-aspnet.md).

IIS 6.0 ve üzeri sürümleri düzenli olarak yalıtılmış bir nesne yönelimli programlama uygulama yeniden olduğunu unutmayın. Varsayılan değer 1740 dakikadır. Desteklenen en yüksek değer 71,582 dakikadır. Bu yeniden başlatma devre dışı bırakılabilir. Bu özellik hakkında daha fazla bilgi için bkz. [PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968).

## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF hizmeti için bir .svc dosyası oluşturma

IIS barındırılan WCF hizmetleri, özel içerik dosyalarını (.svc) içinde IIS uygulaması olarak temsil edilir. Bu model, ASMX sayfaları içinde bir IIS uygulama .asmx dosyalarını olarak temsil edilen şekilde benzerdir. WCF özel işleme yönergesi .svc dosyada ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) barındırılan hizmetlere gelen iletilere yanıt olarak etkinleştirmek altyapı barındırma WCF sağlar. Aşağıdaki deyimde .svc dosya en yaygın sözdizimi aşağıdaki gibidir.

```
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>
```

İçerdiği [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ve tek bir öznitelik `Service`. Değerini `Service` ortak dil çalışma zamanı (CLR) tür adı hizmeti uygulamasının özniteliğidir. Bu yönerge kullanarak, aşağıdaki kodu kullanarak bir hizmet konağı oluşturmak için temel olarak eşdeğerdir.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Hizmet için temel adres listesi oluşturma gibi ek barındırma yapılandırma de yapılabilir. Özel bir kullanabilirsiniz <xref:System.ServiceModel.Activation.ServiceHostFactory> yönergesi özel barındırma çözümler ile kullanılmak üzere genişletmek için. WCF hizmetlerini barındıran IIS uygulamalar oluşturulmasını ve yaşam süresini yönetmekten sorumlu değildir <xref:System.ServiceModel.ServiceHost> örnekleri. Yönetilen WCF barındırma altyapısını gerekli oluşturur <xref:System.ServiceModel.ServiceHost> .svc dosyayı ilk isteği alındığında dinamik olarak örneği. Ya da açıkça kod veya uygulamanın ne zaman dönüştürülmeden tarafından kapatılana kadar örneği serbest bırakılmaz.

.Svc dosyalar için söz dizimi hakkında daha fazla bilgi için bkz: [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>IIS uygulaması için hizmet uygulaması dağıtma

IIS barındırılan WCF hizmetleri ASP.NET 2.0 aynı dinamik derleme modelini kullanın. İle olduğu gibi ASP.NET ve IIS barındırılan WCF hizmetleri, çeşitli konumlarda ve çeşitli şekillerde uygulama kodunu gibi dağıtabilirsiniz:

- Önceden derlenmiş bir .dll dosyası, genel derleme önbelleğinde (GAC) veya uygulamanın \bin dizinine bulunan gibi. Önceden derlenmiş ikili dosyaları, Sınıf Kitaplığı'nın yeni bir sürüm olarak dağıtılmadıkça güncelleştirilmez.

- Uygulamanın \App_Code dizininde derlenmemiş kaynak dosyaları gibi. Bu dizinde bulunan kaynak dosyaları, uygulamanın ilk isteği işlenirken dinamik olarak gerekli değildir. Geri dönüştürüldü ve sonraki isteği aldığında yeniden derlenen uygulamanın tamamı \App_Code dizindeki dosyaların herhangi bir değişiklik neden.

- Derlenmemiş kodu doğrudan .svc dosyasına yerleştirilmiş olarak. Uygulama kodu da olabilir bu hizmetin .svc dosyasında bulunan satır içi sonra \@ServiceHost yönergesi. Satır içi kod değişiklikleri geri dönüştürüldü ve sonraki isteği aldığında yeniden derlenen uygulamanın neden.

ASP.NET 2.0 derleme modeli hakkında daha fazla bilgi için bkz. [ASP.NET derleme genel bakış](https://go.microsoft.com/fwlink/?LinkId=94773).

## <a name="configure-the-wcf-service"></a>WCF hizmetini yapılandırma

IIS barındırılan WCF hizmetlerini yapılandırmalarını uygulamaları Web.config dosyasında depolar. IIS barındırılan hizmetler olarak dışında IIS barındırılan WCF hizmetleri aynı yapılandırma öğelerini ve söz dizimi kullanın. Ancak, aşağıdaki kısıtlamaları IIS barındırma ortamına benzersiz şunlardır:

- IIS barındırılan hizmetler için temel adres.

- IIS dışında barındırma WCF hizmetlerini barındıran bir dizi temel geçirerek Hizmetleri temel adresini denetim uygulamaları adresi için bir URI'leri <xref:System.ServiceModel.ServiceHost> Oluşturucusu veya sağlayarak bir [ \<konak >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) öğesinde hizmet yapılandırmasının. IIS'de barındırılan hizmetler, kendi temel adresi denetleme olanağı yoktur; IIS tarafından barındırılan bir hizmet temel adresini, kendi .svc dosyasının adresidir.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS tarafından barındırılan hizmetleri için uç nokta adresleri

IIS içinde barındırıldığında, uç nokta adresleri hizmeti temsil eden .svc dosyanın göreli adres olarak her zaman değerlendirilir. Örneğin, bir WCF Hizmeti temel adresi ise `http://localhost/Application1/MyService.svc` aşağıdaki uç nokta yapılandırması ile:

```xml
<endpoint address="anotherEndpoint" .../>
```

Bu, üzerinde erişilebilir bir uç nokta sağlar `http://localhost/Application1/MyService.svc/anotherEndpoint`.

Hizmetin göreli adresini en erişilebilir bir uç nokta sağladığından, boş bir dize kullanan benzer şekilde, uç nokta yapılandırma öğesi `http://localhost/Application1/MyService.svc`, temel adres olan.

```xml
<endpoint address="" ... />
```

Ayrıca, IIS tarafından barındırılan hizmet uç noktaları için her zaman göreli uç nokta adresleri kullanmanız gerekir. Tam uç nokta adresi (örneğin, `http://localhost/MyService.svc`) IIS uç noktayı kullanıma sunmayı hizmetini barındıran uygulama için uç nokta adresini işaret etmiyorsa hizmetin dağıtılmasına hatalara yol açabilir. Barındırılan hizmetler için göreli bir uç nokta adresleri kullanarak bu olası çakışmaları ortadan kaldırır.

### <a name="available-transports"></a>Kullanılabilir taşımalar

Barındırılan IIS 5.1 WCF hizmetleri ve HTTP tabanlı iletişimi kullanarak IIS 6.0 kısıtlanır. Bu IIS platformlarda bir HTTP olmayan bağlama bir barındırılan hizmetin yapılandırma hatayla hizmeti etkinleştirme sırasında sonuçlanır. IIS 7.0, desteklenen aktarmalar HTTP, Net.TCP, Net.Pipe, Net.MSMQ ve msmq.formatname için geriye doğru mevcut MSMQ uygulamalarla uyumluluk içerir.

### <a name="http-transport-security"></a>HTTP Taşıma Güvenliği

IIS barındırılan WCF hizmetleri HTTP türünde kullanmak yapabilir olan hizmeti içeren IIS sanal dizini desteklediği sürece aktarım güvenliği (örneğin, HTTPS ve HTTP kimlik doğrulaması şemalarını temel, Özet ve Windows tümleşik kimlik doğrulaması gibi) Ayarlar. HTTP aktarım güvenliği ayarlarını barındırılan uç noktasının binding taşıma güvenlik ayarlarını içeren IIS sanal dizini eşleşmesi gerekir.

Örneğin, HTTP digest kimlik doğrulaması kullanmak üzere yapılandırılmış bir WCF uç nokta da HTTP digest kimlik doğrulamasına izin verecek şekilde yapılandırılmış bir IIS sanal dizinde bulunmalıdır. IIS ve WCF uç noktası ayarlarını eşleşmeyen birleşimlerini hizmeti etkinleştirme sırasında hataya neden.

## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](hosting-in-internet-information-services.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](internet-information-services-hosting-best-practices.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
