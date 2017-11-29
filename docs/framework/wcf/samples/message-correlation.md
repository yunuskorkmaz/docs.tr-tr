---
title: "İleti Bağıntısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54b7b7d9ba247f329fbf3c9040c641e3194d3bfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="message-correlation"></a>İleti Bağıntısı
Bu örnek bir Message Queuing (MSMQ) uygulaması bir MSMQ iletisi nasıl gönderebilirsiniz gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti ve nasıl iletileri bir istek/yanıt senaryosunda göndereni ve alıcısı uygulamalar arasında ilişkili olabilir. Bu örnek MsmqIntegrationBinding bağlama kullanır. Bu durumda, alan hizmetini sıraya alınan iletileri gözlemleyin olanak tanımak için bir kendi kendini barındıran konsol uygulaması hizmetidir. K  
  
 Hizmet gönderenden alınan ileti işler ve gönderene bir yanıt iletisi gönderir. Gönderenin karşılık gelen yanıtı başlangıçta gönderilen isteği alındı. `MessageID` Ve `CorrelationID` ileti özelliklerini istek ve yanıt iletileri ilişkilendirmek için kullanılır.  
  
 `IOrderProcessor` Hizmet sözleşmesini tanımlayan queuing ile kullanım için uygun bir tek yönlü hizmet işlemi. Farklı MSMQ iletileri işlemi sözleşmeleri için otomatik olarak eşlemeye mümkün değildir bir MSMQ iletisinin bir eylem üstbilgisi yok. Bu nedenle, olabilir yalnızca bir işlem sözleşmesi bu durumda. Tanımlamak istiyorsanız daha fazla işlem hizmetinde sözleşmeler, uygulamanın hangi MSMQ üstbilgisinde (örneğin, etiket veya correlationıd değeri) ileti gönderme işlemi sözleşmeyi karar vermek için kullanılabilir bilgileri sağlamanız gerekir. Bu, gösterilmiştir [özel Demux](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 MSMQ iletisi aldığını üstbilgileri işlemi sözleşme farklı parametreler için eşlenen bilgileri de içermiyor. Bu nedenle, işlem sözleşmede yalnızca bir parametre olabilir. Parametre türünde <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` temel alınan MSMQ iletisi içerir. Türünde "T" `MsmqMessage<T>` sınıf MSMQ İleti gövdesi seri verileri temsil eder. Bu örnekte `PurchaseOrder` türü MSMQ İleti gövdesi seri.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 Hizmet işlemini satın alma siparişi işler ve satın alma siparişi ve durumunu içeriğini hizmet konsol penceresinde görüntüler. <xref:System.ServiceModel.OperationBehaviorAttribute> İşlemi sıranın ile bir işlemde listeleme veya işlemi döndürdüğünde işlem tamamlandı olarak işaretlemek için yapılandırır. `PurchaseOrder` Hizmeti tarafından işlenmesi gereken sipariş ayrıntılarını içerir.  
  
```  
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
  
 Özel bir istemci hizmetin kullandığı `OrderResponseClient` MSMQ ileti kuyruğuna göndermek için. Alan ve iletiyi işleyen bir uygulama bir MSMQ uygulaması olduğundan ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, iki uygulama hiçbir örtük hizmet sözleşmesini yoktur. Bu senaryoda Svcutil.exe aracını kullanarak bir proxy şekilde oluşturamıyoruz.  
  
 Özel proxy temelde tüm aynıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan uygulamalar `msmqIntegrationBinding` iletileri göndermek için bağlama. Diğer proxy'leri, bir dizi hizmet işlemleri içermeyecek. Bir Gönder ileti yalnızca işlemdir.  
  
```  
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
  
 Kendi kendini barındırılan hizmetidir. MSMQ tümleştirme taşıma kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmeti içeren <xref:System.Messaging> kod sıranın varlığını denetlemek ve gerekirse oluşturun. Kuyruk adı yapılandırma dosyasından okunur.  
  
```  
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
  
 Sipariş isteklerinin gönderilme MSMQ sırası yapılandırma dosyasının appSettings bölümünde belirtilir. İstemci ve hizmet uç noktaları yapılandırma dosyası system.serviceModel bölümünde tanımlanır. Her ikisini de belirtin `msmqIntegrationbinding` bağlama.  
  
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
  
 İstemci uygulaması kullanan <xref:System.Messaging> dayanıklı ve işlemsel ileti kuyruğuna göndermek için. İleti gövdesi satın alma siparişi içerir.  
  
```  
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
>  Kuyruk adı, ters eğik çizgi ayırıcıları yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Uç noktası adresi msmq.formatname düzeni belirtir ve yerel bilgisayar için "localhost" kullanır. Doğru oluşturulmamış biçim adı MSMQ yönergelerine göre URI msmq.formatname izler.  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 İstemci uygulama kaydeder `messageID` sipariş istek iletisinin hizmetine gönderir ve hizmetinden bir yanıt bekler. Bir yanıt sırada geldikten sonra istemci, gönderilen kullanarak sipariş iletiyle karşılık gelen `correlationID` içeren iletinin özelliği `messageID` sırasını ileti hizmete ilk olarak gönderilen istemci.  
  
```  
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
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Bir yanıt istemciye geri hizmeti alma iletileri gönderir ve istemci görebilirsiniz. İstemci hizmetinden alınan yanıtta görüntüler. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
> [!NOTE]
>  Bu örnek, Message Queuing (MSMQ), yükleme gerektirir. Ayrıca Bkz bölümündeki MSMQ yükleme yönergelerine bakın.  
  
### <a name="to-setup-build-and-run-the-sample"></a>Kurulum, yapı ve örneği çalıştırmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek bilgisayarlı yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet program dosyalarını dile özgü klasörü altındaki \service\bin\ klasöründen hizmet bilgisayara kopyalayın.  
  
2.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
3.  Hizmet bilgisayar adı yerine belirtmek için orderQueueName Client.exe.config dosyasında değiştirmek ".".  
  
4.  Service.exe.config dosyasında yerine istemci bilgisayarın adını belirtmek için istemci uç noktası adresi değiştirmek ".".  
  
5.  Hizmet bilgisayarda bir komut isteminden Service.exe başlatın.  
  
6.  İstemci bilgisayarda bir komut isteminden Client.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de kuyruğa alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968)
