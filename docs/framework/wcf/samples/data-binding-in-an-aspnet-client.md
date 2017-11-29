---
title: "Bir ASP.NET İstemcisinde Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ceb63315d94c0deed161bb294e8f61bf523bb63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-an-aspnet-client"></a>Bir ASP.NET İstemcisinde Veri Bağlama
Bu örnek, tipik bir tarafından döndürülen veri bağlamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web Forms uygulamasında hizmet.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmeti gösterir. İstemci Web Forms uygulama tarayıcıdan erişilebilir örnek oluşur ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Internet Information Services (IIS) tarafından barındırılan hizmeti.  
  
 Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `IWeatherService` adlı bir işlem kullanıma sunan arabirim `GetWeatherData`. Bu işlem bir dizi Şehir kabul eder ve bir dizi döndürür `WeatherData` bir şehir için yüksek ve düşük tahmin edilen sıcaklık temsil eden nesne.  
  
 Üzerinde [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] istemci .aspx sayfası, bir DataGrid denetimi tanımlanır, hizmet tarafından döndürülen veri grafik gösterimi içeren Web. .Aspx sayfa çağrıları kodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hava durumu verileri için hizmet ve veriler için bir dizi döndürür `WeatherData` nesneleri. DataGrid ayarlayarak kendi verisinden alınacağı konumu belirtir, `DataSource` bu diziye özelliği. Veri bağlama DataGrid'in çağrısıyla oluşur `DataBind` yöntemi. Bu kod tümünün barındırılan içinde.`aspx` sayfanın `Page_Load` her zaman kullanıcı tarayıcı sayfasında, verileri yeniler. böylece yöntemi DataGrid denetiminde güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Bu örnek 's istemci Geliştirme Web sunucusu altında çalışan bir Web sitesidir. Geliştirme Web sunucusu başlatmak için komut istemine aşağıdaki komutu yazın: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Ardından 8000/istemciye göz atın. Bilgisayarlar arasında bu örneği çalıştırmak için tüm başvuruları değiştirin `localhost` istemcinin Web.config dosyasında sunucunun bilgisayar adı.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>Ayrıca Bkz.
