---
title: Bağıntı Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121898"
---
# <a name="troubleshooting-correlation"></a>Bağıntı Sorunlarını Giderme
Bağıntı birbirleriyle ve doğru iş akışı örneği iş akışı hizmeti iletileri ilişkilendirmek için kullanılır, ancak doğru şekilde yapılandırılmamışsa, ileti alınmadı ve uygulamalar düzgün çalışmaz. Bu konu, bağıntı sorunlarını giderme için çeşitli yöntemler için genel bir bakış sağlar ve ayrıca bağıntı kullanırken oluşabilecek bazı yaygın sorunlar listelenir.

## <a name="handle-the-unknownmessagereceived-event"></a>UnknownMessageReceived olayını işle
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Olay mevcut örneğine bağıntılı iletileri de dahil olmak üzere, bir hizmet tarafından bilinmeyen bir ileti alındığında gerçekleşir. Şirket içinde barındırılan hizmetler için bu olay ana uygulamada işlenebilir.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 Web barındırılan hizmetler için bu olay bir sınıftan türetme tarafından işlenebilen <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> ve geçersiz kılma <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

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

 Bu özel <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> ardından belirtilebilir `svc` dosya hizmeti.

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 Bu işleyici çağrıldığında ileti kullanılarak alınabilir <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> özelliği <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>ve şu iletiyi benzer.

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

 Gönderilen iletileri incelemek için <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> işleyici neden ileti iş akışı hizmeti örneğine bağıntılı değil hakkında ipuçları sağlayabilir.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>İş akışı ilerlemesini izlemek için izleme kullanma
 İzleme, bir iş akışı ilerlemesini izlemek için bir yol sağlar. Varsayılan olarak, iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, hata yayma ve yer imi sürdürme izleme kayıtları yayılan. Ayrıca, özel izleme kayıtları, özel etkinlikler tarafından yayılabilir. Bağıntı sorunlarını giderirken, etkinlik kayıtlarını yer imi sürdürme kayıtları ve hata yayma kayıtları izleme en kullanışlı olan. Kayıtları İzleme etkinliği iş akışının geçerli ilerleme durumunu belirlemek için kullanılabilir ve hangi Mesajlaşma etkinlik şu anda iletileri için bekleyen belirlemenize yardımcı olabilir. İş akışı tarafından bir ileti alındı ve iş akışındaki tüm hataların bir kaydı hata yayma kayıtlara sağlamak belirttiğinden yer imi sürdürme kayıtları yararlı olur. İzlemeyi etkinleştirmek için istenen belirtin <xref:System.Activities.Tracking.TrackingParticipant> içinde <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> , <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Aşağıdaki örnekte, `ConsoleTrackingParticipant` (gelen [özel izleme](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) örnek) için varsayılan izleme profili kullanılarak yapılandırılır.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 İzleme katılımcı ConsoleTrackingParticipant gibi bir konsol penceresi olan şirket içinde barındırılan iş akışı hizmetleri için kullanışlıdır. Bir Web barındırılan hizmeti için izleme bilgilerini dayanıklı bir depoya kaydeder. bir izleme katılımcı, gibi yerleşik kullanılmalıdır <xref:System.Activities.Tracking.EtwTrackingParticipant>, ya da bilgileri bir dosyaya kaydeden bir özel izleme katılımcı.

 İzleme ve izleme Web barındırılan iş akışı hizmeti için yapılandırma hakkında daha fazla bilgi için bkz. [takip ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [yapılandırma izleme için bir iş akışı](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)ve [ İzleme &#91;WF örnekleri&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) örnekleri.

## <a name="use-wcf-tracing"></a>WCF izleme kullanın
 WCF izleme ve iş akışı hizmetinden ileti akışı izlemeyi sağlar. Bu izleme bilgilerini, özellikle içerik temelli bağıntı için bağıntı sorunlarını giderirken yararlıdır. İzlemeyi etkinleştirmek için istenen izleme dinleyicilerine belirtin `system.diagnostics` bölümünü `web.config` Web barındırılan iş akışı hizmeti ise, dosya veya `app.config` dosyası workflow hizmet kendiliğinden barındırılır. İleti içeriğini izleme dosyası dahil edileceğini belirtin `true` için `logEntireMessage` içinde `messageLogging` öğesinde `diagnostics` bölümünü `system.serviceModel`. Aşağıdaki örnekte iletilerin içeriğine dahil olmak üzere, izleme bilgileri adlı bir dosyaya yazılacak yapılandırılmış `service.svclog`.

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

 Bulunan izleme bilgilerini görüntülemek için `service.svclog`, [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanılır. İleti içeriği görüntüleyin ve tam olarak ne geçirilen ve değeriyle aynı olup olmadığını görmek için içerik temelli bağıntı sorunlarını giderme verdiğinde, bu özellikle yararlı olur <xref:System.ServiceModel.CorrelationQuery> içerik temelli bağıntı için. WCF izleme hakkında daha fazla bilgi için bkz: [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), ve [sorun giderme uygulamanızkullanarakizlemeyi](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Ortak bağlam Exchange bağıntı sorunları
 Belirli türde bir bağlama için bağıntı düzgün çalışması için kullanıldığını bağıntı belirli türlerdeki gerektirir. Örnekler, iki yönlü bağlama gibi gerektiren istek-yanıt bağıntısı <xref:System.ServiceModel.BasicHttpBinding>ve bir bağlam tabanlı gibi bağlama gerektirir bağlam değişimi bağıntısı <xref:System.ServiceModel.BasicHttpContextBinding>. Bu istek-yanıt bağıntısı için yaygın bir sorun değildir, ancak yalnızca Bağlam tabanlı bağlamalar dahil olmak üzere birkaç vardır. Bu nedenle çoğu bağlamaları iki yönlü işlemlerini desteklemek <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, ve <xref:System.ServiceModel.NetTcpContextBinding>. Bu bağlamaların bir tanesini kullanılmaz bir iş akışı hizmeti için ilk çağrı başarılı olacaktır, ancak sonraki çağrılar, şunlarla birlikte başarısız olur <xref:System.ServiceModel.FaultException>.

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Bağlam bağıntı için kullanılan bağlam bilgilerini tarafından döndürülen <xref:System.ServiceModel.Activities.SendReply> için <xref:System.ServiceModel.Activities.Receive> işlemi ise veya iki yönlü bir işlemi kullanarak arayan tarafından belirtilebilir, bağlam bağıntıyı başlatır etkinliği tek yönlü. Bağlamı arayan tarafından gönderilen değil veya iş akışı hizmeti sonra aynı tarafından döndürülen <xref:System.ServiceModel.FaultException> açıklanan daha önce bir sonraki işlemi çalıştırıldığında döndürülür.

## <a name="common-request-reply-correlation-issues"></a>Genel istek-yanıt bağıntısı sorunları
 İstek-yanıt bağıntısı ile kullanılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti ile bir iş akışı hizmeti içinde bir iki yönlü işlemini uygulamak için bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> başka bir Web iki yönlü bir işlem çağıran çifti hizmeti. İki yönlü bir WCF hizmeti işlemi çağrılırken bir hizmet ya da geleneksel olabilir kesinlik temelli kod tabanlı WCF hizmeti veya bir iş akışı hizmeti olabilir. İki yönlü bir bağlama kullanılmalıdır, gibi istek-yanıt bağıntısı kullanılacak <xref:System.ServiceModel.BasicHttpBinding>, ve işlemleri çift yönlü olmalıdır.

 İş akışı hizmeti paralel veya çakışan iki yönlü işlemlerini varsa <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çiftleri ve örtük bağıntı işlemek Yönetim tarafındansağlanan<xref:System.ServiceModel.Activities.WorkflowServiceHost>özellikle yüksek yoğunluk senaryolarda yeterli olmayabilir ve iletileri değil doğru yönlendirilir. Bu sorunun oluşmasını önlemek için her zaman açıkça belirttiğiniz önerilir bir <xref:System.ServiceModel.Activities.CorrelationHandle> istek-yanıt bağıntısı kullanırken. Kullanırken **SendAndReceiveReply** ve **ReceiveAndSendReply** Mesajlaşma bölümünden şablonları **araç kutusu** iş akışı Tasarımcısı'nda bir <xref:System.ServiceModel.Activities.CorrelationHandle> açıkça varsayılan olarak yapılandırılır. Kod kullanarak bir iş akışı oluşturma sırasında <xref:System.ServiceModel.Activities.CorrelationHandle> belirtilen <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> çiftin ilk etkinlik. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.Receive> etkinlik açık bir yapılandırılmış <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> belirtilen <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

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

 Kalıcılık arasında izin verilmez bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti. No-persist bölge hem etkinlikleri tamamlanana kadar sürer oluşturulur. Bir gecikme etkinliği gibi bir etkinliği bu no-persist bölgede ve boşta durumuna gelir iş akışının sağlar, bu konak olduklarında iş akışları kalıcı hale getirmek için yapılandırılmış boş olsa bile iş akışı kalıcı olmaz. Bir kalıcı etkinliği gibi bir etkinlik açıkça no-kalan bölgesinde kalıcı hale getirmek çalışırsa, önemli bir özel durum, iş akışı iptali oluşturulur ve <xref:System.ServiceModel.FaultException> çağırana döndürülür. Önemli özel durum iletisi "System.InvalidOperationException: kalıcı etkinlikleri hiçbir Kalıcılık bloğu içinde bulunan yapılamıyor.". Bu özel durumun çağırana döndürülen değil ancak izleme etkin olup olmadığını gözlemlendi. İleti için <xref:System.ServiceModel.FaultException> "işlemi gerçekleştirilemedi iş akışı örneği '5836145b 7da2 - 49 d 0-a052-a49162adeab6' tamamlandığından" olan arayana döndürülür.

 İstek-yanıt bağıntısı hakkında daha fazla bilgi için bkz: [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Ortak içerik bağıntı sorunları
 Bir iş akışı hizmeti birden çok ileti alır ve istenen örneğine iletilerin verilerinde bir parçasını tanımlayan içerik temelli bağıntı kullanılır. İçerik temelli bağıntı iletisinde, bir müşteri numarası veya sipariş kimliği gibi doğru iş akışı örneği için iletileri yönlendirmek için bu verileri kullanır. Bu bölümde, içerik temelli bağıntı kullanırken oluşabilecek bazı yaygın sorunları açıklar.

### <a name="ensure-the-identifying-data-is-unique"></a>Benzersiz tanımlayıcı veri sağlayın
 Örneği tanımlamak için kullanılan verileri, bir bağıntı anahtarını karma haline getirilir. Bağıntı için kullanılan veri benzersizdir Aksi takdirde karma anahtarında çakışma ortaya çıktığında ve iletilerin misrouted neden güvence altına almak için dikkatli olunması gerekir. Örneğin, aynı ada sahip birden çok müşteriyi olabileceğinden yalnızca müşteri adına dayalı bir bağıntı bir çakışma neden olabilir. İki nokta üst üste (:) iletiyi ileti sorgunun anahtar ve değer daha sonra karma dizesi oluşturmak için sınırlandırmak için zaten kullanıldığından ilişkilendirmek için kullanılan verileri bir parçası olarak kullanılmamalıdır. Kalıcılık kullanılıyorsa geçerli tanımlayıcı verileri önceden Sürdürülen bir örneği tarafından kullanılmamış emin olun. Geçici olarak Kalıcılık devre dışı bırakmak, bu sorunu belirlemenize yardımcı olabilir. WCF izleme hesaplanan bağıntı anahtarı görüntülemek için kullanılabilir ve bu tür bir sorunu hata ayıklama için kullanışlıdır.

### <a name="race-conditions"></a>Yarış durumları
 Bir ileti ve gerçekten başlatılmakta bağıntı alma hizmeti arasında bir süre izleme iletileri yoksayılacak küçük bir aralık mevcuttur. Bu iletiler, bir iş akışı hizmeti bir tek yönlü işlem istemci tarafından geçirilen verileri kullanarak içerik temelli bağıntı başlatır ve çağıran hemen izleme iletileri gönderir, bu zaman aralığı boyunca yoksayılacak. Bu bağıntı başlatmak için iki yönlü bir işlemi kullanarak veya kullanılarak önlenebilir bir <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Bağıntı sorgu sorunları
 Bağıntı sorgular, hangi verilerin iletide ileti ilişkilendirmek için kullanıldığını belirtmek için kullanılır. Bu veriler, bir XPath sorgusu kullanılarak belirtilir. Her şeyin doğru görünüyor olsa bile bir hizmete ileti gönderilir değil, bir XPath sorgusu yerine ileti verinin değerinin eşleşen değişmez bir değer belirtmek için sorun giderme için bir strateji olur. Değişmez değer belirtmek için kullanın `string` işlevi. Aşağıdaki örnekte, bir <xref:System.ServiceModel.MessageQuerySet> değişmez değerini kullanacak şekilde yapılandırılmış `11445` için `OrderId` ve XPath sorgusu kılınmıştır.

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

 Bir XPath sorgusu data korelace alınır, hatalı yapılandırıldıysa, şu iletiyle bir hata döndürülür: "boş bir sonuç kümesi bir bağıntı sorgu üretilenleri kaydeder. Lütfen bağıntı sorguları uç noktası için doğru şekilde yapılandırıldığından emin olun." Bu sorunu gidermek için hızlı bir şekilde, önceki bölümde açıklandığı bir değişmez değer ile XPath sorgusu değiştirmektir. XPath sorgusu Oluşturucusu'nda kullanmanız durumunda bu sorun oluşabilir **bağıntı başlatıcılar Ekle** veya **definice vlastnosti Correlateson** iletişim kutuları ve iş akışı hizmetinizi ileti sözleşmeleri kullanır. Aşağıdaki örnekte, bir ileti anlaşması sınıfı tanımlanır.

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

 Bu ileti anlaşması tarafından kullanılan bir <xref:System.ServiceModel.Activities.Receive> bir iş akışında etkinlik. `CartId` Doğru örneği mesajıyla ileti üst bilgisinde kullanılır. XPath sorgusu, alır, `CartId` bağıntı iletişim kutuları sorgu oluşturulduğunda aşağıdaki hatalı XPath iş akışı Tasarımcısı'nda kullanılarak oluşturulur.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Bu XPath sorgusu doğru olması durumunda <xref:System.ServiceModel.Activities.Receive> etkinlik verilerini parametreleri kullanılır, ancak bir ileti anlaşması kullandığından yanlış. Aşağıdaki XPath sorgusu almak için doğru XPath sorgusu olduğundan `CartId` başlığından.

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

Aşağıdaki örnekte gösterildiği bir <xref:System.ServiceModel.Activities.Receive> etkinlik için yapılandırılmış bir `AddItem` verileri almak için önceki ileti sözleşmesi kullanan işlemi. XPath sorgusu doğru yapılandırılmamış.

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
