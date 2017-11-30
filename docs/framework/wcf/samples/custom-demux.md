---
title: "Özel Demux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7c74648a249ec833f2b0fc8b8f5eea9247dc364
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-demux"></a>Özel Demux
Bu örnek için farklı hizmet işlemleri MSMQ ileti üstbilgilerini nasıl eşlenebilir gösterir şekilde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmetleri kullanan <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> örnekte gösterildiği gibi bir hizmet işlemi kullanmaya sınırlı değildir [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ve [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnekleri.  
  
 Bu örnekte, alan hizmetini sıraya alınan iletileri gözlemleyin sağlamak için bir kendi kendini barındıran konsol uygulaması hizmetidir.  
  
 Hizmet sözleşme `IOrderProcessor`ve Kuyruklar ile kullanım için uygun bir tek yönlü hizmet tanımlar.  
  
```  
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```  
  
 MSMQ iletisine bir eylem üstbilgisi yok. Farklı MSMQ iletileri işlemi sözleşmeleri için otomatik olarak eşlemeye mümkün değildir. Bu nedenle, yalnızca bir işlem sözleşmesi olabilir. Hizmet Implements bu sınırlamanın üstesinden gelmek için <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> yöntemi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Yöntemi, belirli bir hizmet işlemi için belirtilen bir iletinin üstbilgisi eşlemek hizmet sağlar. Bu örnekte, ileti etiketi üstbilgi Hizmet işlemlerini eşlenir. `Name` İşlemi sözleşme parametresinin belirler hangi hizmet işlemi belirli bir ileti etiketi dağıtılması gerekir. Örneğin, "SubmitPurchaseOrder" İleti etiketi üstbilgi içeriyorsa, "SubmitPurchaseOrder" hizmet işlemi çağrılır.  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 Hizmet uygulamalıdır <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> yöntemi <xref:System.ServiceModel.Description.IContractBehavior> arabirimi aşağıdaki örnek kodda gösterildiği gibi. Bu özel geçerlidir `OperationSelector` hizmet framework gönderme çalışma zamanının.  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 Bir ileti dağıtıcısı kişinin geçmelidir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> ClientRuntime alma önce. Varsayılan olarak bir ileti reddedilir eylemi hizmeti tarafından uygulanan herhangi bir sözleşme bulunamadı. Bu onay önlemek için biz uygulayan bir <xref:System.ServiceModel.Description.IEndpointBehavior> adlı `MatchAllFilterBehavior`, herhangi bir iletisi geçişine izin veren `ContractFilter` uygulayarak <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> gibi.  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 Bir ileti hizmeti tarafından alındığında, uygun hizmet işlemi etiket üstbilgisi tarafından sağlanan bilgileri kullanarak gönderilir. İleti gövdesi içine seri durumdan bir `PurchaseOrder` , aşağıdaki örnek kodda gösterildiği gibi nesne.  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 Hizmet kendiliğinden barındırılır. MSMQ kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnek, hizmet sıranın varlığını denetlemek için kod içerir ve sıra yoksa oluşturur. Kuyruk adı yapılandırma dosyasından okunur.  
  
```  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
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
  
 MSMQ kuyruk adı bir yapılandırma dosyasının appSettings bölümünde belirtilmiştir.  
  
> [!NOTE]
>  Kuyruk adı, ters eğik çizgi ayırıcıları yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Uç noktası adresi msmq.formatname düzeni belirtir ve yerel bilgisayar için localhost kullanır. Düzeni izleyen bir yönergeleri adresleme MSMQ biçim adı göre düzgün biçimlendirilmiş sıra adresidir.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Bu örnek yüklenmesini gerektirir [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Hizmeti başlatmak ve istemci çalıştırın.  
  
 Aşağıdaki çıkış istemcide görülür.  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 Aşağıdaki çıkış hizmette görülen gerekir.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet program dosyalarını dile özgü klasörü altındaki \service\bin\ klasöründen hizmet bilgisayara kopyalayın.  
  
2.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
3.  Hizmet bilgisayar adı yerine belirtmek için orderQueueName Client.exe.config dosyasında değiştirmek ".".  
  
4.  Hizmet bilgisayarda bir komut isteminden Service.exe başlatın.  
  
5.  İstemci bilgisayarda bir komut isteminden Client.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de kuyruğa alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143)
