---
title: İşlem Gerçekleştirilmiş MSMQ Bağlama
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 381304bcef40245bac882a4fe4ae18a6998665cf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558188"
---
# <a name="transacted-msmq-binding"></a>İşlem Gerçekleştirilmiş MSMQ Bağlama
Bu örnek, Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirme gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar. Daha kesin bir istemci bir kuyruğa iletiler gönderir. Hizmet iletileri kuyruktan alır. Hizmet ve istemci, bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.  
  
 İşlem, ileti göndermek ve almak için kullanıldığında, aslında iki ayrı işlem vardır. İstemci bir işlem kapsamı iletileri gönderdiğinde istemcinin ve istemci Kuyruk yöneticisi yerel bir işlemdir. Hizmet işlem kapsamı içindeki iletileri aldığında, hizmet ve alıcı Kuyruk yöneticisi yerel bir işlemdir. İstemciyi ve hizmeti aynı işlemde katılan değil olduğunu unutmamak çok önemlidir; Bunun yerine, farklı işlem işlemlerini (örneğin göndermek ve almak gibi) ile birlikte kuyruğa gerçekleştirirken kullandıkları.  
  
 Bu örnekte, istemci bir işlem kapsamında hizmetten toplu iletiler gönderir. Kuyruğa gönderilen iletiler, ardından hizmeti tarafından tanımlanan işlem kapsamında hizmeti tarafından alınır.  
  
 Hizmet sözleşme `IOrderProcessor`aşağıdaki örnek kodda gösterildiği gibi. Kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti arabirimi tanımlar.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Hizmet davranışı ile bir işlem davranışını tanımlar `TransactionScopeRequired` kümesine `true`. Bu, kuyruktan ileti almak için kullanılan aynı işlem kapsamı yöntemi tarafından erişilen tüm kaynak yöneticileri tarafından kullanılmasını sağlar. Ayrıca, yöntem bir özel durum oluşturursa, kuyruğa ileti döndürülür garanti eder. Bu işlemi davranışı ayar olmadan sıraya alınan bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve işlem başarısız olursa, ileti kaybolur şekilde gönderme önce otomatik olarak işlemeleri. İletiyi sıradan okumak için aşağıdaki kodda gösterildiği gibi kullanılan işlem listeleme hizmet işlemleri için en yaygın senaryodur bakın.  

```csharp
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```

 Kendi kendine barındırılan bir hizmettir. MSMQ taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmet sıranın varlığını denetleyin ve henüz yoksa bir kuyruk oluşturmak için kod içerir. Kuyruk adı yapılandırma dosyasından okunur. Tarafından kullanılan taban adresini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
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
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```

 MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  Kuyruk adı bir nokta (.) yolundaki ters eğik çizgi ayırıcılar ve yerel bilgisayar için bir kuyruk kullanma oluştururken kullandığı <xref:System.Messaging>. Windows Communication Foundation (WCF) uç noktası net.msmq şeması ile kuyruk adresini kullanır, "localhost" yerel bilgisayarı belirtmek için kullanır ve kendi yolunda eğik kullanır.  
  
 İstemci işlem kapsamı oluşturur. Kuyruk ile iletişimi, burada tüm iletileri kuyruğa gönderilir ya da hiçbiri iletilerin kuyruğa gönderilen bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir. İşlem çağırarak kararlıdır <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamı üzerinde.  

```csharp
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
// Create the purchase order.  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 İşlem çalıştığını doğrulamak için aşağıdaki örnek kodda gösterildiği gibi işlem kapsamı açıklama satırı yaparak istemci değiştirmek, çözümü yeniden oluşturun ve istemcisini çalıştıran.  

```csharp
//scope.Complete();  
```

 İşlem tamamlanmış sayılmaz olduğundan, iletileri kuyruğa gönderilmez.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın. Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın. İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletileri alır.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletin **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin. MSMQ taşıma güvenlik için iki ilgili özellik <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ Active Directory Tümleştirme seçeneği yüklenmelidir. Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örnek, bir çalışma grubuna veya Active Directory Tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değil veya yüklü Active Directory Tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırma kodda gösterildiği gibi.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security``mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>Ayrıca Bkz.
