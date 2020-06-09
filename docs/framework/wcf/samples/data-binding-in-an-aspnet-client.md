---
title: Bir ASP.NET İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 134e1d7df3ed6bb245a870ad257fa64ad94e4e9c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602602"
---
# <a name="data-binding-in-an-aspnet-client"></a>Bir ASP.NET İstemcisinde Veri Bağlama
Bu örnek, bir Web Forms uygulamasında tipik bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan bir hizmeti gösterir. Örnek, bir tarayıcıdan erişilebilen bir istemci Web Forms uygulamasından ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, `IWeatherService` adlı bir işlemi kullanıma sunan arabirim tarafından tanımlanır `GetWeatherData` . Bu işlem bir şehir dizisini kabul eder ve `WeatherData` bir şehirde yüksek ve düşük tahmini sıcaklığın temsil ettiği nesne dizisini döndürür.  
  
 ASP.NET Client. aspx sayfasında, hizmet tarafından döndürülen verilerin grafik gösterimini içeren bir DataGrid Web denetimi tanımlanmıştır. . Aspx sayfasındaki kod, hava durumu verileri için WCF hizmetini çağırır ve verileri bir nesne dizisine döndürür `WeatherData` . DataGrid, özelliğini bu diziye ayarlayarak verilerinin nereden alınacağını belirtir `DataSource` . Veri bağlama, DataGrid 'in yöntemine yapılan bir çağrıyla oluşur `DataBind` . Bu kodun tümü içinde bulunur.`aspx` sayfanın `Page_Load` yöntemi, bu nedenle Kullanıcı tarayıcı sayfasını her yenilediğinde veriler DataGrid 'de güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Bu örnek istemci, bir geliştirme Web sunucusu altında çalışan bir Web sitesidir. Geliştirme Web sunucusunu başlatmak için komut istemine şunu yazın: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client` . Ardından öğesine gidin `http://localhost:8000/client` . Bu örneği bilgisayarlar arasında çalıştırmak için, `localhost` Istemcinin Web. config dosyasındaki tüm başvuruları sunucusunun bilgisayar adıyla değiştirin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
