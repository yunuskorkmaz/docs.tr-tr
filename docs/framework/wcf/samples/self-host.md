---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a38738c369db3d3f8242bd71ee04a19a669b2cf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144155"
---
# <a name="self-host"></a>Kendini Barındırma
Bu örnek, konsol uygulamasında kendi kendine barındırılan bir hizmetin nasıl uygulanacağını gösterir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Hizmet yapılandırma dosyası Web.config'den App.config'e yeniden adlandırıldı ve ana bilgisayar tarafından kullandığı bir temel adresi yapılandırmak üzere değiştirildi. Hizmet kaynak kodu, yapılandırılan temel `Main` adresi sağlayan bir hizmet ana bilgisayarı oluşturan ve açan statik bir işlev uygulamak üzere değiştirildi. Hizmet uygulaması, her işlem için konsola çıktı yazmak üzere değiştirildi. Hizmetin doğru bitiş noktası adresini yapılandırmak dışında istemci değiştirilmemiştir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnek, aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.ServiceHost> gibi, `CalculatorService` verilen tür için bir oluşturmak için statik bir main işlevi uygular.  
  
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
  
 Bir hizmet Internet Information Services (IIS) veya Windows Process Etkinleştirme Hizmeti'nde (WAS) barındırıldığında, hizmetin temel adresi barındırma ortamı tarafından sağlanır. Kendi kendine barındırılan durumda, temel adresi kendiniz belirtmeniz gerekir. Bu, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) [ \<aşağıdaki ](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)örnek yapılandırmada gösterildiği gibi, temelAdresler>, ev sahibi>, hizmet in alt>alt adresler alt kullanılarak yapılır. `add`  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
