---
title: Bir ASP.NET İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c5faeb99fa8fb153f1ab74f5f00786355af50016
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045086"
---
# <a name="data-binding-in-an-aspnet-client"></a>Bir ASP.NET İstemcisinde Veri Bağlama
Bu örnek, bir Web Forms uygulamasında tipik bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan bir hizmeti gösterir. Örnek, bir tarayıcıdan erişilebilen bir istemci Web Forms uygulamasından ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, adlı `GetWeatherData`bir işlemi kullanıma `IWeatherService` sunan arabirim tarafından tanımlanır. Bu işlem bir şehir dizisini kabul eder ve bir şehirde yüksek ve `WeatherData` düşük tahmini sıcaklığın temsil ettiği nesne dizisini döndürür.  
  
 ASP.NET Client. aspx sayfasında, hizmet tarafından döndürülen verilerin grafik gösterimini içeren bir DataGrid Web denetimi tanımlanmıştır. . Aspx sayfasındaki kod, hava durumu verileri için WCF hizmetini çağırır ve verileri bir `WeatherData` nesne dizisine döndürür. DataGrid, `DataSource` özelliğini bu diziye ayarlayarak verilerinin nereden alınacağını belirtir. Veri bağlama, DataGrid 'in `DataBind` yöntemine yapılan bir çağrıyla oluşur. Bu kodun tümü içinde bulunur.`aspx` `Page_Load` sayfanın yöntemi, bu nedenle Kullanıcı tarayıcı sayfasını her yenilediğinde veriler DataGrid 'de güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Bu örnek istemci, bir geliştirme Web sunucusu altında çalışan bir Web sitesidir. Geliştirme Web sunucusunu başlatmak için komut istemine şunu yazın: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Ardından öğesine `http://localhost:8000/client`gidin. Bu örneği bilgisayarlar arasında çalıştırmak için, istemcinin Web. config `localhost` dosyasındaki tüm başvuruları sunucusunun bilgisayar adıyla değiştirin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
