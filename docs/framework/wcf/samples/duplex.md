---
title: "Çift Yönlü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b0c5b5dc6bff78f06df75f4b5a9c5c3a8647dbf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="duplex"></a><span data-ttu-id="f77d2-102">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="f77d2-102">Duplex</span></span>
<span data-ttu-id="f77d2-103">Çift yönlü örnek tanımlamak ve çift yönlü sözleşme uygulamak gösterir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="f77d2-104">Çift yönlü iletişimi bir istemci bir hizmet ile oturum kurar ve hizmet üzerinde hizmet istemciye iletiler gönderebilir bir kanal sağlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="f77d2-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="f77d2-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f77d2-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="f77d2-106">Çift yönlü sözleşme arabirimleri çifti tanımlanan — birincil arabirim istemci hizmeti ve istemcisine hizmetinden bir geri çağırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f77d2-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="f77d2-107">Bu örnekte `ICalculatorDuplex` arabirimi sonucu oturumu üzerinden hesaplama matematik işlemleri gerçekleştirmek istemci izin verir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="f77d2-108">Sonuçları döndürür hizmet `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f77d2-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="f77d2-109">İstemci ile hizmet arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlam kurulmalıdır için çift yönlü sözleşme bir oturum gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f77d2-110">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f77d2-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f77d2-111">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="f77d2-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="f77d2-112">Çift yönlü sözleşme şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="f77d2-112">The duplex contract is defined as follows:</span></span>  
  
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
  
 <span data-ttu-id="f77d2-113">`CalculatorService` Sınıfı uygulayan birincil `ICalculatorDuplex` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f77d2-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="f77d2-114">Hizmet kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu.</span><span class="sxs-lookup"><span data-stu-id="f77d2-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="f77d2-115">Adlı özel özellik `Callback` istemciye geri çağırma kanal erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f77d2-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="f77d2-116">Hizmet, istemciye geri çağırma arabirimi üzerinden ileti göndermek için geri çağırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="f77d2-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>  
  
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
  
 <span data-ttu-id="f77d2-117">İstemci hizmetinden iletileri almak için çift yönlü sözleşme geri çağırma arabirimi uygulayan bir sınıf sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="f77d2-118">Örnekte, bir `CallbackHandler` sınıfı uygulamak için tanımlanmış `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f77d2-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>  
  
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
  
 <span data-ttu-id="f77d2-119">Çift yönlü sözleşme gerektirir oluşturan proxy bir <xref:System.ServiceModel.InstanceContext> yapım sağlanacak.</span><span class="sxs-lookup"><span data-stu-id="f77d2-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="f77d2-120">Bu <xref:System.ServiceModel.InstanceContext> site olarak geri çağırma arabirimini uygulayan ve geri hizmetinden gönderilen iletileri işleyen bir nesne için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f77d2-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="f77d2-121">Bir <xref:System.ServiceModel.InstanceContext> örneği ile oluşturulan `CallbackHandler` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f77d2-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="f77d2-122">Bu nesne hizmetinden geri çağırma arabirimi istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="f77d2-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
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
  
 <span data-ttu-id="f77d2-123">Yapılandırma oturum iletişim ve çift yönlü iletişimi destekleyen bir bağlama sağlamak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f77d2-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="f77d2-124">`wsDualHttpBinding` Oturum iletişimi destekler ve her yön için bir tane çift HTTP bağlantılarını sağlayarak çift yönlü iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f77d2-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="f77d2-125">Hizmette yalnızca yapılandırmasında kullanılan bağlama farktır.</span><span class="sxs-lookup"><span data-stu-id="f77d2-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="f77d2-126">İstemcide, sunucu istemciye aşağıdaki örnek yapılandırmada gösterildiği gibi bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="f77d2-127">Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimde istemciye döndürülen iletiler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f77d2-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="f77d2-128">Her bir ara sonucu, tüm işlemleri tamamlandıktan sonra tüm denklemi arkasından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="f77d2-129">İstemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f77d2-129">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f77d2-130">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f77d2-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f77d2-131">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f77d2-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f77d2-132">C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f77d2-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f77d2-133">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f77d2-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f77d2-134">İstemci makineler arası yapılandırmasında çalıştırırken, "localhost" hem de değiştirdiğinizden emin olun `address` özniteliği [endpoint](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi ve `clientBaseAddress` özniteliği [ \< bağlama >](../../../../docs/framework/misc/binding.md) öğesinin [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) öğesi için aşağıdaki gösterildiği gibi uygun makine adı:</span><span class="sxs-lookup"><span data-stu-id="f77d2-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [endpoint](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>  
  
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
>  <span data-ttu-id="f77d2-135">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f77d2-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f77d2-136">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f77d2-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f77d2-137">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f77d2-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f77d2-138">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f77d2-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a><span data-ttu-id="f77d2-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f77d2-139">See Also</span></span>
