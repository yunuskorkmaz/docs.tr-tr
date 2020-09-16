---
title: MSMQ Etkinleştirme
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 349eadb8f517993c343e81656204ad25e62ed931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555243"
---
# <a name="msmq-activation"></a>MSMQ Etkinleştirme

Bu örnek, Windows Işlem etkinleştirme hizmeti 'nde (WAS) bir ileti sırasından okunan uygulamaların nasıl barındırılacağını gösterir. Bu örnek, `netMsmqBinding` ve [Iki yönlü iletişim](two-way-communication.md) örneğine göre ' nı kullanır. Bu durumda hizmet, Web 'de barındırılan bir uygulamadır ve istemci, gönderilen satın alma siparişlerinin durumunu gözlemleyecek şekilde kendi kendine barındırılır ve konsola çıkış verir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!NOTE]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> \<InstallDrive>: \ WF_WCF_Samples
>
> Bu dizin yoksa, tüm WCF ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> \<InstallDrive>: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.

Windows Server 2008 için yeni işlem etkinleştirme mekanizması olan Windows Işlem etkinleştirme hizmeti (WAS), daha önce yalnızca HTTP tabanlı uygulamalar tarafından HTTP tabanlı olmayan protokolleri kullanan uygulamalara sunulan IIS benzeri özellikler sağlar. Windows Communication Foundation (WCF), TCP, adlandırılmış kanallar ve MSMQ gibi WCF tarafından desteklenen HTTP olmayan protokoller üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcısı arabirimini kullanır. HTTP olmayan protokoller üzerinden istek alma işlevselliği, SMSvcHost.exe çalıştıran yönetilen Windows Hizmetleri tarafından barındırılır.

Net. MSMQ dinleyicisi bağdaştırıcısı hizmeti (Netmsmqetkinleştirici) kuyruktaki iletileri temel alarak sıraya alınmış uygulamaları etkinleştirir.

İstemci, bir işlemin kapsamı içinde hizmete satın alma siparişleri gönderir. Hizmet, siparişleri bir işlem içinde alır ve işler. Bu hizmet daha sonra istemciyi siparişin durumuyla geri çağırır. İki yönlü iletişimi kolaylaştırmak için, istemci ve hizmetin her ikisi de, satın alma siparişlerinin ve sipariş durumunun kuyruğa alınması için kuyrukları kullanır.

Hizmet sözleşmesi, `IOrderProcessor` sıraya alma ile çalışan tek yönlü hizmet işlemlerini tanımlar. Hizmet işlemi, istemciye sıra durumları göndermek için yanıt uç noktasını kullanır. Yanıt uç noktasının adresi, sipariş durumunu istemciye geri göndermek için kullanılan kuyruğun URI 'sidir. Sipariş işleme uygulaması bu sözleşmeyi uygular.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

Sıra durumunun gönderileceği yanıt sözleşmesi istemci tarafından belirtilir. İstemci sipariş durumu sözleşmesini uygular. Hizmet, sipariş durumunu istemciye geri göndermek için bu sözleşmenin oluşturulan istemcisini kullanır.

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

Hizmet işlemi gönderilen satın alma siparişini işler. , <xref:System.ServiceModel.OperationBehaviorAttribute> Sıradaki iletiyi almak ve hizmet işleminin tamamlanmasından sonra işlemin otomatik olarak tamamlanması için kullanılan işlemde otomatik kayıt belirtmek üzere hizmet işlemine uygulanır. `Orders`Sınıfı sipariş işleme işlevselliğini Kapsüller. Bu durumda, satın alma sırasını bir sözlüğe ekler. İçindeki hizmet işleminin kayıtlı olduğu işlem, sınıftaki işlemler için kullanılabilir `Orders` .

Hizmet işlemi, gönderilen satın alma siparişinin işlenmesine ek olarak, siparişin durumu hakkında istemciye geri yanıt verir.

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

Kullanılacak istemci bağlaması bir yapılandırma dosyası kullanılarak belirtilir.

MSMQ kuyruğu adı, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir. Hizmetin uç noktası, yapılandırma dosyasının System. serviceModel bölümünde tanımlanır.

> [!NOTE]
> MSMQ kuyruğu adı ve uç nokta adresi biraz farklı adresleme kuralları kullanır. MSMQ sırası adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır. WCF uç nokta adresi bir net. MSMQ: Scheme belirtir, yerel bilgisayar için "localhost" kullanır ve yolunda eğik çizgi kullanır. Uzak bilgisayarda barındırılan bir kuyruktan okumak için, "." ve "localhost" değerini uzak bilgisayar adıyla değiştirin.

WAS ' de hizmet kodunu barındırmak için sınıf adına sahip bir. svc dosyası kullanılır.

Service. svc dosyasının kendisi oluşturmak için bir yönerge içerir `OrderProcessorService` .

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

Service. svc dosyası, System.Transactions.dll yüklendiğinden emin olmak için bir derleme yönergesi de içerir.

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

İstemci bir işlem kapsamı oluşturur. Hizmet ile iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin başarılı veya başarısız olduğu atomik bir birim olarak işlenmesine neden olur. İşlem, işlem kapsamında çağırarak yürütülür `Complete` .

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

İstemci kodu, `IOrderStatus` hizmetten sipariş durumunu almak için sözleşmeyi uygular. Bu durumda, sipariş durumunu yazdırır.

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

Sıra durumu kuyruğu `Main` yönteminde oluşturulur. İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş durumu hizmetini barındıracak sıra durumu hizmeti yapılandırmasını içerir.

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

Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem sunucu hem de istemci konsol pencereleri içinde görüntülenir. İstemciden sunucudan ileti alın ' a bakabilirsiniz. Sunucu ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.

İstemci, sunucu tarafından gönderilen sıra durumu bilgilerini görüntüler:

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. WAS etkinleştirmesi için gerekli olduğundan, IIS 7,0 ' nin yüklü olduğundan emin olun.

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun. Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:

    1. **Başlat** menüsünde, **Denetim Masası**' nı seçin.

    2. **Programlar ve Özellikler '** i seçin.

    3. **Windows özelliklerini aç veya kapat**' a tıklayın.

    4. **Özellikler Özeti**' nin altında **Özellik Ekle**' ye tıklayın.

    5. **Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

4. Bir komut penceresinden client.exe yürüterek istemciyi çalıştırın. Bu, kuyruğu oluşturur ve ona bir ileti gönderir. İletiyi okurken hizmetin sonucunu görmek için istemciyi çalışır durumda bırakın

5. MSMQ etkinleştirme hizmeti varsayılan olarak ağ hizmeti olarak çalışır. Bu nedenle, uygulamayı etkinleştirmek için kullanılan sıranın ağ hizmeti için alma ve göz atma izinlerine sahip olması gerekir. Bu, Message Queuing MMC kullanılarak eklenebilir:

    1. **Başlat** menüsünde **Çalıştır**' a tıklayın `Compmgmt.msc` ve yazın ve ENTER tuşuna basın.

    2. **Hizmetler ve uygulamalar**altında **Message Queuing**' ı genişletin.

    3. **Özel kuyruklar**' a tıklayın.

    4. Kuyruğa (servicemodelsamples/service. svc) sağ tıklayın ve **Özellikler**' i seçin.

    5. **Güvenlik** sekmesinde, **Ekle** ' ye tıklayın ve ağ hizmetine göz atma ve alma izinleri verin.

6. Windows Işlem etkinleştirme hizmeti 'ni (WAS) MSMQ etkinleştirmesini destekleyecek şekilde yapılandırın.

    Kolaylık olması halinde, örnek dizinde bulunan AddMsmqSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki adımlar uygulanır.

    1. Net. MSMQ etkinleştirmesini desteklemek için, önce varsayılan Web sitesi önce net. MSMQ protokolüne bağlanmalıdır. Bu, IIS 7,0 yönetim araç takımı ile yüklenen appcmd.exe kullanılarak yapılabilir. Yükseltilmiş (yönetici) komut isteminden aşağıdaki komutu çalıştırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

        Bu komut, varsayılan Web sitesine bir net. MSMQ site bağlaması ekler.

    2. Bir sitedeki tüm uygulamalar ortak bir net. MSMQ bağlamasını paylaşır, ancak her uygulama net. MSMQ desteğini tek tek etkinleştirebilir. /Servicemodelsamples uygulaması için net. MSMQ ' yı etkinleştirmek için, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

        Bu komut, ve kullanarak/servicemodelsamples uygulamasına erişilmesini sağlar `http://localhost/servicemodelsamples` `net.msmq://localhost/servicemodelsamples` .

7. Daha önce yapmadıysanız, MSMQ etkinleştirme hizmeti 'nin etkinleştirildiğinden emin olun. **Başlat** menüsünde **Çalıştır**' a tıklayın ve yazın `Services.msc` . **Net. MSMQ dinleyicisi bağdaştırıcısı**için Hizmetler listesinde arama yapın. Sağ tıklayın ve **Özellikler**' i seçin. **Başlangıç türünü** **Otomatik**olarak ayarlayın, **Uygula** ' ya tıklayın ve **Başlat** düğmesine tıklayın. Bu adım yalnızca, net. MSMQ dinleyicisi bağdaştırıcısı hizmetinin ilk kullanımından önce bir kez yapılmalıdır.

8. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin. Ayrıca, satın alma siparişi gönderen istemcideki kodu, satın alma siparişi gönderilirken kuyruğun URI 'sindeki bilgisayar adını yansıtacak şekilde değiştirin. Aşağıdaki kodu kullanın:

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. Bu örnek için eklemiş olduğunuz net. MSMQ site bağlamasını kaldırın.

    Kolaylık olması açısından, aşağıdaki adımlar örnek dizinde bulunan RemoveMsmqSiteBinding. cmd adlı bir toplu iş dosyasında uygulanır:

    1. Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. MSMQ ' yı kaldırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

    2. Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak net. MSMQ site bağlamasını kaldırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

    > [!WARNING]
    > Toplu iş dosyasını çalıştırmak, .NET Framework sürüm 2,0 kullanılarak çalıştırılacak DefaultAppPool öğesini sıfırlar.

Varsayılan olarak `netMsmqBinding` , bağlama aktarımında güvenlik etkindir. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel` , birlikte taşıma güvenliği türü belirlenir. Varsayılan olarak, kimlik doğrulama modu olarak ayarlanır `Windows` ve koruma düzeyi olarak ayarlanır `Sign` . Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ 'nun bir etki alanının parçası olması gerekir. Bu örneği bir etki alanının parçası olmayan bir bilgisayarda çalıştırırsanız, şu hata alınır: "kullanıcının iç Message Queuing sertifikası yok".

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırmak için

1. Bilgisayarınız bir etki alanının parçası değilse, aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini yok olarak ayarlayarak aktarım güvenliğini kapatın.

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.

    > [!NOTE]
    > Ayarı `security mode` `None` `MsmqAuthenticationMode` , ayarına `MsmqProtectionLevel` ve güvenliğine eşdeğerdir `Message` `None` .

3. Bir çalışma grubuna katılmış bir bilgisayarda etkinleştirmeyi etkinleştirmek için, hem etkinleştirme hizmeti hem de çalışan işleminin belirli bir kullanıcı hesabıyla çalıştırılması gerekir (her ikisi için de aynı olmalıdır) ve kuyruğun belirli kullanıcı hesabı için ACL 'Leri olmalıdır.

     Çalışan işleminin çalıştırıldığı kimliği değiştirmek için:

    1. Inetmgr.exe çalıştırın.

    2. **Uygulama havuzları**altında, **AppPool** öğesine sağ tıklayın (genellikle **DefaultAppPool**) ve **uygulama havuzu varsayılanlarını ayarla..**. seçeneğini belirleyin.

    3. Kimlik özelliklerini belirli kullanıcı hesabını kullanacak şekilde değiştirin.

     Etkinleştirme hizmetinin altında çalıştığı kimliği değiştirmek için:

    1. Services. msc dosyasını çalıştırın.

    2. **Net. MsmqListener bağdaştırıcısını**sağ tıklatın ve **Özellikler**' i seçin.

4. Hesabı **oturum açma** sekmesinden değiştirin.

5. Çalışma grubunda, hizmet kısıtlanmamış bir belirteç kullanarak da çalışmalıdır. Bunu yapmak için, komut penceresinde aşağıdakileri çalıştırın:

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))
