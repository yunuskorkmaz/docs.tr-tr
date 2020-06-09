---
title: Çift Yönlü
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 77eab6a4975fc67c20558a53f399c7e709215587
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575205"
---
# <a name="duplex"></a>Çift Yönlü

Çift yönlü örnek, bir çift yönlü sözleşmenin nasıl tanımlanacağını ve uygulanacağını gösterir. Çift yönlü iletişim, bir istemci bir hizmetle oturum kurduğunda ve hizmete, hizmetin istemciye geri ileti gönderebileceği bir kanal veren bir kanala sahip olduğunda gerçekleşir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır. Bir çift yönlü sözleşme, istemciden hizmete bir birincil arabirim ve hizmetten istemciye bir geri çağırma arabirimi olarak tanımlanmış bir arabirim çifti olarak tanımlanır. Bu örnekte, `ICalculatorDuplex` arabirimi istemcinin matematik işlemleri gerçekleştirmesini sağlar ve sonucu bir oturum üzerinden hesaplıyor. Hizmet, arabirimdeki sonuçları döndürür `ICalculatorDuplexCallback` . Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır. Çift yönlü sözleşme aşağıdaki gibi tanımlanır:

```csharp
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

`CalculatorService`Sınıfı, birincil arabirimini uygular `ICalculatorDuplex` . Hizmet, her bir <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumun sonucunu korumak için örnek modunu kullanır. Adlı özel özellik, `Callback` istemciye geri çağırma kanalına erişmek için kullanılır. Hizmet geri çağırma arabirimi aracılığıyla istemciye ileti göndermek için geri aramayı kullanır.

```csharp
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
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

İstemci, hizmetten ileti almak için çift yönlü sözleşmenin geri çağırma arabirimini uygulayan bir sınıf sağlamalıdır. Örnekte, `CallbackHandler` arabirimi uygulamak için bir sınıf tanımlanmıştır `ICalculatorDuplexCallback` .

```csharp
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

Bir çift yönlü sözleşme için oluşturulan ara sunucu, <xref:System.ServiceModel.InstanceContext> oluşturma sırasında bir için bir sağlanması gerekir. Bu, <xref:System.ServiceModel.InstanceContext> geri çağırma arabirimini uygulayan ve hizmetten geri gönderilen iletileri işleyen bir nesnenin sitesi olarak kullanılır. , <xref:System.ServiceModel.InstanceContext> Sınıfının bir örneğiyle oluşturulur `CallbackHandler` . Bu nesne hizmetten geri çağırma arabirimindeki istemciye gönderilen iletileri işler.

```csharp
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

Yapılandırma, hem oturum iletişimini hem de çift yönlü iletişimi destekleyen bir bağlama sunacak şekilde değiştirilmiştir. , `wsDualHttpBinding` Oturum iletişimini destekler ve her yön için bir tane olmak üzere ÇIFT http bağlantısı sağlayarak çift yönlü iletişime olanak sağlar. Hizmette, yapılandırmadaki tek fark, kullanılan bağlamadır. İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi sunucunun istemciye bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.

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

Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye geri döndürülen iletileri görürsünüz. Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir. İstemcisini kapatmak için ENTER tuşuna basın.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

    > [!IMPORTANT]
    > İstemciyi bir çapraz makine yapılandırmasında çalıştırırken, aşağıdaki şekilde gösterildiği gibi, öğesinin hem `address` öğesi özniteliğinde [ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md) hem de öğesi `clientBaseAddress` öğesinin özniteliği için [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) uygun makinenin adıyla birlikte "localhost" öğesini değiştirdiğinizden emin olun:

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
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
