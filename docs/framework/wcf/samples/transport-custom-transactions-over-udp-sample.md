---
title: 'Taşıma: UDP üzerinden Özel İşlemler Örneği'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: fcbc0ef6e747af953f545a06da965835595dd419
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423891"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Taşıma: UDP üzerinden Özel İşlemler Örneği
Bu örnek, Windows Communication Foundation (WCF)[taşıma genişletilebilirliğine](../../../../docs/framework/wcf/samples/transport-extensibility.md) [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğini temel alır. Özel işlem akışını desteklemek için UDP aktarım örneğini genişletir ve <xref:System.ServiceModel.Channels.TransactionMessageProperty> özelliğinin kullanımını gösterir.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>UDP aktarım örneğindeki kod değişiklikleri  
 İşlem akışını göstermek için örnek, `ICalculatorContract` için hizmet sözleşmesini `CalculatorService.Add()`için bir işlem kapsamı gerektirecek şekilde değiştirir. Örnek ayrıca, `Add` işleminin sözleşmesine ek bir `System.Guid` parametresi ekler. Bu parametre, istemci işleminin tanımlayıcısını hizmete geçirmek için kullanılır.  
  
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
  
 [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği, iletileri bir istemci ve hizmet arasında GEÇIRMEK için UDP paketlerini kullanır. [Taşıma: özel aktarım örneği](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) , iletileri aktarmak için aynı mekanizmayı kullanır, ancak bir işlem akışlı olduğunda, kodlanmış ILETIYLE birlikte UDP paketine eklenir.  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`, ileti varlığıyla geçerli işlemin yayma belirtecini birleştirmek ve bir arabelleğe yerleştirmek için yeni işlevsellik içeren bir yardımcı yöntemdir.  
  
 Özel işlem akışı taşıması için, istemci uygulamasının işlem akışı gerektirdiğini ve bu bilgileri WCF 'ye hangi hizmet işlemlerini iletmesini bilmelidir. Ayrıca, Kullanıcı işleminin Aktarım katmanına iletilmesi için bir mekanizma olmalıdır. Bu örnek, bu bilgileri almak için "WCF ileti denetçiler" kullanır. Burada uygulanan istemci ileti denetçisi, `TransactionFlowInspector`olarak adlandırılan aşağıdaki görevleri gerçekleştirir:  
  
- Belirli bir ileti eylemi için bir işlemin akışını mı yoksa (Bu `IsTxFlowRequiredForThisOperation()`gerçekleşir) belirler.  
  
- `TransactionFlowProperty`kullanarak geçerli ortam hareketini iletiye ekler (Bu işlem, `BeforeSendRequest()`için yapılır).  
  
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
  
 `TransactionFlowInspector` kendisine özel bir davranış kullanılarak çerçeveye geçirilir: `TransactionFlowBehavior`.  
  
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
  
 Önceki mekanizmaya sahip olan Kullanıcı kodu, hizmet işlemini çağırmadan önce bir `TransactionScope` oluşturur. İleti denetçisi, hizmet işlemine taşınmasının gerekli olması durumunda işlemin aktarıma geçirilmesini sağlar.  
  
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
  
 İstemciden bir UDP paketi aldıktan sonra, hizmet iletiyi ayıklayarak iletiyi ve muhtemelen bir işlemi geri alır.  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`, `TransactionMessageBuffer.WriteTransactionMessageBuffer()`tarafından gerçekleştirilen serileştirme sürecini ters yükleyen yardımcı yöntemdir.  
  
 Bir işlem içinde akıtıdıysa, `TransactionMessageProperty`iletiye eklenir.  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Bu, Dispatcher 'ın işlemi dağıtım zamanında almasını sağlar ve ileti tarafından belirtilen hizmet işlemini çağırırken onu kullanır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Geçerli örnek, [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine benzer şekilde çalıştırılmalıdır. Çalıştırmak için, hizmeti UdpTestService. exe ile başlatın. [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]çalıştırıyorsanız, hizmeti yükseltilmiş ayrıcalıklarla başlatmanız gerekir. Bunu yapmak için dosya Gezgini 'nde UdpTestService. exe ' ye sağ tıklayın ve **yönetici olarak çalıştır**' a tıklayın.  
  
3. Bu, aşağıdaki çıktıyı üretir.  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. Şu anda, istemcisini UdpTestClient. exe ' yi çalıştırarak başlatabilirsiniz. İstemci tarafından üretilen çıkış aşağıdaki gibidir.  
  
    ```console 
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. Hizmet çıktısı aşağıdaki gibidir.  
  
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
  
6. Hizmet uygulaması, `CalculatorService.Add()` işleminin `clientTransactionId` parametresinde, hizmet işleminin tanımlayıcısına kadar, istemci tarafından gönderilen işlem tanımlayıcısıyla eşleşiyorsa `The client transaction has flowed to the service` iletiyi görüntüler. Bir eşleşme yalnızca istemci işlemi hizmete akan ise elde edilir.  
  
7. İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara karşı çalıştırmak için, hizmet uygulaması penceresinde ENTER tuşuna basın ve ardından test istemcisini yeniden çalıştırın. Hizmette aşağıdaki çıktıyı görmeniz gerekir.  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. İstemcisini hizmete karşı çalıştırmak daha önce olduğu gibi benzer bir çıktı üretir.  
  
9. Svcutil. exe kullanarak istemci kodunu ve yapılandırmayı yeniden oluşturmak için, hizmet uygulamasını başlatın ve örnek kök dizininden aşağıdaki Svcutil. exe komutunu çalıştırın.  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Svcutil. exe ' nin `sampleProfileUdpBinding`için bağlama uzantısı yapılandırması üretmediğini unutmayın; el ile eklemeniz gerekir.  
  
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
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
