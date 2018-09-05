---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 904eee34b8be02dfab560069ef5491200be9cf07
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522639"
---
# <a name="poison-message-handling-in-msmq-40"></a>MSMQ 4.0'da Zehirli İleti İşleme
Bu örnek, zehirli ileti bir hizmet olarak işleme gerçekleştirmek nasıl gösterir. Bu örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek. Bu örnekte `netMsmqBinding`. Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.  
  
 Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar. Daha kesin bir istemci bir kuyruğa iletiler gönderir. Hizmet iletileri kuyruktan alır. Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.  
  
 Zehirli ileti, ileti okuma hizmeti iletiyi işlerken art arda bir kuyruktan okunur ve bu nedenle altında ileti okuma işlemi sonlandıran bir iletidir. Bu gibi durumlarda, ileti yeniden denenir. İletiyle ilgili bir sorun varsa bu teorik olarak süresiz geçebilir. Kuyruktan okunmak ve hizmet işlemini çağırmak için işlemleri kullandığınızda yalnızca oluşabilir olduğunu unutmayın.  
  
 MSMQ sürümüne bağlı olarak, tam zehirli iletilerin algılanması için sınırlı algılama NetMsmqBinding destekler. Ardından iletiyi zarar olarak algılandı sonra birkaç şekilde işlenebilir. Yeniden MSMQ sürümüne bağlı olarak, NetMsmqBinding zehirli iletilerin tam işleme için sınırlı işlemeyi destekler.  
  
 Bu örnek sağlanan sınırlı zehirli özelliklerini göstermektedir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform ve sağlanan tam zehirli tesis [!INCLUDE[wv](../../../../includes/wv-md.md)]. Her iki örneklerinde hedefi olan zehirli ileti dışarı Taşı sırasına ardından zehirli ileti hizmeti tarafından hizmet başka bir kuyruk için.  
  
## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 Poison örnek işleme  
 İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ zehirli iletileri depolamak için kullanılan bir zehirli alt kuyruk olanak sağlar. Bu örnek, en iyi zehirli iletileri kullanarak uğraşmanızı gösterir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Zehirli ileti algılama [!INCLUDE[wv](../../../../includes/wv-md.md)] oldukça karmaşık olduğundan. Yardımcı algılama 3 özellikleri vardır. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Sayıda belirli bir ileti kuyruktan yeniden okuma ve işleme uygulamaya gönderilen. Bunu yeniden kuyruğa ileti uygulamaya dağıtılamaz veya uygulama hizmeti işleminin geri işlem yapar çünkü alınan olduğunda yeniden bir ileti kuyruktan okunur. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> yeniden deneme kuyruğa ileti taşınır sayısıdır. Zaman <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> olan üst sınıra ulaşıldı, yeniden deneme kuyruğa ileti taşınır. Özellik <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> sonra iletiyi taşındıysa yeniden deneme kuyruktan geri ana kuyruğa zaman gecikmesi. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0 değerine sıfırlanır. İleti yeniden denenir. İleti okumak için tüm denemeler başarısız olursa, ileti zarar olarak işaretlenir.  
  
 İleti zarar olarak işaretlendikten sonra ileti ile ayarlarına göre dağıtılır <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> sabit listesi. Olası değerler yinelemek için:  
  
-   Hata (varsayılan): hata dinleyicisi ve ayrıca hizmet ana bilgisayarı için.  
  
-   Bırakma: ileti bırakmak.  
  
-   Taşıma: zehirli ileti alt kuyruğuna ileti taşınır. Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   Reddet: ileti reddetmek için gönderene ileti gönderilirken geçerliliğini yitirmiş kuyruk. Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Örnek kullanmayı gösterir `Move` zehirli ileti için değerlendirme. `Move` zehirli alt kuyruğuna Taşı iletiyi neden olur.  
  
 Hizmet sözleşme `IOrderProcessor`, kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Hizmet işlemi, sipariş işleme bildiren bir ileti görüntüler. Zehirli ileti işlevselliğini göstermek için `SubmitPurchaseOrder` hizmet işlemi hizmeti rastgele bir çağrıda işlem geri alınacak bir özel durum oluşturur. Bu iletinin geri sıraya koymak neden olur. Sonuçta ileti zarar işaretlenir. Yapılandırma, zehirli ileti zehirli alt kuyruğuna Taşı şekilde ayarlanır.  

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
 Zehirli ileti hizmet son zehirli ileti kuyruktan iletileri okuyan ve işler.  
  
 Zehirli ileti kuyruğu iletilerinde zehirli ileti hizmet uç noktasından farklı iletisi işliyor hizmete gönderilen iletileri ' dir. Bu nedenle, zehirli ileti hizmet iletileri kuyruktan okuyan, WCF kanal katmanını uyuşmazlığı uç noktaların bulur ve bu iletiyi göndermez. Bu durumda, ileti işleme hizmeti siparişin ele ancak zehirli ileti hizmet tarafından alınan. İleti farklı bir uç noktaya yönelik bile iletiyi almaya devam etmek biz eklemelisiniz bir `ServiceBehavior` filtre adreslerine eşleştirme ölçütü olduğu ileti ele alınan herhangi bir hizmet uç noktası eşleştirilecek. Bu, başarılı bir şekilde zehirli ileti kuyruktan okunmak iletilerini işlemek için gereklidir.  
  
 Zehirli ileti hizmet uygulaması kendi hizmet uygulaması için çok benzer. Bu sözleşme uygular ve siparişleri işler. Kod örneği aşağıdaki gibidir.  

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

 Sipariş işleme sırası kuyruktan iletileri okuyan hizmet, zehirli ileti hizmeti zehirli alt kuyruktan iletileri okur. Zehirli sıranın "poison" adlı bir alt kuyruk ana sıranın ve MSMQ tarafından otomatik olarak oluşturulur. Erişmek için ana kuyruk adından sağlayan bir ";" ve alt kuyruk adı, bu durumda-"Aşağıdaki örnek yapılandırmada gösterildiği zehirli".  
  
> [!NOTE]
>  MSMQ v3.0 örnek zehirli kuyruk adı yerine iletiye geçtiğimizi kuyruk bir alt kuyruk değil.  
  
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
  
 Örneği çalıştırdığınızda, konsol pencerelerinde istemci, hizmet ve zehirli ileti hizmet etkinlikleri görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi Hizmetleri kapatılmaya için ENTER tuşuna basın.  
  
 Hizmet çalışıyor, sipariş işleme başlar ve işlemesini sonlandırmak rastgele başlatır. İleti sırası işlediği gösteriyorsa, istemci hizmeti aslında bir ileti sonlandırıldı görene kadar başka bir iletiyi göndermeyi yeniden çalıştırabilirsiniz. Yapılandırılmış zehirli ayarlarına bağlı olarak, ileti son zehirli kuyruğa geçmeden önce işleme için bir kez denenir.  
  
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
  
 Zehirli kuyruktan zehirlenmiş iletiyi okumak için zehirli ileti hizmet başlatın. Bu örnekte, zehirli ileti hizmeti iletiyi okur ve işler. Sonlandırılacak ve zarar satınalma siparişi zehirli ileti hizmet tarafından okunur görebilir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletin **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin ve localhost yerine sunucunun gerçek ana bilgisayar'ı yansıtmak için kuyruk adları değiştirme [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkin. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte aktarım güvenliği türünü belirleyin. Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Kimlik doğrulama ve imzalama özelliği sağlamak MSMQ için bir etki alanının parçası olması gerekir. Bu örnek, bir etki alanının parçası olmayan bir bilgisayar üzerinde çalıştırırsanız, aşağıdaki hatayı alırsınız: "kullanıcının iç message queuing sertifika mevcut değil".  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği için bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyi ayarlayarak aktarım güvenliği devre dışı kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
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
  
2.  Örneği çalıştırmadan önce PoisonMessageServer, sunucu ve istemci üzerindeki yapılandırmayı değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarlamakla eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel`, ve `Message` güvenlik `None`.  
  
3.  Sırayla çalışması Meta veri değişimi için size bir URL http bağlaması ile kaydedin. Bu, hizmetin bir yükseltilmiş komut istemi penceresine çalıştırmanızı gerektirir. Aksi takdirde, bir özel durum gibi alın: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a>Ayrıca Bkz.
