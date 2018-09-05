---
title: İşlem Yapılan Toplu İşlem
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: abada9aaf5fac8f05599467f385e708e1898832f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558514"
---
# <a name="transacted-batching"></a>İşlem Yapılan Toplu İşlem
Bu örnek, hizmetteki okuma Message Queuing (MSMQ) kullanarak toplu olarak gösterilmiştir. İşlenen toplu işleme kuyruğa alınan iletişim hizmetteki okumalar performans iyileştirme özelliği içindir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar. Daha kesin bir istemci bir kuyruğa iletiler gönderir. Hizmet iletileri kuyruktan alır. Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.  
  
 Bu örnek, toplu işleme gösterir. İşlenen toplu işleme, kuyruk ve bunları işlemeye çok iletileri okunurken tek bir işlem kullanımı sağlayan bir davranıştır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletin **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.  
  
    > [!NOTE]
    >  Bu örnekte istemci iletileri yüzlerce toplu bir parçası olarak gönderir. Bu işlem biraz zaman ayırın hizmet uygulaması için normal bir durumdur.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örnek, bir çalışma grubuna veya active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin. MSMQ taşıma güvenlik için iki ilgili özellik <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ active directory tümleştirme seçeneği yüklenmelidir. Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.  
  
2.  Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
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
  
    </system.serviceModel>  
    ```  
  
3.  Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security``mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.  
  
4.  Veritabanı uzak bir bilgisayarda çalıştırmak için bağlantı dizesi, veritabanının bulunduğu bilgisayara işaret edecek şekilde değiştirin.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örneği çalıştırmak için MSMQ yüklü olması ve SQL veya SQL Express gereklidir.  
  
## <a name="demonstrates"></a>Gösteriler  
 İşlenen toplu işleme davranışını örnek gösterir. İşlenen toplu işleme aktarım MSMQ ile sağlanan bir performans iyileştirme özelliği kuyruğa olur.  
  
 Gerçekten işlemler vardır ileti göndermek ve almak için kullanıldığında 2 hareketlerin ayırın. İstemci bir işlem kapsamı iletileri gönderdiğinde istemcinin ve istemci Kuyruk yöneticisi yerel bir işlemdir. Hizmet işlem kapsamı içindeki iletileri aldığında, hizmet ve alıcı Kuyruk yöneticisi yerel bir işlemdir. İstemciyi ve hizmeti aynı işlemde katılan değil olduğunu unutmamak çok önemlidir; Bunun yerine farklı işlemler işlemlerini (örneğin göndermek ve almak gibi) ile birlikte kuyruğa gerçekleştirirken kullandıkları.  
  
 Aşağıdaki örnekte birden çok hizmet işlemleri yürütülmesi için tek bir işlem kullanırız. Bu, yalnızca Performans İyileştirme özelliği kullanılır ve uygulama semantiği etkilemez. Örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Açıklamalar  
 Bu örnekte, istemci bir işlem kapsamında hizmetten toplu iletiler gönderir. Performans iyileştirmesi göstermek için çok sayıda ileti göndereceğiz; Bu durumda, 2500 iletileri kadar.  
  
 Kuyruğa gönderilen iletiler, ardından hizmeti tarafından tanımlanan işlem kapsamında hizmeti tarafından alınır. Toplu işleme olmadan, bu hizmet işlemi her çalıştırılışı için 2500 işlemlerde sonuçlanır. Bu, sistemin performansını etkiler. İki kaynak yöneticileri ilgili - olduğu için MSMQ sırası ve `Orders` veritabanı-her tür işlem DTC işlem olduğu. Biz tek bir işlemde toplu iletiler ve hizmet işlemi çağrılarını gerçekleşen çok daha az sayıda sağlayarak işlemleri kullanarak iyileştirin.  
  
 Toplu işlem özelliğiyle kullanırız:  
  
-   İşlenen toplu işleme davranışını yapılandırmasında belirtme.  
  
-   Bir toplu iş boyutu tek bir işlem kullanılarak okumak için ileti sayısı bakımından belirtme.  
  
-   Eş zamanlı toplu çalıştırmak için en fazla sayısını belirleme.  
  
 Bu örnekte, performans kazancı elde edildi işlem sayısı 100 hizmet işlemleri tek bir işlemde bir işlem gerçekleştirmeden önce çağrılır sağlayarak azaltarak göstereceğiz.  
  
 Hizmet davranışı ile bir işlem davranışını tanımlar `TransactionScopeRequired` kümesine `true`. Bu, kuyruktan ileti almak için kullanılan aynı işlem kapsamı yöntemi tarafından erişilen tüm kaynak yöneticileri tarafından kullanılmasını sağlar. Bu örnekte, iletideki satın alma siparişi bilgileri depolamak için bir temel veritabanı kullanın. İşlem kapsamı yöntemi bir özel durum oluşturursa, kuyruğa ileti döndürülür garanti eder. Bu işlemi davranışı ayar olmadan sıraya alınan bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve böylece işlem başarısız olursa, ileti kaybolur dağıtılmasından önce otomatik olarak tamamlar. Aşağıdaki kodda gösterildiği gibi bir kuyruktan ileti okumak için kullanılan işlem listeleme hizmet işlemleri için en yaygın senaryodur bakın.  
  
 Unutmayın `ReleaseServiceInstanceOnTransactionComplete` ayarlanır `false`. Bu, toplu işleme için önemli bir gereksinimdir. Özellik `ReleaseServiceInstanceOnTransactionComplete` üzerinde `ServiceBehaviorAttribute` hizmet örneği ile işlem tamamlandıktan sonra yapmanız gerekenler gösterir. Varsayılan olarak, hizmet örneği, işlem tamamlandıktan sonra serbest bırakılır. Toplu işleme için çekirdek gönderme sırasındaki ileti sayısını ve okuma için tek bir işlem kullanımı yönüdür. Bu nedenle hizmet örneği serbest çok kullanımını toplu beklenenden önce negating işlem Tamamlanıyor yukarı sona erer. Bu özellik ayarlanırsa `true` ve toplu işlem doğrulama davranışını bir özel durum oluşturursa işlenen toplu işleme davranışını uç noktasına eklenir.  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```

 `Orders` Sınıfı sırayla işlenmesini kapsüller. Bu örnekte veritabanı ile satın alma siparişi bilgileri güncelleştirir.  

```csharp
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```

 Toplu işleme davranışını ve yapılandırmasını, hizmet uygulama yapılandırmasında belirtilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Toplu iş boyutu, sistem bir ipucu verir. Örneğin, 20 bir toplu iş boyutu belirtirseniz, ardından 20 ileti okunacağı ve tek bir işlem kullanılarak gönderilen ve işlem taahhüt eder. Ancak, toplu iş boyutu ulaşılmadan önce burada batch hareketi durumlar vardır.  
>   
>  Her bir işlemle ilişkili hareket oluşturulduktan sonra yolunda başlatan bir zaman aşımı olur. Bu zaman aşımı süresi dolduğunda işlem iptal edildi. Toplu iş boyutu bile ulaşılmadan önce süresi dolacak şekilde bu zaman aşımı için mümkündür. Toplu işlem nedeniyle durdurma, yeniden çalışma önlemek için `TransactedBatchingBehavior` işlem üzerinde ne kadar süre kaldığını olup olmadığını kontrol eder. İşlem zaman aşımı değerini %80 kullanılması durumunda işlem taahhüt eder.  
>   
>  Daha fazla ileti kuyruğu sonra toplu iş boyutu yerine getirilmesi için beklemek yerine varsa <xref:System.ServiceModel.Description.TransactedBatchingBehavior> hareketi tamamlar.  
>   
>  Toplu iş boyutu seçimi, uygulamaya bağlıdır. Toplu iş boyutu çok küçükse, istediğiniz performans alamayabilir. Diğer taraftan toplu iş boyutu çok büyük ise, performans düşebilir. Örneğin, işlem artık canlı ve veritabanınızda kilitler barındırmıyorsa veya işlem kullanılmayan, geri ve iş Yinele olanak batch neden olabilecek kilitlenen.  
  
 İstemci işlem kapsamı oluşturur. Kuyruk ile iletişimi, burada tüm iletileri kuyruğa gönderilir ya da hiçbiri iletilerin kuyruğa gönderilen bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir. İşlem çağırarak kararlıdır <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamı üzerinde.  

```csharp
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
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
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın. Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın. İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletilerini alır. İletilerin bir toplu işte okuyun ve işlenen olarak sıralı bir çıkış görebilirsiniz.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Ayrıca Bkz.
