---
title: Çift Yönlü İletişim
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143765"
---
# <a name="two-way-communication"></a>Çift Yönlü İletişim
Bu örnek, MSMQ üzerinden işlemyapılı iki yönlü sıralı iletişimin nasıl gerçekleştirililebildiğini gösterir. Bu örnek `netMsmqBinding` bağlama kullanır. Bu durumda, hizmet sıralı iletileri alan hizmeti gözlemlemenize olanak tanıyan, kendi kendine barındırılan bir konsol uygulamasıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu [örnek, İşlenmiş MSMQ Bağlama'ya](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)dayanmaktadır.  
  
 Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar. İstemci kuyruğa ileti gönderir ve hizmet kuyruktan iletiler alır. Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Bu örnek, kuyrukları kullanarak 2 yönlü iletişimi gösterir. İstemci, bir işlem kapsamından kuyruğa satınalma siparişleri gönderir. Hizmet siparişleri alır, siparişi işler ve ardından bir işlem kapsamında sıradan gelen siparişin durumuyla istemciyi geri çağırır. İstemci ve hizmet, çift yönlü iletişimi kolaylaştırmak için hem satınalma siparişlerini hem de sipariş durumunu enqueue olarak sıralar.  
  
 Hizmet sözleşmesi, `IOrderProcessor` kuyruk kullanımına uygun tek yönlü hizmet işlemlerini tanımlar. Hizmet işlemi, sipariş durumlarını göndermek için kullanılacak yanıt bitiş noktasını içerir. Yanıt bitiş noktası, sipariş durumunu istemciye geri göndermek için sıranın URI'sidir. Sipariş işleme uygulaması bu sözleşmeyi uygular.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 Sipariş durumunu göndermek için yanıt sözleşmesi istemci tarafından belirtilir. İstemci sipariş durumu sözleşmesini uygular. Hizmet, sipariş durumunu istemciye geri göndermek için bu sözleşmenin oluşturulan proxy'sini kullanır.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Hizmet işlemi, gönderilen satınalma siparişini işler. Sıradan <xref:System.ServiceModel.OperationBehaviorAttribute> ileti almak ve hizmet işleminin tamamlanmasından sonra hareketlerin otomatik olarak tamamlanması için kullanılan bir harekette otomatik listine belirtmek için hizmet işlemine uygulanır. Sınıf, `Orders` sipariş işleme işlevini kapsüller. Bu durumda, bir sözlüğe satınalma siparişi ekler. Hizmet işleminin kaydolduğu işlem sınıftaki `Orders` işlemler için kullanılabilir.  
  
 Hizmet işlemi, gönderilen satınalma siparişini işleme ek olarak, siparişin durumu yla ilgili olarak istemciye yanıt verir.  

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

 MSMQ sıra adı yapılandırma dosyasının bir uygulama Ayarları bölümünde belirtilir. Hizmetin bitiş noktası yapılandırma dosyasının System.ServiceModel bölümünde tanımlanır.  
  
> [!NOTE]
> MSMQ sıra adı ve bitiş noktası adresi biraz farklı adresleme kuralları kullanır. MSMQ sıra adı, yerel makine için bir nokta (.) kullanır ve yoluna ayırıcıları ters eğir. Windows Communication Foundation (WCF) uç nokta adresi net.msmq belirtir: şema, yerel makine için "localhost" kullanır ve yoluna ileri eğik çizgiler kullanır. Uzak makinede barındırılan bir kuyruktan okumak için uzak makine adına "." ve "localhost" adını değiştirin.  
  
 Hizmet kendi kendine barındırılır. MSMQ aktarımını kullanırken, kullanılan sıra önceden oluşturulmalıdır. Bu el ile veya kod yoluyla yapılabilir. Bu örnekte, hizmet sıranın varlığını denetler ve gerekirse oluşturur. Sıra adı yapılandırma dosyasından okunur. Temel adres [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmetproxy oluşturmak için kullanılır.  

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

 İstemci bir hareket oluşturur. Sırayla iletişim, işlem kapsamında gerçekleşir ve tüm iletilerin başarılı veya başarısız olduğu bir atomik birim olarak ele alınmasına neden olur.  

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

 İstemci kodu, `IOrderStatus` hizmetten sipariş durumu almak için sözleşmeyi uygular. Bu durumda, sipariş durumunu yazdırır.  

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

 `Main` Yöntemde sipariş durum sırası oluşturulur. İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi sipariş durumu hizmetini barındıracak sipariş durumu hizmeti yapılandırmasını içerir.  
  
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
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsolu pencerelerinde görüntülenir. Hizmetin istemciden ileti aldığını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
 Hizmet satınalma siparişi bilgilerini görüntüler ve sipariş durumu sırasına sipariş durumunu geri gönderdiğini gösterir.  
  
```console  
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
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
    > [!NOTE]
    > Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adlarını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.  
  
 Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkinleştirilir. MSMQ aktarım güvenliği için iki <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ilgili özellik vardır ve varsayılan `Windows` olarak kimlik doğrulama modu `Sign`ayarlanır ve koruma düzeyi . MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için bir etki alanının parçası olması ve MSMQ için etkin dizin tümleştirme seçeneğinin yüklenmesi gerekir. Bu örneği bu ölçütleri karşılamayan bir bilgisayarda çalıştırıyorsanız bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Bir çalışma grubuna katılan veya etkin dizin tümleştirmesi olmayan bir bilgisayarda örnek çalıştırmak için  
  
1. Bilgisayarınız bir etki alanının parçası değilse veya etkin dizin tümleştirmesi yüklü değilse, kimlik doğrulama `None` modunu ve koruma düzeyini aşağıdaki örnek yapılandırmada gösterildiği gibi ayarlayarak aktarım güvenliğini kapatın:  
  
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
  
2. İstemci yapılandırması için güvenliği kapatmak aşağıdakileri oluşturur:  
  
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
  
3. Bu örnek için `OrderProcessorService`hizmet. Güvenlik modunu ayarlamak için bağlama anında bağlandıktan sonra bir `None`kod satırı ekleyin.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Örneği çalıştırmadan önce hem sunucuda hem de istemcide yapılandırmayı değiştirdiğinden emin olun.  
  
    > [!NOTE]
    > `security mode` Ayar, `None` ayarına <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> veya `Message` güvenlik `None`'e eşdeğerdir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
