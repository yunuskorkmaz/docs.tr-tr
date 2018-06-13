---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: d0ddab7832e308336d5bfb1c5f75fd13fe63fe72
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809511"
---
# <a name="poison-message-handling-in-msmq-40"></a>MSMQ 4.0'da Zehirli İleti İşleme
Bu örnek, bir hizmet olarak işleme zehir iletisi gerçekleştirmek gösterilmiştir. Bu örnek dayanır [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek. Bu örnekte `netMsmqBinding`. Hizmeti, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulamasıdır.  
  
 Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar. Daha hassas bir şekilde istemci kuyruğa ileti gönderir. Hizmet kuyruktan iletileri alır. Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Zararlı bir ileti, ileti okunurken hizmeti iletiyi işleyemediğinde kuyruktan art arda okunur ve bu nedenle altında ileti okuma işlemi sonlandırır bir iletidir. Böyle durumlarda, ileti yeniden denenir. İleti ile ilgili bir sorun varsa bu teorik olarak sonsuza kadar geçebilir. Sıradan Okuma ve hizmet işlemini çağırmak için işlemleri kullandığınızda yalnızca oluşabilir olduğunu unutmayın.  
  
 MSMQ sürümlerine göre NetMsmqBinding zarar iletileri tam algılanması için sınırlı algılama destekler. Ardından ileti zarar gibi algılandı sonra çeşitli yollarla işlenebilir. Yeniden MSMQ sürümlerine göre NetMsmqBinding zarar iletileri tam işlenmesi için sınırlı işleme destekler.  
  
 Bu örnek sağlanan sınırlı zararlı tesislerde gösterilmektedir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform ve sağlanan tam zararlı tesis [!INCLUDE[wv](../../../../includes/wv-md.md)]. Her iki örneklerinde hedefi olan zehir iletisi dışarı Taşı kuyruğunu sonra zehir iletisi hizmeti tarafından hizmet başka bir kuyruğa.  
  
## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 Poison örnek işleme  
 İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ zarar iletileri depolamak için kullanılan bir zarar alt sıra olanak sağlar. Bu örneği kullanarak zarar iletileri postalarla en iyi uygulama gösterir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Zehir iletisi algılama [!INCLUDE[wv](../../../../includes/wv-md.md)] oldukça karmaşık değil. Algılama Yardım 3 özellikleri vardır. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Sayıda belirli bir ileti kuyruktan yeniden okuma ve işleme için uygulama gönderilen. Bu geri sıraya ileti uygulamaya gönderilen olamaz veya uygulama işlem hizmet işlemini geri alır. geçirdiğinizde bir ileti kuyruktan yeniden okunur. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> yeniden deneme kuyruğuna ileti taşınır sayısıdır. Zaman <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> olan ulaşıldı, yeniden kuyruğa ileti taşınır. Özellik <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> geçmesi ileti taşınırken yeniden deneme sıradan geri ana sıranın zaman gecikmesi. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0 değerine sıfırlanır. İleti yeniden denenir. İleti okumak için tüm denemeleri başarısız, ileti zarar olarak işaretlenir.  
  
 İleti zarar olarak işaretlendikten sonra ileti ile ayarlara göre dağıtılır <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> numaralandırması. Olası değerler yinelemek için:  
  
-   Hata (varsayılan): dinleyici ve ayrıca hizmet konağı alınmasını.  
  
-   Açılan: ileti bırakılamadı.  
  
-   Taşıma: ileti zehir iletisi alt sıraya taşınamadı. Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   Reddetme: ileti reddetmek için gönderene ileti gönderme sahipsiz sıra. Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Örnek kullanarak gösterir `Move` zehir iletisi için eğilimi. `Move` İletinin zararlı alt kuyruğuna Taşı neden olur.  
  
 Hizmet sözleşme `IOrderProcessor`, kuyruklar ile kullanım için uygun bir tek yönlü hizmet tanımlar.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Hizmet işlemi, sipariş işleme bildiren bir ileti görüntülenir. Zehir iletisi işlevselliğini göstermek için `SubmitPurchaseOrder` hizmet işlemi rastgele çağrılması hizmeti ile ilgili işlem geri almak için bir özel durum oluşturur. Bu iletinin kuyrukta geri yerleştirilecek neden olur. Sonunda iletisi poison işaretlenmiş. Zehir iletisi zarar alt kuyruğuna taşımak için yapılandırmasını ayarlayın.  

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

 Hizmet yapılandırması aşağıdaki zehirli ileti özellikleri içerir: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.  
  
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
  
## <a name="processing-messages-from-the-poison-message-queue"></a>Zehirli ileti kuyruktan iletileri işleme  
 Zehirli ileti hizmeti son zehirli ileti kuyruktan iletileri okur ve onları işler.  
  
 Zehirli ileti sıradaki iletiler zehir iletisi hizmet uç noktasından farklı olabilir iletisi işliyor hizmetine gönderilen iletiler ' dir. Bu nedenle, zehirli ileti hizmeti kuyruktan iletileri okuduğunda WCF kanalı katman uyuşmazlığı uç noktalarını bulur ve ileti göndermez. Bu durumda, ileti hizmeti işlem sırasını ele ancak zehir iletisi hizmeti tarafından alınan. İleti için farklı bir uç noktası ele olsa bile iletisini almaya devam etmek için biz eklemelisiniz bir `ServiceBehavior` eşleştirme ölçütü olduğu için ileti ele herhangi bir hizmet uç nokta eşleşecek şekilde filtre adreslere. Bu, başarılı bir şekilde zehirli ileti kuyruğundan okumak iletileri işlemek için gereklidir.  
  
 Zehir iletisi hizmet uygulaması kendi hizmet uygulaması çok benzer. Sözleşme uygular ve siparişleri işler. Kod örneği aşağıdaki gibidir.  

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

 Sipariş kuyruktan iletileri okur hizmeti işlem sırasını zehir iletisi hizmeti zararlı alt kuyruktan iletileri okur. Zararlı sıranın ana sıranın alt bir sıra, "poison" olarak adlandırılır ve MSMQ tarafından otomatik olarak oluşturulur. Erişmek için ana sıranın adından sağlayan bir ";" ve alt sıra adı, bu durumda-"Aşağıdaki örnek yapılandırmada gösterildiği gibi zararlı".  
  
> [!NOTE]
>  MSMQ v3.0 örnek zararlı sıra adı yerine biz iletiye taşınmış sıranın alt bir sıra değil.  
  
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
  
 Örneği çalıştırdığınızda, istemci, hizmet ve zehir iletisi hizmet etkinlikleri konsol pencerelerinde görüntülenir. İstemci hizmeti alma iletileri görebilirsiniz. Her konsol penceresinde Hizmetleri'ni kapatmak için ENTER tuşuna basın.  
  
 Hizmeti çalıştıran, sipariş işleme başlatır ve işlem sonlandırmak rastgele başlatır. İleti sırası işlediğinden gösteriyorsa, istemci hizmeti aslında bir ileti sonlandırıldı görene kadar başka bir iletiyi göndermeyi yeniden çalıştırabilirsiniz. Yapılandırılmış zararlı ayarlarına bağlı olarak, ileti, son zararlı kuyruğuna geçmeden önce işleme için bir kez denenir.  
  
```  
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
  
 Zarar görmüş ileti zararlı kuyruktan okunmak üzere zehir iletisi hizmeti başlatın. Bu örnekte, zehirli ileti hizmeti iletiyi okur ve işler. Sonlandırılacak ve zarar satın alma siparişi zehir iletisi hizmeti tarafından okunur görebilir.  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin ve localhost yerine gerçek ana bilgisayar yansıtmak üzere sıra adları değiştirme [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkindir. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenemedi. Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Kimlik doğrulaması ve imzalama özellik MSMQ için bir etki alanının parçası olması gerekir. Bu örnek bir etki alanının parçası olmayan bir bilgisayarda çalıştırmanız gerekiyorsa aşağıdaki hata iletisini: "kullanıcının iç message queuing sertifikası yok".  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örnek bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     Uç noktanın bindingConfiguration özniteliğini ayarlayarak uç nokta bağlama ile ilişkili olduğundan emin olun.  
  
2.  Örneği çalıştırmadan önce PoisonMessageServer, sunucu ve istemci yapılandırmasına değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarına eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel`, ve `Message` güvenlik `None`.  
  
3.  İş Meta veri değişimi için sırayla biz http bağlama ile bir URL kaydedin. Bu hizmet bir yükseltilmiş komut istemi penceresine çalıştırmanızı gerektirir. Aksi halde, bir özel durum gibi alın: işlenmeyen özel durum: System.ServiceModel.AddressAccessDeniedException: HTTP URL kaydedemedi http://+:8000/ServiceModelSamples/service/. İşleminizi bu ad alanına erişim hakları yok (bkz http://go.microsoft.com/fwlink/?LinkId=70353 Ayrıntılar için). System.Net.HttpListenerException--->: erişim reddedildi.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a>Ayrıca Bkz.
