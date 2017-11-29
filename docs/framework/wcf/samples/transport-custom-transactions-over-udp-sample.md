---
title: "Taşıma: UDP üzerinden Özel İşlemler Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c1586b763d98776468322144019407c7c6cc27a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Taşıma: UDP üzerinden Özel İşlemler Örneği
Bu örnek dayanır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) içinde örnek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [taşıma genişletilebilirliği](../../../../docs/framework/wcf/samples/transport-extensibility.md). Özel işlem akışını desteklemek üzere UDP taşıma örnek genişletir ve kullanımını gösteren <xref:System.ServiceModel.Channels.TransactionMessageProperty> özelliği.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>UDP taşıma örnekteki kod değişiklikleri  
 İşlem akışını göstermek için hizmet sözleşmesi için örnek değişiklikleri `ICalculatorContract` için bir işlem kapsamı gerektirecek şekilde `CalculatorService.Add()`. Örnek ayrıca fazladan ekler `System.Guid` anlaşmasını parametresi `Add` işlemi. Bu parametre, hizmete istemci işlem tanıtıcısı geçirmek için kullanılır.  
  
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
  
 [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek iletileri bir istemci ve hizmet arasında geçirmek için UDP paketlerini kullanır. [Taşıma: özel aktarım örnek](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) aynı mekanizmayı kullanır iletileri taşıma için ancak bir işlem akıtılan tıklattığınızda, UDP paket kodlanmış ileti birlikte eklenir.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`ileti varlıkla geçerli işlem için yayma belirteci birleştirme ve bir arabelleğe yerleştirmek için yeni işlevler içeren bir yardımcı yöntemdir.  
  
 İşlem akışını hangi hizmet işlemleri gerektiren istemci uygulaması özel işlem akışı taşıma için bilmeniz gerekir ve bu bilgileri geçirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Aktarım katmanı kullanıcı hareketi iletmek için bir mekanizma olmalıdır. Bu örnekte "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti denetçiler" Bu bilgileri almak için. Çağrılan Burada, uygulandığı istemci ileti denetçisi `TransactionFlowInspector`, aşağıdaki görevleri gerçekleştirir:  
  
-   Bir işlem için belirli bir ileti eylemi aktarılan olup olmadığını belirler (Bu gerçekleşir `IsTxFlowRequiredForThisOperation()`).  
  
-   Geçerli ortam işlem kullanarak iletiyi iliştirir `TransactionFlowProperty`, bir işlem akışını gerekiyorsa (Bu yapılır `BeforeSendRequest()`).  
  
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
  
 `TransactionFlowInspector` Kendi özel davranış kullanarak framework geçirilir: `TransactionFlowBehavior`.  
  
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
  
 Kullanıcı kodu yerinde önceki mekanizması ile oluşturur bir `TransactionScope` hizmet işlemi çağırmadan önce. İleti denetçisi hizmet işlemi aktarılan gerekli olması durumunda işlem aktarmaya geçirilir sağlar.  
  
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
  
 UDP paket istemciden alındıktan sonra hizmet, ileti ve büyük olasılıkla bir işlem ayıklamak için çıkarır.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`tarafından gerçekleştirilen seri hale getirme işlemi ters bir yardımcı yöntemdir `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Bir işlem içinde eylemine aktarıldı yoksa iletiye eklenir `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Bu dağıtıcı işlemin gönderme zaman alır ve ileti tarafından ele hizmet işlemi çağrılırken kullanan sağlar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Geçerli örnek benzer şekilde çalıştırılması gerektiğini [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek. Çalıştırmak için UdpTestService.exe sahip hizmet başlatın. Çalıştırıyorsanız, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], yükseltilmiş ayrıcalıklarla hizmetini başlatmanız gerekir. Bunu yapmak için de UdpTestService.exe sağ [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] tıklatıp **yönetici olarak çalıştır**.  
  
3.  Bu şu çıkışı üretir.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  Şu anda istemci UdpTestClient.exe çalıştırarak başlatabilirsiniz. İstemci tarafından üretilen çıkış aşağıdaki gibidir.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  Hizmet çıktı aşağıdaki gibidir.  
  
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
  
6.  Hizmet uygulaması iletisini görüntüler `The client transaction has flowed to the service` , istemci tarafından gönderilen işlem tanımlayıcısı eşleşebilmesi durumunda `clientTransactionId` parametresinin `CalculatorService.Add()` hizmeti işlemi tanımlayıcısına işlemi. Yalnızca istemci işlemin hizmete akışı yapılan işlem varsa bir eşleşme elde edilir.  
  
7.  İstemci uygulaması yapılandırması'nı kullanarak yayımlanan uç noktalarına karşı çalıştırmak için hizmeti uygulama penceresinde ENTER tuşuna basın ve test istemcisi yeniden çalıştırın. Hizmette şu çıktı görmeniz gerekir.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  İstemci karşı hizmet artık çalışır önceki gibi benzer bir çıktı üretir.  
  
9. İstemci kodu ve Svcutil.exe kullanarak yapılandırmayı yeniden oluşturmak için hizmet uygulamasını başlatın ve sonra örnek kök dizininden aşağıdaki Svcutil.exe komutu çalıştırın.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Svcutil.exe bağlama uzantısı yapılandırması oluşturmaz Not `sampleProfileUdpBinding`; el ile eklemeniz gerekir.  
  
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
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
