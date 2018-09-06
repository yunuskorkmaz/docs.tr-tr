---
title: Tek Yönlü
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 25720285e29641c3c040444cb643af2790f10d3b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740733"
---
# <a name="one-way"></a>Tek Yönlü
Bu örnek, bir hizmet sözleşmesi ile tek yönlü hizmet işlemleri gösterir. İstemci, hizmet işlemlerini çift yönlü hizmet işlemleri ile olduğu gibi tamamlanması için beklemez. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve kullandığı `wsHttpBinding` bağlama. Bu örnekte, alan ve istekleri işleyen hizmet gözlemleyin sağlamak için şirket içinde barındırılan bir konsol uygulaması hizmetidir. İstemci ayrıca bir konsol uygulamasıdır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Tek yönlü hizmet sözleşmesi oluşturmak için hizmet sözleşmesini tanımlama, Uygula <xref:System.ServiceModel.OperationContractAttribute> sınıfı her işleme ve ayarlama <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> için `true` aşağıdaki örnek kodda gösterildiği gibi:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 İstemci hizmet işlemleri tamamlamak beklemez göstermek için aşağıdaki örnek kodda gösterildiği gibi bu örnek hizmeti kodunda bir 5 saniyelik gecikme uygular:  
  
```  
/ This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 İstemci hizmeti çağırıp, çağrı, hizmeti işlemin tamamlanmasını beklemenize gerek kalmadan döndürür.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi hizmet ve istemci aşağı kapatmak için ENTER tuşuna basın.  
  
 İstemci hizmeti önceden tek yönlü hizmet işlemleri için bir istemci beklemez gösteren tamamlanır. İstemci çıktısı aşağıdaki gibidir:  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Aşağıdaki hizmet çıktı gösterilmektedir:  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
>  HTTP, tanımı gereği, bir istek/yanıt protokoldür; bir istekte bulunulduğunda bir yanıt döndürülür. Bu, hatta HTTP üzerinden sunulan bir tek yönlü hizmet işlemi için geçerlidir. İşlem çağrıldığında, hizmet işlemi yürütüldü önce hizmet 202 bir HTTP durum kodu döndürür. Bu durum kodu istek işleme için kabul edildi, ancak işleme henüz tamamlanmamış anlamına gelir. Hizmetten 202 yanıtının alıncaya kadar blokları işlemi çağıran istemci. Oturumları kullanacak şekilde yapılandırılmış bir bağlama kullanarak birden çok yönlü ileti gönderildiğinde bu bazı beklenmeyen davranışlara neden olabilir. `wsHttpBinding` Bu örnekte kullanılan bağlama oturumları kullanmak için bir güvenlik bağlamı'kurmak için varsayılan olarak yapılandırılır. Varsayılan olarak, bir oturumda ileti bunlar gönderildiği sırada ulşamasını garanti edilir. Bir oturumda ikinci bir ileti gönderildiğinde, ilk iletiyi işleyene kadar bu nedenle, bu işlenmedi. Bunun sonucu olarak, önceki iletinin işlenmesi tamamlanıncaya kadar istemci 202 yanıtının bir ileti almadığında ' dir. İstemci için bu nedenle görünür her bir sonraki işlemi çağrısının blok. Bu davranışı önlemek için bu örnek, çalışma zamanının eşzamanlı olarak işlemek için ayrı örnekleri iletiler gönderme yapılandırır. Örnek kümelerini <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> için `PerCall` böylece her ileti farklı bir örneği tarafından işlenebilir. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanır `Multiple` teker teker iletilerini dağıtmak birden fazla iş parçacığı izin vermek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  İstemcisini çalıştıran ve istemci hizmeti kapatılıyor önce bilgisayarı önce hizmeti çalıştırın. Hizmet gitmiş olduğundan güvenlik oturumu düzgün bir şekilde istemci kapattığınızda olamaz, bu istemci özel durumu önler.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a>Ayrıca Bkz.
