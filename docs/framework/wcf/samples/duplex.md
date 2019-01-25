---
title: Çift Yönlü
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 73e95f3a0abe8d19644a004cdac16a2246a4502f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534010"
---
# <a name="duplex"></a><span data-ttu-id="26bbe-102">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="26bbe-102">Duplex</span></span>
<span data-ttu-id="26bbe-103">Çift yönlü örnek tanımlaması ve çift yönlü sözleşme nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="26bbe-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="26bbe-104">Bir istemci bir hizmeti ile bir oturumu oluşturur ve hizmet üzerinde hizmet istemciye iletileri gönderebilir bir kanal sağlar. çift yönlü iletişim gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="26bbe-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="26bbe-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="26bbe-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="26bbe-106">Çift yönlü sözleşme çifti arabirimleri tanımlanan — birincil arabirim istemciden hizmete ve hizmetten geri çağırma arabirimi istemciye.</span><span class="sxs-lookup"><span data-stu-id="26bbe-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="26bbe-107">Bu örnekte `ICalculatorDuplex` sonucu bir oturumu üzerinden hesaplama matematik işlemlerini gerçekleştirmek üzere istemci arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="26bbe-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="26bbe-108">Sonuçlar döndürüyor hizmet `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="26bbe-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="26bbe-109">Hizmet ve istemci arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlamı yeniden kurulması için çift yönlü sözleşme bir oturumu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="26bbe-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26bbe-110">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="26bbe-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="26bbe-111">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="26bbe-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="26bbe-112">Çift yönlü sözleşme şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="26bbe-112">The duplex contract is defined as follows:</span></span>  
  
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
  
 <span data-ttu-id="26bbe-113">`CalculatorService` Sınıfın uyguladığı birincil `ICalculatorDuplex` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="26bbe-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="26bbe-114">Hizmeti kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu.</span><span class="sxs-lookup"><span data-stu-id="26bbe-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="26bbe-115">Adlı bir özel özellik `Callback` istemci geri çağırma kanala erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26bbe-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="26bbe-116">Hizmet aracılığıyla geri çağırma arabirimi istemciye ileti göndermek için geri çağırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="26bbe-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>  
  
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
        Callback.Equation(equation + " = " + result.ToString());  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += " + " + n.ToString();  
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
  
 <span data-ttu-id="26bbe-117">İstemci, hizmeti iletileri almak için çift yönlü sözleşme geri arama arabirimini uygulayan bir sınıf sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26bbe-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="26bbe-118">Örnekte, bir `CallbackHandler` sınıfı uygulamak için tanımlanmış `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="26bbe-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>  
  
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
  
 <span data-ttu-id="26bbe-119">Çift yönlü sözleşme gerektirir, oluşturulan proxy bir <xref:System.ServiceModel.InstanceContext> yapım sırasında sağlanacak.</span><span class="sxs-lookup"><span data-stu-id="26bbe-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="26bbe-120">Bu <xref:System.ServiceModel.InstanceContext> site olarak geri arama arayüzü uygular ve hizmetinden gönderilen iletileri işleyen bir nesne için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26bbe-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="26bbe-121">Bir <xref:System.ServiceModel.InstanceContext> örneği ile oluşturulmuş olan `CallbackHandler` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="26bbe-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="26bbe-122">Bu nesne, hizmetten geri çağırma arabirimi istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="26bbe-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
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
  
 <span data-ttu-id="26bbe-123">Yapılandırma, oturum iletişim hem çift yönlü iletişimi destekleyen bir bağlama sağlamak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="26bbe-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="26bbe-124">`wsDualHttpBinding` Oturumu iletişimi destekler ve her yön için bir ikili HTTP bağlantılarını sağlayarak çift yönlü iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="26bbe-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="26bbe-125">Hizmette kullanılan bağlama yapılandırmadaki tek fark var.</span><span class="sxs-lookup"><span data-stu-id="26bbe-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="26bbe-126">İstemcide, sunucu istemciye aşağıdaki örnek yapılandırmada gösterildiği bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26bbe-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="26bbe-127">Örneği çalıştırmak için üzerinde hizmetinden gönderilen geri çağırma arabirimi istemciye döndürülen iletileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="26bbe-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="26bbe-128">Tüm işlemler tamamlandıktan sonra tüm denklemi ardından her ara sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="26bbe-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="26bbe-129">İstemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="26bbe-129">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26bbe-130">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="26bbe-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="26bbe-131">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26bbe-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="26bbe-132">Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26bbe-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="26bbe-133">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26bbe-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="26bbe-134">İstemci bir çapraz makine yapılandırmaya çalışırken, hem de "localhost" değiştirdiğinizden emin olması `address` özniteliği [uç nokta](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi ve `clientBaseAddress` özniteliği [ \< bağlama >](../../../../docs/framework/misc/binding.md) öğesinin [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) öğesi ile gösterildiği gibi aşağıdaki uygun makine adı:</span><span class="sxs-lookup"><span data-stu-id="26bbe-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [endpoint](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>  
  
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
>  <span data-ttu-id="26bbe-135">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="26bbe-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="26bbe-136">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="26bbe-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="26bbe-137">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="26bbe-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26bbe-138">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="26bbe-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a><span data-ttu-id="26bbe-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26bbe-139">See also</span></span>
