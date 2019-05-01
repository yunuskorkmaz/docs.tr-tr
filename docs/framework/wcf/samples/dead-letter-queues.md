---
title: Teslim Edilemeyen İletiler Sırası
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 379b6901e835a6820d194edda1d7727df789bfd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051968"
---
# <a name="dead-letter-queues"></a>Teslim Edilemeyen İletiler Sırası
Bu örnek ve teslim başarısız olmuş bir iletiyi işlemek nasıl gösterir. Dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek. Bu örnekte `netMsmqBinding` bağlama. Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.

> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

> [!NOTE]
>  Bu örnek yalnızca üzerinde kullanılabilir olan her uygulama geçerliliğini yitirmiş kuyruk gösterir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Örnek, varsayılan sistem genelinde kuyruklar için MSMQ 3.0 kullanmak üzere değiştirilebilir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].

 Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar. Daha kesin bir istemci bir kuyruğa iletiler gönderir. Hizmet iletileri kuyruktan alır. Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.

 Kuyruğa alınan iletişim belirli bir miktarda dormancy içerebildiğinden, bir yaşam süresi değerini zamanından daha sonradır geçti, ileti uygulamaya teslim değil emin olmak için iletide ilişkilendirmek isteyebilirsiniz. Durumda, burada bir uygulama bir ileti teslim başarısız olup olmadığını bilgilendirilmesi gerekir vardır. Bu durumların tümünde gibi zaman yaşam iletideki süresi doldu veya iletinin teslim başarısız, ileti sahipsiz sıraya konur. Gönderen uygulamayı iletileri teslim edilemeyen okuyabilir ve herhangi bir eylemi başarısız teslim nedenlerle düzeltme ve ileti yeniden gönderme aralığı düzeltme girişimlerinde bulunun.

 Teslim edilemeyen kuyrukta `NetMsmqBinding` bağlama şu özelliklerde ifade edilir:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Gerekli istemci tarafından eski ileti sırası türünü express özellik. Bu numaralandırma aşağıdaki değerlere sahip:

- `None`: Hiçbir eski ileti sırası istemci tarafından gereklidir.

- `System`: Sistem eski ileti sırası ölü iletileri depolamak için kullanılır. Sistem eski ileti sırası bilgisayarda çalışan tüm uygulamalar tarafından paylaşılır.

- `Custom`: Kullanarak belirtilen özel bir eski ileti sırası <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> özelliği ölü iletileri depolamak için kullanılır. Bu özellik yalnızca üzerinde kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Aynı bilgisayarda çalışan diğer uygulamalarla paylaşmak yerine, uygulamanın kendi geçerliliğini yitirmiş kuyruk kullanmanız gerekir, bu kullanılır.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> belirli bir kuyruğa atılacak kullanmak için express özellik. Bu yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].

 Bu örnekte, istemci bir işlem kapsamında hizmetten toplu iletiler gönderir ve "zaman yaşam" Bu iletileri (yaklaşık 2 saniye) için rastgele düşük bir değer belirtir. İstemci Ayrıca, süresi dolan iletileri kuyruğa kullanmak için özel bir sahipsiz sırayı belirtir.

 İstemci uygulama, sahipsiz sırayı ve ileti göndermek ya da yeniden deneme iletileri okumak veya özgün iletinin teslim edilemeyen sırasına ve ileti göndermek neden olan hatayı düzeltin. Bu örnekte, istemci bir hata iletisi görüntüler.

 Hizmet sözleşme `IOrderProcessor`aşağıdaki örnek kodda gösterildiği gibi.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Hizmet kod budur [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Hizmet ile iletişim bir işlem kapsamında gerçekleştirilir. Hizmet iletileri kuyruktan okuyan işlemi gerçekleştirir ve işlemin sonuçları görüntüler. Uygulama eski ileti sırası için teslim edilemeyen iletiler de oluşturur.

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

 İstemcinin yapılandırma hizmete erişmek ileti için kısa bir süre belirtir. Belirtilen süre içinde ileti iletilemedi, ileti süresi dolmadan ve eski ileti sırası için taşınır.

> [!NOTE]
>  Bu, istemcinin belirtilen süre içinde hizmet kuyruğa ileti teslim mümkündür. Teslim edilemeyen Hizmeti'ni çalışırken görmek emin olmak için İstemci Hizmeti başlatmadan önce çalıştırmalısınız. İleti zaman aşımına uğrar ve edilemeyen hizmete teslim edilir.

 Uygulama, eski ileti sırası kullanmak için hangi sıranın tanımlamanız gerekir. Sıra belirtilmezse, varsayılan sistem genelinde işlem eski ileti sırası eski iletilerin sıraya almak için kullanılır. Bu örnekte, istemci uygulamayı kendi uygulama sahipsiz sırayı belirtir.

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

 Teslim edilemeyen mesaj servisi iletileri teslim edilemeyen kuyruktaki iletileri okur. Edilemeyen mesaj hizmeti uygulayan `IOrderProcessor` sözleşme. Uygulaması ancak değil işlem siparişlere. Teslim edilemeyen mesaj servisi siparişleri işleme olanağı yok ve bir istemci hizmetidir.

> [!NOTE]
>  Eski ileti sırası istemci kuyruk ve istemci Kuyruk yöneticisi için yereldir.

 Bir ileti teslimi ve gerçekleştirilen işlemlerin düzeltici önlemleri başarısız oldu. nedeni edilemeyen mesaj hizmeti uygulaması denetler. Bir ileti başarısızlık iki numaralandırmalara yakalanan <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Alabileceğiniz <xref:System.ServiceModel.Channels.MsmqMessageProperty> gelen <xref:System.ServiceModel.OperationContext> aşağıdaki örnek kodda gösterildiği gibi:

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succed ", po);
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

 Geçerliliğini yitirmiş kuyruk iletilerindeki iletiyi işlemeyi hizmetine gönderilen iletileri ' dir. Bu nedenle, kuyruktan iletileri teslim edilemeyen mesaj servisi okur, Windows Communication Foundation (WCF) kanal katmanını uyuşmazlığı uç noktaların bulur ve ileti göndermez. Bu durumda, ileti işleme hizmeti siparişin ele ancak edilemeyen mesaj hizmeti tarafından alındı. Farklı bir uç noktasına yönelik bir ileti almak için bir adres filtresi eşleşen herhangi bir adres için belirtilen `ServiceBehavior`. Bu, başarılı bir şekilde teslim edilemeyen kuyruktan okunmak iletilerini işlemek için gereklidir.

 Başarısızlık nedeni bu örnekte, zaman aşımına uğradı ileti iletinin teslim edilemeyen mesaj servisi beşe. Diğer nedenlerle, aşağıdaki örnek kodda gösterildiği gibi teslim hatası gösterir:

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

 Aşağıdaki örnek, bir edilemeyen mesaj yapılandırmasını gösterir:

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

 Çalışan örnek eski ileti sırası her uygulama için nasıl çalıştığını görmek için çalıştırmayı 3 yürütülebilir dosyaları vardır; İstemci, hizmeti ve her uygulama için teslim edilemeyen kuyruktan okuyan ve hizmete ileti beşe edilemeyen hizmet. Konsol uygulamaları windows konsol çıkışında ile tümü.

> [!NOTE]
>  Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez. İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletilerini alır. Hizmeti başlatın ve böylece kuyruğa oluşturulabilir kapatılmalıdır.

 İstemci, istemci çalıştırırken, ileti görüntülenir:

```
Press <ENTER> to terminate client.
```

 İletiyi göndermek istemci çalıştı ancak kısa bir zaman aşımı iletisi süresi doldu ve artık her uygulama için eski ileti sırası olarak sıraya alınır.

 İletiyi okur ve görüntüler hata kodu ve ileti hizmet beşe edilemeyen hizmet çalıştırılacaktır.

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

 Hizmet başlar ve ardından yakın iletiyi okur ve işler.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012'de Sunucu Yöneticisi'ni açın.

    2. Genişletin **özellikleri** sekmesi.

    3. Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.

    4. Denetleme **işlem** kutusu.

    5. Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.

3. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Örnek tek veya çoklu bilgisayar yapılandırma değişikliği kuyrukta adları uygun şekilde, localhost bilgisayarın tam adıyla değiştirerek çalıştırıp yönergeleri [WindowsCommunicationFoundationörnekleriniçalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği için bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyi ayarlayarak aktarım güvenliği devre dışı kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Uç nokta bağlamayla ilişkili uç noktanın ayarlayarak olduğundan emin olun `bindingConfiguration` özniteliği.

2. Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemci üzerindeki yapılandırmayı değiştirdiğinizden emin olun.

    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarlamakla eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.

## <a name="comments"></a>Açıklamalar
 Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkin. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte aktarım güvenliği türünü belirleyin. Varsayılan kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Kimlik doğrulama ve imzalama özelliği sağlamak MSMQ için bir etki alanının parçası olması gerekir. Bir etki alanının parçası olmayan bir bilgisayarda bu örneği çalıştırmak, şu hatayı alırsınız: "Kullanıcının iç message queuing sertifikası yok".

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
