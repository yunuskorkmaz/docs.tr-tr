---
title: Bağıntı Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: a5942c13bb4026cfeb8f664c60fb658373ffcca5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596714"
---
# <a name="troubleshooting-correlation"></a>Bağıntı Sorunlarını Giderme
Bağıntı, iş akışı hizmeti iletilerini birbirleriyle ve doğru iş akışı örneğiyle ilişkilendirmek için kullanılır, ancak doğru yapılandırılmamışsa, iletiler alınmaz ve uygulamalar düzgün çalışmayacaktır. Bu konu, bağıntı sorunlarını gidermeye yönelik çeşitli yöntemlere genel bir bakış sağlar ve bağıntı kullandığınızda oluşabilecek bazı yaygın sorunları da listeler.

## <a name="handle-the-unknownmessagereceived-event"></a>UnknownMessageReceived olayını işleme
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>Bu olay, mevcut bir örnekle bağıntılı olmayan iletiler de dahil olmak üzere bir hizmet tarafından bilinmeyen bir ileti alındığında meydana gelir. Şirket içinde barındırılan hizmetler için bu olay ana bilgisayar uygulamasında işlenebilir.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 Web 'de barındırılan hizmetler için bu olay bir sınıf türeterek <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> ve geçersiz kılınarak işlenebilir <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A> .

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

 Bu özel <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> daha sonra `svc` hizmetin dosyasında belirtilebilir.

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 Bu işleyici çağrıldığında, ileti <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> öğesinin özelliği kullanılarak alınabilir <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> ve aşağıdaki iletiye benzecektir.

```xml
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

 İşleyiciye dağıtılan iletilerin İnceleme, <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> iletinin neden iş akışı hizmeti örneğiyle bağıntılı olduğuna ilişkin ipuçları verebilir.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Iş akışının Ilerlemesini Izlemek için Izleme kullanma
 İzleme, bir iş akışının ilerlemesini izlemek için bir yol sağlar. Varsayılan olarak, izleme kayıtları iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, hata yayma ve yer işareti sürdürme için yayınlanır. Ayrıca, özel izleme kayıtları özel etkinlikler tarafından dağıtılabilir. Bağıntı sorunlarını giderirken, etkinlik izleme kayıtları, yer işareti sürdürme kayıtları ve hata yayma kayıtları en yararlı seçenektir. Etkinlik izleme kayıtları, iş akışının geçerli ilerlemesini belirlemek için kullanılabilir ve şu anda ileti için bekleyen mesajlaşma etkinliğini belirlemenize yardımcı olabilir. Yer işareti sürdürme kayıtları, iş akışı tarafından bir iletinin alındığını ve hata yayma kayıtları iş akışındaki hataların bir kaydını sağlar. İzlemeyi etkinleştirmek için, <xref:System.Activities.Tracking.TrackingParticipant> içinde istediğiniz ' ı belirtin <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Aşağıdaki örnekte, `ConsoleTrackingParticipant` ( [özel izleme](../../windows-workflow-foundation/samples/custom-tracking.md) örneğinden) varsayılan izleme profili kullanılarak yapılandırılır.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Consoletrackingkatılımcı gibi bir izleme katılımcısı, bir konsol penceresi olan şirket içinde barındırılan iş akışı hizmetleri için yararlıdır. Web 'de barındırılan bir hizmet için izleme bilgilerini sürekli bir depoya kaydeden bir izleme katılımcısı, yerleşik <xref:System.Activities.Tracking.EtwTrackingParticipant> veya bilgileri bir dosyaya kaydeden özel bir izleme katılımcısı gibi kullanılmalıdır.

 Web 'de barındırılan bir iş akışı hizmeti için izlemeyi izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Iş akışı için izlemeyi yapılandırma](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)ve [&#91;WF örnekleri&#93;](../../windows-workflow-foundation/samples/tracking.md) örnekleri.

## <a name="use-wcf-tracing"></a>WCF Izlemeyi kullan
 WCF izleme, bir iş akışı hizmetine veya bir iş akışı hizmetinden ileti akışını izlemeyi sağlar. Bu izleme bilgileri, özellikle içerik tabanlı bağıntı için, bağıntı sorunlarını giderirken yararlıdır. İzlemeyi etkinleştirmek için, `system.diagnostics` `web.config` iş akışı hizmeti Web 'de barındırılıyorsa veya `app.config` iş akışı hizmeti kendiliğinden barındırılıyorsa dosyayı dosyanın bölümünde, istenen izleme dinleyicilerini belirtin. İletilerin içeriğini izleme dosyasına eklemek için `true` `logEntireMessage` `messageLogging` bölümündeki öğesinde için öğesini belirtin `diagnostics` `system.serviceModel` . Aşağıdaki örnekte, iletilerin içeriği de dahil olmak üzere izleme bilgileri, adlı bir dosyaya yazılacak şekilde yapılandırılmıştır `service.svclog` .

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

 İçinde yer alan izleme bilgilerini görüntülemek için `service.svclog` , [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanılır. Bu özellikle, ileti içeriğini görüntüleyebildiğinden ve tam olarak neyin geçtiğini ve <xref:System.ServiceModel.CorrelationQuery> içerik tabanlı bağıntı için ile eşleşip eşleşmediğini görmenizi sağladığından, içerik tabanlı bağıntı sorunları giderirken yararlıdır. WCF izleme hakkında daha fazla bilgi için bkz. [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Izlemeyi yapılandırma](../diagnostics/tracing/configuring-tracing.md)ve [uygulamanızın sorunlarını gidermek için izlemeyi kullanma](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Ortak bağlam değişim bağıntı sorunları
 Belirli bağıntı türleri, bağıntı doğru şekilde çalışması için belirli bir bağlama türünün kullanılmasını gerektirir. Örnek olarak, gibi iki yönlü bir bağlama gerektiren istek-yanıt bağıntısını ve gibi <xref:System.ServiceModel.BasicHttpBinding> bağlam tabanlı bağlama gerektiren bağlam değişim bağıntısını içerir <xref:System.ServiceModel.BasicHttpContextBinding> . Çoğu bağlama iki yönlü işlemleri destekler. bu nedenle, istek-yanıt bağıntısı için yaygın bir sorun değildir, ancak, ve dahil olmak üzere yalnızca el ile bağlam tabanlı bağlamalar <xref:System.ServiceModel.BasicHttpContextBinding> vardır <xref:System.ServiceModel.WSHttpContextBinding> <xref:System.ServiceModel.NetTcpContextBinding> . Bu bağlamalardan biri kullanılmazsa, bir iş akışı hizmetine yapılan ilk çağrı başarılı olur, ancak sonraki çağrılar aşağıdaki gibi başarısız olur <xref:System.ServiceModel.FaultException> .

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Bağlam bağıntısı için kullanılan bağlam bilgileri, <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> iki yönlü bir işlem kullanılırken bağlam bağıntısını Başlatan etkinliğe veya işlem tek yönlü ise çağıran tarafından belirtilebilecek şekilde döndürülebilir. Bağlam, çağıran tarafından gönderilmezse veya iş akışı hizmeti tarafından döndürülürse, <xref:System.ServiceModel.FaultException> sonraki bir işlem çağrıldığında daha önce açıklanan daha önce de açıklanacaktır.

## <a name="common-request-reply-correlation-issues"></a>Ortak Istek-yanıt bağıntı sorunları
 İstek-Yanıt Bağıntısı, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde iki yönlü bir işlem ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> başka bir Web hizmetinde iki yönlü bir işlem çağıran bir çifte bir çifte birlikte kullanılır. Bir WCF hizmetinde iki yönlü bir işlem çağrılırken, hizmet geleneksel bir kesinlik temelli kod tabanlı WCF hizmeti olabilir veya bir iş akışı hizmeti olabilir. İstek-yanıt bağıntısını kullanmak için iki yönlü bağlama kullanılmalıdır, örneğin <xref:System.ServiceModel.BasicHttpBinding> , ve işlemler iki yönlü olmalıdır.

 İş akışı hizmetinin paralel veya çakışan ya da çiftler halinde iki yönlü işlemleri varsa, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> tarafından sunulan örtük bağıntı tanıtıcısı yönetimi, <xref:System.ServiceModel.Activities.WorkflowServiceHost> özellikle yüksek stres senaryolarında yeterli olmayabilir ve iletiler doğru şekilde yönlendirilmeyebilir. Bu sorunun oluşmasını önlemek için, <xref:System.ServiceModel.Activities.CorrelationHandle> istek-yanıt bağıntısını kullanırken her zaman açıkça bir belirtmeniz önerilir. İş akışı tasarımcısında **araç kutusunun** Mesajlaşma bölümünde **SendAndReceiveReply** ve **ReceiveAndSendReply** şablonları kullanılırken, <xref:System.ServiceModel.Activities.CorrelationHandle> Varsayılan olarak açıkça yapılandırılır. Kodu kullanarak bir iş akışı oluştururken, <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> çiftteki ilk etkinliğin içinde belirtilir. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.Receive> etkinlik öğesinde belirtilen açık ile yapılandırılır <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .

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

 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Çift veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çift arasında Kalıcılık kullanılmasına izin verilmiyor. Her iki etkinlik de tamamlanana kadar devam eden kalıcı olmayan bir bölge oluşturulur. Gecikme etkinliği gibi bir etkinlik bu kalıcı olmayan bir bölgede yer alıyorsa ve iş akışının boşta olmasına neden oluyorsa, ana bilgisayar boşta kaldığında iş akışlarını kalıcı hale getirmek üzere yapılandırılmış olsa bile, iş akışı devam etmez. Kalıcı etkinlik gibi bir etkinlik, kalıcı olmayan bir bölgede açık bir şekilde kalıcı hale getirmeye çalışırsa, önemli bir özel durum oluşturulur, iş akışı iptal edilir ve <xref:System.ServiceModel.FaultException> çağrı yapana döndürülür. Önemli özel durum iletisi "System. InvalidOperationException: Persist etkinlikleri kalıcı olmayan bloklar içinde yer alamaz.". Bu özel durum çağırana döndürülmüyor, ancak izleme etkinse gözlemlenebilir. <xref:System.ServiceModel.FaultException>Arayan için döndürülen ileti ", WorkflowInstance ' 5836145b-7dav2-49d0-a052-a49162adeab6 ' tamamlandığı için işlem gerçekleştirilemedi.

 İstek-yanıt bağıntısı hakkında daha fazla bilgi için bkz. [istek-yanıt](request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Ortak Içerik bağıntı sorunları
 İçerik tabanlı bağıntı, bir iş akışı hizmeti birden çok ileti aldığında ve değiştirilen iletilerde bir veri parçası istenen örneği tanımlarsa kullanılır. İçerik tabanlı bağıntı, iletileri doğru iş akışı örneğine yönlendirmek için bir müşteri numarası veya sipariş KIMLIĞI gibi iletideki bu verileri kullanır. Bu bölümde, içerik tabanlı bağıntı kullanılırken oluşabilecek bazı yaygın sorunlar açıklanmaktadır.

### <a name="ensure-the-identifying-data-is-unique"></a>Tanımlayıcı verilerin benzersiz olduğundan emin olun
 Örneği tanımlamak için kullanılan veriler bir bağıntı anahtarına karma hale getirilir. Bağıntı için kullanılan verilerin benzersiz olduğundan emin olmak için dikkatli olunmalıdır, aksi takdirde karma anahtardaki çakışmaların oluşması ve iletilerin hatalı yönlendirilmesine neden olabilir. Örneğin, aynı ada sahip birden fazla müşteri olabileceğinden, yalnızca müşteri adı temelinde bir bağıntı çakışmasına neden olabilir. İki nokta (:) ileti sorgusunun anahtar ve değerini daha sonra karma hale getirilen dizeyi oluşturacak şekilde sınırlandırmak için zaten kullanıldığından, iletiyi ilişkilendirmek için kullanılan verilerin bir parçası olarak kullanılmamalıdır. Kalıcılık kullanılıyorsa, geçerli tanımlama verilerinin önceden kalıcı bir örnek tarafından kullanılmadığından emin olun. Kalıcılığı geçici olarak devre dışı bırakmak bu sorunu belirlemenize yardımcı olabilir. WCF izleme, hesaplanan bağıntı anahtarını görüntülemek için kullanılabilir ve bu tür bir sorunu ayıklamak için faydalıdır.

### <a name="race-conditions"></a>Yarış durumları
 Bir ileti alma ile bağıntıdan başlatılan bağıntı arasında küçük bir boşluk vardır ve bu süre, izleme iletilerinin yok sayılacak olur. Bir iş akışı hizmeti, istemciden tek yönlü bir işlem üzerinden geçirilen verileri kullanarak içerik tabanlı bağıntıyı başlatır ve arayan anında izleme iletileri gönderdiğinde, bu iletiler bu Aralık sırasında yok sayılır. Bu, bağıntıyı başlatmak için iki yönlü bir işlem kullanılarak veya kullanılarak kaçınılabilir <xref:System.ServiceModel.Activities.TransactedReceiveScope> .

### <a name="correlation-query-issues"></a>Bağıntı sorgusu sorunları
 Bağıntı sorguları, iletiyi ilişkilendirmek için hangi verilerin kullanıldığını belirtmek için kullanılır. Bu veriler bir XPath sorgusu kullanılarak belirtilir. Her şey doğru gibi görünse de bir hizmete gönderilen iletiler dağıtılmazsa, sorun gidermeye yönelik bir strateji, bir XPath sorgusu yerine ileti verilerinin değeriyle eşleşen bir sabit değer belirtmektir. Bir sabit değer belirtmek için `string` işlevini kullanın. Aşağıdaki örnekte, <xref:System.ServiceModel.MessageQuerySet> , için değişmez değer değerini kullanacak şekilde yapılandırılmıştır `11445` `OrderId` ve XPath sorgusu açıklama olarak ayarlanır.

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

 Bir XPath sorgusu, hiçbir bağıntı verisi alınmadıysa yanlış yapılandırılmışsa şu iletiyle bir hata döndürülür: "bir bağıntı sorgusu boş bir sonuç kümesi verdi. Lütfen uç nokta için bağıntı sorgularının doğru yapılandırıldığından emin olun. " Bu sorunu gidermeye yönelik bir hızlı yol, XPath sorgusunun önceki bölümde açıklanan şekilde değişmez değer değeriyle değiştirilmesini kullanmaktır. Bu sorun, **bağıntı başlatıcıları** veya **CorrelatesOn tanımı** Ekle iletişim kutularında XPath sorgu oluşturucuyu kullanırsanız ve iş akışı hizmetiniz ileti sözleşmeleri kullanıyorsa oluşabilir. Aşağıdaki örnekte, bir ileti sözleşmesi sınıfı tanımlanmıştır.

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

 Bu ileti sözleşmesi <xref:System.ServiceModel.Activities.Receive> bir iş akışındaki etkinlik tarafından kullanılır. `CartId`İleti üstbilgisinde ileti doğru örnekle ilişkilendirmek için kullanılır. Öğesini alan XPath sorgusu, `CartId` iş akışı tasarımcısında bağıntı iletişim kutuları kullanılarak oluşturulduysa, şu yanlış XPath sorgusu oluşturulur.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Bu XPath sorgusu, <xref:System.ServiceModel.Activities.Receive> etkinlik veriler için parametreler kullanıyorsa, ancak bir ileti sözleşmesi kullandığı için doğru olacaktır. Aşağıdaki XPath sorgusu, üst bilgisinden alınacak doğru XPath sorgusudur `CartId` .

```
sm:header()/tempuri:CartId
```

Bu, iletinin gövdesini inceleyerek onaylanır.

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

Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.Receive> `AddItem` verileri almak için önceki ileti sözleşmesini kullanan bir işlem için yapılandırılmış bir etkinlik gösterilmektedir. XPath sorgusu doğru bir şekilde yapılandırılmıştır.

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
