---
title: Çift Yönlü
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 54b941541ae0da4900608e61f08f4ed99c9ea472
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265162"
---
# <a name="duplex"></a>Çift Yönlü
Çift yönlü örnek tanımlaması ve çift yönlü sözleşme nasıl gösterir. Bir istemci bir hizmeti ile bir oturumu oluşturur ve hizmet üzerinde hizmet istemciye iletileri gönderebilir bir kanal sağlar. çift yönlü iletişim gerçekleşir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Çift yönlü sözleşme çifti arabirimleri tanımlanan — birincil arabirim istemciden hizmete ve hizmetten geri çağırma arabirimi istemciye. Bu örnekte `ICalculatorDuplex` sonucu bir oturumu üzerinden hesaplama matematik işlemlerini gerçekleştirmek üzere istemci arabirimi sağlar. Sonuçlar döndürüyor hizmet `ICalculatorDuplexCallback` arabirimi. Hizmet ve istemci arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlamı yeniden kurulması için çift yönlü sözleşme bir oturumu gerektirir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır. Çift yönlü sözleşme şu şekilde tanımlanır:  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,  
                 CallbackContract=typeof(ICalculatorDuplexCallback))]  
public interface ICalculatorDuplex  
{  
    [OperationContract(IsOneWay = true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
}  
  
public interface ICalculatorDuplexCallback  
{  
    [OperationContract(IsOneWay = true)]  
    void Result(double result);  
    [OperationContract(IsOneWay = true)]  
    void Equation(string eqn);  
}  
```  
  
 `CalculatorService` Sınıfın uyguladığı birincil `ICalculatorDuplex` arabirimi. Hizmeti kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu. Adlı bir özel özellik `Callback` istemci geri çağırma kanala erişmek için kullanılır. Hizmet aracılığıyla geri çağırma arabirimi istemciye ileti göndermek için geri çağırma kullanır.  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorDuplex  
{  
    double result = 0.0D;  
    string equation;  
  
    public CalculatorService()  
    {  
        equation = result.ToString();  
    }  
  
    public void Clear()  
    {  
        Callback.Equation(equation + " = " + result.ToString());  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += " + " + n.ToString();  
        Callback.Result(result);  
    }  
    ...  
    ICalculatorDuplexCallback Callback  
    {  
        get  
        {  
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();  
        }  
    }  
}  
```  
  
 İstemci, hizmeti iletileri almak için çift yönlü sözleşme geri arama arabirimini uygulayan bir sınıf sağlamanız gerekir. Örnekte, bir `CallbackHandler` sınıfı uygulamak için tanımlanmış `ICalculatorDuplexCallback` arabirimi.  
  
```  
public class CallbackHandler : ICalculatorDuplexCallback  
{  
   public void Result(double result)  
   {  
      Console.WriteLine("Result({0})", result);  
   }  
  
   public void Equation(string equation)  
   {  
      Console.WriteLine("Equation({0}", equation);  
   }  
}  
```  
  
 Çift yönlü sözleşme gerektirir, oluşturulan proxy bir <xref:System.ServiceModel.InstanceContext> yapım sırasında sağlanacak. Bu <xref:System.ServiceModel.InstanceContext> site olarak geri arama arayüzü uygular ve hizmetinden gönderilen iletileri işleyen bir nesne için kullanılır. Bir <xref:System.ServiceModel.InstanceContext> örneği ile oluşturulmuş olan `CallbackHandler` sınıfı. Bu nesne, hizmetten geri çağırma arabirimi istemciye gönderilen iletileri işler.  
  
```  
// Construct InstanceContext to handle messages on callback interface.  
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());  
  
// Create a client.  
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);  
  
Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");  
Console.WriteLine();  
  
// Call the AddTo service operation.  
double value = 100.00D;  
client.AddTo(value);  
  
// Call the SubtractFrom service operation.  
value = 50.00D;  
client.SubtractFrom(value);  
  
// Call the MultiplyBy service operation.  
value = 17.65D;  
client.MultiplyBy(value);  
  
// Call the DivideBy service operation.  
value = 2.00D;  
client.DivideBy(value);  
  
// Complete equation.  
client.Clear();  
  
Console.ReadLine();  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 Yapılandırma, oturum iletişim hem çift yönlü iletişimi destekleyen bir bağlama sağlamak üzere değiştirildi. `wsDualHttpBinding` Oturumu iletişimi destekler ve her yön için bir ikili HTTP bağlantılarını sağlayarak çift yönlü iletişim sağlar. Hizmette kullanılan bağlama yapılandırmadaki tek fark var. İstemcide, sunucu istemciye aşağıdaki örnek yapılandırmada gösterildiği bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.  
  
```xml  
<client>  
  <endpoint name=""  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="wsDualHttpBinding"   
            bindingConfiguration="DuplexBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
</client>  
  
<bindings>  
  <!-- Configure a binding that support duplex communication. -->  
  <wsDualHttpBinding>  
    <binding name="DuplexBinding"   
             clientBaseAddress="http://localhost:8000/myClient/">  
    </binding>  
  </wsDualHttpBinding>  
</bindings>  
```  
  
 Örneği çalıştırmak için üzerinde hizmetinden gönderilen geri çağırma arabirimi istemciye döndürülen iletileri görürsünüz. Tüm işlemler tamamlandıktan sonra tüm denklemi ardından her ara sonuçlar görüntülenir. İstemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  İstemci bir çapraz makine yapılandırmaya çalışırken, hem de "localhost" değiştirdiğinizden emin olması `address` özniteliği [uç nokta](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi ve `clientBaseAddress` özniteliği [ \< bağlama >](../../../../docs/framework/misc/binding.md) öğesinin [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) öğesi ile gösterildiği gibi aşağıdaki uygun makine adı:  
  
    ```xml  
    <client>  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    </client>  
    ...  
    <wsDualHttpBinding>  
    <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">  
    </binding>  
    </wsDualHttpBinding>  
    ```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a>Ayrıca Bkz.
