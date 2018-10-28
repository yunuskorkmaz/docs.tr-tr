---
title: MSMQ Etkinleştirme
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 20287af1c1d93bbdcfa83d88e5790284fbbff170
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194130"
---
# <a name="msmq-activation"></a>MSMQ Etkinleştirme
Bu örnek, bir ileti kuyruktan okunmak uygulamaların Windows İşlem Etkinleştirme Hizmeti (WAS) barındırmak nasıl gösterir. Bu örnekte `netMsmqBinding` ve dayanır [iki yönlü iletişimi](../../../../docs/framework/wcf/samples/two-way-communication.md) örnek. Bu durumda Web barındırılan bir uygulama hizmetidir ve istemci kendiliğinden barındırılır ve gönderilen satın alma siparişleri durumunu izlemek için konsola çıkışı.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
> [!NOTE]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  \<Installdrive >: \WF_WCF_Samples  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm WCF indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  \<Installdrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows İşlem Etkinleştirme Hizmeti (WAS), yeni işlem etkinleştirme mekanizması [!INCLUDE[lserver](../../../../includes/lserver-md.md)], daha önce yalnızca HTTP tabanlı uygulamalara HTTP olmayan protokolleri kullanan uygulamalar için kullanılabilen IIS gibi özellikler sağlar. Windows Communication Foundation (WCF), MSMQ TCP ve adlandırılmış kanallar gibi bir WCF tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcı arabirimini kullanır. HTTP olmayan protokolleri üzerinden isteklerini almak için işlevselliği, SMSvcHost.exe içinde çalışan yönetilen Windows Hizmetleri tarafından barındırılır.  
  
 (NetMsmqActivator) Net.Msmq dinleyici bağdaştırıcı hizmeti, iletileri sıraya göre kuyruğa alınmış uygulamaları etkinleştirir.  
  
 İstemci hizmetinden bir işlem kapsamında satın alma siparişleri gönderir. Hizmet, bir işlemde siparişleri alır ve işler. Hizmet daha sonra siparişin durumunu istemcisiyle geri çağırır. İki yönlü iletişimi kolaylaştırmak için kuyruğa satın alma siparişleri ve sipariş durumu sıralara istemciyi ve hizmeti kullanın.  
  
 Hizmet sözleşmesi `IOrderProcessor` queuing ile birlikte çalışan tek yönlü hizmet işlemleri tanımlar. Hizmet işlemi yanıt uç nokta sırasını durumları istemciye göndermek için kullanır. Yanıt uç noktasının, sipariş durumunun istemciye geri göndermek için kullanılan kuyruk URI'sini adresidir. Uygulama işleme sırası, bu sözleşme uygular.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Sipariş durumu için belirtilen istemci tarafından gönderilecek yanıt anlaşması. Sipariş durumu sözleşme istemciye uygular. Hizmet, bu sözleşmenin oluşturulan istemci siparişinizin durumu istemciye geri göndermek için kullanır.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Hizmet işlemi gönderilen satın alma siparişi işler. <xref:System.ServiceModel.OperationBehaviorAttribute> Otomatik kayıt hizmeti işleminin tamamlanması hareket otomatik tamamlama ve kuyruk iletiyi almak için kullanılan işlem belirtmek için hizmet işlemi uygulanır. `Orders` Sınıfı sipariş işleme işlevselliğini kapsüller. Bu durumda, satın alma siparişi bir sözlüğe ekler. Hizmet işlemi kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.  
  
 Siparişin durumunu istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }
}
```  
  
 Kullanılacak bağlama istemci, bir yapılandırma dosyası kullanarak belirtilir.  
  
 MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir. Hizmet için uç nokta yapılandırma dosyasının System.serviceModel bölümünde tanımlanır.  
  
> [!NOTE]
>  MSMQ kuyruk adı ve uç nokta adresi adresleme biraz farklı kuralları kullanın. MSMQ kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. Bir net.msmq WCF uç nokta adresini belirtir: düzeni, "localhost" yerel bilgisayarı ve eğik kendi yolunda kullanır. Uzak bilgisayarda barındırılan bir kuyruktan okunur değiştirin "." ve "localhost" uzak bilgisayar adı.  
  
 Bir sınıfın adını .svc dosyasıyla WAS hizmeti kodunda barındırmak için kullanılır.  
  
 Service.svc dosyası oluşturmak için bir yönergeyi içeren `OrderProcessorService`.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Service.svc dosya System.Transactions.dll yüklendiğinden emin olmak için bir derleme yönergesi de içerir.  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 İstemci işlem kapsamı oluşturur. Hizmeti ile iletişimi, burada tüm iletileri başarılı veya başarısız bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir. İşlem çağırarak kararlıdır `Complete` işlem kapsamı üzerinde.  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
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
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 İstemci kodu uygulayan `IOrderStatus` siparişinizin durumu hizmetinden almak üzere sözleşme. Bu durumda, siparişinizin durumu yazdırır.  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 Durum sırasını oluşturulan `Main` yöntemi. Aşağıdaki örnek yapılandırmada gösterildiği gibi istemci yapılandırması sipariş durumu hizmeti barındırmak için sipariş durumu hizmeti yapılandırması içerir.  
  
```xml  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem sunucu hem de istemci konsol penceresi görüntülenir. Sunucunun istemciden iletilerini görebilirsiniz. Her konsol penceresi sunucu ve istemci kapatmak için ENTER tuşuna basın.  
  
 İstemci, sunucu tarafından gönderilen sipariş durumu bilgilerini görüntüler:  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gerekli olduğu gibi yüklenir.  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:  
  
    1.  Gelen **Başlat** menüsünde seçin **Denetim Masası**.  
  
    2.  Seçin **programlar ve Özellikler**.  
  
    3.  Tıklayın **Windows özelliklerini aç veya Kapat**.  
  
    4.  Altında **özellikler özeti**, tıklayın **Özellik Ekle**.  
  
    5.  Genişletin **Microsoft .NET Framework 3.0** düğüm ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  İstemci, bir komut penceresinden client.exe yürüterek çalıştırın. Bu, bir sıra oluşturur ve ona bir ileti gönderir. İleti okuma hizmet sonucunu görmek için çalıştıran istemci bırakın  
  
5.  MSMQ Etkinleştirme hizmeti varsayılan olarak ağ hizmeti olarak çalışır. Bu nedenle, uygulamayı etkinleştirmek için kullanılan kuyruk olmalıdır alır ve ağ hizmeti için izinleri göz at. Bu, Message Queuing MMC kullanarak eklenebilir:  
  
    1.  Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın `Compmgmt.msc` ve ENTER tuşuna basın.  
  
    2.  Altında **hizmetler ve uygulamalar**, genişletme **Message Queuing**.  
  
    3.  Tıklayın **özel sıralar**.  
  
    4.  ' % S'sıra (servicemodelsamples/Service.svc) sağ tıklatın ve seçin **özellikleri**.  
  
    5.  Üzerinde **güvenlik** sekmesinde **Ekle** gözlem verin ve alma izinleri ağ hizmeti için.  
  
6.  MSMQ etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.  
  
     Kolaylık, örnek dizininde AddMsmqSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki adımlar uygulanır.  
  
    1.  NET.MSMQ etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.msmq protokole bağlı olmalıdır. Bu yapılabilir ile birlikte yüklenen appcmd.exe kullanarak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Yönetimi araç. (Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Tek metin satırı komutudur.  
  
         Bu komut, varsayılan Web sitesine net.msmq site bağlaması ekler.  
  
    2.  Bir sitedeki tüm uygulamaları genel net.msmq bağlama paylaşsa da her uygulama net.msmq destek ayrı ayrı etkinleştirebilirsiniz. /Servicemodelsamples uygulamanın NET.MSMQ etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Tek metin satırı komutudur.  
  
         Bu komut kullanılarak erişilecektir /servicemodelsamples uygulamayı etkinleştirir `http://localhost/servicemodelsamples` ve `net.msmq://localhost/servicemodelsamples`.
  
7.  Daha önce yapmadıysanız, MSMQ Etkinleştirme Hizmeti'nın etkin olduğundan emin olun. Gelen **Başlat** menüsünde tıklatın **çalıştırın**ve türü `Services.msc`. Arama için Hizmetler listesi **Net.Msmq dinleyici bağdaştırıcısı**. Sağ tıklayıp **özellikleri**. Ayarlama **başlangıç türü** için **otomatik**, tıklayın **Uygula** tıklatıp **Başlat** düğmesi. Bu adım yalnızca bir kez Net.Msmq dinleyici bağdaştırıcı hizmeti ilk kullanımlar yapılmalıdır.  
  
8.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md). Ayrıca, satın alma siparişi gönderirken URİ'sini sıra bilgisayar adını yansıtacak şekilde satınalma siparişi gönderen istemci kodu değiştirin. Aşağıdaki kodu kullanın:  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Eklediğiniz net.msmq site bağlaması için bu örnek kaldırın.  
  
     Kolaylık, örnek dizininde RemoveMsmqSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki adımlar uygulanır:  
  
    1.  NET.MSMQ yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tek metin satırı komutudur.  
  
    2.  Net.msmq site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Tek metin satırı komutudur.  
  
    > [!WARNING]
    >  Toplu iş dosyasını çalıştırarak .NET Framework sürüm 2.0 kullanarak çalışacak şekilde DefaultAppPool sıfırlar.  
  
 Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkin. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte aktarım güvenliği türünü belirleyin. Varsayılan kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Kimlik doğrulama ve imzalama özelliği sağlamak MSMQ için bir etki alanının parçası olması gerekir. Bu örnek, bir etki alanının parçası olmayan bir bilgisayar üzerinde çalıştırırsanız, aşağıdaki hata alınır: "kullanıcının iç message queuing sertifika mevcut değil".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği için bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değilse, hiçbiri aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyi ayarlayarak aktarım güvenliği devre dışı bırakın.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasını değiştirin.  
  
    > [!NOTE]
    >  Ayarı `security mode` için `None` ayarlamakla eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.  
  
3.  Bir çalışma alanına katılmış bir bilgisayar etkinleştirmesi için hem Etkinleştirme hizmeti hem de çalışan işlemi (her ikisi için aynı olmalıdır) belirli bir kullanıcı hesabı ile çalıştırılmalıdır ve kuyruk ACL'leri belirli bir kullanıcı hesabı için olmalıdır.  
  
     Altında çalışan işlemini çalıştıran kimliği değiştirmek için:  
  
    1.  Inetmgr.exe çalıştırın.  
  
    2.  Altında **uygulama havuzları**, sağ **AppPool** (genellikle **DefaultAppPool**) ve **uygulama havuzu Varsayılanlarını Ayarla...** .  
  
    3.  Belirli bir kullanıcı hesabını kullanmak üzere kimlik özelliklerini değiştirin.  
  
     Etkinleştirme altında çalışacağı kimliği değiştirmek için:  
  
    1.  Services.msc dosyasını çalıştırın.  
  
    2.  Sağ **Net.MsmqListener bağdaştırıcısı**ve **özellikleri**.  
  
4.  Hesabında değişiklik **oturum açma** sekmesi.  
  
5.  Bir çalışma grubunda hizmeti sınırsız bir belirteç kullanarak da çalıştırılmalıdır. Bunu yapmak için bir komut penceresinde aşağıdaki komutu çalıştırın:  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
