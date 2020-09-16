---
title: Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma
description: IIS 'de barındırılan bir WCF hizmetini geliştirmek ve dağıtmak için gereken görevler hakkında bilgi edinin ve bileşen yüklemesinin doğrulanması ile başlar
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 5d9a0b80cc75baec2325b778cee7daa68531f2d5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557573"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma

Internet Information Services (IIS) içinde barındırılan Windows Communication Foundation (WCF) hizmetini geliştirme ve dağıtma aşağıdaki görevlerden oluşur:

- IIS, ASP.NET, WCF ve WCF etkinleştirme bileşeninin doğru bir şekilde yüklendiğinden ve kaydedildiğinden emin olun.

- Yeni bir IIS uygulaması oluşturun veya var olan bir ASP.NET uygulamasını yeniden kullanın.

- WCF hizmeti için bir. svc dosyası oluşturun.

- Hizmet uygulamasını IIS uygulamasına dağıtın.

- WCF hizmetini yapılandırın.

IIS tarafından barındırılan bir WCF hizmeti oluşturma hakkında ayrıntılı yönergeler için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS, ASP.NET ve WCF 'Nin doğru bir şekilde yüklendiğinden ve kaydedildiğinden emin olun

IIS tarafından barındırılan WCF hizmetlerinin düzgün çalışması için WCF, IIS ve ASP.NET yüklü olmalıdır. WCF yükleme yordamları (.NET Framework bir parçası olarak), ASP.NET ve IIS işletim sisteminize bağlı olarak değişir. WCF ve .NET Framework yükleme hakkında daha fazla bilgi için bkz. [geliştiricilere yönelik .NET Framework yükleme](../../install/guide-for-developers.md). Windows 10 ' a IIS yüklemek için, **Denetim Masası** 'nda **Programlar ve Özellikler** ' i açın ve ardından **Windows özelliklerini aç veya kapat**' ı seçin. **Windows özellikleri**' nde **Internet Information Services** seçin ve ardından **Tamam**' ı seçin.

![IIS ile vurgulanan Windows özellikleri](./media/windows-features-iis.png)

Diğer işletim sistemlerine IIS yükleme yönergeleri [Windows Vista ve Windows 7 ' de IIS yükleme](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) ve [Windows Server 2012 R2 üzerinde IIS 8,5 yükleme](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)' de bulunabilir.

.NET Framework yükleme işlemi, IIS makinede zaten mevcutsa WCF 'yi IIS ile otomatik olarak kaydeder. IIS .NET Framework sonrasında yüklenirse, WCF 'yi IIS ve ASP.NET 'e kaydetmek için ek bir adım gerekir. Bunu, işletim sisteminize bağlı olarak aşağıdaki şekilde yapabilirsiniz:

- Windows 7 ve Windows Server 2003: WCF 'yi IIS ile kaydetmek için [ServiceModel Kayıt Aracı (ServiceModelReg.exe)](../servicemodelreg-exe.md) aracını kullanın. Bu aracı kullanmak için, [Visual Studio Geliştirici Komut İstemi](../../tools/developer-command-prompt-for-vs.md) **ServiceModelReg.exe/i/x** yazın.

- Windows 7: son olarak, ASP.NET 'in .NET Framework sürüm 4 veya üstünü kullanacak şekilde yapılandırıldığını doğrulamanız gerekir. Bunu, ASPNET_Regiis aracını seçeneğiyle çalıştırarak yapabilirsiniz `–i` . Daha fazla bilgi için bkz. [ASP.NET IIS kayıt aracı](/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Yeni bir IIS uygulaması oluşturun veya var olan bir ASP.NET uygulamasını yeniden kullanın

IIS tarafından barındırılan WCF Hizmetleri bir IIS uygulamasının içinde bulunmalıdır. WCF hizmetlerini özel olarak barındırmak için yeni bir IIS uygulaması oluşturabilirsiniz. Alternatif olarak, zaten ASP.NET 2,0 içeriğini barındıran mevcut bir uygulamaya (örneğin. aspx sayfaları ve ASP.NET Web Hizmetleri [ASMX]) bir WCF Hizmeti dağıtabilirsiniz. Bu seçenekler hakkında daha fazla bilgi için, [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md)' deki "wcf 'yi ASP.net Ile yan yana barındırma" ve "wcf hizmetleri ASP.NET uyumluluk modunda barındırma" bölümlerine bakın.

IIS 6,0 ve sonraki sürümlerin, yalıtılmış nesne odaklı bir programlama uygulamasını düzenli aralıklarla yeniden başlatdığına göz önünde unutmayın. Varsayılan değer 1740 dakikadır. Desteklenen en yüksek değer 71.582 dakikadır. Bu yeniden başlatma devre dışı bırakılabilir. Bu özellik hakkında daha fazla bilgi için bkz. [PeriodicRestartTime](/previous-versions/iis/6.0-sdk/ms525914(v=vs.90)).

## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF hizmeti için bir. svc dosyası oluşturma

IIS 'de barındırılan WCF Hizmetleri, IIS uygulamasının içinde özel içerik dosyaları (. svc dosyaları) olarak gösterilir. Bu model, ASMX sayfalarının bir IIS uygulamasının içinde. asmx dosyaları olarak temsil edildiği yönteme benzer. Bir. svc dosyası, WCF barındırma altyapısının gelen iletilere yanıt olarak barındırılan Hizmetleri etkinleştirmesini sağlayan, WCF 'ye özgü bir işleme yönergesi ([ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)) içerir. Bir. svc dosyası için en yaygın sözdizimi aşağıdaki deyimdir.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesini ve tek bir özniteliği içerir `Service` . Özniteliğin değeri, `Service` hizmet uygulamasının ortak dil çalışma zamanı (CLR) türü adıdır. Bu yönergeyi kullanmak, aşağıdaki kodu kullanarak bir hizmet ana bilgisayarı oluşturmaya temelde eşdeğerdir.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Hizmetin temel adres listesini oluşturma gibi ek barındırma yapılandırması da yapılabilir. Özel <xref:System.ServiceModel.Activation.ServiceHostFactory> barındırma çözümleriyle kullanım için yönergeyi genişletmek üzere özel bir de kullanabilirsiniz. WCF hizmetlerini barındıran IIS uygulamaları, örneklerin oluşturulmasını ve yaşam süresini yönetmekten sorumludur <xref:System.ServiceModel.ServiceHost> . Yönetilen WCF barındırma altyapısı, <xref:System.ServiceModel.ServiceHost> . svc dosyası için ilk istek alındığında gerekli örneği dinamik olarak oluşturur. Kod ya da uygulama geri dönüştürüldüğünde, örnek açıkça kapatılana kadar serbest bırakılır.

. Svc dosyaları için sözdizimi hakkında daha fazla bilgi için bkz. [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Hizmet uygulamasını IIS uygulamasına dağıtma

IIS 'de barındırılan WCF Hizmetleri, ASP.NET 2,0 ile aynı dinamik derleme modelini kullanır. ASP.NET ' de olduğu gibi, IIS tarafından barındırılan WCF Hizmetleri için uygulama kodunu çeşitli konumlarda aşağıdaki gibi çeşitli yollarla dağıtabilirsiniz:

- Genel derleme önbelleğinde (GAC) veya uygulamanın \bin dizininde bulunan önceden derlenmiş bir. dll dosyası olarak. Sınıf kitaplığının yeni bir sürümü dağıtılana kadar önceden derlenmiş ikili dosyalar güncellenmez.

- Uygulamanın \ App_Code dizininde bulunan derlenmemiş kaynak dosyaları olarak. Bu dizinde bulunan kaynak dosyaları, uygulamanın ilk isteği işlenirken dinamik olarak gereklidir. \ App_Code dizinindeki dosyalarda yapılan değişiklikler, bir sonraki istek alındığında tüm uygulamanın geri dönüştürülüp yeniden derlenmesine neden olur.

- Derlenmemiş kod olarak doğrudan. svc dosyasına yerleştirilmiş. Uygulama kodu Ayrıca, Service 'in. svc dosyasında, ServiceHost yönergesinden sonra satır içi olarak da bulunabilir \@ . Satır içi kodda yapılan değişiklikler, bir sonraki istek alındığında uygulamanın geri dönüştürülüp yeniden derlenmesine neden olur.

ASP.NET 2,0 derleme modeli hakkında daha fazla bilgi için bkz. [ASP.net derlemesine genel bakış](/previous-versions/aspnet/ms178466(v=vs.100)).

## <a name="configure-the-wcf-service"></a>WCF hizmetini yapılandırma

IIS tarafından barındırılan WCF Hizmetleri, yapılandırmalarını uygulamalar Web.config dosyasında depolar. IIS tarafından barındırılan hizmetler, IIS dışında barındırılan WCF Hizmetleri ile aynı yapılandırma öğelerini ve sözdizimini kullanır. Ancak, aşağıdaki kısıtlamalar IIS barındırma ortamına özgüdür:

- IIS tarafından barındırılan hizmetlerin temel adresleri.

- WCF hizmetlerini IIS dışında barındıran uygulamalar, bir dizi temel adres URI 'sini <xref:System.ServiceModel.ServiceHost> oluşturucuya geçirerek veya hizmetin yapılandırmasında bir öğe sağlayarak barındırdıkları hizmetlerin temel adresini denetleyebilir [\<host>](../../configure-apps/file-schema/wcf/host.md) . IIS 'de barındırılan hizmetlerin kendi temel adreslerini denetleme yeteneği yoktur; IIS tarafından barındırılan bir hizmetin temel adresi. svc dosyasının adresidir.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS tarafından barındırılan hizmetler için uç nokta adresleri

IIS 'de barındırıldığında, uç nokta adresleri her zaman hizmeti temsil eden. svc dosyasının adresine göreli olarak değerlendirilir. Örneğin, bir WCF hizmetinin temel adresi `http://localhost/Application1/MyService.svc` aşağıdaki uç nokta yapılandırmasıyla varsa:

```xml
<endpoint address="anotherEndpoint" />
```

Bu, tarihinde erişilebilecek bir uç nokta sağlar `http://localhost/Application1/MyService.svc/anotherEndpoint` .

Benzer şekilde, göreli adres olarak boş bir dize kullanan uç nokta yapılandırma öğesi, temel adres olan ' de erişilebilen bir uç nokta sağlar `http://localhost/Application1/MyService.svc` .

```xml
<endpoint address="" />
```

IIS tarafından barındırılan hizmet uç noktaları için her zaman göreli uç nokta adreslerini kullanmanız gerekir. Tam bir uç nokta adresi sağlamak (örneğin,), uç nokta `http://localhost/MyService.svc` adresi uç noktayı kullanıma sunan IIS-uygulamasına işaret edilmezse, hizmet dağıtımında hatalara yol açabilir. Barındırılan hizmetler için göreli uç nokta adreslerini kullanmak bu olası çakışmaları önler.

### <a name="available-transports"></a>Kullanılabilir aktarımlar

IIS 5,1 ve IIS 6,0 ' de barındırılan WCF Hizmetleri, HTTP tabanlı iletişim kullanılarak kısıtlıdır. Bu IIS platformlarında, barındırılan bir hizmeti HTTP olmayan bir bağlama kullanacak şekilde yapılandırmak, hizmet etkinleştirme sırasında bir hatayla sonuçlanır. IIS 7,0 için desteklenen aktarımlar, mevcut MSMQ uygulamalarıyla geriye dönük uyumluluk için HTTP, net. TCP, net. pipe, net. MSMQ ve MSMQ. formatname ' i içerir.

### <a name="http-transport-security"></a>HTTP Taşıma Güvenliği

IIS tarafından barındırılan WCF Hizmetleri, hizmeti içeren IIS sanal dizini bu ayarları desteklediğinde HTTP aktarım güvenliği (örneğin, Basic, Digest ve Windows tümleşik kimlik doğrulaması gibi) tarafından kullanılabilir. Barındırılan bir uç noktanın bağlamasındaki HTTP aktarım güvenliği ayarları, kendisini içeren IIS sanal dizinindeki taşıma güvenliği ayarlarıyla eşleşmelidir.

Örneğin, HTTP Özet kimlik doğrulaması kullanmak üzere yapılandırılmış bir WCF uç noktası, HTTP Özet kimlik doğrulamasına izin verecek şekilde yapılandırılmış bir IIS sanal dizininde bulunmalıdır. IIS ayarlarının ve WCF uç nokta ayarlarının eşleşmeyen birleşimleri, hizmet etkinleştirme sırasında bir hatayla sonuçlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](hosting-in-internet-information-services.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](internet-information-services-hosting-best-practices.md)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
