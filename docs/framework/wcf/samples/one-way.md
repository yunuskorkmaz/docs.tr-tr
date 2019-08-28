---
title: Tek Yönlü
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: f392fad0461dab4dff6e5e4efe0070d7017a700b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039051"
---
# <a name="one-way"></a>Tek Yönlü
Bu örnekte, tek yönlü hizmet işlemlerine sahip bir hizmet kişisi gösterilmektedir. İstemci, iki yönlü hizmet işlemlerinde olduğu gibi hizmet işlemlerinin tamamlanmasını beklemez. Bu örnek, [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) başlama ve `wsHttpBinding` bağlamayı kullanma tabanlıdır. Bu örnekteki hizmet, istekleri alan ve işleyen hizmeti gözlemlemenizi sağlayan, kendinden konak bir konsol uygulamasıdır. İstemci Ayrıca bir konsol uygulamasıdır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Tek yönlü bir hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın, her bir işleme <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulayın ve aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` gibi olarak ayarlayın:  
  
```csharp
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
  
 İstemcinin hizmet işlemlerinin tamamlanmasını beklemediğini göstermek için, bu örnekteki hizmet kodu aşağıdaki örnek kodda gösterildiği gibi beş saniyelik bir gecikme uygular:  
  
```csharp
// This service class implements the service contract.  
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
  
 İstemci hizmeti çağırdığında, çağrı, hizmet işleminin tamamlanmasını beklememeden geri döner.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Her bir konsol penceresinde, hem hizmeti hem de istemcisini kapatmak için ENTER tuşuna basın.  
  
 İstemci, bir istemcinin tek yönlü hizmet işlemlerinin tamamlanmasını beklemez olduğunu gösteren hizmetin önünde tamamlanır. İstemci çıktısı aşağıdaki gibidir:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Aşağıdaki hizmet çıktısı gösterilir:  
  
```console  
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
> HTTP, tanım, istek/yanıt protokolü; istek yapıldığında bir yanıt döndürülür. Bu, HTTP üzerinden kullanıma sunulan tek yönlü bir hizmet işlemi için de geçerlidir. İşlem çağrıldığında hizmet, hizmet işlemi yürütülmeden önce 202 HTTP durum kodunu döndürür. Bu durum kodu, isteğin işleme için kabul edildiği anlamına gelir, ancak işlem henüz tamamlanmadı. İşlemi çağıran istemci, hizmetten 202 yanıtını alıncaya kadar engeller. Bu, oturumları kullanmak üzere yapılandırılmış bir bağlama kullanılarak birden çok tek yönlü ileti gönderildiğinde beklenmeyen davranışlara neden olabilir. Bu `wsHttpBinding` örnekte kullanılan bağlama, varsayılan olarak bir güvenlik bağlamı oluşturmak için oturumları kullanacak şekilde yapılandırılmıştır. Varsayılan olarak, bir oturumdaki iletilerin gönderildikleri sırada gelmesi garanti edilir. Bu nedenle, bir oturumdaki ikinci ileti gönderildiğinde, ilk ileti işlenene kadar işlenmeyecektir. Bunun sonucunda, istemcinin önceki iletinin işlenmesi tamamlanana kadar bir ileti için 202 yanıtını almamıştır. Bu nedenle, istemci sonraki işlem çağrısındaki blok olarak görünür. Bu davranışı önlemek için, bu örnek çalışma zamanını, işleme için farklı örneklere eşzamanlı olarak ileti göndermek üzere yapılandırır. Örnek, her <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> iletinin `PerCall` farklı bir örnek tarafından işlenebilmesi için olarak ayarlanır. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, tek seferde `Multiple` ileti gönderimi için birden fazla iş parçacığına izin vermek üzere olarak ayarlanır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!NOTE]
> İstemcisini çalıştırmadan önce hizmeti çalıştırın ve hizmeti kapatmadan önce istemciyi kapatın. Bu, hizmet kaybolduğu için istemci güvenlik oturumunu düzgün bir şekilde kapatamadığında istemci özel durumunu önler.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
