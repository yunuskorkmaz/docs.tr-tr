---
title: Çift Yönlü İletişim
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 7bc513d270a860c104255ac5df6f6d890f6b2b0d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424216"
---
# <a name="two-way-communication"></a>Çift Yönlü İletişim
Bu örnek, MSMQ üzerinden işlem temelli iki yönlü sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir. Bu örnek `netMsmqBinding` bağlamasını kullanır. Bu durumda hizmet, sıraya alınan iletileri alma hizmetinin gözlemlebilmenizi sağlayan, kendine barındırılan bir konsol uygulamasıdır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, [IŞLENEN MSMQ bağlamasını](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)temel alır.  
  
 Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. İstemci bir kuyruğa ileti gönderir ve hizmet kuyruktan iletileri alır. Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Bu örnek, kuyrukları kullanarak 2 yönlü iletişimi gösterir. İstemci, bir işlemin kapsamındaki satınalma emirlerini kuyruğa gönderir. Hizmet siparişleri alır, sırayı işler ve sonra bir işlemin kapsamındaki sıradaki sıra durumuyla istemciyi geri çağırır. İki yönlü iletişimi kolaylaştırmak için, istemci ve hizmetin her ikisi de, satın alma siparişlerinin ve sipariş durumunun kuyruğa alınması için kuyrukları kullanır.  
  
 Hizmet sözleşmesi `IOrderProcessor`, sıraya alma kullanımı ile ilgili tek yönlü hizmet işlemlerini tanımlar. Hizmet işlemi, sipariş durumlarını göndermek için kullanılacak yanıt uç noktasını içerir. Yanıt uç noktası, sipariş durumunun istemciye geri gönderilmesi için kuyruğun URI 'sidir. Sipariş işleme uygulaması bu sözleşmeyi uygular.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 Sıra durumunu göndermek için gereken yanıt sözleşmesi, istemci tarafından belirtilir. İstemci sipariş durumu sözleşmesini uygular. Hizmet, sipariş durumunu istemciye geri göndermek için bu sözleşmenin oluşturulan ara sunucusunu kullanır.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Hizmet işlemi gönderilen satın alma siparişini işler. <xref:System.ServiceModel.OperationBehaviorAttribute>, işlem sırasında iletiyi almak ve hizmet işleminin tamamlanmasından otomatik olarak tamamlamak için kullanılan bir işlemde otomatik kayıt belirtmek üzere hizmet işlemine uygulanır. `Orders` sınıfı sıra işleme işlevselliğini Kapsüller. Bu durumda, satın alma sırasını bir sözlüğe ekler. Hizmet işleminin kayıtlı olduğu işlem, `Orders` sınıfındaki işlemler için kullanılabilir.  
  
 Hizmet işlemi, gönderilen satın alma siparişinin işlenmesine ek olarak, siparişin durumunda istemciye geri yanıt verir.  

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

 MSMQ kuyruğu adı, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir. Hizmetin uç noktası, yapılandırma dosyasının System. ServiceModel bölümünde tanımlanır.  
  
> [!NOTE]
> MSMQ kuyruğu adı ve uç nokta adresi biraz farklı adresleme kuralları kullanır. MSMQ sırası adı, yerel makine için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır. Windows Communication Foundation (WCF) uç noktası adresi bir net. MSMQ: Scheme belirtir, yerel makine için "localhost" kullanır ve yolunda eğik çizgi kullanır. Uzak makinede barındırılan bir kuyruktan okumak için, "." ve "localhost" değerini uzak makine adıyla değiştirin.  
  
 Hizmet kendi kendine barındırılır. MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte hizmet, sıranın varlığını denetler ve gerekirse oluşturur. Sıra adı yapılandırma dosyasından okundu. Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete proxy oluşturmak için kullanılır.  

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

 İstemci bir işlem oluşturur. Kuyrukla iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin başarılı veya başarısız olduğu atomik bir birim olarak işlenmesine neden olur.  

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

 İstemci kodu, hizmetten sipariş durumunu almak için `IOrderStatus` sözleşmesini uygular. Bu durumda, sipariş durumunu yazdırır.  

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

 Sıra durumu kuyruğu `Main` yönteminde oluşturulur. İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş durumu hizmetini barındıracak sıra durumu hizmeti yapılandırmasını içerir.  
  
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
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
 Hizmet, satın alma siparişi bilgilerini görüntüler ve sipariş durumunu sipariş durumu kuyruğuna geri gönderdiğini gösterir.  
  
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
  
 İstemci, hizmet tarafından gönderilen sıra durumu bilgilerini görüntüler.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
    > [!NOTE]
    > Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil. exe ' yi kullanırsanız, istemci yapılandırmasındaki uç nokta adlarını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.  
  
 <xref:System.ServiceModel.NetMsmqBinding>varsayılan olarak, taşıma güvenliği etkinleştirilmiştir. MSMQ aktarım güvenliği, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` varsayılan olarak, kimlik doğrulama modu `Windows` olarak ayarlanır ve koruma düzeyi `Sign`olarak ayarlanır. Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ için, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir. Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örneği bir çalışma grubuna katılmış veya Active Directory Tümleştirmesi olmadan bir bilgisayarda çalıştırmak için  
  
1. Bilgisayarınız bir etki alanının parçası değilse veya Active Directory Tümleştirmesi yüklü değilse, aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini `None` olarak ayarlayarak aktarım güvenliğini kapatın:  
  
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
  
3. Bu örnek için hizmet `OrderProcessorService`bir bağlama oluşturur. Güvenlik modunu `None`olarak ayarlamak için bağlama örneği oluşturulduktan sonra bir kod satırı ekleyin.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.  
  
    > [!NOTE]
    > `security mode` `None` ayarlanması <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> veya `Message` güvenlik `None`ayarı ile eşdeğerdir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
