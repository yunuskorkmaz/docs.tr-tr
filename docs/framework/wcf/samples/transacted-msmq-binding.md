---
title: İşlem Gerçekleştirilmiş MSMQ Bağlama
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: ebf93ba5b7497d30ff7efceea3bd7ca827d5b502
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423896"
---
# <a name="transacted-msmq-binding"></a>İşlem Gerçekleştirilmiş MSMQ Bağlama

Bu örnek, Message Queuing (MSMQ) kullanılarak işlenen sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. Daha kesin olarak, istemci iletileri bir kuyruğa gönderir. Hizmet kuyruktaki iletileri alır. Bu nedenle, hizmet ve istemcinin bir kuyruk kullanarak iletişim kurmak için aynı anda çalışması gerekmez.

İletileri göndermek ve almak için işlemler kullanıldığında, aslında iki ayrı işlem vardır. İstemci bir işlemin kapsamı içinde ileti gönderdiğinde, işlem istemciye ve istemci kuyruğu yöneticisine yereldir. Hizmet, işlem kapsamındaki iletileri aldığında işlem, hizmete ve alma kuyruğu Yöneticisi 'ne yereldir. İstemcinin ve hizmetin aynı işleme katılmadığından emin olmak çok önemlidir; Bunun yerine, kuyrukla birlikte işlemlerini gerçekleştirirken farklı işlemler (örneğin, gönder ve Al) kullanıyor.

Bu örnekte, istemci, bir işlemin kapsamı içinde hizmete bir toplu işlem iletisi gönderir. Kuyruğa gönderilen iletiler daha sonra hizmet tarafından tanımlanan işlem kapsamı içinde hizmet tarafından alınır.

Hizmet sözleşmesi aşağıdaki örnek kodda gösterildiği gibi `IOrderProcessor`. Arabirim, kuyruklarla kullanım için uygun olan tek yönlü bir hizmeti tanımlar.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

Hizmet davranışı, `true`olarak ayarlanan `TransactionScopeRequired` bir işlem davranışını tanımlar. Bu, sıradan iletiyi almak için kullanılan aynı işlem kapsamının, yöntemi tarafından erişilen herhangi bir kaynak yöneticisi tarafından kullanılmasını sağlar. Ayrıca Yöntem bir özel durum oluşturursa, iletinin kuyruğa döndürüldüğünden de garanti edilir. Bu işlem davranışını ayarlamadan, kuyruğa alınmış bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve işlem başarısız olursa ileti kaybedildiğinden göndermeden önce otomatik olarak işleme konur. En yaygın senaryo, aşağıdaki kodda gösterildiği gibi sıradan iletiyi okumak için kullanılan işlemde listeleme için hizmet işlemlerine yöneliktir.

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

Hizmet kendi kendine barındırılır. MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte hizmet, sıranın varlığını denetlemek ve yoksa kuyruğu oluşturmak için kod içerir. Sıra adı yapılandırma dosyasından okundu. Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete proxy oluşturmak için kullanılır.

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

MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> Sıra adı, <xref:System.Messaging>kullanarak kuyruğu oluştururken Yerel bilgisayar ve ters eğik çizgi ayırıcılar için bir nokta (.) kullanır. Windows Communication Foundation (WCF) uç noktası, net. MSMQ şeması ile kuyruk adresini kullanır, yerel bilgisayarı belirtmek için "localhost" kullanır ve yolunda eğik çizgi kullanır.

İstemci bir işlem kapsamı oluşturur. Kuyrukla iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin sıraya gönderildiği veya hiçbir iletinin sıraya gönderilmediği atomik bir birim olarak işlenmesine neden olur. İşlem, işlem kapsamındaki <xref:System.Transactions.TransactionScope.Complete%2A> çağırarak işlenir.

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

İşlemlerin çalıştığını doğrulamak için, aşağıdaki örnek kodda gösterildiği gibi işlem kapsamını inceleyerek istemciyi değiştirin, çözümü yeniden derleyin ve istemciyi çalıştırın.

```csharp
//scope.Complete();
```

İşlem tamamlanmadığı için iletiler kuyruğa gönderilmez.

Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın. Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun. İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve iletileri almaya devam edebilirsiniz.

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir. Sıra yoksa, hizmet bir tane oluşturur. Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz. Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012 ' de Sunucu Yöneticisi açın.

    2. **Özellikler** sekmesini genişletin.

    3. **Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

<xref:System.ServiceModel.NetMsmqBinding>varsayılan olarak, taşıma güvenliği etkinleştirilmiştir. MSMQ aktarım güvenliği, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>için iki ilgili özellik vardır. Varsayılan olarak, kimlik doğrulama modu `Windows` olarak ayarlanır ve koruma düzeyi `Sign`olarak ayarlanır. MSMQ için kimlik doğrulama ve imzalama özelliğini sağlamak üzere, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir. Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Örneği bir çalışma grubuna katılmış veya Active Directory tümleştirme olmadan bir bilgisayarda çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse veya Active Directory tümleştirme yüklü değilse, aşağıdaki örnek yapılandırma kodunda gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini `None` olarak ayarlayarak aktarım güvenliğini kapatın.

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
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
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

2. Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.

    > [!NOTE]
    > `security mode` `None` ayarlanması, `Message` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>ve `None`güvenliğini ayarlamaya eşdeğerdir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
