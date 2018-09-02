---
title: 'Taşıma: UDP üzerinden Özel İşlemler Örneği'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: b3a105194ceef9d9091dfbc9521fd47978517f89
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452722"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="ab323-102">Taşıma: UDP üzerinden Özel İşlemler Örneği</span><span class="sxs-lookup"><span data-stu-id="ab323-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="ab323-103">Bu örnek dayanır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Windows Communication Foundation (WCF) örnek[taşıma genişletilebilirliği](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="ab323-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="ab323-104">UDP taşıma örnek özel işlem akışını destekleyecek şekilde genişletir ve kullanımını gösteren <xref:System.ServiceModel.Channels.TransactionMessageProperty> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ab323-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="ab323-105">UDP taşıma örnek içinde kod değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ab323-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="ab323-106">İşlem akışını göstermek için örnek için hizmet sözleşmesi değişiklikleri `ICalculatorContract` işlem kapsamı için gerektirecek şekilde `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="ab323-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="ab323-107">Örnek ayrıca ek ekler `System.Guid` anlaşmasını parametresi `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="ab323-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="ab323-108">Bu parametre, hizmete istemci işlem tanıtıcısı geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab323-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="ab323-109">[Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek, bir istemci ve hizmet arasında iletileri geçirmek için UDP paketlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab323-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="ab323-110">[Taşıma: özel aktarım örnek](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) aynı düzeneğini taşımak için iletileri, ancak bir işlem akışı yapılan işlemler, kodlanan ileti birlikte UDP paket içine eklenir.</span><span class="sxs-lookup"><span data-stu-id="ab323-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="ab323-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` Yayma belirteci için geçerli işlem iletisi varlıkla birleştirin ve bir arabelleğe yerleştirmek için yeni işlevler içeren bir yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ab323-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="ab323-112">İşlem akışını hangi hizmet işlemleri gerektirir, özel işlem akışı taşıma için istemci uygulaması bilmeniz gerekir ve bu bilgiler için WCF geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="ab323-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="ab323-113">Aktarım katmanı kullanıcı harekete ileten bir mekanizma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab323-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="ab323-114">Bu örnek "WCF ileti denetçileri" kullanır. Bu bilgiyi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ab323-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="ab323-115">Çağrılan burada uygulanan istemci ileti denetçisi `TransactionFlowInspector`, aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="ab323-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="ab323-116">Bir işlem için belirli bir ileti eylem aktarılan olup olmadığını belirler. (Bu yer alan `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="ab323-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="ab323-117">Geçerli ortam hareket kullanarak iletiyi ekler `TransactionFlowProperty`, bir işlem akışını gerekiyorsa (Bu yapılır `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="ab323-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```  
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
  
 <span data-ttu-id="ab323-118">`TransactionFlowInspector` Kendisini çerçevesi için özel bir davranış kullanılarak geçirilir: `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="ab323-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```  
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
  
 <span data-ttu-id="ab323-119">Yerinde önceki mekanizması ile kullanıcı kod oluşturur bir `TransactionScope` hizmet işlemi çağırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="ab323-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="ab323-120">İleti Inspector'ı hizmet işlemine akış gerekli olması durumunda işlem aktarmaya geçirilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab323-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```  
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
  
 <span data-ttu-id="ab323-121">İstemciden bir UDP paket aldıktan sonra hizmet, ileti ve büyük olasılıkla bir işlem ayıklamak için seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="ab323-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="ab323-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` yardımcı yöntemi tarafından gerçekleştirilen seri hale getirme işlemi tersine çevirir `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="ab323-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="ab323-123">Bir işlem eylemine aktarıldı, iletiye eklenir `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="ab323-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="ab323-124">Bu, dağıtıcı işlem gönderme zaman alır ve ileti tarafından ele alınan hizmet işlemi çağrılırken kullanan sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab323-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab323-125">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ab323-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ab323-126">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab323-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="ab323-127">Geçerli örneğe benzer şekilde çalıştırılması gereken [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="ab323-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="ab323-128">Çalıştırmak için hizmeti UdpTestService.exe ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="ab323-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="ab323-129">Çalıştırıyorsanız [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], yükseltilmiş ayrıcalıklarla hizmetini başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab323-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="ab323-130">Bunu yapmak için de UdpTestService.exe sağ [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] tıklatıp **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="ab323-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="ab323-131">Bu, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="ab323-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="ab323-132">Şu anda istemci UdpTestClient.exe çalıştırarak yeniden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab323-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="ab323-133">İstemci tarafından üretilen çıkış aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="ab323-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="ab323-134">Hizmet çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="ab323-134">The service output is as follows.</span></span>  
  
    ```  
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
  
6.  <span data-ttu-id="ab323-135">Hizmet uygulaması iletisini görüntüler `The client transaction has flowed to the service` de istemci tarafından gönderilen işlem tanımlayıcısı eşleşebilir, `clientTransactionId` parametresinin `CalculatorService.Add()` işlemi, hizmeti işlemi tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="ab323-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="ab323-136">İstemci işlem hizmetine yalnızca aktarılan değilse bir eşleştirme elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ab323-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="ab323-137">İstemci uygulama uç noktalarına karşı yapılandırmayla yayımlanan çalıştırmak için hizmet uygulama penceresinde ENTER tuşuna basın ve ardından test istemcisinin yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab323-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="ab323-138">Hizmette aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab323-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="ab323-139">İstemci karşı hizmet artık çalışır önceki gibi benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="ab323-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="ab323-140">İstemci kodu ve Svcutil.exe kullanarak yapılandırmayı yeniden oluşturmak için hizmet uygulamasını başlatın ve ardından örnek kök dizininden aşağıdaki Svcutil.exe komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab323-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="ab323-141">Bağlama uzantı yapılandırması için svcutil.exe oluşturmaz Not `sampleProfileUdpBinding`; el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab323-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
>  <span data-ttu-id="ab323-142">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ab323-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab323-143">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ab323-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ab323-144">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ab323-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab323-145">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ab323-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="ab323-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab323-146">See Also</span></span>  
 [<span data-ttu-id="ab323-147">Taşıma: UDP</span><span class="sxs-lookup"><span data-stu-id="ab323-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
