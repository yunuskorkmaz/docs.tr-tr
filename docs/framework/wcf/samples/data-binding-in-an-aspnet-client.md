---
title: Bir ASP.NET İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 07e03a4580795b3424f63cec8f93fea2039b6733
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339417"
---
# <a name="data-binding-in-an-aspnet-client"></a>Bir ASP.NET İstemcisinde Veri Bağlama
Bu örnek, bir Web Forms uygulaması normal bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verinin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmette gösterir. İstemci Web Forms uygulaması bir tarayıcı ve Internet Information Services (IIS) tarafından barındırılan bir WCF Hizmeti erişilebilir örnek oluşur.  
  
 Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `IWeatherService` adlı bir işlem sunan arabirimi `GetWeatherData`. Bu işlem, bir dizi şehirlerin kabul eder ve bir dizi döndürür `WeatherData` bir şehir için tahmin edilen yüksek ve düşük sıcaklık temsil eden nesneleri.  
  
 Üzerinde [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] istemci .aspx sayfası, bir DataGrid denetimi tanımlanır, hizmet tarafından döndürülen veri grafik gösterimi içeren Web. .Aspx sayfasında kod hava durumu verilerine yönelik WCF Hizmeti çağırır ve verileri için bir dizi döndürür `WeatherData` nesneleri. DataGrid ayarlayarak onun verilerinin alınacağı konumu belirtir, `DataSource` bu diziyi özelliği. DataGrid'in çağrısıyla veri bağlama gerçekleşir `DataBind` yöntemi. Tüm bu kod içinde bulunur.`aspx` sayfanın `Page_Load` yöntemi, her kullanıcının tarayıcı sayfasında, verileri yeniler. Bu nedenle, DataGrid'deki güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Bu örnek'ın istemci Geliştirme Web sunucusu altında çalışan bir Web sitesidir. Geliştirme Web sunucusunu başlatmak için komut istemine aşağıdaki komutu yazın: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Ardından gözatın `http://localhost:8000/client`. Bilgisayarlar arasında bu örneği çalıştırmak için tüm başvuruları değiştirin `localhost` istemcinin Web.config dosyasında sunucusunun bilgisayar adına sahip.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
