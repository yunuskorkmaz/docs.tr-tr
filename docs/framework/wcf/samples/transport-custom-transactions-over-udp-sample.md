---
title: 'Taşıma: UDP üzerinden Özel İşlemler Örneği'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ce1e6f0aedff46aaf58e22d8c23c37b03f8789dd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596545"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="e6760-102">Taşıma: UDP üzerinden Özel İşlemler Örneği</span><span class="sxs-lookup"><span data-stu-id="e6760-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="e6760-103">Bu örnek, Windows Communication Foundation (WCF)[taşıma genişletilebilirliğine](transport-extensibility.md) [taşıma: UDP](transport-udp.md) örneğini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e6760-103">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="e6760-104">Özel işlem akışını desteklemek için UDP aktarım örneğini genişletir ve özelliğinin kullanımını gösterir <xref:System.ServiceModel.Channels.TransactionMessageProperty> .</span><span class="sxs-lookup"><span data-stu-id="e6760-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="e6760-105">UDP aktarım örneğindeki kod değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e6760-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="e6760-106">İşlem akışını göstermek için örnek, hizmet sözleşmesini `ICalculatorContract` için bir işlem kapsamı gerektirecek şekilde değiştirir `CalculatorService.Add()` .</span><span class="sxs-lookup"><span data-stu-id="e6760-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="e6760-107">Örnek ayrıca işlem sözleşmesine ek bir `System.Guid` parametre ekler `Add` .</span><span class="sxs-lookup"><span data-stu-id="e6760-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="e6760-108">Bu parametre, istemci işleminin tanımlayıcısını hizmete geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6760-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="e6760-109">[Taşıma: UDP](transport-udp.md) örneği, iletileri bir istemci ve hizmet arasında GEÇIRMEK için UDP paketlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6760-109">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="e6760-110">[Taşıma: özel aktarım örneği](transport-custom-transactions-over-udp-sample.md) , iletileri aktarmak için aynı mekanizmayı kullanır, ancak bir işlem akışlı olduğunda, kodlanmış ILETIYLE birlikte UDP paketine eklenir.</span><span class="sxs-lookup"><span data-stu-id="e6760-110">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="e6760-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`, ileti varlığıyla geçerli işlemin yayma belirtecini birleştirmek ve bir arabelleğe yerleştirmek için yeni işlevsellik içeren bir yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e6760-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="e6760-112">Özel işlem akışı taşıması için, istemci uygulamasının işlem akışı gerektirdiğini ve bu bilgileri WCF 'ye hangi hizmet işlemlerini iletmesini bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e6760-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="e6760-113">Ayrıca, Kullanıcı işleminin Aktarım katmanına iletilmesi için bir mekanizma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6760-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="e6760-114">Bu örnek, bu bilgileri almak için "WCF ileti denetçiler" kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6760-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="e6760-115">Burada uygulanan istemci ileti denetçisi `TransactionFlowInspector` aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e6760-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="e6760-116">Belirli bir ileti eylemi için bir işlemin akışını isteyip istemediğinizi belirler (Bu, içinde gerçekleşir `IsTxFlowRequiredForThisOperation()` ).</span><span class="sxs-lookup"><span data-stu-id="e6760-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="e6760-117">`TransactionFlowProperty`, Bir işlemin akan olması gerekiyorsa (Bu, ' de yapılır), geçerli ortam hareketini iletiye iliştirir `BeforeSendRequest()` .</span><span class="sxs-lookup"><span data-stu-id="e6760-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="e6760-118">`TransactionFlowInspector`Kendisine özel bir davranış kullanılarak Framework 'e geçirilir: `TransactionFlowBehavior` .</span><span class="sxs-lookup"><span data-stu-id="e6760-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="e6760-119">Yukarıdaki mekanizmaya sahip olan Kullanıcı kodu, `TransactionScope` hizmet işlemini çağırmadan önce bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6760-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="e6760-120">İleti denetçisi, hizmet işlemine taşınmasının gerekli olması durumunda işlemin aktarıma geçirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6760-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="e6760-121">İstemciden bir UDP paketi aldıktan sonra, hizmet iletiyi ayıklayarak iletiyi ve muhtemelen bir işlemi geri alır.</span><span class="sxs-lookup"><span data-stu-id="e6760-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="e6760-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`, tarafından gerçekleştirilen serileştirme sürecini tersine çevirecek yardımcı yöntemdir `TransactionMessageBuffer.WriteTransactionMessageBuffer()` .</span><span class="sxs-lookup"><span data-stu-id="e6760-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="e6760-123">Bir işlem içinde akan ise, içindeki iletiye eklenir `TransactionMessageProperty` .</span><span class="sxs-lookup"><span data-stu-id="e6760-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="e6760-124">Bu, Dispatcher 'ın işlemi dağıtım zamanında almasını sağlar ve ileti tarafından belirtilen hizmet işlemini çağırırken onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6760-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6760-125">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e6760-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e6760-126">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e6760-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e6760-127">Geçerli örnek, [Transport: UDP](transport-udp.md) örneğine benzer şekilde çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6760-127">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="e6760-128">Çalıştırmak için, hizmeti UdpTestService. exe ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="e6760-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="e6760-129">Windows Vista çalıştırıyorsanız, hizmeti yükseltilmiş ayrıcalıklarla başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6760-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="e6760-130">Bunu yapmak için dosya Gezgini 'nde UdpTestService. exe ' ye sağ tıklayın ve **yönetici olarak çalıştır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e6760-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="e6760-131">Bu, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="e6760-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="e6760-132">Şu anda, istemcisini UdpTestClient. exe ' yi çalıştırarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6760-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="e6760-133">İstemci tarafından üretilen çıkış aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="e6760-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="e6760-134">Hizmet çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="e6760-134">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="e6760-135">Hizmet uygulaması, `The client transaction has flowed to the service` istemcinin tarafından gönderilen işlem tanımlayıcısıyla, `clientTransactionId` işlemin parametresinde, `CalculatorService.Add()` hizmet işleminin tanımlayıcısına kadar bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e6760-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="e6760-136">Bir eşleşme yalnızca istemci işlemi hizmete akan ise elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e6760-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="e6760-137">İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara karşı çalıştırmak için, hizmet uygulaması penceresinde ENTER tuşuna basın ve ardından test istemcisini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6760-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="e6760-138">Hizmette aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6760-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="e6760-139">İstemcisini hizmete karşı çalıştırmak daha önce olduğu gibi benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="e6760-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="e6760-140">Svcutil. exe kullanarak istemci kodunu ve yapılandırmayı yeniden oluşturmak için, hizmet uygulamasını başlatın ve örnek kök dizininden aşağıdaki Svcutil. exe komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6760-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="e6760-141">Svcutil. exe ' nin için bağlama uzantısı yapılandırması oluşturmadığına `sampleProfileUdpBinding` ; bunu el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6760-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="e6760-142">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6760-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6760-143">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e6760-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e6760-144">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e6760-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6760-145">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e6760-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="e6760-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6760-146">See also</span></span>

- [<span data-ttu-id="e6760-147">Taşıma: UDP</span><span class="sxs-lookup"><span data-stu-id="e6760-147">Transport: UDP</span></span>](transport-udp.md)
