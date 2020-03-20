---
title: Teslim Edilemeyen İletiler Sırası
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: eab1c52f4d0b3d0f82cf561a9478ea8233598e1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144954"
---
# <a name="dead-letter-queues"></a>Teslim Edilemeyen İletiler Sırası
Bu örnek, teslimbaşarısız olan iletilerin nasıl işleyeceğini ve işleyeceğini gösterir. [İşlenmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayanmaktadır. Bu örnek `netMsmqBinding` bağlama kullanır. Hizmet, sıraya alınan iletileri alan hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

> [!NOTE]
> Bu örnek, yalnızca Windows Vista'da kullanılabilen her uygulama ölü harf sıranı gösterir. Örnek, Windows Server 2003 ve Windows XP'de MSMQ 3.0 için varsayılan sistem çapındaki kuyrukları kullanacak şekilde değiştirilebilir.

 Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar. Daha doğrusu, istemci sıraya ileti gönderir. Hizmet, kuyruktan iletiler alır. Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.

 Sıralı iletişim belirli bir miktarda uyku damıtma içerebileceğinden, iletinin zaman geçtiyse uygulamaya teslim edilmediğinden emin olmak için iletide bir zaman-canlı değeri ilişkilendirmek isteyebilirsiniz. Ayrıca, bir uygulamanın iletinin teslimde başarısız olup olmadığı konusunda bilgilendirilmeleri gereken durumlar da vardır. İletide yayınlanacak zaman dolduğunda veya ileti nin teslimi başarısız olduğunda, ileti nin ölü harf kuyruğuna konması gibi tüm bu gibi durumlarda. Gönderme uygulaması daha sonra ölü harf kuyruğundaki iletileri okuyabilir ve hiçbir eylemden başarısız teslimin nedenlerini düzeltmeye ve iletiyi yeniden göndermeye kadar değişen düzeltici eylemlerde bulunabilir.

 `NetMsmqBinding` Bağlamadaki ölü harf sırası aşağıdaki özelliklerle ifade edilir:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>istemci tarafından gerekli ölü harf sırası türünü ifade etmek için özellik. Bu numaralandırma aşağıdaki değerlere sahiptir:

- `None`: İstemci tarafından ölü harf sırası gerekmez.

- `System`: Sistem ölü harf sırası ölü iletileri depolamak için kullanılır. Sistem ölü harf sırası bilgisayarda çalışan tüm uygulamalar tarafından paylaşılır.

- `Custom`: Ölü iletileri depolamak <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> için özelliği kullanarak belirtilen özel bir ölü harf sırası kullanılır. Bu özellik yalnızca Windows Vista'da kullanılabilir. Bu, uygulamanın aynı bilgisayarda çalışan diğer uygulamalarla paylaşmak yerine kendi ölü harf sırasını kullanması gerektiğinde kullanılır.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>ölü harf sırası olarak kullanılacak belirli sırayı ifade etme özelliği. Bu yalnızca Windows Vista'da kullanılabilir.

 Bu örnekte, istemci bir işlem kapsamından hizmete bir toplu ileti gönderir ve bu iletiler için "canlı kullanım süresi" için rasgele düşük bir değer belirtir (yaklaşık 2 saniye). İstemci ayrıca, süresi dolmuş iletileri sıraya girmek için kullanılacak özel bir ölü harf kuyruğu da belirtir.

 İstemci uygulaması ölü harf kuyruğundaki iletileri okuyabilir ve iletiyi yeniden göndermeyi deneyebilir veya özgün iletinin ölü harf kuyruğuna yerleştirilmesine ve iletiyi göndermesine neden olan hatayı düzeltebilir. Örnekte, istemci bir hata iletisi görüntüler.

 Hizmet sözleşmesi, `IOrderProcessor`aşağıdaki örnek kodda gösterildiği gibi.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Örnekteki hizmet [kodu, İşlenmiş MSMQ Bağlama'ya](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)ait.

 Hizmetle iletişim bir işlem kapsamında gerçekleşir. Hizmet kuyruktaki iletileri okur, işlemi gerçekleştirir ve ardından işlemin sonuçlarını görüntüler. Uygulama ayrıca ölü harfli iletiler için ölü harf sırası oluşturur.

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

 İstemcinin yapılandırması, iletinin hizmete ulaşması için kısa bir süre belirtir. İleti belirtilen süre içinde iletilemiyorsa, iletinin süresi doluyor ve ölü harf sırasına taşınır.

> [!NOTE]
> İstemcinin iletiyi belirtilen süre içinde servis kuyruğuna teslim etmesi mümkündür. Ölü harf hizmetini iş başında gördüğünüzden emin olmak için, hizmeti başlatmadan önce istemciyi çalıştırmalısınız. İleti zaman ları dışarı ve ölü harf servisine teslim edilir.

 Uygulama, ölü harf sırası olarak hangi sıranın kullanılacağını tanımlamalıdır. Sıra belirtilmemişse, varsayılan sistem genelinde ki işlem li harf sırası ölü iletileri sıraya almak için kullanılır. Bu örnekte, istemci uygulaması kendi uygulama ölü harf sırasını belirtir.

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

 Ölü harfli ileti hizmeti, ölü harf kuyruğundan gelen iletileri okur. Ölü harfli ileti hizmeti `IOrderProcessor` sözleşmeyi uygular. Ancak uygulanması siparişleri işlemek değildir. Ölü harfileti hizmeti bir istemci hizmetidir ve siparişleri işleme imla sıyrık ları yoktur.

> [!NOTE]
> Ölü harf sırası bir istemci sırasıdır ve istemci sıra yöneticisi için yereldir.

 Ölü harfli ileti hizmeti uygulaması, iletinin teslimi başarısız olmasının nedenini denetler ve düzeltici önlemler alır. İleti başarısızlığının nedeni iki sayısallandırmada yakalanır <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Aşağıdaki örnek <xref:System.ServiceModel.Channels.MsmqMessageProperty> kodda <xref:System.ServiceModel.OperationContext> gösterildiği gibi alabilirsiniz:

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

 Ölü harf kuyruğundaki iletiler, iletiyi işleyen hizmete gönderilen iletilerdir. Bu nedenle, ölü harfileti hizmeti kuyruktaki iletileri okuduğunda, Windows Communication Foundation (WCF) kanal katmanı uyuşmazlığı uç noktalarda bulur ve iletiyi göndermez. Bu durumda, ileti sipariş işleme hizmetine yöneliktir, ancak ölü harf iletisi hizmeti tarafından alınır. Farklı bir uç noktaya yönelik bir ileti almak için, herhangi bir adresle `ServiceBehavior`eşleşen bir adres filtresi . Bu, ölü harf kuyruğundan okunan iletileri başarıyla işlemek için gereklidir.

 Bu örnekte, başarısız olmasının nedeni iletinin zaman lanmış olmasıysa, ölü harf iletisi hizmeti iletiyi yeniden gönderir. Diğer tüm nedenlerle, aşağıdaki örnek kodda gösterildiği gibi teslim hatasını görüntüler:

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

 Aşağıdaki örnek, ölü harfli ileti yapılandırmasını gösterir:

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

 Örneği çalıştıran, ölü harf sırasının her uygulama için nasıl çalıştığını görmek için çalıştırılabilen 3 yürütülebilir vardır; istemci, hizmet ve her uygulama için ölü harf kuyruğundan okuyan ve iletiyi hizmete yeniden gönderen bir ölü harf hizmeti. Tüm konsol pencerelerinde çıkış ile konsol uygulamaları.

> [!NOTE]
> Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışır durumda olması gerekmez. İstemciyi çalıştırabilir, kapatabilir ve sonra hizmeti başlatabilir ve yine de iletilerini alır. Sıranın oluşturulabilmesi için hizmeti başlatıp kapatmanız gerekir.

 İstemciyi çalıştırırken, istemci iletiyi görüntüler:

```console
Press <ENTER> to terminate client.
```

 İstemci iletiyi göndermeyi denedi, ancak kısa bir zaman aşımıyla iletinin süresi doldu ve artık her uygulama için ölü harf kuyruğunda sıraya girdi.

 Daha sonra, iletiyi okuyan ve hata kodunu görüntüleyen ve iletiyi hizmete geri gönderen ölü harf li servisini çalıştırırsınız.

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 Hizmet başlar ve sonra dargın iletiyi okur ve işler.

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

2. Önce hizmet çalıştırılırsa, sıranın mevcut olduğundan emin olmak için denetler. Sıra yoksa, hizmet bir tane oluşturur. Sırayı oluşturmak için önce hizmeti çalıştırabilir veya MSMQ Sıra Yöneticisi aracılığıyla bir hizmet oluşturabilirsiniz. Windows 2008'de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012'de Sunucu Yöneticisi'ni açın.

    2. **Özellikler** sekmesini genişletin.

    3. Özel **İleti Kuyrukları'nı**sağ tıklatın ve **Yeni**, **Özel Sıra'yı**seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni `ServiceModelSamplesTransacted` sıranın adı olarak girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

4. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak için sıra adlarını uygun şekilde değiştirin, localhost'u bilgisayarın tam adı ile değiştirin ve [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Bir çalışma grubuna katılan bir bilgisayarda örnek çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modunu ve koruma `None` düzeyini aşağıdaki örnek yapılandırmada gösterildiği gibi ayarlayarak aktarım güvenliğini kapatın:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Bitiş noktasının özniteliğini ayarlayarak bitiş noktasının `bindingConfiguration` bağlamayla ilişkili olduğundan emin olun.

2. Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemcideki yapılandırmayı değiştirdiğinden emin olun.

    > [!NOTE]
    > `None` Ayar `security mode` ayarı `MsmqAuthenticationMode` `MsmqProtectionLevel` ve `Message` güvenlik ' `None`e eşittir.

## <a name="comments"></a>Yorumlar
 `netMsmqBinding` Varsayılan olarak bağlama aktarımı ile güvenlik etkinleştirilir. İki özellik `MsmqAuthenticationMode` `MsmqProtectionLevel`ve birlikte aktarım güvenlik türünü belirler. Varsayılan olarak kimlik doğrulama modu `Windows` ayarlanır ve koruma `Sign`düzeyi . MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için, bir etki alanının parçası olması gerekir. Bu örneği etki alanının parçası olmayan bir bilgisayarda çalıştırıyorsanız, aşağıdaki hatayı alırsınız: "Kullanıcının iç ileti sıraya alma sertifikası yok".

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
