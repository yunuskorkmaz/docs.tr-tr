---
title: İleti Bağıntısı
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e4cd5dfd6f03370a408dc6f8fb39c983db3d43df
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061172"
---
# <a name="message-correlation"></a>İleti Bağıntısı
Bu örnek nasıl bir Message Queuing (MSMQ) uygulaması bir MSMQ iletisinin bir Windows Communication Foundation (WCF) hizmetine gönderebilir ve iletileri bir istek/yanıt senaryosunda gönderen ve alıcı uygulamalar arasında nasıl eşleştirilebilir gösterir. Bu örnek MsmqIntegrationBinding bağlama kullanır. Bu durumda, alan hizmet kuyruğa alınmış iletileri gözlemleyin olanak sağlamak için şirket içinde barındırılan bir konsol uygulaması hizmetidir. K  
  
 Hizmet gönderenden alınan iletiyi işleyen ve gönderene bir yanıt iletisi gönderir. Başlangıçta gönderilen isteği aldığı yanıtı gönderen ilişkilendirir. `MessageID` Ve `CorrelationID` iletinin özellikleri, istek ve yanıt iletilerinin ilişkilendirmek için kullanılır.  
  
 `IOrderProcessor` Hizmet sözleşmesini tanımlayan queuing ile kullanım için uygun olan bir tek yönlü hizmet işlemi. Bir MSMQ iletisinin bir eylem üst bilgisi olmadığından, işlem sözleşmeleri farklı MSMQ iletileri otomatik olarak eşlemeye mümkün değildir. Bu nedenle, olabilir yalnızca bir işlem anlaşması bu durumda. Tanımlamak istiyorsanız hizmette daha fazla işlem sözleşmeleri, uygulamanın hangi üstbilgisinde MSMQ (örneğin, etiket veya Correlationıd) ileti göndermek için hangi işlem anlaşması karar vermek için kullanılabilir bilgileri sağlamanız gerekir. Bu gösterilmiştir [özel Demux](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 MSMQ iletisinin, ayrıca hangi üstbilgileri da işlem anlaşması farklı parametrelerle eşlenir bilgi içermiyor. Bu nedenle, işlem anlaşması içinde yalnızca bir parametresi olabilir. Parametre türüdür <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` temel alınan MSMQ iletisi içerir. ' % S'tür "T" içinde `MsmqMessage<T>` sınıf MSMQ ileti gövdesine seri verileri temsil eder. Bu örnekte `PurchaseOrder` türü MSMQ ileti gövdesine seri.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 Hizmet işlemi, satın alma siparişi işleyen ve satın alma siparişi ve durumunu içeriğini hizmet konsol penceresinde görüntüler. <xref:System.ServiceModel.OperationBehaviorAttribute> İşlemi sıranın ile bir işlem listeleme ve işlem döndürdüğünde işlem tamamlandı olarak işaretlemek için yapılandırır. `PurchaseOrder` Hizmet tarafından işlenmesi gereken sipariş ayrıntılarını içerir.  

```csharp
// Service class that implements the service contract.  
public class OrderProcessorService : IOrderProcessor  
{  
   [OperationBehavior(TransactionScopeRequired = true,   
          TransactionAutoComplete = true)]  
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)  
   {  
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;  
       Random statusIndexer = new Random();  
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
       Console.WriteLine("Processing {0} ", po);  
       //Send a response to the client that the order has been received   
         and is pending fullfillment.   
       SendResponse(ordermsg);  
    }  
  
    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)  
    {  
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");  
  
        //Set the correlation ID such that the client can correlate the response to the order.  
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);  
        orderResponsemsg.CorrelationId = ordermsg.Id;  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.SendOrderResponse(orderResponsemsg);  
            scope.Complete();  
        }  
  
        client.Close();  
    }  
}  
```

 Özel bir istemci hizmetin kullandığı `OrderResponseClient` MSMQ ileti sırasına göndermek için. Alan ve iletiyi işleyen bir uygulama bir MSMQ uygulama ve WCF uygulaması olduğundan iki uygulama arasında örtük hizmet sözleşme yok. Bu nedenle bu senaryoda Svcutil.exe aracını kullanarak bir proxy oluşturamıyoruz.  
  
 Özel ara sunucu temel olarak kullanan tüm WCF uygulamaları aynı olduğundan `msmqIntegrationBinding` ileti göndermek için bağlama. Diğer proxy'leri, bir dizi hizmet işlemleri içermez. Bir gönderme iletisi yalnızca işlemdir.  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderResponse  
{  
  
    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]  
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse  
{  
  
    public OrderResponseClient()  
    { }  
  
    public OrderResponseClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SendOrderResponse(msg);  
    }  
}  
```

 Kendi kendine barındırılan bir hizmettir. MSMQ tümleştirme taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmeti içeren <xref:System.Messaging> kod kuyruk varlığını denetleyin ve gerekirse oluşturun. Kuyruk adı yapılandırma dosyasından okunur.  

```csharp
public static void Main()  
{  
       // Get the MSMQ queue name from application settings in configuration.  
      string queueName =   
                ConfigurationManager.AppSettings["orderQueueName"];  
      // Create the transacted MSMQ queue if necessary.  
      if (!MessageQueue.Exists(queueName))  
                MessageQueue.Create(queueName, true);  
     // Create a ServiceHost for the OrderProcessorService type.  
     using (ServiceHost serviceHost = new   
                   ServiceHost(typeof(OrderProcessorService)))  
     {  
            serviceHost.Open();  
            // The service can now be accessed.  
            Console.WriteLine("The service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.ReadLine();  
            // Close the ServiceHost to shutdown the service.  
            serviceHost.Close();  
      }  
}  
```
  
 Sipariş istekleri gönderildiği MSMQ sırası yapılandırma dosyasının appSettings bölümünde belirtilir. İstemci ve hizmet uç noktaları yapılandırma dosyasının system.serviceModel bölümünde tanımlanır. Her ikisini birden belirtin `msmqIntegrationbinding` bağlama.  
  
```xml  
<appSettings>  
  <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
  
<system.serviceModel>  
  <client>  
    <endpoint    name="OrderResponseEndpoint"   
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"  
              binding="msmqIntegrationBinding"  
              bindingConfiguration="OrderProcessorBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">  
    </endpoint>  
  </client>  
  
  <services>  
    <service   
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"  
                            binding="msmqIntegrationBinding"  
                bindingConfiguration="OrderProcessorBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">  
      </endpoint>  
    </service>  
  </services>  
  
  <bindings>  
    <msmqIntegrationBinding>  
      <binding name="OrderProcessorBinding" >  
        <security mode="None" />  
      </binding>  
    </msmqIntegrationBinding>  
  </bindings>  
  
</system.serviceModel>  
```  
  
 İstemci uygulaması kullanan <xref:System.Messaging> dayanıklı ve işlem tabanlı ileti kuyruğa göndermek için. İleti gövdesi, satın alma siparişi içerir.  

```csharp
static void PlaceOrder()  
{  
    //Connect to the queue  
    MessageQueue orderQueue =   
            new MessageQueue(  
                    ConfigurationManager.AppSettings["orderQueueName"])   
    // Create the purchase order.  
    PurchaseOrder po = new PurchaseOrder();  
    po.CustomerId = "somecustomer.com";  
    po.PONumber = Guid.NewGuid().ToString();  
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
    lineItem1.ProductId = "Blue Widget";  
    lineItem1.Quantity = 54;  
    lineItem1.UnitCost = 29.99F;  
  
    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
    lineItem2.ProductId = "Red Widget";  
    lineItem2.Quantity = 890;  
    lineItem2.UnitCost = 45.89F;  
  
    po.orderLineItems = new PurchaseOrderLineItem[2];  
    po.orderLineItems[0] = lineItem1;  
    po.orderLineItems[1] = lineItem2;  
  
    Message msg = new Message();  
    msg.UseDeadLetterQueue = true;  
    msg.Body = po;  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new      
     TransactionScope(TransactionScopeOption.Required))  
    {  
        // Submit the purchase order.  
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
        // Complete the transaction.  
        scope.Complete();  
    }  
    //Save the messageID for order response correlation.  
    orderMessageID = msg.Id;  
    Console.WriteLine("Placed the order, waiting for response...");  
}  
```

 Sırası yanıtlarını alındığı MSMQ sırası, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.  
  
> [!NOTE]
>  Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. WCF uç nokta adresini msmq.formatname düzenini belirtir ve "localhost" yerel bilgisayarı kullanır. MSMQ yönergelerine göre uri'sindeki msmq.formatname düzgün biçimlendirilmiş biçim adı izler.  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 İstemci uygulama kaydeder `messageID` siparişi istek iletisinin hizmetine gönderir ve hizmetten bir yanıt bekler. Bir yanıt kuyrukta geldikten istemci, gönderilen kullanarak ileti ile ilişkilendirir `correlationID` içeren ileti özelliği `messageID` sırasını iletisi başlangıçta gönderilen istemci.  

```csharp
static void DisplayOrderStatus()  
{  
    MessageQueue orderResponseQueue = new   
     MessageQueue(ConfigurationManager.AppSettings              
                  ["orderResponseQueueName"]);  
    //Create a transaction scope.  
    bool responseReceived = false;  
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;  
    while (!responseReceived)  
    {  
       Message responseMsg;  
       using (TransactionScope scope2 = new    
         TransactionScope(TransactionScopeOption.Required))  
       {  
          //Receive the Order Response message.  
          responseMsg =   
              orderResponseQueue.Receive  
                   (MessageQueueTransactionType.Automatic);  
          scope2.Complete();  
     }  
     responseMsg.Formatter = new   
     System.Messaging.XmlMessageFormatter(new Type[] {   
         typeof(PurchaseOrder) });  
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;  
    //Check if the response is for the order placed.  
    if (orderMessageID == responseMsg.CorrelationId)  
    {  
       responseReceived = true;  
       Console.WriteLine("Status of current Order: OrderID-{0},Order   
            Status-{1}", responsepo.PONumber, responsepo.Status);  
    }  
    else  
    {  
       Console.WriteLine("Status of previous Order: OrderID-{0},Order    
            Status-{1}", responsepo.PONumber, responsepo.Status);  
    }  
  }  
}  
```

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. Hizmet alma iletileri bir yanıtı istemciye geri gönderir ve istemci görebilirsiniz. Hizmetten alınan yanıtı istemciye görüntüler. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
> [!NOTE]
>  Bu örnek, Message Queuing (MSMQ), yükleme gerektirir. Ayrıca Bkz bölümündeki MSMQ yükleme yönergelerine bakın.  
  
### <a name="to-setup-build-and-run-the-sample"></a>Kurulum, derleme ve örneği çalıştırmak için  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletin **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek bilgisayarlı yapılandırmada örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet program dosyaları \service\bin\ klasöründen dile özgü klasörü altında hizmet bilgisayara kopyalayın.  
  
2.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.  
  
3.  Yerine hizmeti bilgisayarın adını belirtmek için orderQueueName Client.exe.config dosyasında değiştirme ".".  
  
4.  Service.exe.config dosyasında yerine istemci bilgisayarın adını belirtmek için istemci uç nokta adresini Değiştir ".".  
  
5.  Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.  
  
6.  İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968)
