---
title: Oturumlar ve Kuyruklar
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144105"
---
# <a name="sessions-and-queues"></a>Oturumlar ve Kuyruklar
Bu örnek, İleti Queuing (MSMQ) aktarımı üzerinden sıraya alınan iletişimde ilgili iletilerin nasıl gönderilip alınılsüreceğini gösterir. Bu örnek `netMsmqBinding` bağlama kullanır. Hizmet, sıraya alınan iletileri alan hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar. Daha doğrusu, istemci sıraya ileti gönderir. Hizmet, kuyruktan iletiler alır. Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Bazen, istemci bir grupta birbiriyle ilişkili bir dizi ileti gönderir. İletilerin birlikte veya belirli bir sırada işlenmesi gerektiğinde, tek bir alıcı uygulama tarafından işlenmek üzere onları gruplandırmak için bir kuyruk kullanılabilir. Bu, özellikle bir sunucu grubunda birden fazla uygulama aldığında önemlidir ve bir ileti grubunun aynı alıcı uygulama tarafından işlendiğinden emin olmak gerekir. Sıralanan oturumlar, aynı anda işlenmesi gereken ilgili ileti kümesini göndermek ve almak için kullanılan bir mekanizmadır. Sıralanmış oturumlar, bu deseni sergilemek için bir hareket gerektirir.  
  
 Örnekte, istemci tek bir işlem kapsamında bir oturumun parçası olarak hizmete bir dizi ileti gönderir.  
  
 Hizmet sözleşmesi, `IOrderTaker`kuyruklarla kullanıma uygun tek yönlü bir hizmeti tanımlayan sözleşmedir. Aşağıdaki <xref:System.ServiceModel.SessionMode> örnek kodda gösterilen sözleşmede kullanılan iletilerin oturumun bir parçası olduğunu gösterir.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 Hizmet, hizmet işlemlerini, ilk işlemin bir harekette kaydedilen, ancak hareketi otomatik olarak tamamlamayan şekilde tanımlar. Sonraki işlemler de aynı işlem de kaydolmak, ancak otomatik olarak tamamlanmaz. Oturumdaki son işlem işlemi otomatik olarak tamamlar. Bu nedenle, aynı işlem hizmet sözleşmesinde çeşitli işlem çağrıları için kullanılır. İşlemlerden herhangi biri özel durum atarsa, işlem geri alınır ve oturum sıraya geri alınır. Son işlemin başarıyla tamamlanmasından sonra, işlem yapılır. Hizmet, `PerSession` bir <xref:System.ServiceModel.InstanceContextMode> oturumdaki tüm iletileri hizmetin aynı örneğinde almak için kullanır.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 Hizmet kendi kendine barındırılır. MSMQ aktarımını kullanırken, kullanılan sıra önceden oluşturulmalıdır. Bu el ile veya kod yoluyla yapılabilir. Bu örnekte, hizmet <xref:System.Messaging> sıranın varlığını denetlemek için kod içerir ve gerekirse bunu oluşturur. Sıra adı <xref:System.Configuration.ConfigurationManager.AppSettings%2A> sınıfı kullanarak yapılandırma dosyasından okunur.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();
    }  
}  
```

 MSMQ sıra adı yapılandırma dosyasının bir uygulama Ayarları bölümünde belirtilir. Hizmetin bitiş noktası yapılandırma dosyasının system.serviceModel bölümünde tanımlanır ve bağlamayı `netMsmqBinding` belirtir.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 İstemci bir hareket kapsamı oluşturur. Oturumdaki tüm iletiler işlem kapsamı içinde kuyruğa gönderilir ve tüm iletilerin başarılı veya başarısız olduğu bir atomik birim olarak ele alınmasına neden olur. Hareket arayarak <xref:System.Transactions.TransactionScope.Complete%2A>işlenir.  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> Oturumdaki tüm iletiler için yalnızca tek bir işlem kullanabilirsiniz ve işlem gerçekleştirmeden önce oturumdaki tüm iletilerin gönderilmesi gerekir. İstemciyi kapatmak oturumu kapatır. Bu nedenle, oturumdaki tüm iletileri sıraya göndermek için işlem tamamlanmadan önce istemcinin kapatılması gerekir.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsolu pencerelerinde görüntülenir. Hizmetin istemciden ileti aldığını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın. Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışır durumda olması gerekmediğini unutmayın. İstemciyi çalıştırabilir, kapatabilir ve sonra hizmeti başlatabilir ve yine de iletilerini alır.  
  
 Müşteriye.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 Serviste.  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
 Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkinleştirilir. MSMQ aktarım güvenliği için iki <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ilgili <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` özellik vardır, yani, ve `Windows` varsayılan olarak, kimlik `Sign`doğrulama modu ayarlanır ve koruma düzeyi . MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için bir etki alanının parçası olması ve MSMQ için etkin dizin tümleştirme seçeneğinin yüklenmesi gerekir. Bu örneği bu ölçütleri karşılamayan bir bilgisayarda çalıştırıyorsanız bir hata alırsınız.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Bir çalışma grubuna katılan veya etkin dizin tümleştirmesi olmayan bir bilgisayarda örnek çalıştırmak için  
  
1. Bilgisayarınız bir etki alanının parçası değilse veya etkin dizin tümleştirmesi yüklü değilse, kimlik doğrulama `None` modunu ve koruma düzeyini aşağıdaki örnek yapılandırmada gösterildiği gibi ayarlayarak aktarım güvenliğini kapatın.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. Örneği çalıştırmadan önce hem sunucuda hem de istemcide yapılandırmayı değiştirdiğinden emin olun.  
  
    > [!NOTE]
    > Güvenlik modunu `None` ayarla, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>ayara `Message` ve `None`güvenlik 'e eşittir.  
