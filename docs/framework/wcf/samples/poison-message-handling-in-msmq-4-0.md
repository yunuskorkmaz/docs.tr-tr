---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: d1d23ffd600e7f770b942899ecc3b493b84c605a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837824"
---
# <a name="poison-message-handling-in-msmq-40"></a>MSMQ 4.0'da Zehirli İleti İşleme
Bu örnek, bir hizmette çok zararlı ileti işlemenin nasıl gerçekleştirileceğini gösterir. Bu örnek, [IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayalıdır. Bu örnek `netMsmqBinding`kullanır. Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.

 Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. Daha kesin olarak, istemci iletileri bir kuyruğa gönderir. Hizmet kuyruktaki iletileri alır. Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.

 Zararlı ileti, iletiyi okuyan hizmet iletiyi işleyemeyecek ve bu nedenle iletinin okunduğu işlemi sonlandırdığında bir kuyruktan sürekli okunan bir iletidir. Bu gibi durumlarda ileti yeniden denenir. Bu, iletiyle ilgili bir sorun varsa teorik olarak sonsuza kadar devam edebilir. Bu, yalnızca kuyruktan okumak ve hizmet işlemini çağırmak için işlem kullandığınızda gerçekleşebilir.

 NetMsmqBinding, MSMQ sürümüne bağlı olarak, zarar iletilerinin tam algılanması için sınırlı algılamayı destekler. İleti kired olarak algılandıktan sonra, çeşitli yollarla işlenebilir. MSMQ sürümüne bağlı olarak, NetMsmqBinding, zarar iletilerinin tam işlenmesini sağlamak için sınırlı işlemeyi destekler.

 Bu örnek, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformunda ve Windows Vista 'da sunulan tam zararlı tesislerde sunulan sınırlı zarar özelliklerini gösterir. Her iki örnekte de amaç, zarar mesajını sıradan başka bir kuyruğa taşır ve bu da bir zarar iletisi hizmeti tarafından hizmet verebilir.

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v 4.0 zarar Işleme örneği
 Windows Vista 'da, MSMQ, zarar iletilerini depolamak için kullanılabilen bir zarar alt sıra özelliği sağlar. Bu örnek, Windows Vista kullanarak zarar iletileriyle ilgili en iyi yöntemi gösterir.

 Windows Vista 'da zehirli ileti algılama oldukça karmaşıktır. Algılamaya yardımcı olan 3 özellik vardır. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A>, belirli bir iletinin kuyruktan yeniden okunduğu ve işlenmek üzere uygulamaya dağıtıldığı sayıdır. İleti uygulamaya dağıtılamadı veya uygulama işlemi hizmet işleminde geri götürüliyorsa, bir ileti sıraya geri alındığında kuyruktan yeniden okunabilir. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>, iletinin yeniden deneme kuyruğuna kaç kez taşındığını sayısıdır. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> ulaşıldığında, ileti yeniden deneme kuyruğuna taşınır. Özellik <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>, ileti yeniden deneme sırasından ana sıraya geri taşındıktan sonraki zaman gecikmesi olur. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0 ' a sıfırlanır. İleti yeniden denenir. İletiyi okuma denemeleri başarısız olduysa, ileti kired olarak işaretlenir.

 İleti kired olarak işaretlendiğinde, ileti <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> Numaralandırmadaki ayarlara göre dağıtılır. Olası değerleri yeniden yinelemek için:

- Hata (varsayılan): dinleyiciye ve ayrıca hizmet konağına hata vermek Için.

- Bırakın: iletiyi bırakmak Için.

- Taşı: iletiyi zarar iletisi alt kuyruğuna taşımak Için. Bu değer yalnızca Windows Vista 'da kullanılabilir.

- Reddet: iletiyi, gönderenin teslim edilemeyen ileti kuyruğuna geri göndererek iletiyi reddetmek Için. Bu değer yalnızca Windows Vista 'da kullanılabilir.

 Örnek, zarar iletisi için `Move` eğilimini kullanmayı gösterir. `Move`, iletinin zarar alt kuyruğuna taşınmasına neden olur.

 Hizmet sözleşmesi, kuyruklarla birlikte kullanılmak üzere uygun tek yönlü bir hizmeti tanımlayan `IOrderProcessor`.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Hizmet işlemi, sırayı işlediğini belirten bir ileti görüntüler. Zarar iletisi işlevselliğini göstermek için `SubmitPurchaseOrder` hizmeti işlemi, hizmetin rastgele bir çağrısında işlemi geri almak için bir özel durum oluşturur. Bu, iletinin sıraya geri alınmasına neden olur. Sonuç olarak ileti, zarar olarak işaretlenir. Yapılandırma, zarar iletisini zarar alt kuyruğuna taşımak üzere ayarlanır.

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 Hizmet yapılandırması şu zarar iletisi özelliklerini içerir: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a>Zarar iletisi kuyruğundan iletileri işleme
 Zarar iletisi hizmeti, son zarar iletisi kuyruğundan iletileri okur ve bunları işler.

 Zarar iletisi sırasındaki iletiler, iletiyi işleyen hizmete yönelik mesajlar, bu da zarar iletisi hizmet uç noktasından farklı olabilir. Bu nedenle, zarar iletisi hizmeti sıradaki iletileri okuduğunda, WCF kanal katmanı uç noktalarında uyuşmazlığını bulur ve iletiyi göndermez. Bu durumda, ileti sipariş işleme hizmetine değinmekte, ancak zarar iletisi hizmeti tarafından alınmakta olur. İleti farklı bir uç noktaya adreslenmiş olsa bile iletiyi almaya devam etmek için, eşleşme ölçütünün iletinin adreslendiği tüm hizmet uç noktaları ile eşleşmesi durumunda adresleri filtrelemek için bir `ServiceBehavior` eklememiz gerekir. Bu, zarar ileti sırasından okunan iletileri başarıyla işlemek için gereklidir.

 Zarar iletisi Hizmeti uygulamasının kendisi, hizmet uygulamasına çok benzer. Sözleşmeyi uygular ve siparişleri işler. Kod örneği aşağıdaki gibidir.

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 Sipariş sırasından iletileri okuyan sipariş işleme hizmetinin aksine, zarar iletisi hizmeti, zarar alt kuyruğundan iletileri okur. Poison kuyruğu ana sıranın alt kuyruğudur, "Poison" olarak adlandırılır ve MSMQ tarafından otomatik olarak oluşturulur. Bu durumda, aşağıdaki örnek yapılandırmada gösterildiği gibi ana sıra adını, ardından ";" ve alt sıra adını (Bu örnekte "Poison") belirtin.

> [!NOTE]
> MSMQ v 3.0 örneğinde, zarar sırası adı, iletiyi taşıdığımız sıra yerine bir alt kuyruk değildir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 Örneği çalıştırdığınızda, istemci, hizmet ve zarar iletisi hizmeti etkinlikleri konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Hizmetleri kapatmak için her bir konsol penceresinde ENTER tuşuna basın.

 Hizmet çalışmaya başlar, siparişlerin işlenmesi ve rastgele işlem, işlemeyi sonlandırmaya başlar. İleti siparişi işlediğini gösteriyorsa, hizmetin gerçekten bir iletiyi sonlandırdığını görene kadar başka bir ileti göndermek için istemciyi yeniden çalıştırabilirsiniz. Yapılandırılan zarar ayarlarına bağlı olarak, ileti son zararlı bir sıraya taşınmadan önce işleme için bir kez denenir.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 Zarar sırasından zarar görmüş iletiyi okumak için zarar iletisi hizmetini başlatın. Bu örnekte, zarar iletisi hizmeti iletiyi okur ve işler. Sonlandırılan ve zarar veren satın alma sırasının, zarar iletisi hizmeti tarafından okunduğunu görebilirsiniz.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir. Sıra yoksa, hizmet bir tane oluşturur. Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz. Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012 ' de Sunucu Yöneticisi açın.

    2. **Özellikler** sekmesini genişletin.

    3. **Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için, kuyruk adlarını localhost yerine gerçek ana bilgisayar adını yansıtacak şekilde değiştirin ve [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

 `netMsmqBinding` bağlama taşıması ile varsayılan olarak güvenlik etkindir. İki özellik, `MsmqAuthenticationMode` ve `MsmqProtectionLevel`birlikte taşıma güvenliği türünü belirleme. Varsayılan olarak, kimlik doğrulama modu `Windows` olarak ayarlanır ve koruma düzeyi `Sign`olarak ayarlanır. Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ 'nun bir etki alanının parçası olması gerekir. Bu örneği bir etki alanının parçası olmayan bir bilgisayarda çalıştırırsanız, şu hatayı alırsınız: "kullanıcının iç Message Queuing sertifikası yok".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse, aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini `None` olarak ayarlayarak aktarım güvenliğini kapatın:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Uç noktanın bindingConfiguration özniteliğini ayarlayarak, bitiş noktasının bağlama ile ilişkili olduğundan emin olun.

2. Örneği çalıştırmadan önce, Kirmessageserver, sunucu ve istemcideki yapılandırmayı değiştirdiğinizden emin olun.

    > [!NOTE]
    > `security mode` `None` ayarlanması, `Message` `MsmqAuthenticationMode`, `MsmqProtectionLevel`ve `None`güvenliğini ayarlamaya eşdeğerdir.  
  
3. Meta veri değişimi 'nin çalışması için, http bağlamasıyla bir URL kaydedebiliyoruz. Bu, hizmetin yükseltilmiş bir komut penceresinde çalıştırılmasını gerektirir. Aksi takdirde, şöyle bir özel durum alırsınız: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
