---
title: Çift Yönlü İletişim
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 319b63ff1eefdab4c23932294c3f1970f204601e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276983"
---
# <a name="two-way-communication"></a>Çift Yönlü İletişim
Bu örnek, MSMQ kuyruğa alınan hizmetteki iki yönlü iletişim gerçekleştirme gösterir. Bu örnekte `netMsmqBinding` bağlama. Bu durumda, kuyruğa alınmış iletiler alma hizmeti gözlemleyin olanak tanıyan bir şirket içinde barındırılan bir konsol uygulaması hizmetidir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar. İstemci bir kuyruğa ileti gönderir ve hizmet iletileri kuyruktan alır. Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.  
  
 Bu örnek 2 yönlü iletişimi kuyruklarını kullanan gösterir. İstemci, sıradan bir işlem kapsamında satın alma siparişleri gönderir. Hizmet siparişleri alır, sipariş işleme ve daha sonra geri istemci siparişin durumunu içeren bir işlem kapsamındaki sırasından çağırır. İki yönlü iletişimi kolaylaştırmak için kuyruğa satın alma siparişleri ve sipariş durumu sıralara istemciyi ve hizmeti kullanın.  
  
 Hizmet sözleşmesi `IOrderProcessor` queuing kullanımını uygun bir tek yönlü hizmet işlemleri tanımlar. Hizmet işlemi için sipariş durumları göndermek için kullanılacak yanıt uç nokta içerir. Sıranın URI'sini sipariş durumunun istemciye geri gönderilecek yanıt uç noktadır. Uygulama işleme sırası, bu sözleşme uygular.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 Sipariş durumu gönderilecek yanıt anlaşması, istemci tarafından belirtilir. Sipariş durumu sözleşme istemciye uygular. Hizmet, bu sözleşmenin oluşturulan proxy siparişinizin durumu istemciye geri göndermek için kullanır.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Hizmet işlemi gönderilen satın alma siparişi işler. <xref:System.ServiceModel.OperationBehaviorAttribute> İşlem tamamlandığında hizmet işleminin otomatik tamamlama ve kuyruk iletiyi almak için kullanılan bir işlemde otomatik kaydı belirtmek için hizmet işlemi uygulanır. `Orders` Sınıfı sipariş işleme işlevselliğini kapsüller. Bu durumda, satın alma siparişi bir sözlüğe ekler. Hizmet işlemi kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.  
  
 Siparişin durumunu istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir. Hizmet için uç nokta yapılandırma dosyasının System.ServiceModel bölümünde tanımlanır.  
  
> [!NOTE]
>  MSMQ kuyruk adı ve uç nokta adresi adresleme biraz farklı kuralları kullanın. MSMQ kuyruk adı yerel makine ve ters eğik çizgi ayırıcılar yolundaki bir nokta (.) kullanır. Windows Communication Foundation (WCF) uç nokta adresini belirten bir net.msmq: şeması, "localhost" için yerel makine ve eğik kendi yolu kullanır. Uzak makinede barındırılan bir kuyruktan okunur değiştirin "." ve "localhost" uzak makine adı.  
  
 Kendi kendine barındırılan bir hizmettir. MSMQ taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmet sırası varlığını denetler ve, gerekirse oluşturur. Kuyruk adı yapılandırma dosyasından okunur. Tarafından kullanılan taban adresini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```

 İstemci, bir işlem oluşturur. Kuyruk ile iletişimi, burada tüm iletileri başarılı veya başarısız bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir.  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 İstemci kodu uygulayan `IOrderStatus` siparişinizin durumu hizmetinden almak üzere sözleşme. Bu durumda, siparişinizin durumu yazdırır.  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,   
                                                           status);  
    }  
}  
```

 Durum sırasını oluşturulan `Main` yöntemi. Aşağıdaki örnek yapılandırmada gösterildiği gibi istemci yapılandırması sipariş durumu hizmeti barındırmak için sipariş durumu hizmeti yapılandırması içerir.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service   
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
              binding="netMsmqBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
 Hizmet satın alma siparişi bilgileri görüntüler ve sipariş durumunun durumu sırasını geri gönderdiği gösterir.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 İstemci, hizmet tarafından gönderilen sipariş durumu bilgilerini görüntüler.  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, uç nokta adları istemci kodu eşleştirilecek istemci yapılandırmasında değişiklik emin olun.  
  
 Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin. MSMQ taşıma güvenlik için iki ilgili özellik <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ active directory tümleştirme seçeneği yüklenmelidir. Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örnek, bir çalışma grubuna veya active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"   
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2.  Bir istemci yapılandırması için güvenlik kapatma aşağıdakileri oluşturur:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service   
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
                    binding="netMsmqBinding"   
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3.  Bu örnek bir bağlama oluşturur `OrderProcessorService`. Güvenlik modu ayarlamak için bağlama örneği sonra bir kod satırını ekleyin `None`.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> veya `Message` güvenlik `None`.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a>Ayrıca Bkz.
