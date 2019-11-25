---
title: Çift Yönlü
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 9b5d839bb4a678f105e128671fbda729e2c730b7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141797"
---
# <a name="duplex"></a><span data-ttu-id="a1f82-102">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="a1f82-102">Duplex</span></span>

<span data-ttu-id="a1f82-103">Çift yönlü örnek, bir çift yönlü sözleşmenin nasıl tanımlanacağını ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="a1f82-104">Çift yönlü iletişim, bir istemci bir hizmetle oturum kurduğunda ve hizmete, hizmetin istemciye geri ileti gönderebileceği bir kanal veren bir kanala sahip olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="a1f82-105">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a1f82-106">Bir çift yönlü sözleşme, istemciden hizmete bir birincil arabirim ve hizmetten istemciye bir geri çağırma arabirimi olarak tanımlanmış bir arabirim çifti olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="a1f82-107">Bu örnekte, `ICalculatorDuplex` arabirimi istemcinin matematik işlemleri gerçekleştirmesini sağlar ve sonucu bir oturum üzerinden hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="a1f82-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="a1f82-108">Hizmet, `ICalculatorDuplexCallback` arabirimindeki sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1f82-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="a1f82-109">Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="a1f82-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1f82-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a1f82-111">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a1f82-112">Çift yönlü sözleşme aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="a1f82-112">The duplex contract is defined as follows:</span></span>

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

<span data-ttu-id="a1f82-113">`CalculatorService` sınıfı, birincil `ICalculatorDuplex` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="a1f82-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="a1f82-114">Hizmet, her bir oturumun sonucunu korumak için <xref:System.ServiceModel.InstanceContextMode.PerSession> örnek modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="a1f82-115">İstemciye geri çağırma kanalına erişmek için `Callback` adlı bir özel özellik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="a1f82-116">Hizmet geri çağırma arabirimi aracılığıyla istemciye ileti göndermek için geri aramayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

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

<span data-ttu-id="a1f82-117">İstemci, hizmetten ileti almak için çift yönlü sözleşmenin geri çağırma arabirimini uygulayan bir sınıf sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="a1f82-118">Örnekte, `ICalculatorDuplexCallback` arabirimini uygulamak için bir `CallbackHandler` sınıfı tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

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

<span data-ttu-id="a1f82-119">Bir çift yönlü sözleşme için oluşturulan ara sunucu, oluşturma sırasında bir <xref:System.ServiceModel.InstanceContext> sağlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="a1f82-120">Bu <xref:System.ServiceModel.InstanceContext>, geri çağırma arabirimini uygulayan ve hizmetten geri gönderilen iletileri işleyen bir nesnenin sitesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="a1f82-121">Bir <xref:System.ServiceModel.InstanceContext> `CallbackHandler` sınıfının örneğiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a1f82-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="a1f82-122">Bu nesne hizmetten geri çağırma arabirimindeki istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="a1f82-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

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

<span data-ttu-id="a1f82-123">Yapılandırma, hem oturum iletişimini hem de çift yönlü iletişimi destekleyen bir bağlama sunacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="a1f82-124">`wsDualHttpBinding`, oturum iletişimini destekler ve her yön için bir tane olmak üzere çift HTTP bağlantısı sağlayarak çift yönlü iletişime olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1f82-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="a1f82-125">Hizmette, yapılandırmadaki tek fark, kullanılan bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="a1f82-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="a1f82-126">İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi sunucunun istemciye bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="a1f82-127">Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye geri döndürülen iletileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a1f82-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="a1f82-128">Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="a1f82-129">İstemcisini kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a1f82-129">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1f82-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a1f82-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a1f82-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a1f82-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a1f82-132">Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1f82-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="a1f82-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1f82-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a1f82-134">İstemciyi bir siteler arası yapılandırmada çalıştırırken, aşağıdaki şekilde gösterildiği gibi, "localhost" öğesini [\<client > öğesinin\<uç noktası >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) hem de `clientBaseAddress` [WSDualHttpBinding\<](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) öğesinin > [bağlama\<](../../configure-apps/file-schema/wcf/bindings.md) öğesinin `address` özniteliğinde değiştirdiğinizden emin olun:</span><span class="sxs-lookup"><span data-stu-id="a1f82-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

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
> <span data-ttu-id="a1f82-135">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1f82-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1f82-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a1f82-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a1f82-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="a1f82-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1f82-138">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1f82-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
