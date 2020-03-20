---
title: Bir ASP.NET İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145013"
---
# <a name="data-binding-in-an-aspnet-client"></a>Bir ASP.NET İstemcisinde Veri Bağlama
Bu örnek, tipik bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin bir Web Forms uygulamasında nasıl bağlanılsüreceğini gösterir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek, istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmet gösterir. Örnek, bir tarayıcıdan erişilebilen bir istemci Web Formları uygulamasından ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, adı verilen `IWeatherService` `GetWeatherData`bir işlemi ortaya çıkaran arabirim tarafından tanımlanır. Bu işlem bir dizi şehri kabul eder `WeatherData` ve bir şehir için yüksek ve düşük tahmin edilen sıcaklığı temsil eden bir dizi nesne döndürür.  
  
 ASP.NET istemci .aspx sayfasında, hizmet tarafından döndürülen verilerin grafik gösterimini içeren bir DataGrid Web denetimi tanımlanır. .aspx sayfasındaki kod, hava durumu verileri için WCF hizmetini `WeatherData` arar ve verileri bir dizi nesneye döndürür. DataGrid, özelliğini `DataSource` bu diziye ayarlayarak verilerini nereden alacağını belirtir. Veri bağlama, DataGrid'in `DataBind` yöntemine yapılan bir çağrıyla oluşur. Bu kodun tümü.`aspx` sayfanın `Page_Load` yöntemi, böylece kullanıcı tarayıcı sayfasını her yenilesin, veriler DataGrid'de güncellenir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Bu örneğin istemcisi, geliştirme Web sunucusu altında çalışan bir Web sitesidir. Geliştirme Web sunucusunu başlatmak için komut istemine `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`aşağıdakileri yazın: . Sonra göz `http://localhost:8000/client`atın. Bu örneği bilgisayarlarda çalıştırmak için, `localhost` istemcinin Web.config dosyasındaki tüm başvuruları sunucunun bilgisayar adı ile değiştirin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
