---
title: Windows Communication Foundation'dan İleti Kuyruğuna
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2ea59c7f1ef2ac6f22500a13eb9bb4456149b7c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation'dan İleti Kuyruğuna
Bu örnek gösterilmektedir nasıl bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama bir Message Queuing (MSMQ) uygulamaya bir ileti gönderebilir. Hizmeti, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulamasıdır. Hizmet ve istemci aynı anda çalışıyor olması gerekmez.  
  
 Hizmet kuyruktan iletileri alır ve siparişleri işler. Hizmet işlem bir sıra oluşturur ve bir ileti alındı ileti işleyicisini, aşağıdaki örnek kodda gösterildiği gibi ayarlar.  

```csharp
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```

 Ne zaman bir ileti alındığında sırası, ileti işleyicisi `ProcessOrder` çağrılır.  

```csharp
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```

 Hizmet ayıklar `ProcessOrder` MSMQ İleti gövdesi ve sırasını işler.  
  
 MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Kuyruk adı, ters eğik çizgi ayırıcıları yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.  
  
 İstemci bir satın alma siparişi oluşturur ve aşağıdaki örnek kodda gösterildiği gibi bir işlem kapsamı içinde satın alma siparişi gönderir.  

```csharp
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```

 İstemci bir özel istemci sıralı MSMQ ileti kuyruğuna göndermek için kullanır. Alan ve iletiyi işleyen bir uygulama bir MSMQ uygulaması olduğundan ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, iki uygulama hiçbir örtük hizmet sözleşmesini yoktur. Bu nedenle, bu senaryoda Svcutil.exe aracını kullanarak bir proxy oluşturamıyoruz.  
  
 Özel istemci temelde tüm aynıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan uygulamalar `MsmqIntegration` iletileri göndermek için bağlama. Diğer istemcilerden farklı olarak, bir dizi hizmet işlemleri içermeyecek. Bir Gönder ileti yalnızca işlemdir.  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir. İstemci hizmeti alma iletileri görebilirsiniz. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın. Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması sahip olmadığını unutmayın. Örneğin, istemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala kendi ileti alacaksınız.  
  
> [!NOTE]
>  Bu örnek, Message Queuing yüklemesini gerektirir. ' Ndaki yükleme yönergelerine bakın [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968).  
  
### <a name="to-setup-build-and-run-the-sample"></a>Kurulum, yapı ve örneği çalıştırmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder. Hizmet sırası mevcut değilse oluşturur. İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.  
  
    1.  Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Genişletme **özellikleri** sekmesi.  
  
    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.  
  
    4.  Denetleme **işlem** kutusu.  
  
    5.  Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek bilgisayarlı yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet program dosyalarını dile özgü klasörü altındaki \service\bin\ klasöründen hizmet bilgisayara kopyalayın.  
  
2.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
3.  Hizmet bilgisayar adı yerine belirtmek için istemci uç noktası adresi Client.exe.config dosyasında değiştirmek ".".  
  
4.  Hizmet bilgisayarda bir komut isteminden Service.exe başlatın.  
  
5.  İstemci bilgisayarda bir komut isteminden Client.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968)
