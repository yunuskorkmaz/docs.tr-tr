---
title: Bir ASP.NET İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 2db29e0c4cdb87961430b80f317160b90e6756d0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715378"
---
# <a name="data-binding-in-an-aspnet-client"></a>Bir ASP.NET İstemcisinde Veri Bağlama
Bu örnek, bir Web Forms uygulamasında tipik bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan bir hizmeti gösterir. Örnek, bir tarayıcıdan erişilebilen bir istemci Web Forms uygulamasından ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, `GetWeatherData`adlı bir işlem sunan `IWeatherService` arabirimi tarafından tanımlanır. Bu işlem bir şehir dizisini kabul eder ve bir şehirde yüksek ve düşük tahmin edilen sıcaklığı temsil eden `WeatherData` nesnelerden oluşan bir dizi döndürür.  
  
 ASP.NET Client. aspx sayfasında, hizmet tarafından döndürülen verilerin grafik gösterimini içeren bir DataGrid Web denetimi tanımlanmıştır. . Aspx sayfasındaki kod, hava durumu verileri için WCF hizmetini çağırır ve verileri bir `WeatherData` nesneleri dizisine döndürür. DataGrid, `DataSource` özelliğini bu diziye ayarlayarak verilerinin nereden alınacağını belirtir. Veri bağlama, DataGrid 'in `DataBind` yöntemi çağrısıyla oluşur. Bu kodun tümü içinde bulunur.`aspx` sayfanın `Page_Load` yöntemi, bu nedenle Kullanıcı tarayıcı sayfasını her yenilediğinde veriler DataGrid 'de güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Bu örnek istemci, bir geliştirme Web sunucusu altında çalışan bir Web sitesidir. Geliştirme Web sunucusunu başlatmak için komut istemine aşağıdakini yazın: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. `http://localhost:8000/client`gidin. Bu örneği bilgisayarlar arasında çalıştırmak için, istemcinin Web. config dosyasındaki tüm `localhost` başvurularını sunucunun bilgisayar adıyla değiştirin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
