---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144246"
---
# <a name="poison-message-handling-in-msmq-40"></a>MSMQ 4.0'da Zehirli İleti İşleme
Bu örnek, bir hizmette zehirli ileti işlemenin nasıl gerçekleştirilgösterdiğini gösterir. Bu [örnek, Transacted MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayanmaktadır. Bu örnek `netMsmqBinding`te . Hizmet, sıraya alınan iletileri alan hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır.

 Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar. Daha doğrusu, istemci sıraya ileti gönderir. Hizmet, kuyruktan iletiler alır. Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.

 Zehirli ileti, iletiyi okuyan hizmet iletiyi işleyemediğinde ve bu nedenle iletinin okunduğu işlemi sonlandırdığinde, bir kuyruktan sürekli olarak okunan iletidir. Bu gibi durumlarda, ileti yeniden denendir. İletiyle ilgili bir sorun varsa, bu teorik olarak sonsuza kadar devam edebilir. Bu yalnızca kuyruktan okumak ve hizmet işlemini çağırmak için hareketleri kullandığınızda oluşabilir.

 MSMQ sürümüne dayanarak, NetMsmqBinding zehirli mesajların tam tespiti için sınırlı algılama destekler. İleti nin zehirlendiği tespit edildikten sonra, çeşitli şekillerde ele alınabilir. Yine, MSMQ sürümüne dayalı, NetMsmqBinding zehirli mesajların tam işleme sınırlı işleme destekler.

 Bu örnek, Windows Server 2003 ve Windows XP platformunda sağlanan sınırlı zehir lenme olanaklarını ve Windows Vista'da sağlanan tam zehir lenme olanaklarını göstermektedir. Her iki örnekte de amaç, zehir iletisini sıranın dışına başka bir sıraya taşımaktır. Bu sıra daha sonra bir zehirli ileti hizmeti tarafından servis edilebilir.

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 Zehir İşleme Örneği
 Windows Vista'da, MSMQ zehirli iletileri depolamak için kullanılabilecek bir zehirli alt sıra olanağı sağlar. Bu örnek, Windows Vista kullanarak zehirli iletilerle başa çıkmanın en iyi uygulamalarını göstermektedir.

 Windows Vista'daki zehirli ileti algılama sı sofistikedir. Algılamaya yardımcı olan 3 özellik vardır. Belirli <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> bir iletinin kuyruktan yeniden okunması ve işleme için uygulamaya gönderilmesi sayısıdır. İleti uygulamaya gönderilemediği için sıraya geri konulduğunda bir ileti kuyruktan yeniden okunur veya uygulama hizmet işleminde hareketi geri alır. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>iletinin yeniden deneme kuyruğuna kaç kez taşındığıdır. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Erişildiğinde, ileti yeniden deneme sırasına taşınır. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> Özellik, iletinin yeniden deneme kuyruğundan ana kuyruğa geri taşındığı zaman gecikmesidir. Sıfırlanır <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0.0.'dır. İleti yeniden denendi. İletiyi okumaya yönelik tüm denemeler başarısız olduysa, ileti zehirli olarak işaretlenir.

 İleti zehirli olarak işaretlendikten sonra, ileti numaralandırmadaki <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> ayarlara göre ele alınır. Olası değerleri yinelemek için:

- Hata (varsayılan): Dinleyiciyi ve hizmet ana bilgisayarını hata etmek.

- Bırak: İletiyi bırakmak için.

- Taşı: İletiyi zehirli ileti alt sırasına taşımak için. Bu değer yalnızca Windows Vista'da kullanılabilir.

- Reddet: İletiyi reddetmek ve iletiyi gönderenin ölü harf kuyruğuna geri göndermek. Bu değer yalnızca Windows Vista'da kullanılabilir.

 Örnek, zehir mesajının eğiliminin `Move` kullanılmasını gösteriyor. `Move`iletinin zehirli alt sıraya taşınmasına neden olur.

 Hizmet sözleşmesi, `IOrderProcessor`kuyruklarla kullanıma uygun tek yönlü bir hizmeti tanımlayan sözleşmedir.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Hizmet işlemi, siparişi işlettiğini belirten bir ileti görüntüler. Zehir iletisi işlevselliğini `SubmitPurchaseOrder` göstermek için, hizmet işlemi, hizmetin rasgele bir çağırması üzerine hareketi geri almak için bir özel durum atar. Bu, iletinin sıraya geri konmasını neden olur. Sonunda mesaj zehir olarak işaretlenir. Yapılandırma, zehir iletisini zehir alt sırasına taşımak için ayarlanmıştır.

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

 Hizmet yapılandırması aşağıdaki zehirli ileti `receiveRetryCount` `maxRetryCycles`özelliklerini `retryCycleDelay`içerir: , , ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Zehirli ileti kuyruğundaki iletileri işleme
 Zehirli ileti hizmeti son zehirli ileti kuyruğundaki iletileri okur ve işler.

 Zehirli ileti kuyruğundaki iletiler, iletiyi işleyen hizmete yönlendirilen ve zehirli ileti hizmeti bitiş noktasından farklı olabilecek iletilerdir. Bu nedenle, zehirli ileti hizmeti kuyruktaki iletileri okuduğunda, WCF kanal katmanı bitiş noktalarındaki uyumsuzluğu bulur ve iletiyi göndermez. Bu durumda, ileti sipariş işleme hizmetine yöneliktir, ancak zehirli ileti hizmeti tarafından alınır. İleti farklı bir bitiş noktasına yönlendirilse bile iletiyi almaya `ServiceBehavior` devam etmek için, iletinin adreslendiği herhangi bir hizmet bitiş noktasıyla eşleşecek şekilde eşleşmek için filtre adreslerine bir eklememiz gerekir. Bu, zehirli ileti kuyruğundan okuduğunuz iletileri başarıyla işlemek için gereklidir.

 Zehirli ileti hizmeti uygulamasının kendisi hizmet uygulamasına çok benzer. Sözleşmeyi uygular ve emirleri işler. Kod örneği aşağıdaki gibidir.

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

 Sipariş kuyruğundan iletileri okuyan sipariş işleme hizmetinin aksine, zehirli ileti hizmeti zehirli alt sıradaki iletileri okur. Zehir sırası ana sıranın bir alt sırasıdır, "zehir" olarak adlandırılır ve msmq tarafından otomatik olarak oluşturulur. Erişmek için, aşağıdaki örnek yapılandırmada gösterildiği gibi, bu durumda -"zehir" ve ardından gelen ana sıra adını ";" ve alt sıra adını sağlayın.

> [!NOTE]
> MSMQ v3.0 için örnekte, zehir sıraadı bir alt sıra değil, daha çok iletiyi taşıdığımız sıradır.

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

 Örneği çalıştırdığınızda, istemci, hizmet ve zehirli ileti hizmeti etkinlikleri konsol pencerelerinde görüntülenir. Hizmetin istemciden ileti aldığını görebilirsiniz. Hizmetleri kapatmak için her konsol penceresinde ENTER tuşuna basın.

 Hizmet çalışmaya, siparişleri işlemeye ve rasgele işleme sonlandırmaya başlar başlar. İleti siparişi işlettiğini gösteriyorsa, hizmetin bir iletiyi gerçekten sonlandırdığını görene kadar istemciyi başka bir ileti göndermek için yeniden çalıştırabilirsiniz. Yapılandırılan zehir ayarlarına bağlı olarak, ileti son zehir kuyruğuna taşımadan önce bir kez işlenmek üzere denendi.

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

 Zehir kuyruğundan zehirli mesajı okumak için zehir mesajı servisini başlatın. Bu örnekte, zehirli ileti hizmeti iletiyi okur ve işler. Sonlandırılan ve zehirlenen satın alma siparişinin zehirli mesaj servisi tarafından okunduğunu görebilirsiniz.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

2. Önce hizmet çalıştırılırsa, sıranın mevcut olduğundan emin olmak için denetler. Sıra yoksa, hizmet bir tane oluşturur. Sırayı oluşturmak için önce hizmeti çalıştırabilir veya MSMQ Sıra Yöneticisi aracılığıyla bir hizmet oluşturabilirsiniz. Windows 2008'de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012'de Sunucu Yöneticisi'ni açın.

    2. **Özellikler** sekmesini genişletin.

    3. Özel **İleti Kuyrukları'nı**sağ tıklatın ve **Yeni**, **Özel Sıra'yı**seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni `ServiceModelSamplesTransacted` sıranın adı olarak girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

4. Örneği tek veya çapraz bilgisayar yapılandırmasında çalıştırmak için, sıra adlarını localhost yerine gerçek ana bilgisayar adını yansıtacak şekilde değiştirin ve [Windows Communication Foundation Samples'i çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.

 `netMsmqBinding` Varsayılan olarak bağlama aktarımı ile güvenlik etkinleştirilir. İki özellik `MsmqAuthenticationMode` `MsmqProtectionLevel`ve birlikte aktarım güvenlik türünü belirler. Varsayılan olarak, kimlik doğrulama modu `Windows` ayarlanır ve koruma `Sign`düzeyi . MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için, bir etki alanının parçası olması gerekir. Bu örneği etki alanının parçası olmayan bir bilgisayarda çalıştırıyorsanız, aşağıdaki hatayı alırsınız: "Kullanıcının iç ileti sıraya alma sertifikası yok".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Bir çalışma grubuna katılan bir bilgisayarda örnek çalıştırmak için

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

     Bitiş noktasının bağlamaYapılandırma özniteliğini ayarlayarak bitiş noktasının bağlamayla ilişkili olduğundan emin olun.

2. Örneği çalıştırmadan önce PoisonMessageServer, sunucu ve istemcideki yapılandırmayı değiştirdiğinden emin olun.

    > [!NOTE]
    > `None` Ayar, `security mode` ayarına `MsmqAuthenticationMode` `MsmqProtectionLevel`ve `Message` güvenlik `None`'e eşittir.  
  
3. Meta Veri Alışverişi'nin çalışması için http binding içeren bir URL kaydettiriyoruz. Bu, hizmetin yükseltilmiş bir komut penceresinde çalışmasını gerektirir. Aksi takdirde, gibi bir `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`özel durum olsun: .  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
