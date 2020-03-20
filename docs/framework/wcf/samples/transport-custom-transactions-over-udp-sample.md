---
title: 'Taşıma: UDP üzerinden Özel İşlemler Örneği'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ba9fb91623606d3aaba5ba56784b20bb92d343a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143804"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="33e57-102">Taşıma: UDP üzerinden Özel İşlemler Örneği</span><span class="sxs-lookup"><span data-stu-id="33e57-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="33e57-103">Bu örnek, Windows Communication Foundation (WCF)[Transport Extensibility'deki](../../../../docs/framework/wcf/samples/transport-extensibility.md) [UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33e57-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="33e57-104">Özel işlem akışını desteklemek için UDP Transport örneğini genişletir <xref:System.ServiceModel.Channels.TransactionMessageProperty> ve özelliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33e57-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="33e57-105">UDP Taşıma Numunesindeki Kod Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="33e57-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="33e57-106">Hareket akışını göstermek için, `ICalculatorContract` `CalculatorService.Add()`örnek için bir işlem kapsamı gerektirecek şekilde hizmet sözleşmesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="33e57-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="33e57-107">Örnek ayrıca `System.Guid` `Add` işlemin sözleşmesine fazladan bir parametre ekler.</span><span class="sxs-lookup"><span data-stu-id="33e57-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="33e57-108">Bu parametre, istemci hareketinin tanımlayıcısını hizmete geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33e57-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="33e57-109">[Aktarım: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği, istemci ve hizmet arasında ileti leri iletmek için UDP paketlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="33e57-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="33e57-110">[Aktarım: Özel Aktarım Örneği](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) iletileri taşımak için aynı mekanizmayı kullanır, ancak bir hareket aktığında, kodlanmış iletiyle birlikte UDP paketine eklenir.</span><span class="sxs-lookup"><span data-stu-id="33e57-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="33e57-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`ileti varlığı ile geçerli hareket için yayılma belirteci birleştirmek ve bir arabellek içine yerleştirmek için yeni işlevsellik içeren bir yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="33e57-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="33e57-112">Özel işlem akışı aktarımı için istemci uygulamasının hangi hizmet işlemlerinin hareket akışı gerektirdiğini bilmesi ve bu bilgileri WCF'ye aktarması gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e57-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="33e57-113">Kullanıcı işlemini aktarım katmanına iletmek için bir mekanizma da olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33e57-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="33e57-114">Bu örnek, bu bilgileri elde etmek için "WCF ileti denetçileri" kullanır.</span><span class="sxs-lookup"><span data-stu-id="33e57-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="33e57-115">Burada uygulanan istemci ileti sile `TransactionFlowInspector`denetçisi, adı verilen, aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="33e57-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="33e57-116">Belirli bir ileti eylemi için bir işlemin aktaması gerekip gerekmediğini belirler (bu `IsTxFlowRequiredForThisOperation()`gerçekleşir).</span><span class="sxs-lookup"><span data-stu-id="33e57-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="33e57-117">Bir işlemin akması gerekiyorsa (bu `TransactionFlowProperty`işlem `BeforeSendRequest()`yapılır) kullanarak iletiye geçerli ortam işlemini bağlar.</span><span class="sxs-lookup"><span data-stu-id="33e57-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="33e57-118">Kendisi `TransactionFlowInspector` özel bir davranış kullanılarak çerçeveye `TransactionFlowBehavior`geçirilir: .</span><span class="sxs-lookup"><span data-stu-id="33e57-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="33e57-119">Önceki mekanizma yerinde olduğu için, kullanıcı kodu `TransactionScope` hizmet işlemini aramadan önce bir kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33e57-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="33e57-120">İleti denetçisi, hizmet işlemine akması gerektiğinde işlemin taşımaya geçirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="33e57-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="33e57-121">İstemciden bir UDP paketi aldıktan sonra, hizmet iletiyi ve büyük olasılıkla bir hareketi ayıklamak için paketi deserialize eder.</span><span class="sxs-lookup"><span data-stu-id="33e57-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="33e57-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()``TransactionMessageBuffer.WriteTransactionMessageBuffer()`tarafından gerçekleştirilen serileştirme işlemini tersine çeviren yardımcı yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="33e57-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="33e57-123">Bir hareket aktıysa, `TransactionMessageProperty`'deki iletiye eklenir.</span><span class="sxs-lookup"><span data-stu-id="33e57-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="33e57-124">Bu, sevk irsaliyesi'nin hareketi sevkiyat zamanında almasını ve ileti tarafından adreslenen servis işlemini ararken kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="33e57-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33e57-125">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="33e57-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="33e57-126">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="33e57-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="33e57-127">Geçerli [örnek, Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine benzer şekilde çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33e57-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="33e57-128">Çalıştırmak için, UdpTestService.exe ile hizmet başlatın.</span><span class="sxs-lookup"><span data-stu-id="33e57-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="33e57-129">Windows Vista'yı çalıştırıyorsanız, hizmeti yüksek ayrıcalıklarla başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e57-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="33e57-130">Bunu yapmak için, Dosya Gezgini'nde UdpTestService.exe'ye sağ tıklayın ve **yönetici olarak çalıştır'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="33e57-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="33e57-131">Bu, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="33e57-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="33e57-132">Şu anda, UdpTestClient.exe çalıştırarak istemci başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e57-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="33e57-133">İstemci tarafından üretilen çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="33e57-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="33e57-134">Hizmet çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="33e57-134">The service output is as follows.</span></span>  
  
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
  
6. <span data-ttu-id="33e57-135">Hizmet uygulaması, `The client transaction has flowed to the service` `clientTransactionId` `CalculatorService.Add()` istemci tarafından gönderilen hareket tanımlayıcısını, işlemin parametresinde, hizmet hareketinin tanımlayıcısına eşleştirebiliyorsa iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="33e57-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="33e57-136">Eşleşme, yalnızca istemci hareketi hizmete akmışsa elde edilir.</span><span class="sxs-lookup"><span data-stu-id="33e57-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="33e57-137">İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara göre çalıştırmak için hizmet uygulama penceresinde ENTER tuşuna basın ve test istemcisini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33e57-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="33e57-138">Hizmette aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e57-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="33e57-139">İstemciyi hizmete karşı çalıştırmak artık eskisi gibi benzer çıktı lar üretir.</span><span class="sxs-lookup"><span data-stu-id="33e57-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="33e57-140">Svcutil.exe kullanarak istemci kodunu ve yapılandırmasını yeniden oluşturmak için servis uygulamasını başlatın ve ardından aşağıdaki Svcutil.exe komutunu örneğin kök dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33e57-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="33e57-141">Svcutil.exe için bağlayıcı uzantısı yapılandırma oluşturmaz `sampleProfileUdpBinding`unutmayın; el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e57-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
> <span data-ttu-id="33e57-142">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="33e57-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33e57-143">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="33e57-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="33e57-144">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="33e57-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33e57-145">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="33e57-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="33e57-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33e57-146">See also</span></span>

- [<span data-ttu-id="33e57-147">Taşıma: UDP</span><span class="sxs-lookup"><span data-stu-id="33e57-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
