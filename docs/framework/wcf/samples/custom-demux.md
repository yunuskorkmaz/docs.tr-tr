---
title: Özel Demux
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: 1542743a6e1658bad162d7ee9ca73e6b9b0444e2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395667"
---
# <a name="custom-demux"></a>Özel Demux
Bu örnek, böylece Windows Communication Foundation (WCF) kullanan hizmetleri nasıl MSMQ İleti üstbilgileri için farklı hizmet işlemleri eşlenebilir gösterir <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> gösterildiği şekilde bir hizmet işlemi kullanarak sınırlı [ Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ve [Message Queuing Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnekleri.  
  
 Bu örnekte, alan hizmet kuyruğa alınmış iletileri gözlemleyin sağlamak için şirket içinde barındırılan bir konsol uygulaması hizmetidir.  
  
 Hizmet sözleşme `IOrderProcessor`ve Kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar.  

```csharp
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

 Bir MSMQ iletisinin bir eylem üst bilgisi yok. İşlem sözleşmeleri farklı MSMQ iletileri otomatik olarak eşlemeye mümkün değildir. Bu nedenle, yalnızca bir işlem anlaşması olabilir. Hizmet uygular bu sınırlamanın üstesinden gelmek için <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> yöntemi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Yöntemi bir özel hizmet işlemi için belirtilen bir üst bilgi iletisinin eşlemek bir hizmet sağlar. Bu örnekte, hizmet işlemleri için ileti etiketi üstbilgi eşlenir. `Name` Da işlem anlaşması parametresinin belirler hangi hizmet işlemi için belirli bir ileti etiket dağıtılması gerekir. İleti etiketi başlığı "SubmitPurchaseOrder" içeriyorsa, örneğin, "SubmitPurchaseOrder" hizmet işlemi çağrılır.  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 Hizmet uygulamalıdır <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> yöntemi <xref:System.ServiceModel.Description.IContractBehavior> arabirimi aşağıdaki örnek kodda gösterildiği gibi. Bu özel geçerlidir `OperationSelector` hizmet framework gönderme çalışma zamanı.  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 Bir ileti dağıtıcısı kişinin geçmelidir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> ClientRuntime için alma önce. Varsayılan olarak bir ileti reddedilir eylem hizmeti tarafından uygulanan herhangi bir sözleşme bulunamadı. Bu onay önlemek için biz uygulayan bir <xref:System.ServiceModel.Description.IEndpointBehavior> adlı `MatchAllFilterBehavior`, herhangi bir ileti geçişine izin veren `ContractFilter` uygulayarak <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> gibi.  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 Hizmet tarafından bir ileti alındığında, uygun bir hizmet işlemi etiket üstbilgisi tarafından sağlanan bilgileri kullanarak gönderilir. İletisinin gövdesi seri durumdan bir `PurchaseOrder` aşağıdaki örnek kodda gösterildiği gibi nesne.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 Hizmet kendiliğinden barındırılır. MSMQ kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmet sırası varlığını denetlemek için kod içeren ve kuyruk yoksa oluşturur. Kuyruk adı yapılandırma dosyasından okunur.  

```csharp
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

 MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir.  
  
> [!NOTE]
>  Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. WCF uç nokta adresini msmq.formatname düzenini belirtir ve yerel bilgisayar için localhost kullanır. Düzen izleyen bir yönergeleri adresleme MSMQ biçim adına göre düzgün biçimlendirilmiş bir kuyruk adresidir.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Bu örnek yüklenmesini gerektirir [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Hizmeti başlatın ve istemci çalıştırın.  
  
 Aşağıdaki çıktı, istemcide görülür.  
  
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
  
 Aşağıdaki çıktı, hizmette görülen gerekir.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletin **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet program dosyaları \service\bin\ klasöründen dile özgü klasörü altında hizmet bilgisayara kopyalayın.  
  
2.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.  
  
3.  Yerine hizmeti bilgisayarın adını belirtmek için orderQueueName Client.exe.config dosyasında değiştirme ".".  
  
4.  Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.  
  
5.  İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=95143)
