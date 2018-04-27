---
title: Çift Yönlü İletişim
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9eb37e7e307bc9748113e5580ee96c8863d3ef89
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="two-way-communication"></a>Çift Yönlü İletişim
Bu örnek üzerinde MSMQ hizmetteki iki yönlü kuyruğa alınan iletişim gerçekleştirme gösterir. Bu örnekte `netMsmqBinding` bağlama. Bu durumda, sıraya alınan iletileri alma hizmeti izlemek izin veren bir kendi kendini barındıran konsol uygulaması hizmetidir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek dayanır [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar. İstemci kuyruğa ileti gönderir ve hizmet kuyruktan iletileri alır. Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Bu örnek 2 yönlü iletişimi kuyrukları kullanma gösterilmektedir. İstemci bir işlem kapsamı içinde sıradan satınalma siparişi gönderir. Hizmet siparişleri alır, sipariş işleme ve geri sırasını durumunu istemcisiyle bir işlem kapsamı içinde sırasından çağırır. Çift yönlü iletişimi kolaylaştırmak için istemci ve hizmet enqueue satınalma siparişi ve sipariş durumu sıralara kullanın.  
  
 Hizmet sözleşmesi `IOrderProcessor` queuing kullanımına uygun tek yönlü hizmet işlemleri tanımlar. Hizmet işlemini sipariş durumları göndermek için kullanılacak yanıt uç noktası içerir. Sipariş durumu istemciye göndermek için sıra URI'sini yanıt uç noktadır. Uygulama işlem sırası bu sözleşmenin uygular.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 Sipariş durumu gönderilecek yanıt sözleşmesi istemci tarafından belirtilir. İstemci, sipariş durumu sözleşme uygular. Hizmet, bu sözleşmenin oluşturulan proxy sipariş durumu istemciye göndermek için kullanır.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Hizmet işlemini gönderilen satın alma siparişi işler. <xref:System.ServiceModel.OperationBehaviorAttribute> Kuyruk ve hizmet işlemi tamamlandıktan hareketlerinin otomatik tamamlama ileti almak için kullanılan bir işlemde otomatik kaydı belirtmek için hizmet işlemi uygulanır. `Orders` Sınıfı, sipariş işleme işlevselliği yalıtır. Bu durumda, satın alma siparişi bir sözlüğe ekler. Hizmet işlemi içinde kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.  
  
 Sipariş durumlarını istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.  

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

 MSMQ kuyruk adı bir yapılandırma dosyasının appSettings bölümünde belirtilmiştir. Hizmeti için uç noktaya yapılandırma dosyası System.ServiceModel bölümünde tanımlanır.  
  
> [!NOTE]
>  MSMQ sırası ad ve uç nokta adresi biraz farklı adresleme yöntemini kullanın. MSMQ sırası adı yerel makine ve eğik çizgi ayırıcıları yolundaki bir nokta (.) kullanır. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Uç noktası adresi bir net.msmq belirtir: şeması, "localhost" için yerel makineyi ve eğik kendi yolunu kullanır. Uzak makinede barındırılan bir kuyruktan okumak için Değiştir "." ve "localhost" ile uzak makine adı.  
  
 Kendi kendini barındırılan hizmetidir. MSMQ taşıma kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnek, hizmet sıranın varlığını denetler ve, gerekirse oluşturur. Kuyruk adı yapılandırma dosyasından okunur. Temel adres tarafından kullanılan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.  

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

 İstemci bir işlem oluşturur. Sıra ile iletişim, burada tüm iletileri başarılı veya başarısız atomik bir birim olarak değerlendirilmesi için neden işlem kapsamı içinde gerçekleşir.  

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

 İstemci kodu uygulayan `IOrderStatus` hizmetinden sipariş durumunu almak sözleşme. Bu durumda, sipariş durumu yazdırır.  

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

 Durum sırasını oluşturulan `Main` yöntemi. İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi sipariş durumu hizmeti barındırmak için sipariş durum hizmet yapılandırmasını içerir.  
  
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
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir. İstemci hizmeti alma iletileri görebilirsiniz. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
 Hizmet satın alma siparişi bilgileri görüntüler ve geri durumu sırasını sipariş durumu gönderiyor gösterir.  
  
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
  
 İstemci hizmeti tarafından gönderilen sipariş durum bilgilerini görüntüler.  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adları değiştirdiğinizden emin olun.  
  
 Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, taşıma güvenliği etkindir. MSMQ taşıma güvenliği için iki ilgili özellikler yok <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Bir etki alanının parçası olması gerekir ve kimlik doğrulaması ve imzalama özelliği, MSMQ için MSMQ active directory tümleştirme seçeneğini yüklü olması gerekir. Bu ölçütleri karşılayan olmayan bir bilgisayarda bu örnek çalıştırırsanız, bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örnek bir çalışma grubu ya da active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok gerekirse kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakmak `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
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
  
2.  İstemci yapılandırması için güvenlik kapatma aşağıdaki oluşturur:  
  
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
  
3.  Hizmeti bu örnek için bir bağlama oluşturur `OrderProcessorService`. Güvenlik modu ayarlamak için bağlama örneği sonra bir kod satırını ekleyin `None`.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasına değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarına eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> veya `Message` güvenlik `None`.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a>Ayrıca Bkz.
