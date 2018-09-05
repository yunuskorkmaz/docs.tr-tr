---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: c413a26e8e7a0e76712eb98c5ad1bb822d75ae6f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659471"
---
# <a name="self-host"></a>Kendini Barındırma
Bu örnek, şirket içinde barındırılan hizmeti bir konsol uygulamasında uygulamak nasıl gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Hizmet yapılandırma dosyası için App.config Web.config dosyasından olarak yeniden adlandırıldı ve ana bilgisayar kullanan bir taban adresini yapılandırmak için değiştirilebilir. Statik uygulamak için hizmet kaynak kodu değiştirilmiş `Main` oluşturur ve yapılandırılmış temel adresini sağlayan bir hizmet konağı açar işlevi. Hizmet uygulaması, her işlem için konsola çıkışını yazmak için değiştirildi. İstemci, hizmetin doğru uç nokta adresini yapılandırma dışında değiştirilmemiş olmuştur.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örneği oluşturmak için bir statik main işlevi uygulayan bir <xref:System.ServiceModel.ServiceHost> için verilen `CalculatorService` , aşağıdaki örnek kodda gösterildiği gibi yazın.  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 Bir hizmeti Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırılan hizmetin taban adresi barındırma ortamı tarafından sağlanır. Şirket içinde barındırılan durumda kendiniz temel adresini belirtmelisiniz. Bu yapılır kullanarak `add` öğe, alt [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), alt [ \<konak >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), alt [ \<hizmet > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
