---
title: "MSMQ Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4c3d1dc8116e9c1b26febc4d8473b15d8648c01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="msmq-activation"></a>MSMQ Etkinleştirme
Bu örnek, bir iletiyi kuyruktan okunur uygulamaların Windows İşlem Etkinleştirme Hizmeti (WAS) barındırmak gösterilmiştir. Bu örnekte `netMsmqBinding` ve dayanır [iki yönlü iletişim](../../../../docs/framework/wcf/samples/two-way-communication.md) örnek. Bu durumda Web barındırdığı bir uygulama hizmetidir ve istemci kendiliğinden barındırılır ve gönderilen satınalma siparişi durumunu izlemek için konsola çıkarır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
> [!NOTE]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  \<InstallDrive >: \WF_WCF_Samples  
>   
>  Bu dizin mevcut değilse, Git [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank" ve [!INCLUDE[wf](../../../../includes/wf-md.md)] için örnekleri [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] tüm indirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  \<InstallDrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows İşlem Etkinleştirme Hizmeti (WAS), yeni bir işlem etkinleştirme mekanizmasıdır için [!INCLUDE[lserver](../../../../includes/lserver-md.md)], daha önce yalnızca HTTP tabanlı uygulamalara HTTP olmayan protokolleri kullanan uygulamalar için kullanılabilen IIS benzeri özellikleri sağlar. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Dinleyici Bağdaştırıcısı arabirimi tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletişim kurmak için kullandığı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]TCP, Adlandırılmış Kanallar ve MSMQ gibi. HTTP olmayan protokolleri isteklerini almak için işlevselliği SMSvcHost.exe içinde çalışan yönetilen Windows Hizmetleri tarafından barındırılır.  
  
 Sıradaki iletileri göre sıraya alınan uygulamaları Net.Msmq Dinleyici Bağdaştırıcısı hizmeti (NetMsmqActivator) etkinleştirir.  
  
 İstemci bir işlem kapsamı içinde hizmetinden satınalma siparişi gönderir. Hizmet bir işlem içinde siparişleri alır ve bunları işler. Hizmeti daha sonra geri sırasını durumunu istemcisiyle çağırır. Çift yönlü iletişimi kolaylaştırmak için istemci ve hizmet enqueue satınalma siparişi ve sipariş durumu sıralara kullanın.  
  
 Hizmet sözleşmesi `IOrderProcessor` queuing ile birlikte çalışan tek yönlü hizmet işlemleri tanımlar. Hizmet işlemini yanıt uç nokta sırasını durumları istemciye göndermek için kullanır. Yanıt uç noktanın, sipariş durumu istemciye göndermek için kullanılan sıra URI'sini adresidir. Uygulama işlem sırası bu sözleşmenin uygular.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 İstemci tarafından belirtildiği için sipariş durumu gönderilecek yanıt sözleşmesi. İstemci, sipariş durumu sözleşme uygular. Hizmet, bu sözleşmenin oluşturulan istemci sipariş durumu istemciye göndermek için kullanır.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Hizmet işlemini gönderilen satın alma siparişi işler. <xref:System.ServiceModel.OperationBehaviorAttribute> Otomatik kaydı kuyruk ve hizmet işleminin tamamlanması hareket otomatik tamamlama ileti almak için kullanılan işlem belirtmek üzere hizmet işlemi uygulanır. `Orders` Sınıfı, sipariş işleme işlevselliği yalıtır. Bu durumda, satın alma siparişi bir sözlüğe ekler. Hizmet işlemi içinde kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.  
  
 Sipariş durumu hakkında istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.  
  
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
```  
  
 Kullanılacak bağlama istemci, bir yapılandırma dosyası kullanarak belirtilir.  
  
 MSMQ kuyruk adı bir yapılandırma dosyasının appSettings bölümünde belirtilmiştir. Hizmeti için uç noktaya yapılandırma dosyası System.serviceModel bölümünde tanımlanır.  
  
> [!NOTE]
>  MSMQ sırası ad ve uç nokta adresi biraz farklı adresleme yöntemini kullanın. MSMQ kuyruk adı, ters eğik çizgi ayırıcıları yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Uç noktası adresi bir net.msmq belirtir: şeması, "localhost" yerel bilgisayarda ve eğik, yolunu kullanır. Uzak bilgisayarda bulunan bir sıradan okumak için Değiştir "." ve "localhost" uzak bilgisayar adı.  
  
 Sınıfın adını .svc dosyasıyla WAS hizmeti kodunda barındırmak için kullanılır.  
  
 Service.svc dosyası oluşturmak için bir yönergeyi içeren `OrderProcessorService`.  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Service.svc dosya System.Transactions.dll yüklendiğinden emin olmak için bir derleme yönergesi de içerir.  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 İstemci bir işlem kapsamı oluşturur. Hizmet ile iletişim, burada tüm iletileri başarılı veya başarısız atomik bir birim olarak değerlendirilmesi için neden işlem kapsamı içinde gerçekleşir. İşlem çağırarak gerçekleştirilir `Complete` işlem kapsamında.  
  
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
  
 İstemci kodu uygulayan `IOrderStatus` hizmetinden sipariş durumunu almak sözleşme. Bu durumda, sipariş durumu yazdırır.  
  
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
  
 Durum sırasını oluşturulan `Main` yöntemi. İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi sipariş durumu hizmeti barındırmak için sipariş durum hizmet yapılandırmasını içerir.  
  
```csharp  
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
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem sunucu hem de istemci konsol penceresi görüntülenir. İstemciden iletilerini sunucu görebilirsiniz. Her konsol penceresinde sunucu ve istemci kapatmak için ENTER tuşuna basın.  
  
 İstemci sunucu tarafından gönderilen sipariş durum bilgileri görüntüler:  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gerekli olduğundan, yüklenir.  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Ayrıca, yüklemelisiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP olmayan etkinleştirme bileşenleri:  
  
    1.  Gelen **Başlat** menüsünde seçin **Denetim Masası**.  
  
    2.  Seçin **programlar ve Özellikler**.  
  
    3.  Tıklatın **Windows özelliklerini aç veya Kapat**.  
  
    4.  Altında **Özellik Özeti**, tıklatın **Özellik Ekle**.  
  
    5.  Genişletme **Microsoft .NET Framework 3.0** düğümü ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  İstemci, bir komut penceresinde client.exe yürüterek çalıştırın. Bu sıranın oluşturur ve bir ileti gönderir. İleti okuma hizmet sonuçlarını görmek için çalıştıran istemci bırakın  
  
5.  MSMQ Etkinleştirme hizmeti varsayılan olarak ağ hizmeti olarak çalışır. Bu nedenle, uygulamayı etkinleştirmek için kullanılan sıra olmalıdır almak ve ara ağ hizmeti için izinler. Bu, Message Queuing MMC kullanarak eklenebilir:  
  
    1.  Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın `Compmgmt.msc` ve ENTER tuşuna basın.  
  
    2.  Altında **hizmetler ve uygulamalar**, genişletin **Message Queuing**.  
  
    3.  Tıklatın **özel sıralar**.  
  
    4.  Sıranın (servicemodelsamples/Service.svc) sağ tıklatın ve seçin **özellikleri**.  
  
    5.  Üzerinde **güvenlik** sekmesini tıklatın, **Ekle** gözlem verin ve alma izinleri ağ hizmeti için.  
  
6.  MSMQ etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.  
  
     Kolaylık sağlamak üzere aşağıdaki adımları örnek dizininde bulunan AddMsmqSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.  
  
    1.  NET.MSMQ etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.msmq protokole bağlı olmalıdır. Bu yapılabilir ile yüklenen appcmd.exe kullanarak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yönetim araç takımı. (Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Bu komut, metnin tek bir satırdır.  
  
         Bu komut net.msmq site bağlaması varsayılan Web sitesine ekler.  
  
    2.  Bir sitedeki tüm uygulamaları ortak net.msmq bağlama paylaşmak rağmen her uygulama net.msmq desteğini ayrı ayrı etkinleştirebilirsiniz. NET.MSMQ /servicemodelsamples uygulama için etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Bu komut, metnin tek bir satırdır.  
  
         Bu komut /servicemodelsamples uygulama tarafından http://localhost/servicemodelsamples ve net.msmq://localhost/servicemodelsamples kullanarak erişilmesini sağlar.  
  
7.  Daha önce yapmadıysanız, MSMQ Etkinleştirme hizmeti etkin olduğundan emin olun. Gelen **Başlat** menüsünde tıklatın **çalıştırmak**ve türü `Services.msc`. İçin Hizmetler listesi arama **Net.Msmq dinleyici bağdaştırıcısı**. Sağ tıklatıp **özellikleri**. Ayarlama **başlangıç türü** için **otomatik**, tıklatın **Uygula** tıklatıp **Başlat** düğmesi. Bu adım yalnızca bir kez Net.Msmq Dinleyici Bağdaştırıcısı hizmeti ilk kullanımını önce yapılmalıdır.  
  
8.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md). Ayrıca, satın alma siparişi gönderirken sıranın URI'sini bilgisayar adını yansıtacak şekilde satın alma siparişi gönderen istemci kodu değiştirin. Aşağıdaki kodu kullanın:  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Eklediğiniz net.msmq site bağlaması Bu örnek için kaldırın.  
  
     Kolaylık sağlamak üzere aşağıdaki adımları örnek dizininde bulunan RemoveMsmqSiteBinding.cmd adlı bir toplu iş dosyasında uygulanır:  
  
    1.  NET.MSMQ yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Bu komut, metnin tek bir satırdır.  
  
    2.  Net.msmq site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Bu komut, metnin tek bir satırdır.  
  
    > [!WARNING]
    >  Toplu iş dosyasını çalıştırarak .NET Framework sürüm 2.0 kullanarak çalışacak şekilde DefaultAppPool sıfırlanır.  
  
 Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkindir. İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenemedi. Varsayılan olarak kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`. Kimlik doğrulaması ve imzalama özellik MSMQ için bir etki alanının parçası olması gerekir. Bu örnek, bir etki alanının parçası olmayan bir bilgisayarda çalıştırmak, şu hata alındı: "kullanıcının iç message queuing sertifikası yok".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örnek bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için  
  
1.  Bilgisayarınız bir etki alanının parçası değilse, taşıma güvenliği None aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyi ayarlanarak açın.  
  
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
    >  Ayarı `security mode` için `None` ayarına eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.  
  
3.  Bir çalışma alanına katılmış bir bilgisayar etkinleştirme etkinleştirmek için etkinleştirme hizmeti ve çalışan işlemi (her ikisi için aynı olması gerekir) belirli bir kullanıcı hesabı ile çalıştırılmalıdır ve sıra ACL'ler belirli bir kullanıcı hesabı için olmalıdır.  
  
     Çalışan işlemin altında çalıştığı kimliğini değiştirmek için:  
  
    1.  İnetmgr.exe'yi çalıştırın.  
  
    2.  Altında **uygulama havuzları**, sağ **AppPool** (genellikle **DefaultAppPool**) ve **uygulama havuzu Varsayılanlarını Ayarla...** .  
  
    3.  Belirli bir kullanıcı hesabı kullanmak için kimlik özelliklerini değiştirin.  
  
     Etkinleştirme altında çalışacağı kimliği değiştirmek için:  
  
    1.  Services.msc dosyasını çalıştırın.  
  
    2.  Sağ **Net.MsmqListener bağdaştırıcısı**ve seçin **özellikleri**.  
  
4.  Hesabında değişiklik **oturum açma** sekmesi.  
  
5.  Bir çalışma grubunda, sınırsız belirteci kullanarak hizmet bir da çalıştırmanız gerekir. Bunu yapmak için bir komut penceresinde aşağıdaki komutu çalıştırın:  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
