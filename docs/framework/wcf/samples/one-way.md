---
title: Tek Yönlü
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 5cb3619d56720333f23d933a8f356e8b0268c4d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505713"
---
# <a name="one-way"></a>Tek Yönlü
Bu örnek bir tek yönlü hizmet işlemleri hizmet kişiyle gösterir. İstemci, hizmet işlemlerinin çift yönlü hizmet işlemleri ile olduğu gibi tamamlamak beklemez. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve kullandığı `wsHttpBinding` bağlama. Bu örnekte, alan ve istekleri işleyen hizmet izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulaması hizmetidir. İstemci ayrıca bir konsol uygulamasıdır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Tek yönlü hizmet sözleşmesi oluşturmak için hizmet sözleşmesini tanımlama, uygulama <xref:System.ServiceModel.OperationContractAttribute> sınıf her işleme ve ayarlayın <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> için `true` aşağıdaki örnek kodda gösterildiği gibi:  
  
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
  
 İstemci hizmet işlemleri tamamlamak beklemez göstermek için aşağıdaki örnek kodda gösterildiği gibi beş saniyelik gecikme, bu örnek hizmet kodunda uygular:  
  
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
  
 İstemci hizmet aradığında, çağrı hizmet işlemin tamamlanmasını beklemeden döndürür.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir. İstemci hizmeti alma iletileri görebilirsiniz. Her konsol penceresinde hem hizmet hem de istemci kapatmak için ENTER tuşuna basın.  
  
 İstemci, bir istemci tek yönlü hizmet işlemleri için beklemez gösteren hizmet öncesinde tamamlanır. İstemci çıktı aşağıdaki gibidir:  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Aşağıdaki hizmet çıkış gösterilir:  
  
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
>  HTTP, tanım olarak, bir istek/yanıt protokoldür; bir istek yapıldığında, bir yanıt döndürdü. Bu, hatta HTTP üzerinden kullanıma sunulan bir tek yönlü hizmet işlemi için geçerlidir. İşlemi çağrıldığında, hizmet işlemi yürütüldü önce hizmet 202 bir HTTP durum kodunu döndürür. Bu durum kodu istek işleme için kabul edildi ancak işlem henüz tamamlanmadı anlamına gelir. İşlemi blokları kadar adlı istemci hizmetinden 202 yanıtı alır. Oturumları kullanmak üzere yapılandırılmış bir bağlamayı kullanarak birden fazla tek yönlü ileti gönderildiğinde bu bazı beklenmeyen davranışlara neden olabilir. `wsHttpBinding` Bu örnekte kullanılan bağlama oturumları kullanmak için bir güvenlik bağlamı oluşturmak için varsayılan olarak yapılandırılır. Varsayılan olarak, bir oturumdaki iletilerin gönderilmiş sıraya ulaşması garanti. Bir oturumda ikinci bir ileti gönderildiğinde, ilk iletiyi işleyene kadar bu nedenle, onu işlenmedi. Bu önceki iletisinin işlem tamamlanana kadar istemci 202 yanıt iletisi için almaz sonucudur. İstemci bu nedenle görünüyor her sonraki işlem çağrısı blok. Bu davranışı önlemek için bu örnek çalışma zamanının eşzamanlı olarak işlemek için ayrı örneklerini iletileri gönderme yapılandırır. Örnek kümeleri <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> için `PerCall` böylece her ileti başka bir örneği tarafından işlenebilir. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanmış `Multiple` iletileri gönderme aynı anda birden çok iş parçacığı izin vermek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  İstemciyi çalıştırın ve hizmeti kapatılıyor önce istemciyi aşağı kapatmak önce hizmeti çalıştırın. Hizmet kaldırılmıştır olduğundan istemci güvenlik oturumu düzgün bir şekilde kapatılamıyor olduğunda bu istemci özel durumu önler.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a>Ayrıca Bkz.
