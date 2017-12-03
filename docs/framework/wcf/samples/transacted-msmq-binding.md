---
title: "İşlem Gerçekleştirilmiş MSMQ Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: "50"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd656bed608811a5a04a47849bf915f708a62a9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-msmq-binding"></a>İşlem Gerçekleştirilmiş MSMQ Bağlama
Bu örnek, Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirmek gösterilmiştir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar. Daha hassas bir şekilde istemci kuyruğa ileti gönderir. Hizmet kuyruktan iletileri alır. Hizmet ve istemci, bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 İleti gönderme ve alma için işlemleri kullanıldığında aslında iki ayrı işlemler vardır. İstemci bir işlem kapsamı içinde iletileri gönderdiğinde, istemci ve istemci sıra yöneticisi yerel bir işlemdir. Hizmet işlem kapsamı içinde ileti aldığında, hizmet ve alıcı sıra yöneticisi yerel bir işlemdir. İstemci ve hizmet aynı işlemde yer almayan olduğunu unutmamak önemlidir; Bunun yerine, farklı işlemler işlemlerini (örneğin gönderme ve alma gibi) sıra ile gerçekleştirirken kullanıyordur.  
  
 Bu örnekte, istemci bir işlem kapsamı içinde hizmetinden toplu iletiler gönderir. Bu sıraya gönderilen iletileri sonra hizmet hizmet tarafından tanımlanan işlem kapsamı içinde tarafından alınır.  
  
 Hizmet sözleşme `IOrderProcessor`, aşağıdaki örnek kodda gösterildiği gibi. Sıralar ile kullanım için uygun bir tek yönlü hizmet arabirimi tanımlar.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 Bir işlemi davranışı ile hizmet davranışını tanımlayan `TransactionScopeRequired` kümesine `true`. Bu yöntem tarafından erişilen tüm kaynak yöneticileri kuyruktan ileti almak için kullanılan aynı işlem kapsamı kullandığı sağlar. Ayrıca, yöntemi bir özel durum oluşturursa ileti kuyruğuna döndürülür garanti eder. Bu işlemi davranışı ayarı olmadan sıraya alınmış bir kanal iletiyi sıradan okumak için bir işlem oluşturur ve işlem başarısız olursa, ileti kaybolur şekilde, otomatik olarak gönderme önce kaydeder. Aşağıdaki kodda gösterildiği gibi sıradan ileti okumak için kullanılır işlemdeki listeleme hizmet işlemleri için en yaygın senaryodur bakın.  
  
```  
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
  
 Kendi kendini barındırılan hizmetidir. MSMQ taşıma kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmet sırası varlığını denetlemek ve henüz yoksa sırayı oluşturmak için kod içerir. Kuyruk adı yapılandırma dosyasından okunur. Temel adres tarafından kullanılan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.  
  
```  
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
>  Kuyruk adı bir nokta (.) yolundaki ters eğik çizgi ayırıcılar ve yerel bilgisayar için sıra kullanarak oluştururken kullandığı <xref:System.Messaging>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Uç nokta sıra adresini kullanır yerel bilgisayarı belirtmek için "localhost" net.msmq şeması ile kullanır ve kullandığı yolundaki eğik.  
  
 İstemci bir işlem kapsamı oluşturur. Sıra ile iletişim, bu sıraya gönderilen tüm iletileri veya hiçbiri iletileri kuyruğa gönderilen olduğu atomik bir birim olarak kabul edilmesi neden işlem kapsamı içinde gerçekleşir. İşlem çağırarak gerçekleştirilir <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamında.  
  
```  
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
  
 İşlemler çalıştığını doğrulamak için aşağıdaki örnek kodda gösterildiği gibi işlem kapsamı yorum istemci değiştirmek, çözümü yeniden derleyin ve istemci çalıştırın.  
  
```  
//scope.Complete();  
```  
  
 İşlem tamamlanmamış olduğundan, iletileri kuyruğa gönderilmez.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir. İstemci hizmeti alma iletileri görebilirsiniz. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın. Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması sahip olmadığını unutmayın. İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala iletilerini alır.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, taşıma güvenliği etkindir. MSMQ taşıma güvenliği için iki ilgili özellikler yok <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Bir etki alanının parçası olması gerekir ve kimlik doğrulaması ve imzalama özelliği, MSMQ için MSMQ Active Directory tümleştirme seçeneğini yüklü olması gerekir. Bu ölçütleri karşılayan olmayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örnek bir çalışma grubu ya da Active Directory Tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değil veya yüklü Active Directory Tümleştirmesi yok gerekirse kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakmak `None` aşağıdaki örnek yapılandırma kodda gösterildiği gibi.  
  
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
  
2.  Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasına değiştirdiğinizden emin olun.  
  
    > [!NOTE]
    >  Ayarı `security``mode` için `None` ayarına eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>Ayrıca Bkz.
