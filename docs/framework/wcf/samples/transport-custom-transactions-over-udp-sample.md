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
# <a name="transport-custom-transactions-over-udp-sample"></a>Taşıma: UDP üzerinden Özel İşlemler Örneği
Bu örnek, Windows Communication Foundation (WCF)[Transport Extensibility'deki](../../../../docs/framework/wcf/samples/transport-extensibility.md) [UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine dayanmaktadır. Özel işlem akışını desteklemek için UDP Transport örneğini genişletir <xref:System.ServiceModel.Channels.TransactionMessageProperty> ve özelliğin kullanımını gösterir.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>UDP Taşıma Numunesindeki Kod Değişiklikleri  
 Hareket akışını göstermek için, `ICalculatorContract` `CalculatorService.Add()`örnek için bir işlem kapsamı gerektirecek şekilde hizmet sözleşmesini değiştirir. Örnek ayrıca `System.Guid` `Add` işlemin sözleşmesine fazladan bir parametre ekler. Bu parametre, istemci hareketinin tanımlayıcısını hizmete geçirmek için kullanılır.  
  
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
  
 [Aktarım: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği, istemci ve hizmet arasında ileti leri iletmek için UDP paketlerini kullanır. [Aktarım: Özel Aktarım Örneği](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) iletileri taşımak için aynı mekanizmayı kullanır, ancak bir hareket aktığında, kodlanmış iletiyle birlikte UDP paketine eklenir.  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`ileti varlığı ile geçerli hareket için yayılma belirteci birleştirmek ve bir arabellek içine yerleştirmek için yeni işlevsellik içeren bir yardımcı yöntemdir.  
  
 Özel işlem akışı aktarımı için istemci uygulamasının hangi hizmet işlemlerinin hareket akışı gerektirdiğini bilmesi ve bu bilgileri WCF'ye aktarması gerekir. Kullanıcı işlemini aktarım katmanına iletmek için bir mekanizma da olmalıdır. Bu örnek, bu bilgileri elde etmek için "WCF ileti denetçileri" kullanır. Burada uygulanan istemci ileti sile `TransactionFlowInspector`denetçisi, adı verilen, aşağıdaki görevleri gerçekleştirir:  
  
- Belirli bir ileti eylemi için bir işlemin aktaması gerekip gerekmediğini belirler (bu `IsTxFlowRequiredForThisOperation()`gerçekleşir).  
  
- Bir işlemin akması gerekiyorsa (bu `TransactionFlowProperty`işlem `BeforeSendRequest()`yapılır) kullanarak iletiye geçerli ortam işlemini bağlar.  
  
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
  
 Kendisi `TransactionFlowInspector` özel bir davranış kullanılarak çerçeveye `TransactionFlowBehavior`geçirilir: .  
  
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
  
 Önceki mekanizma yerinde olduğu için, kullanıcı kodu `TransactionScope` hizmet işlemini aramadan önce bir kod oluşturur. İleti denetçisi, hizmet işlemine akması gerektiğinde işlemin taşımaya geçirilmesini sağlar.  
  
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
  
 İstemciden bir UDP paketi aldıktan sonra, hizmet iletiyi ve büyük olasılıkla bir hareketi ayıklamak için paketi deserialize eder.  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()``TransactionMessageBuffer.WriteTransactionMessageBuffer()`tarafından gerçekleştirilen serileştirme işlemini tersine çeviren yardımcı yöntemdir.  
  
 Bir hareket aktıysa, `TransactionMessageProperty`'deki iletiye eklenir.  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Bu, sevk irsaliyesi'nin hareketi sevkiyat zamanında almasını ve ileti tarafından adreslenen servis işlemini ararken kullanmasını sağlar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
2. Geçerli [örnek, Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine benzer şekilde çalıştırılmalıdır. Çalıştırmak için, UdpTestService.exe ile hizmet başlatın. Windows Vista'yı çalıştırıyorsanız, hizmeti yüksek ayrıcalıklarla başlatmanız gerekir. Bunu yapmak için, Dosya Gezgini'nde UdpTestService.exe'ye sağ tıklayın ve **yönetici olarak çalıştır'ı**tıklatın.  
  
3. Bu, aşağıdaki çıktıyı üretir.  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. Şu anda, UdpTestClient.exe çalıştırarak istemci başlatabilirsiniz. İstemci tarafından üretilen çıktı aşağıdaki gibidir.  
  
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
  
6. Hizmet uygulaması, `The client transaction has flowed to the service` `clientTransactionId` `CalculatorService.Add()` istemci tarafından gönderilen hareket tanımlayıcısını, işlemin parametresinde, hizmet hareketinin tanımlayıcısına eşleştirebiliyorsa iletiyi görüntüler. Eşleşme, yalnızca istemci hareketi hizmete akmışsa elde edilir.  
  
7. İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara göre çalıştırmak için hizmet uygulama penceresinde ENTER tuşuna basın ve test istemcisini yeniden çalıştırın. Hizmette aşağıdaki çıktıyı görmeniz gerekir.  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. İstemciyi hizmete karşı çalıştırmak artık eskisi gibi benzer çıktı lar üretir.  
  
9. Svcutil.exe kullanarak istemci kodunu ve yapılandırmasını yeniden oluşturmak için servis uygulamasını başlatın ve ardından aşağıdaki Svcutil.exe komutunu örneğin kök dizininden çalıştırın.  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Svcutil.exe için bağlayıcı uzantısı yapılandırma oluşturmaz `sampleProfileUdpBinding`unutmayın; el ile eklemeniz gerekir.  
  
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
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
