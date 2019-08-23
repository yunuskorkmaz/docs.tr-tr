---
title: Teslim Edilemeyen İletiler Sırası
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: a1e9ad000b83aab1e0d17d3443e1bd6f87310c9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962623"
---
# <a name="dead-letter-queues"></a>Teslim Edilemeyen İletiler Sırası
Bu örnek, teslimin başarısız olduğu iletileri nasıl işleyeceğinizi ve işleyeceğini gösterir. Bu [işlem, IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğini temel alır. Bu örnek, `netMsmqBinding` bağlamayı kullanır. Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!NOTE]
> Bu örnek, yalnızca üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)]kullanılabilir olan her bir uygulama atılacak ileti sırasını gösterir. Örnek, ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] [!INCLUDE[wxp](../../../../includes/wxp-md.md)]üzerinde MSMQ 3,0 için varsayılan sistem genelinde kuyrukları kullanacak şekilde değiştirilebilir.

 Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. Daha kesin olarak, istemci iletileri bir kuyruğa gönderir. Hizmet kuyruktaki iletileri alır. Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.

 Kuyruğa alınan iletişim belirli bir miktarda devre dışı olabileceğinden, iletinin saati geçmiş olursa uygulamaya teslim edilmediğini sağlamak için ileti üzerinde bir yaşam süresi değeri ilişkilendirmek isteyebilirsiniz. Ayrıca, bir iletinin teslim başarısız olup olmadığını bir uygulamanın bilgilendirilmesi gereken durumlar da vardır. Bu durumların tümünde, iletideki yaşam süresi dolduğunda veya ileti teslimi başarısız olduğunda, ileti atılacak bir sıra kuyruğuna konur. Gönderen uygulama daha sonra teslim edilemeyen ileti sırasındaki iletileri okuyabilir ve başarısız teslimat nedenlerini düzeltmek ve iletiyi yeniden göndermek için hiçbir eylemde yer alan düzeltici eylemler gerçekleştirebilir.

 `NetMsmqBinding` Bağlamadaki atılacak ileti sırası aşağıdaki özelliklerde ifade edilir:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>istemcisi için gerekli atılacak ileti sırası türünü ifade eden özellik. Bu numaralandırma aşağıdaki değerlere sahiptir:

- `None`: İstemci için atılacak mektup kuyruğu gerekmez.

- `System`: Kullanılmayan iletileri depolamak için sistem atılacak mektup kuyruğu kullanılır. Sistem atılacak ileti kuyruğu, bilgisayarda çalışan tüm uygulamalar tarafından paylaşılır.

- `Custom`: <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> Özelliği kullanılarak belirtilen özel bir atılacak mektup kuyruğu, ölü iletileri depolamak için kullanılır. Bu özellik yalnızca ' de [!INCLUDE[wv](../../../../includes/wv-md.md)]kullanılabilir. Bu, uygulamanın aynı bilgisayar üzerinde çalışan diğer uygulamalarla paylaşılması yerine kendi atılacak bir sıra kullanması gerektiğinde kullanılır.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>bir atılacak ileti sırası olarak kullanılacak sırayı ifade etmek için özelliği. Bu yalnızca içinde [!INCLUDE[wv](../../../../includes/wv-md.md)]kullanılabilir.

 Bu örnekte, istemci, bir işlemin kapsamı içinde hizmete toplu bir ileti gönderir ve bu iletiler için "yaşam süresi" (yaklaşık 2 saniye) için rastgele bir düşük değer belirtir. İstemci Ayrıca, kullanım dışı olan iletileri sıraya almak için kullanılacak özel bir atılacak mektup kuyruğu belirtir.

 İstemci uygulaması, teslim edilemeyen ileti sırasındaki iletileri okuyabilir ve iletiyi göndermeyi yeniden deneyebilir ya da özgün iletinin atılacak ileti kuyruğuna yerleştirilmesine neden olan hatayı düzeltebilir ve iletiyi gönderebilirler. Örnekte istemci bir hata iletisi görüntüler.

 Hizmet sözleşmesi aşağıdaki örnek `IOrderProcessor`kodda gösterildiği gibi olur.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Örnekteki hizmet kodu, [Işlem TEMELLI MSMQ bağlamadır](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Hizmet ile iletişim, bir işlemin kapsamı içinde gerçekleşir. Hizmet kuyruktaki iletileri okur, işlemi gerçekleştirir ve sonra işlemin sonuçlarını görüntüler. Uygulama, atılacak iletiler için atılacak mektup kuyruğu da oluşturur.

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 İstemcinin yapılandırması, iletinin hizmete ulaşması için kısa bir süre belirtir. İleti belirtilen süre içinde iletilemez, iletinin süresi dolar ve atılacak ileti kuyruğuna taşınır.

> [!NOTE]
> İstemci, iletiyi belirtilen süre içinde hizmet kuyruğuna teslim etmek mümkündür. İşlem sırasında atılacak ileti hizmetini gördiğinizden emin olmak için, hizmeti başlatmadan önce istemcisini çalıştırmalısınız. İleti zaman aşımına uğrar ve atılacak ileti hizmetine gönderilir.

 Uygulamanın, atılacak ileti sırası olarak hangi kuyruğun kullanılacağını tanımlamanız gerekir. Hiçbir kuyruk belirtilmemişse, ölü iletileri sıraya almak için varsayılan sistem genelinde işlem atılacak ileti sırası kullanılır. Bu örnekte, istemci uygulaması kendi uygulama atılacak mektup sırasını belirtir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 Atılacak ileti hizmeti, iletileri atılacak ileti sırasından okur. Teslim edilemeyen ileti hizmeti `IOrderProcessor` sözleşmeyi uygular. Ancak, bu uygulama, siparişlerin işlenmesi için değildir. Atılacak ileti hizmeti bir istemci hizmetidir ve siparişleri işleme olanağı yoktur.

> [!NOTE]
> Atılacak ileti sırası bir istemci kuyruğu ve istemci kuyruğu yöneticisinin yereldir.

 Atılacak ileti hizmeti uygulamasının bir ileti tesliminin başarısız olup olmadığını denetler ve düzeltici ölçüler alır. İleti hatasının nedeni, ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>olmak üzere iki Numaralandırmalarla yakalanır. Aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.Channels.MsmqMessageProperty> <xref:System.ServiceModel.OperationContext> gibi öğesinden öğesini alabilirsiniz:

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 Atılacak ileti sırasındaki iletiler, iletiyi işleyen hizmete yönelik iletilerdir. Bu nedenle, atılacak ileti hizmeti sıradaki iletileri okuduğunda, Windows Communication Foundation (WCF) Kanal katmanı bitiş noktalarında uyuşmazlığını bulur ve iletiyi göndermez. Bu durumda, ileti sipariş işleme hizmetine değinilmesi, ancak atılacak ileti hizmeti tarafından alınır. Farklı bir uç noktaya yönelik bir ileti almak için, içinde `ServiceBehavior`herhangi bir adresle eşleşecek bir adres filtresi belirtilir. Bu, atılacak ileti sırasından okunan iletileri başarıyla işlemek için gereklidir.

 Bu örnekte, hata nedeni iletinin zaman aşımına uğraması durumunda, atılacak ileti hizmeti iletiyi yeniden sonlandırır. Diğer tüm nedenlerden dolayı, aşağıdaki örnek kodda gösterildiği gibi teslim hatası görüntülenir:

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 Aşağıdaki örnek, atılacak bir ileti için yapılandırmayı gösterir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 Örneği çalıştırırken, her uygulama için atılacak ileti sırasının nasıl çalıştığını görmek için çalıştırılacak 3 yürütülebilir dosya vardır; her uygulama için atılacak ileti sırasından okuyan ve iletiyi yeniden sonlandıran istemci, hizmet ve atılacak ileti hizmeti. Hepsi konsol Windows 'da çıkışı olan konsol uygulamalardır.

> [!NOTE]
> Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışıyor olması gerekmez. İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir. Kuyruğun oluşturulabilmesi için hizmeti başlatmanız ve kapatmanız gerekir.

 İstemci çalıştırılırken, istemci şu iletiyi görüntüler:

```
Press <ENTER> to terminate client.
```

 İstemci iletiyi gönderilmeye çalıştı, ancak kısa bir zaman aşımıyla, iletinin süresi doldu ve artık her uygulama için atılacak ileti kuyruğunda sıraya alındı.

 Daha sonra iletiyi okuyan ve hata kodunu görüntüleyen ve iletiyi hizmete geri sonlandıran atılacak mektup hizmetini çalıştırırsınız.

```
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 Hizmet başlar ve sonra yeniden gönderilen iletiyi okur ve işler.

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir. Sıra yoksa, hizmet bir tane oluşturur. Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz. Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012 ' de Sunucu Yöneticisi açın.

    2. **Özellikler** sekmesini genişletin.

    3. **Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni `ServiceModelSamplesTransacted` kuyruğun adı olarak girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için, localhost 'u bilgisayarın tam adıyla değiştirip [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modunu ve koruma düzeyini `None` aşağıdaki örnek yapılandırmada gösterildiği gibi olarak ayarlayarak aktarım güvenliğini kapatın:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Uç noktanın `bindingConfiguration` özniteliğini ayarlayarak bitiş noktasının bağlama ile ilişkili olduğundan emin olun.

2. Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemcideki yapılandırmayı değiştirdiğinizden emin olun.

    > [!NOTE]
    >  `security mode` Ayarı,`MsmqProtectionLevel` ayarına ve güvenliğineeşdeğerdir.`Message` `None` `MsmqAuthenticationMode` `None`

## <a name="comments"></a>Açıklamalar
 Varsayılan olarak, `netMsmqBinding` bağlama aktarımında güvenlik etkindir. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenir. Varsayılan olarak, kimlik doğrulama modu olarak `Windows` ayarlanır ve koruma düzeyi olarak `Sign`ayarlanır. Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ 'nun bir etki alanının parçası olması gerekir. Bu örneği bir etki alanının parçası olmayan bir bilgisayarda çalıştırırsanız, şu hatayı alırsınız: "Kullanıcının iç Message Queuing sertifikası yok".

> [!IMPORTANT]
>  Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
