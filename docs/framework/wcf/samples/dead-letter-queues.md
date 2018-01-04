---
title: "Teslim Edilemeyen İletiler Sırası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09a41abc8bc9fc3469ba35d7c7cfbe85d05ca174
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dead-letter-queues"></a>Teslim Edilemeyen İletiler Sırası
Bu örnek, işler ve işlem teslim başarısız olmuş iletileri gösterilmiştir. Bağlı olduğu [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek. Bu örnekte `netMsmqBinding` bağlama. Hizmeti, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulamasıdır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
> [!NOTE]
>  Bu örnek yalnızca kullanılabilir olan her uygulama sahipsiz sıra gösteren [!INCLUDE[wv](../../../../includes/wv-md.md)]. Örnek üzerinde MSMQ 3.0 için varsayılan sistem genelinde kuyruklarını kullanma değiştirilebilir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar. Daha hassas bir şekilde istemci kuyruğa ileti gönderir. Hizmet kuyruktan iletileri alır. Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Kuyruğa alınan iletişim dormancy belirli bir miktar içerebildiğinden, yaşam süresi değeri zamanından daha sonra geçti, ileti uygulamaya teslim değil emin olmak için iletideki ilişkilendirmek isteyebilirsiniz. Burada bir uygulama bir ileti teslim başarısız olup olmadığını haberdar olmak gerekir durumlarda da vardır. Bu durumların tümünde gibi zaman yaşam ileti üzerinde süresi dolmuş veya ileti teslim başarısız olduğunda, ileti sahipsiz sıraya konur. Gönderen uygulama teslim edilemeyen kuyruğundaki iletileri okumak ve herhangi bir eylemi başarısız Teslimat nedenleri düzeltme ve iletiyi yeniden göndermeyi aralığı düzeltme girişimlerinde bulunun.  
  
 Sahipsiz sıra `NetMsmqBinding` bağlama aşağıdaki özelliklerinde ifade:  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>İstemci tarafından gerekli sahipsiz sırayı tür express özelliği. Bu numaralandırma aşağıdaki değerlere sahiptir:  
  
-   `None`: Hiçbir eski ileti sırası istemci tarafından gereklidir.  
  
-   `System`: Sistem sahipsiz sırayı ölü iletileri depolamak için kullanılır. Sistem sahipsiz sırayı bilgisayar üzerinde çalışan tüm uygulamalar tarafından paylaşılır.  
  
-   `Custom`Kullanarak belirtilen özel sahipsiz sırayı <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> özelliği ölü iletileri depolamak için kullanılır. Bu özellik yalnızca üzerinde kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Bu uygulama aynı bilgisayarda çalışan diğer uygulamalarla paylaşma yerine kendi sahipsiz sıra kullanmalıdır olduğunda kullanılır.  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>belirli sıranın atılacak kullanmak için express özelliği. Bu yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Bu örnekte, istemci hizmetinden bir işlem kapsamı içinde toplu iletiler gönderir ve "zaman yaşam" Bu iletiler (yaklaşık 2 saniye) için rasgele düşük bir değer belirtir. İstemci ayrıca sıraya alma süresi dolan iletileri kullanmak için özel bir sahipsiz sırayı belirtir.  
  
 İstemci uygulaması, sahipsiz sırayı ve ileti göndermek ya da yeniden deneme iletiler okuma ya da teslim edilemeyen sırasına ve ileti göndermek özgün ileti nedeniyle hatayı düzeltin. Örnekte, istemci bir hata iletisi görüntüler.  
  
 Hizmet sözleşme `IOrderProcessor`, aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 Örnek hizmet kodunda budur [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Hizmet ile iletişim bir işlem kapsamı içinde yer alır. Hizmet kuyruktan iletileri okur, işlemi gerçekleştirir ve işlemin sonuçlarını görüntüler. Uygulama atılacak teslim edilemeyen iletiler için de oluşturur.  
  
```  
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
  
 İstemcinin yapılandırma iletisinin hizmete erişmek kısa bir süre belirtir. Belirtilen süre içinde ileti iletilemedi, ileti süresi dolar ve sahipsiz sıraya taşınır.  
  
> [!NOTE]
>  İstemcinin belirtilen süre içinde hizmet kuyruğuna ileti teslim mümkündür. Eylem sahipsiz hizmetinde gördüğünüz emin olmak için İstemci Hizmeti başlatmadan önce çalıştırmanız gerekir. İletiyi zaman aşımına uğradı ve teslim edilemeyen hizmete teslim edilir.  
  
 Uygulamanın kendi eski ileti sırası olarak kullanmak için hangi kuyruğa tanımlamanız gerekir. Sıra belirtilmezse, varsayılan sistem genelinde işleme uygun eski ileti sırası eski iletilerin sıraya almak için kullanılır. Bu örnekte, istemci uygulaması, kendi uygulama sahipsiz sırayı belirtir.  
  
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
  
 Teslim edilemeyen ileti hizmeti iletileri teslim edilemeyen kuyruktaki iletileri okur. Teslim edilemeyen ileti hizmeti uygulayan `IOrderProcessor` sözleşme. Kendi uygulama ancak değil işlem siparişler. Teslim edilemeyen ileti hizmeti istemci hizmeti ve siparişleri işlemek için olanaklara sahip değil.  
  
> [!NOTE]
>  Sahipsiz sıra bir istemci sıra ve istemci sıra yerel olan.  
  
 Teslim edilemeyen iletisi hizmet uygulaması bir ileti teslim ve gerçekleştirilen işlemlerin düzeltici önlemleri başarısız nedeni denetler. Bir ileti başarısızlık nedeni iki numaralandırmalara yakalanan <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Alabilirsiniz <xref:System.ServiceModel.Channels.MsmqMessageProperty> gelen <xref:System.ServiceModel.OperationContext> aşağıdaki örnek kodda gösterildiği gibi:  
  
```  
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
    ….  
}  
```  
  
 İletileri teslim edilemeyen sırasındaki ileti işlenirken hizmetine gönderilen iletiler ' dir. Bu nedenle, ne zaman teslim edilemeyen ileti hizmeti okur iletileri sıradan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanal katmanını uyuşmazlığı uç noktalarını bulur ve ileti göndermez. Bu durumda, ileti hizmeti işlem sırasını ele ancak teslim edilemeyen ileti hizmeti tarafından alınan. Farklı bir uç noktası için gönderilen bir ileti almak için bir adres filtresinin eşleşen herhangi bir adres için belirtilen `ServiceBehavior`. Bu, başarılı bir şekilde teslim edilemeyen kuyruktan okunmak iletileri işlemek için gereklidir.  
  
 Başarısızlık nedeni ise, bu örnekte, teslim edilemeyen ileti hizmeti ileti iletinin zaman aşımına uğradı düzenini yeniden gönderir. Diğer nedenlerle, aşağıdaki örnek kodda gösterildiği gibi teslim hatası gösterir:  
  
```  
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
  
 Aşağıdaki örnek, bir teslim edilemeyen ileti için yapılandırmayı gösterir:  
  
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
  
 Örnek çalışır durumda sahipsiz sırayı her uygulama için nasıl çalıştığını görmek için 3 yürütülebilir dosyaların vardır; İstemci, hizmet ve her uygulama için teslim edilemeyen kuyruktaki iletileri okur ve hizmet iletiye yeniden gönderir sahipsiz hizmet. Tüm konsol uygulamaları konsol pencerelerinin çıktısında ile görüşün.  
  
> [!NOTE]
>  Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması gerekmez. İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala kendi iletilerini alır. Hizmeti başlatmak ve böylece sıranın oluşturulabilir kapatıldı.  
  
 İstemci çalıştırırken, istemci iletisini görüntüler:  
  
```  
Press <ENTER> to terminate client.  
```  
  
 İstemci ileti göndermeye çalıştı, ancak kısa bir zaman aşımı iletisi süresi ve her uygulama için teslim edilemeyen sırasındaki şimdi sıraya.  
  
 Ardından, iletiyi okur ve hata kodunu görüntüler ve iletiye hizmeti yeniden gönderir sahipsiz hizmeti de çalıştırın.  
  
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
  
 Hizmet başlatır ve ardından yakın iletiyi okur ve işler.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Örnek tek veya çapraz bilgisayar yapılandırması değişikliği kuyrukta adları uygun şekilde, localhost bilgisayarın tam adıyla değiştirerek çalıştırın ve yönergeleri izleyin için [Windows Communication Foundation örnekleriçalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örnek bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için  
  
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
  
     Uç nokta bağlama ile ilişkili uç noktanın ayarlayarak olduğundan emin olun `bindingConfiguration` özniteliği.  
  
2.  Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemci yapılandırmasına değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarına eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.  
  
## <a name="comments"></a>Açıklamalar  
 Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkindir. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenemedi. Varsayılan olarak kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Kimlik doğrulaması ve imzalama özellik MSMQ için bir etki alanının parçası olması gerekir. Bu örnek bir etki alanının parçası olmayan bir bilgisayarda çalıştırmanız gerekiyorsa aşağıdaki hata iletisini: "kullanıcının iç message queuing sertifikası yok".  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a>Ayrıca Bkz.
