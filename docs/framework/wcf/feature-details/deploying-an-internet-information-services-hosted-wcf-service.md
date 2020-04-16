---
title: Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463861"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma

Internet Information Services (IIS) tarafından barındırılan bir Windows Communication Foundation (WCF) hizmeti geliştirmek ve dağıtmak aşağıdaki görevlerden oluşur:

- IIS, ASP.NET, WCF ve WCF etkinleştirme bileşeninin doğru şekilde yüklendiğinden ve kaydedildiğinden emin olun.

- Yeni bir IIS uygulaması oluşturun veya varolan bir ASP.NET uygulamayı yeniden kullanın.

- WCF hizmeti için bir .svc dosyası oluşturun.

- Hizmet uygulamasını IIS uygulamasına dağıtın.

- WCF hizmetini yapılandırın.

IIS tarafından barındırılan bir WCF hizmeti oluşturmanın ayrıntılı bir bölümü için [bkz.](how-to-host-a-wcf-service-in-iis.md)

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS, ASP.NET ve WCF'nin Doğru Yüklü ve Kayıtlı olduğundan Emin Olun

IIS tarafından barındırılan WCF hizmetlerinin düzgün çalışması için WCF, IIS ve ASP.NET yüklenmesi gerekir. WCF yükleme yordamları (.NET Framework'ün bir parçası olarak), ASP.NET ve IIS işletim sisteminize bağlı olarak değişir. WCF ve .NET Framework'ün yüklenmesi hakkında daha fazla bilgi için [geliştiriciler için .NET Framework'e yükleyin'](../../install/guide-for-developers.md)e bakın. IIS'yi Windows 10'a yüklemek için **Denetim Masası'nda** **Programlar ve Özellikler'i** açın ve ardından Windows özelliklerini **açıp kapat'ı**seçin. **Windows**Özellikleri'nde, **Internet Information Services'ı** seçin ve ardından **Tamam'ı**seçin.

![IIS ile Windows Özellikleri vurgulanır](./media/windows-features-iis.png)

IIS'yi diğer işletim sistemlerine yüklemek için gerekli talimatları [Windows Vista ve Windows 7'deki Install IIS'de ve](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) Windows Server [2012 R2'de IIS 8.5'i yükleyin.](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)

.NET Framework için yükleme işlemi, IIS makinede zaten mevcutsa WCF'yi otomatik olarak IIS'ye kaydeder. IIS .NET Framework'den sonra yüklenirse, WCF'yi IIS ve ASP.NET kaydetmek için ek bir adım gerekir. İşletim sisteminize bağlı olarak bunu aşağıdaki gibi yapabilirsiniz:

- Windows 7 ve Windows Server 2003: IIS ile WCF kayıt [servicemodel kayıt aracı (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) aracını kullanın. Bu aracı kullanmak için Visual Studio için Developer Command [Prompt'a](../../tools/developer-command-prompt-for-vs.md) **ServiceModelReg.exe /i /x** yazın.

- Windows 7: Son olarak, ASP.NET.NET Framework sürüm 4 veya sonraki sürümlerini kullanacak şekilde yapılandırıldığınızı doğrulamanız gerekir. Seçeneği ile `–i` ASPNET_Regiis aracı çalıştırarak bunu. Daha fazla bilgi için [ASP.NET IIS Kayıt Aracı'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))bakın.

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Yeni bir IIS Uygulaması Oluşturma veya Varolan bir ASP.NET Uygulamasını Yeniden Kullanma

IIS tarafından barındırılan WCF hizmetleri bir IIS uygulamasının içinde yer almalıdır. WCF hizmetlerini yalnızca barındıracak yeni bir IIS uygulaması oluşturabilirsiniz. Alternatif olarak, bir WCF hizmetini zaten 2,0 içeriği ASP.NET barındıran varolan bir uygulamaya (.aspx sayfaları ve ASP.NET Web hizmetleri [ASMX] gibi) dağıtabilirsiniz. Bu seçenekler hakkında daha fazla bilgi için WCF [Hizmetleri ve ASP.NET'daki](wcf-services-and-aspnet.md)"ASP.NET ile WCF Hizmetlerini ASP.NET Uyumluluk Modunda Barındırma" bölümlerine bakın.

IIS 6.0 ve sonraki sürümlerin düzenli olarak yalıtılmış nesne yönelimli programlama uygulamasını yeniden başlattığını unutmayın. Varsayılan değer 1740 dakikadır. Desteklenen maksimum değer 71.582 dakikadır. Bu yeniden başlatma devre dışı bilebilir. Bu özellik hakkında daha fazla bilgi için [PeriodicRestartTime'a](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90))bakın.

## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF Hizmeti için bir .svc Dosyası Oluşturma

IIS'de barındırılan WCF hizmetleri, IIS uygulamasında özel içerik dosyaları (.svc dosyaları) olarak temsil edilir. Bu model, ASMX sayfalarının bir IIS uygulamasının içinde .asmx dosyaları olarak temsil edilmesine benzer. .svc dosyası, WCF barındırma altyapısının gelen iletilere yanıt olarak barındırılan hizmetleri etkinleştirmesine olanak tanıyan WCF'ye özgü bir işleme yönergesi[\@(ServiceHost)](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)içerir. .svc dosyası için en yaygın sözdizimi aşağıdaki ifadededir.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ve tek bir `Service`öznitelik oluşur. Özniteliğin `Service` değeri, hizmet uygulamasının ortak dil çalışma zamanı (CLR) türü adıdır. Bu yönergeyi kullanmak temelde aşağıdaki kodu kullanarak bir hizmet ana bilgisayar oluşturmaya eşdeğerdir.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Hizmet için temel adreslerin listesini oluşturmak gibi ek barındırma yapılandırması da yapılabilir. Yönergeyi özel <xref:System.ServiceModel.Activation.ServiceHostFactory> barındırma çözümleriyle kullanmak üzere genişletmek için özel bir de kullanabilirsiniz. WCF hizmetlerini barındıran IIS uygulamaları, örneklerin oluşturulmasını <xref:System.ServiceModel.ServiceHost> ve kullanım ömrünü yönetmekten sorumlu değildir. Yönetilen WCF barındırma altyapısı, <xref:System.ServiceModel.ServiceHost> .svc dosyası için ilk istek geldiğinde gerekli örneği dinamik olarak oluşturur. Örnek, kod tarafından açıkça kapatılana veya uygulama geri dönüştürülene kadar serbest bırakılmaz.

.svc dosyaları için sözdizimi hakkında daha fazla bilgi için [ \@ServiceHost'a](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)bakın.

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Hizmet Uygulamasını IIS Uygulamasına Dağıtma

IIS'de barındırılan WCF hizmetleri, ASP.NET 2.0 ile aynı dinamik derleme modelini kullanır. tıpkı ASP.NET olduğu gibi, IIS tarafından barındırılan WCF hizmetlerinin uygulama kodunu aşağıdaki gibi çeşitli konumlarda çeşitli şekillerde dağıtabilirsiniz:

- Genel derleme önbelleğinde (GAC) veya uygulamanın \bin dizininde bulunan önceden derlenmiş bir .dll dosyası olarak. Önceden derlenmiş ikililer, sınıf kitaplığınyeni bir sürümü dağıtılana kadar güncelleştirilmez.

- Uygulamanın \App_Code dizininde bulunan derlenmemiş kaynak dosyaları olarak. Bu dizinde bulunan kaynak dosyaları, uygulamanın ilk isteğini işlerken dinamik olarak gereklidir. \App_Code dizinindeki dosyalarda yapılan değişiklikler, bir sonraki istek alındığında tüm uygulamanın geri dönüştürülmesine ve yeniden derlenmesine neden olur.

- Doğrudan .svc dosyasına yerleştirilen derlenmemiş kod olarak. Uygulama kodu, \@ServiceHost yönergesi'nden sonra hizmetin .svc dosyasında satır içi de bulunabilir. Satır satır kodunda yapılan değişiklikler, uygulamanın bir sonraki istek alındığı zaman geri dönüştürülmesine ve yeniden derlenmesine neden olur.

ASP.NET 2.0 derleme modeli hakkında daha fazla bilgi için [derlemeye genel ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100))bakın.

## <a name="configure-the-wcf-service"></a>WCF Hizmetini yapılandırma

IIS tarafından barındırılan WCF hizmetleri yapılandırmalarını Web.config dosyasındaki uygulamalarda saklar. IIS tarafından barındırılan hizmetler, IIS dışında barındırılan WCF hizmetleriyle aynı yapılandırma öğelerini ve sözdizimini kullanır. Ancak, aşağıdaki kısıtlamalar IIS barındırma ortamına özgüdür:

- IIS tarafından barındırılan hizmetlerin temel adresleri.

- IIS dışında WCF hizmetlerini barındıran uygulamalar, bir dizi temel adres URI'sini <xref:System.ServiceModel.ServiceHost> oluşturucuya geçirerek veya hizmetyapılandırmasında ana [ \<bilgisayar>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) öğesi sağlayarak barındırdıkları hizmetlerin temel adresini denetleyebilir. IIS'de barındırılan hizmetlerin temel adreslerini kontrol etme yeteneği yoktur; IIS tarafından barındırılan bir hizmetin temel adresi ,.svc dosyasının adresidir.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS Tarafından Barındırılan Hizmetler için Uç Nokta Adresleri

IIS'de barındırıldığında, uç nokta adresleri her zaman hizmeti temsil eden .svc dosyasının adresine göre olarak kabul edilir. Örneğin, bir WCF hizmetinin temel `http://localhost/Application1/MyService.svc` adresi aşağıdaki uç nokta yapılandırmasıyla birlikteyse:

```xml
<endpoint address="anotherEndpoint" />
```

Bu, 'de `http://localhost/Application1/MyService.svc/anotherEndpoint`ulaşılabilecek bir uç nokta sağlar.

Benzer şekilde, göreli adres olarak boş bir dize kullanan bitiş noktası `http://localhost/Application1/MyService.svc`yapılandırma öğesi, temel adres olan bitiş noktası olarak ulaşılabilir bir uç nokta sağlar.

```xml
<endpoint address="" />
```

IIS tarafından barındırılan hizmet bitiş noktaları için her zaman göreli uç nokta adreslerini kullanmanız gerekir. Tam nitelikli bir uç nokta adresi sağlamak `http://localhost/MyService.svc`(örneğin, uç nokta adresi bitiş noktasını ortaya çıkaran hizmeti barındıran IIS uygulamasına işaret etmiyorsa, hizmetin dağıtımında hatalara neden olabilir. Barındırılan hizmetler için göreli uç nokta adreslerinin kullanılması bu olası çakışmaları önler.

### <a name="available-transports"></a>Mevcut Taşımalar

IIS 5.1 ve IIS 6.0'da barındırılan WCF hizmetleri, HTTP tabanlı iletişim ikullanmakla sınırlıdır. Bu IIS platformlarında, barındırılan bir hizmeti, hizmet etkinleştirme sırasında bir hatayla sonuçlanan, HTTP olmayan bir bağlama sonucu kullanacak şekilde yapılandırın. IIS 7.0 için desteklenen taşımalar, mevcut MSMQ uygulamalarıyla geriye dönük uyumluluk için HTTP, Net.TCP, Net.Pipe, Net.MSMQ ve msmq.formatname'yi içerir.

### <a name="http-transport-security"></a>HTTP Taşıma Güvenliği

IIS tarafından barındırılan WCF hizmetleri, hizmeti içeren IIS sanal dizini bu ayarları desteklediği sürece HTTP aktarım güvenliğinden (örneğin, Temel, Özet ve Windows Tümleşik Kimlik Doğrulama gibi HTTPS ve HTTP kimlik doğrulama şemaları) yararlanabilir. Barındırılan bitiş noktasının bağlayıcısı üzerindeki HTTP Transport Security ayarları, onu içeren IIS sanal dizinindeki aktarım güvenlik ayarlarıyla eşleşmelidir.

Örneğin, HTTP özet kimlik doğrulaması kullanmak üzere yapılandırılan bir WCF bitiş noktası, HTTP özet kimlik doğrulaması için de yapılandırılan bir IIS sanal dizininde yer almalıdır. IIS ayarları ve WCF uç nokta ayarlarının eşleşmeyen birleşimleri, hizmet etkinleştirme sırasında bir hataya neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](hosting-in-internet-information-services.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](internet-information-services-hosting-best-practices.md)
- [Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
