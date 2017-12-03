---
title: "İşlem Yapılan Toplu İşlem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc04f0ce1d303a32cbf2232c76bfc4ef1143c9ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-batching"></a>İşlem Yapılan Toplu İşlem
Bu örnek, işlenen okuma Message Queuing (MSMQ) kullanarak toplu olarak gösterilmiştir. İşlenen Batching kuyruğa alınan iletişim hizmetteki okuma performansı en iyi duruma getirme özelliğini içindir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar. Daha hassas bir şekilde istemci kuyruğa ileti gönderir. Hizmet kuyruktan iletileri alır. Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Bu örnek, işlenen toplu işleme gösterir. İşlenen toplu işleme sırası ve işlemeden birçok iletileri okunurken tek bir işlem kullanılmasına olanak veren bir davranıştır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
    > [!NOTE]
    >  Bu örnekte istemci iletileri yüzlerce toplu bir parçası olarak gönderir. Bu işlem biraz zaman hizmet uygulaması için normal bir durumdur.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örnek bir çalışma grubu ya da active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, taşıma güvenliği etkindir. MSMQ taşıma güvenliği için iki ilgili özellikler yok <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Bir etki alanının parçası olması gerekir ve kimlik doğrulaması ve imzalama özelliği, MSMQ için MSMQ active directory tümleştirme seçeneğini yüklü olması gerekir. Bu ölçütleri karşılayan olmayan bir bilgisayarda bu örnek çalıştırırsanız, bir hata alırsınız.  
  
2.  Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok gerekirse kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakmak `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:  
  
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
  
3.  Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasına değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security``mode` için `None` ayarına eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.  
  
4.  Veritabanı uzak bir bilgisayarda çalıştırmak için veritabanının bulunduğu bilgisayara işaret eden bağlantı dizesini değiştirin.  
  
## <a name="requirements"></a>Gereksinimler  
 Bu örneği çalıştırmak için MSMQ yüklenmelidir ve SQL veya SQL Express gereklidir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örnek uygulaması yapılan toplu davranış gösterir. Uygulaması yapılan toplu işleme MSMQ ile sağlanan bir performans en iyi duruma getirme özelliği aktarım sıraya olur.  
  
 Gerçekte hareketler vardır ileti gönderme ve alma için kullanıldığında 2 işlemleri ayırın. İstemci bir işlem kapsamı içinde iletileri gönderdiğinde, istemci ve istemci sıra yöneticisi yerel bir işlemdir. Hizmet işlem kapsamı içinde ileti aldığında, hizmet ve alıcı sıra yöneticisi yerel bir işlemdir. İstemci ve hizmet aynı işlemde yer almayan olduğunu unutmamak önemlidir; Bunun yerine farklı işlemler işlemlerini (örneğin gönderme ve alma gibi) sıra ile gerçekleştirirken kullanıyordur.  
  
 Aşağıdaki örnekte birden çok hizmet işlemleri yürütme için tek bir işlem kullanırız. Bu yalnızca bir performans en iyi duruma getirme özelliği kullanılır ve uygulama semantiği etkilemez. Örnek dayanır [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Açıklamalar  
 Bu örnekte, istemci bir işlem kapsamı içinde hizmetinden toplu iletiler gönderir. Performansı en iyi duruma getirme göstermek için size bir sayıda ileti göndereceğiz; Bu durumda, 2500 iletileri kadar.  
  
 Bu sıraya gönderilen iletileri sonra hizmet hizmet tarafından tanımlanan işlem kapsamı içinde tarafından alınır. Toplu işlem olmadan, bu hizmet işlemi her çalıştırılışı için 2500 hareketleri sonuçlanır. Bu, sistemin performansını etkiler. İki kaynak yöneticileri söz konusu - olduğu için MSMQ sırası ve `Orders` veritabanı-her tür işlemdir DTC işlem. Biz iletileri ve hizmet işlem çağrıları toplu gerçekleşen tek bir işlemde çok daha az sayıda sağlayarak işlemleri kullanarak iyileştirin.  
  
 Toplu özellik tarafından kullanırız:  
  
-   Uygulaması yapılan toplu davranışını yapılandırmasında belirtme.  
  
-   Bir toplu iş boyutu tek bir işlem kullanılarak okumak için ileti sayısı bakımından belirtme.  
  
-   Çalıştırmak için eş zamanlı yığın sayısı üst sınırını belirtme.  
  
 Bu örnekte, performans artışı 100 hizmet işlemleri işlem gerçekleştirmeden önce tek bir işlemde çağrılan sağlayarak işlemleri sayısını azaltarak gösteriyoruz.  
  
 Bir işlemi davranışı ile hizmet davranışını tanımlayan `TransactionScopeRequired` kümesine `true`. Bu yöntem tarafından erişilen tüm kaynak yöneticileri kuyruktan ileti almak için kullanılan aynı işlem kapsamı kullandığı sağlar. Bu örnekte, iletideki satın alma siparişi bilgileri depolamak için bir temel veritabanı kullanın. İşlem kapsamı yöntemi bir özel durum oluşturursa ileti kuyruğuna döndürülür garanti eder. Bu işlemi davranışı ayarı olmadan sıraya alınmış bir kanal iletiyi sıradan okumak için bir işlem oluşturur ve böylece işlemi başarısız olursa, ileti kaybolur dağıtılmasından önce otomatik olarak kaydeder. Aşağıdaki kodda gösterildiği gibi kuyruktan ileti okumak için kullanılan işlem listeleme hizmet işlemleri için en yaygın senaryodur bakın.  
  
 Unutmayın `ReleaseServiceInstanceOnTransactionComplete` ayarlanır `false`. Bu, toplu işleme için önemli bir gereksinimdir. Özellik `ReleaseServiceInstanceOnTransactionComplete` üzerinde `ServiceBehaviorAttribute` hizmet örneği işlem tamamlandıktan sonra yapmanız gerekenler gösterir. Varsayılan olarak, hizmet örneği işlem tamamlandıktan sonra yayımlanır. Toplu işleme için çekirdek en boy okumak ve sıradaki birçok ileti gönderme için tek bir işlem kullanılır. Bu nedenle hizmet örneği serbest erken toplu işleme çok kullanımına negating işlem tamamlanmadan yukarı sona erer. Bu özellik ayarlanmışsa `true` ve işlenen toplu işleme davranışını eklenen uç noktasına toplu doğrulama davranışını bir özel durum oluşturur.  
  
```  
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
  
 `Orders` Sınıfı, sipariş işleme yalıtır. Aşağıdaki örnekte veritabanını satın alma siparişi bilgilerle güncelleştirir.  
  
```  
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
  
 Toplu işleme davranışı ve yapılandırmasını hizmet uygulama yapılandırmasında belirtilir.  
  
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
>  Toplu iş boyutu sistem bir ipucu olur. Örneğin, bir toplu iş boyutu 20 belirtirseniz, ardından 20 ileti okuma ve tek bir işlem kullanılarak gönderilen ve işlem taahhüt eder. Ancak toplu iş boyutu ulaşılmadan önce burada Toplu hareketi durumlar vardır.  
>   
>  Her işlemle ilişkili hareket oluşturulduktan sonra ticking başlayan zaman aşımı olur. Bu zaman aşımı süresi dolduğunda işlem iptal edilir. Toplu iş boyutu bile ulaşılmadan önce süresi dolacak şekilde bu zaman aşımı için mümkündür. Toplu işlem nedeniyle durdurma, yeniden çalışma önlemek için `TransactedBatchingBehavior` ne kadar süre işlem sol olup olmadığını kontrol eder. İşlem zaman aşımı % 80 kullanılırsa, işlem taahhüt eder.  
>   
>  Daha fazla ileti sırasındaki sonra toplu iş boyutu yerine getirme için beklemek yerine varsa <xref:System.ServiceModel.Description.TransactedBatchingBehavior> hareketi tamamlar.  
>   
>  Toplu iş boyutu, uygulamanızda bağımlı seçimdir. Yığın boyutu çok küçükse, istenen performans alamayabilirsiniz. Öte yandan yığın boyutu çok büyük ise, performans düşebilir. Örneğin, işleminiz artık canlı ve veritabanınızda kilitleri tutun veya işleminiz kullanılmayan, geri ve iş Yinele için toplu neden olabilecek kilitlenen.  
  
 İstemci bir işlem kapsamı oluşturur. Sıra ile iletişim, bu sıraya gönderilen tüm iletileri veya hiçbiri iletileri kuyruğa gönderilen olduğu atomik bir birim olarak kabul edilmesi neden işlem kapsamı içinde gerçekleşir. İşlem çağırarak gerçekleştirilir <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamında.  
  
```  
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
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir. İstemci hizmeti alma iletileri görebilirsiniz. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın. Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması sahip olmadığını unutmayın. İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala kendi iletilerini alır. İletileri bir toplu işlemde okuma ve işlenen olarak çalışırken çıkış görebilirsiniz.  
  
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
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Ayrıca Bkz.
