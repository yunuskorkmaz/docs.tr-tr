---
title: Tek Yönlü
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183437"
---
# <a name="one-way"></a>Tek Yönlü
Bu örnek, tek yönlü hizmet işlemleri ile bir hizmet teması gösterir. İstemci, iki yönlü servis işlemlerinde olduğu gibi servis işlemlerinin tamamlanmasını beklemez. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanmaktadır ve `wsHttpBinding` bağlama kullanır. Bu örnekteki hizmet, istekleri alan ve işleyen hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır. İstemci aynı zamanda bir konsol uygulamasıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Tek yönlü hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın, <xref:System.ServiceModel.OperationContractAttribute> sınıfı <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` her işlem için uygulayın ve aşağıdaki örnek kodda gösterildiği şekilde ayarlayın:  
  
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
  
 İstemci hizmeti aradığında, arama hizmet işleminin tamamlanmasını beklemeden geri döner.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsolu pencerelerinde görüntülenir. Hizmetin istemciden ileti aldığını görebilirsiniz. Hem hizmeti hem de istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
 İstemci, tek yönlü hizmet işlemlerinin tamamlanmasını beklemediğini göstererek hizmeti önceden bitirir. İstemci çıktısı aşağıdaki gibidir:  
  
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
> HTTP, tanımı gereği, bir istek/yanıt protokolüdür; bir istek yapıldığında, bir yanıt döndürülür. Bu, HTTP üzerinden açığa çıkarılan tek yönlü bir hizmet işlemi için bile geçerlidir. İşlem çağrıldığında, hizmet işlemi yürütülmeden önce hizmet 202'nin BIR HTTP durum kodunu döndürür. Bu durum kodu, isteğin işleme için kabul edildiği, ancak işlemin henüz tamamlanmadığı anlamına gelir. Hizmetten 202 yanıtı alana kadar işlem bloklarını çağıran istemci. Bu, oturumları kullanmak üzere yapılandırılan bir bağlama kullanılarak birden çok tek yönlü ileti gönderildiğinde beklenmeyen bazı davranışlara neden olabilir. Bu `wsHttpBinding` örnekte kullanılan bağlama, bir güvenlik bağlamı oluşturmak için varsayılan olarak oturumları kullanmak üzere yapılandırılır. Varsayılan olarak, oturumdaki iletilerin gönderildikleri sırayla gelmesi garanti edilir. Bu nedenle, bir oturumdaki ikinci ileti gönderildiğinde, ilk ileti işlenene kadar işlenmez. Bunun sonucu, istemci önceki iletinin işlenmesi tamamlanana kadar bir ileti için 202 yanıtı almaz. Bu nedenle istemci, sonraki her işlem çağrısında engelleyebilir gibi görünür. Bu davranışı önlemek için, bu örnek çalışma zamanını iletileri aynı anda işleme için farklı örneklere göndermek için yapılandırır. Örnek, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> her `PerCall` iletinin farklı bir örnek tarafından işlenebileceği şekilde ayarlar. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>aynı `Multiple` anda birden fazla iş parçacığının ileti göndermesine izin verecek şekilde ayarlanmıştır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!NOTE]
> İstemciyi çalıştırmadan önce hizmeti çalıştırın ve hizmeti kapatmadan önce istemciyi kapatın. Bu, istemci hizmet gittiğinden güvenlik oturumunu temiz olarak kapatamıyorsa istemci özel durum önler.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
