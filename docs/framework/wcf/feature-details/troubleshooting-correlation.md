---
title: Bağıntı Sorunlarını Giderme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2de3a8cac6e12d898173f8181b295c3e2e461cc7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="troubleshooting-correlation"></a>Bağıntı Sorunlarını Giderme
Bağıntı iş akışı hizmeti iletileri birbirine ve doğru iş akışı örneği ilişkilendirmek için kullanılır, ancak doğru yapılandırılmamışsa, ileti alınmadı ve uygulamaların düzgün çalışmaz. Bu konuda bağıntı sorunlarını gidermek için çeşitli yöntemler genel bir bakış sağlar ve ayrıca bağıntı kullandığınızda oluşabilecek bazı ortak sorunlar listelenmiştir.  
  
## <a name="handle-the-unknownmessagereceived-event"></a>UnknownMessageReceived olayını işle  
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Olayı var olan bir örneğini bağıntılı iletileri dahil olmak üzere bir hizmet tarafından bilinmeyen bir ileti alındığında oluşur. Kendini barındıran hizmetler için bu olay konak uygulamada işlenebilir.  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 Web barındırılan hizmetler için bu olay bir sınıftan türetilen tarafından işlenip <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> ve geçersiz kılma <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.  
  
```csharp  
class CustomFactory : WorkflowServiceHostFactory  
{  
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)  
    {  
        // Create the WorkflowServiceHost.  
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);  
  
        // Handle the UnknownMessageReceived event.  
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
        {  
            Console.WriteLine("Unknown Message Received:");  
            Console.WriteLine(e.Message);  
        };  
  
        return host;  
    }  
}  
```  
  
 Bu özel <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> sonra belirtilebilir `svc` hizmet için dosya.  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 Bu işleyici çağrıldığında, ileti kullanılarak alınabilir <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> özelliği <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>ve aşağıdaki iletiyi benzeyecektir.  
  
```Output  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
  </s:Header>  
  <s:Body>  
    <AddItem xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItem>  
  </s:Body>  
</s:Envelope>  
```  
  
 Gönderilen iletileri incelemek için <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> işleyici neden ileti bir iş akışı hizmeti örneğine ilişkilendirmek değil hakkında ipuçları sağlayabilir.  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>İş akışı ilerlemesini izlemek için izleme kullanma  
 İzleme, bir iş akışı ilerlemesini izlemek için bir yol sağlar. Varsayılan olarak, iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, arıza yayma ve yer işareti sürdürme izleme kayıtları gösterilen. Ayrıca, özel izleme kayıtları özel etkinlikler tarafından gösterilen. Bağıntı sorunlarını giderirken, etkinlik kayıtları, yer işareti sürdürme kaydeder ve hataya yayma kayıtları izlemeyi en kullanışlı olan. Kayıtları İzleme etkinlik iş akışının geçerli ilerlemesini belirlemek için kullanılabilir ve hangi Mesajlaşma etkinlik iletileri için şu anda bekleyen tanımlamaya yardımcı olabilir. Yer işareti sürdürme kayıtları, iş akışı tarafından bir ileti alındı ve hataya yayma kayıtları, iş akışındaki tüm hataları kaydını sağlar belirttiğinden faydalıdır. İzlemeyi etkinleştirmek için istenen belirtin <xref:System.Activities.Tracking.TrackingParticipant> içinde <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> , <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Aşağıdaki örnekte, `ConsoleTrackingParticipant` (gelen [özel izleme](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) örnek) varsayılan profili izleme kullanılarak yapılandırılır.  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 İzleme katılımcı ConsoleTrackingParticipant gibi bir konsol penceresi sahip kendini barındıran iş akışı hizmetleri için yararlıdır. Web barındırılan bir hizmet için izleme bilgilerini dayanıklı bir depolama alanına oturum izleme katılımcı, yerleşik gibi kullanılmalıdır <xref:System.Activities.Tracking.EtwTrackingParticipant>, veya bilgileri gibi bir dosyaya kaydeder özel izleme katılımcı `TextWriterTrackingParticpant` gelen[ Bir metin dosyası kullanarak izleme](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) örnek.  
  
 İzleme ve bir iş akışı Web barındırılan hizmet için izleme yapılandırma hakkında daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [yapılandırma izleme iş akışı için](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)ve [ İzleme &#91;WF örnekleri&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) örnekleri.  
  
## <a name="use-wcf-tracing"></a>WCF izleme kullanın  
 WCF izleme ve bir iş akışı hizmetinden ileti akışı izlemeyi sağlar. Bu izleme bilgilerini bağıntı sorunlarını, özellikle içerik tabanlı bağıntı sorunlarını giderirken yararlıdır. İzlemeyi etkinleştirmek için istenen izleme dinleyicilerini belirtin `system.diagnostics` bölümünü `web.config` Web barındırılan iş akışı hizmeti ise, dosya veya `app.config` iş akışı hizmeti kendini barındıran ise dosya. İzleme dosyasında iletilerinin içeriğini dahil edileceğini belirtin `true` için `logEntireMessage` içinde `messageLogging` öğesinde `diagnostics` bölümünü `system.serviceModel`. Aşağıdaki örnekte, mesajlarının içeriğini izleme bilgilerini adlı bir dosyaya yazılması için yapılandırılmış `service.svclog`.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
    </sources>  
  
    <sharedListeners>  
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging logEntireMessage="true" logMalformedMessages="false"  
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">  
      </messageLogging>  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Bulunan izleme bilgilerini görüntülemek için `service.svclog`, [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanılır. İleti içeriğini görüntülemek ve tam olarak ne geçirilen ve eşleşen olup olmadığını görmek için içerik tabanlı bağıntı sorunlarını giderme gönderdiğinde, bu özellikle yararlı olur <xref:System.ServiceModel.CorrelationQuery> içerik tabanlı bağıntı için. WCF izleme hakkında daha fazla bilgi için bkz: [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), ve [sorun giderme uygulamanızkullanarakizlemeyi](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="common-context-exchange-correlation-issues"></a>Ortak bağlam Exchange bağıntı sorunları  
 Belirli türde bir bağıntı düzgün çalışması için belirli bir bağlama türü için bağıntı kullanılır gerektirir. Örnekler arasında iki yönlü bağlama gibi gerektirir istek-yanıt bağıntısı <xref:System.ServiceModel.BasicHttpBinding>ve bir bağlam tabanlı gibi bağlama gerektirir bağlam değişimi bağıntısı <xref:System.ServiceModel.BasicHttpContextBinding>. Bu istek-yanıt bağıntısı için yaygın bir sorun değildir ancak dahil olmak üzere içerik tabanlı bağlamalar sayıda vardır çoğu bağlamalar iki yönlü işlemlerini destekleyen <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, ve <xref:System.ServiceModel.NetTcpContextBinding>. Bu bağlamaların bir tanesini kullanılmaz bir iş akışı hizmeti ilk çağrı başarılı olur, ancak sonraki çağrılar başarısız olur şununla <xref:System.ServiceModel.FaultException>.  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 Bağlam bağıntı için kullanılan bağlam bilgilerini tarafından döndürülen <xref:System.ServiceModel.Activities.SendReply> için <xref:System.ServiceModel.Activities.Receive> iki yönlü bir işlem veya kullanma işlemi ise, çağıran tarafından belirtilebilir yükleyen bağlam bağıntı başlatır etkinliği tek yönlü. Bağlam çağıran tarafından gönderilen değil veya iş akışı hizmeti sonra aynı tarafından döndürülen <xref:System.ServiceModel.FaultException> açıklanan daha önce bir sonraki işlemi çalıştırıldığında döndürülür.  
  
 Daha fazla bilgi için bkz: [bağlam değişimi](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
## <a name="common-request-reply-correlation-issues"></a>İstek-yanıt bağıntısı ile ilgili genel sorunları  
 İstek-yanıt bağıntısı ile kullanılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti ile bir iş akışı hizmeti de iki yönlü bir işlem uygulamak için bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iki yönlü bir işlem başka bir Web çağırır çifti hizmet. Bir WCF hizmetindeki iki yönlü bir işlem çağrılırken, hizmet ya da bir geleneksel kesinliği kod tabanlı olabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti veya bir iş akışı hizmeti olabilir. İstek-yanıt bağıntısı iki yönlü bir bağlama kullanılmalıdır, gibi kullanmak için <xref:System.ServiceModel.BasicHttpBinding>, ve işlemler iki yönlü olması gerekir.  
  
 İş akışı hizmeti paralel veya örtüşen iki yönlü işlemlerinde varsa <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çiftleri sonra örtük bağıntı işlemek tarafındansağlananYönetim<xref:System.ServiceModel.Activities.WorkflowServiceHost>özellikle yüksek stres senaryolarda yeterli olmayabilir ve iletileri doğru biçimde yönlendirilemeyebilir. Bu sorunun oluşmasını önlemek için her zaman açıkça belirttiğiniz öneririz bir <xref:System.ServiceModel.Activities.CorrelationHandle> istek-yanıt bağıntısı kullanırken. Kullanırken **SendAndReceiveReply** ve **ReceiveAndSendReply** ileti bölümünden şablonları **araç** iş akışı Tasarımcısı'nda bir <xref:System.ServiceModel.Activities.CorrelationHandle> açıkça varsayılan olarak yapılandırılır. Bir iş akışı kodu kullanarak oluştururken <xref:System.ServiceModel.Activities.CorrelationHandle> belirtilen <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> çiftindeki ilk etkinliğin. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.Receive> etkinliği açık bir yapılandırılmış <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> belirtilen <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = ... // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 Kalıcılık arasında izin verilmez bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti. No-persist bölge hem etkinlikleri tamamlanana kadar sürer oluşturulur. Bir gecikme etkinliği gibi bir etkinlik bu no-persist bölgesinde bulunan ve boşta durumuna iş akışı neden olursa, konak olduklarında iş akışları kalıcı olacak şekilde yapılandırılmış boş olsa bile iş akışı kalıcı olmaz. Kalan etkinliği gibi bir etkinlik açıkça Hayır kalan bölgesinde kalıcı hale getirmek çalışırsa, bir önemli özel durum, iş akışı durdurulduğunda oluşur ve bir <xref:System.ServiceModel.FaultException> çağırana döndürülür. Önemli özel durum iletisi "System.InvalidOperationException: kalıcı etkinlikleri hiçbir Kalıcılık bloğu içinde bulunan yapılamıyor.". Bu özel durumun çağırana döndürülmez ancak izleme etkin olup olmadığını gösterilebilir. İleti için <xref:System.ServiceModel.FaultException> yapana "işlemi gerçekleştirilemedi iş akışı örneği '5836145b-7da2 - 49 d 0-a052-a49162adeab6' tamamlandığından" değil.  
  
 İstek-yanıt bağıntısı hakkında daha fazla bilgi için bkz: [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).  
  
## <a name="common-content-correlation-issues"></a>İçerik bağıntı ile ilgili genel sorunları  
 İçeriğe dayalı bağıntı birden fazla ileti bir iş akışı hizmeti alır ve bir veri alışverişi iletilerindeki parçasını istenen örneğini tanımlar olduğunda kullanılır. İçeriğe dayalı bağıntı iletide, müşteri numarası veya sipariş kimliği iletileri yönlendirmek için doğru iş akışı örneği gibi bu verileri kullanır. Bu bölümde içerik tabanlı bağıntı kullanırken oluşabilecek çeşitli ortak sorunlar açıklanmaktadır.  
  
### <a name="ensure-the-identifying-data-is-unique"></a>Benzersiz tanımlayıcı veri sağlayın  
 Örneği tanımlamak için kullanılan veri bir bağıntı anahtara karma haline getirilir. Bağıntı için kullanılan veri benzersizdir Aksi takdirde karma anahtarında çakışması ortaya ve iletileri misrouted neden güvence altına almak için dikkatli olunması gerekir. Örneğin, aynı ada sahip birden çok müşteri olabileceğinden yalnızca müşteri adına göre bir bağıntı bir çakışma neden olabilir. İki nokta (:) ileti sorgunun anahtar ve değer daha sonra karma dizesi oluşturmak için sınırlandırmak için zaten kullanılmakta olduğundan ileti ilişkilendirmek için kullanılan veri bir parçası olarak kullanılmamalıdır. Kalıcılık kullanılıyorsa, geçerli tanımlayıcı verileri önceden Sürdürülen bir örneği tarafından kullanılmamış emin olun. Geçici olarak Kalıcılık devre dışı bırakma, bu sorunu tanımlamaya yardımcı olabilir. WCF izleme hesaplanan bağıntı anahtarını görüntülemek için kullanılabilir ve bu tür bir sorunu hata ayıklama için faydalıdır.  
  
### <a name="race-conditions"></a>Yarış durumları  
 Bir ileti ve gerçekte başlatılmakta bağıntı alma hizmeti arasındaki süre izleme iletileri yoksayılacak küçük boşluk yoktur. Tek yönlü bir işlem istemciden geçirilen verileri kullanarak bir iş akışı hizmeti içerik tabanlı bağıntı başlatır ve arayan hemen izleme iletileri gönderir, bu zaman aralığı boyunca bu iletiler yoksayılacak. Bu bağıntı başlatmak için iki yönlü bir işlemi kullanarak veya kullanılarak önlenebilir bir <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
### <a name="correlation-query-issues"></a>Bağıntı sorgu sorunları  
 Bağıntı sorgular, hangi verilerin iletide ileti ilişkilendirmek için kullanıldığını belirtmek için kullanılır. Bu veriler, bir XPath sorgusu kullanılarak belirtilir. Her şeyin doğru görünüyor olsa bile bir hizmete ileti gönderilir değil, bir XPath sorgusu yerine ileti veri değeri ile eşleşen bir hazır değer belirtmek için sorun giderme için bir strateji olur. Değişmez değer belirtmek için kullanın `string` işlevi. Aşağıdaki örnekte, bir <xref:System.ServiceModel.MessageQuerySet> değişmez değeri kullanmak üzere yapılandırılmış `11445` için `OrderId` ve XPath sorgusu dışı bırakılmıştır.  
  
```csharp  
MessageQuerySet = new MessageQuerySet  
{  
    {  
        "OrderId",   
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")  
        new XPathMessageQuery("string('11445')")  
    }  
}  
```  
  
 Bir XPath sorgusu bağıntı veri alınır, hatalı yapılandırıldıysa şu iletisiyle bir hata döndürdü: "bağıntı sorgu boş bir sonuç kümesi veriyor. Lütfen bağıntı sorguları uç noktası için doğru şekilde yapılandırıldığından emin olun." Bu sorunu gidermek için hızlı bir şekilde değişmez değerle açıklandığı önceki bölümdeki XPath sorgusu değiştirmektir. XPath Sorgu Oluşturucu'da kullanıyorsanız, bu sorun ortaya çıkabilir **eklemek bağıntı başlatıcıları** veya **CorrelatesOn tanımı** iletişim kutuları ve iş akışı hizmeti ileti sözleşmeleri kullanır. Aşağıdaki örnekte, bir ileti sözleşme sınıfı tanımlanır.  
  
```csharp  
[MessageContract]  
public class AddItemMessage  
{  
    [MessageHeader]  
    public string CartId;  
  
    [MessageBodyMember]  
    public string Item;  
}  
```  
  
 Bu ileti sözleşmesi tarafından kullanılan bir <xref:System.ServiceModel.Activities.Receive> bir iş akışı etkinlik. `CartId` İleti üstbilgisinde doğru örneği iletiye ilişkilendirmek için kullanılır. XPath sorgusu, alır, `CartId` sorgu oluşturulur aşağıdaki hatalı XPath iş akışı Tasarımcısı'nda bağıntı iletişim kutuları kullanılarak oluşturulur.  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 Bu XPath sorgusu doğru olması durumunda <xref:System.ServiceModel.Activities.Receive> etkinlik kullanılan parametreleri için veri, ancak ileti sözleşmesi kullanıldığından geçersiz. Aşağıdaki XPath sorgusu almak için doğru XPath sorgusu değil `CartId` başlığından.  
  
```  
sm:header()/tempuri:CartId  
```  
  
 Bu, ileti gövdesi inceleyerek onaylanabilir.  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>  
  </s:Header>  
  <s:Body>  
    <AddItemMessage xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItemMessage>  
  </s:Body>  
</s:Envelope>  
```  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.ServiceModel.Activities.Receive> etkinlik için yapılandırılmış bir `AddItem` önceki ileti sözleşmesi veri almak için kullandığı işlemi. XPath sorgusu doğru yapılandırılmamış.  
  
```xaml  
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">  
  <Receive.CorrelatesOn>  
    <XPathMessageQuery x:Key="key1">  
      <XPathMessageQuery.Namespaces>  
        <ssx:XPathMessageContextMarkup>  
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>  
        </ssx:XPathMessageContextMarkup>  
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>  
  </Receive.CorrelatesOn>  
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">  
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>  
  </ReceiveMessageContent>  
</Receive>  
```  
  
 İçeriğe dayalı bağıntı hakkında daha fazla bilgi için bkz: [içerik tabanlı](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) ve [bağıntılı hesaplayıcı](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) örnek.
