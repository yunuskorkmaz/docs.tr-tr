---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 5a94eff021074a24df5b8891fe7b418b1fcf3c35
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094923"
---
# <a name="self-host"></a>Kendini Barındırma
Bu örnek, bir konsol uygulamasında kendi kendine barındırılan bir hizmetin nasıl uygulanacağını gösterir. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Hizmet yapılandırma dosyası, Web. config 'den App. config olarak yeniden adlandırıldı ve konağın kullandığı bir temel adres yapılandırmak üzere değiştirildi. Hizmet kaynak kodu, yapılandırılmış temel adresi sağlayan bir hizmet ana bilgisayarı oluşturan ve açan bir statik `Main` işlevi uygulayacak şekilde değiştirilmiştir. Hizmet uygulamasının her işlem için konsola çıkış yazacak şekilde değiştirilmiştir. Hizmetin doğru uç nokta adresini yapılandırma dışında, istemci değiştirilmemiş.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek, aşağıdaki örnek kodda gösterildiği gibi, verilen `CalculatorService` türü için <xref:System.ServiceModel.ServiceHost> oluşturmak üzere statik Main işlevi uygular.  
  
```csharp
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
  
 Bir hizmet Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) içinde barındırılıyorsa, hizmetin temel adresi barındırma ortamı tarafından sağlanır. Şirket içinde barındırılan durumda, temel adresi kendiniz belirtmeniz gerekir. Bu, aşağıdaki örnek yapılandırmada gösterildiği gibi `add` öğesi, [\<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), [>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) [\<ana bilgisayar](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)\<alt öğesi kullanılarak yapılır.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
