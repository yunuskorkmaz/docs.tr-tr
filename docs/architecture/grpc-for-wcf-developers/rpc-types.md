---
title: WCF geliştiricileri için RPC-gRPC türleri
description: WCF tarafından desteklenen uzak yordam çağrısı türlerinin ve gRPC 'de eşdeğerleri gözden geçirme
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ce5bf03b01dff3f7bb201ff08c9065abc2e58360
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846226"
---
# <a name="types-of-rpc"></a>RPC türleri

Windows Communication Foundation (WCF) geliştiricisi olarak, büyük olasılıkla şu türde uzak yordam çağrısı (RPC) ile ilgilenirken kullanılır:

- İstek/yanıt
- Duplex
  - Oturumla tek yönlü çift yönlü
  - Oturumla tam çift yönlü
- Tek yönlü

Bu RPC türlerini, doğal olarak mevcut gRPC kavramlarıyla eşleştirmek mümkündür ve bu bölümde, bu alanların her birine sırayla bakacağız. Benzer örnekler, [Bölüm 5](migrate-wcf-to-grpc.md)' te çok daha ayrıntılı bir şekilde araştıralınacaktır.

| WCF | gRPC |
| --- | ---- |
| Normal istek/yanıt | Li |
| İstemci geri çağırma arabirimi kullanarak oturum ile çift yönlü hizmet | Sunucu akışı |
| Oturumla tam çift yönlü hizmet | Çift yönlü akış |
| Tek yönlü işlemler | İstemci akışı |

## <a name="requestreply"></a>İstek/yanıt

Küçük miktarlarda veri alıp döndüren basit istek/yanıt yöntemleri için, birli RPC olan en basit gRPC modelini kullanın.

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

Görebileceğiniz gibi, bir gRPC birli RPC hizmeti yöntemi uygulamak, gRPC ile bir arabirim uygulamak yerine bir temel sınıf yöntemini geçersiz kıldığınız durumlar hariç, bir WCF işlemi uygulamaya çok benzer. Sunucuda, gRPC temel yöntemleri her zaman bir <xref:System.Threading.Tasks.Task%601>döndürür, ancak istemci hizmeti çağırmak için hem zaman uyumsuz hem de engelleme yöntemleri sağlar.

## <a name="wcf-duplex-one-way-to-client"></a>WCF çift yönlü, tek yönlü istemciye

WCF uygulamaları (belirli bağlamalarla birlikte), istemci ve sunucu arasında kalıcı bir bağlantı oluşturabilir ve sunucu, <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> belirtilen bir *geri çağırma arabirimi* kullanılarak, bağlantı kapatılana kadar istemciye zaman uyumsuz olarak veri gönderebilir özelliði.

gRPC Hizmetleri, ileti akışlarıyla benzer işlevler sağlar. Akışlar, uygulama açısından *tam olarak* WCF çift yönlü hizmetlerine eşlenmiyor, ancak aynı sonuçlar elde edilebilir.

### <a name="grpc-streaming"></a>gRPC akışı

gRPC, istemciden sunucuya ve sunucudan istemciye kalıcı akış oluşturulmasını destekler. Her iki akış türü de aynı anda etkin olabilir; Bu, çift yönlü akış olarak adlandırılır. Akışlar, zaman içinde rastgele, zaman uyumsuz mesajlaşma veya tek bir istek ya da yanıt oluşturmak ve göndermek için çok büyük veri kümelerinin geçirilmesi için kullanılabilir.

Aşağıdaki örnekte, bir sunucu akış RPC gösterilmektedir.

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

Bu sunucu akışı, aşağıdaki kodda gösterildiği gibi bir istemci uygulamasından tüketilebilir:

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> Sunucu akış RPC 'leri, abonelik stili hizmetler için yararlıdır ve veri kümesinin tamamını bellekte oluşturmak verimsiz veya imkansız olduğunda çok büyük veri kümeleri göndermek için de kullanılır. Ancak, akış yanıtları tek bir ileti içinde `repeated` alanları gönderilirken hızlı değildir, bu nedenle küçük veri kümeleri için bir kural akışı kullanılmamalıdır.

### <a name="differences-to-wcf"></a>WCF farkları

WCF çift yönlü hizmeti, birden çok metodu olan bir istemci geri çağırma arabirimi kullanır. GRPC sunucu akışı hizmeti yalnızca tek bir akış üzerinden ileti gönderebilir. Birden çok yöntem gerekiyorsa, farklı iletiler göndermek için [herhangi bir alan veya bir alan](protobuf-any-oneof.md) içeren bir ileti türü kullanın ve bunları işlemek için istemciye kod yazın.

WCF 'de, oturum içeren [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) sınıfı, bağlantı kapatılana ve oturum içinde birden çok yöntem çağrılana kadar etkin tutulur. GRPC 'de, uygulama yöntemi tarafından döndürülen `Task` bağlantı kapatılana kadar tamamlanmamalıdır.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF tek yönlü işlemler ve gRPC istemci akışı

WCF, aktarıma özgü bir onay döndüren tek yönlü işlemler (`[OperationContract(IsOneWay = true)]`ile işaretlenir) sağlar. gRPC hizmeti yöntemleri, boş olsa bile her zaman bir yanıt döndürür ve istemci her zaman bu yanıtı bekler. GRPC 'de "yangın-unut" stil mesajlaşması için bir istemci akış hizmeti oluşturabilirsiniz.

### <a name="thing_logproto"></a>thing_log. proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a>ThingLog istemci örneği

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

Ayrıca, istemci akış RPC 'leri, önceki örnekte gösterildiği gibi yangın ve unutma iletileri için, aynı zamanda sunucuya çok büyük veri kümeleri göndermek için de kullanılabilir. Performans için geçerli uyarı: daha küçük veri kümeleri için normal iletilerde `repeated` alanları kullanın.

## <a name="wcf-full-duplex-services"></a>WCF tam çift yönlü hizmetler

WCF çift yönlü bağlama, istemci ve sunucu arasında devam eden konuşmaları sağlayan hem hizmet arabiriminde hem de istemci geri çağırma arabiriminde birden çok tek yönlü işlemleri destekler. gRPC, iki parametrenin `stream` değiştiriciyle işaretlendiği çift yönlü akış RPC 'ler ile benzer bir şeyi destekler.

### <a name="chatproto"></a>sohbet. proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

Önceki örnekte, uygulama yönteminin hem istek akışını (`IAsyncStreamReader<MessageRequest>`) hem de yanıt akışını (`IServerStreamWriter<MessageResponse>`) aldığını ve bağlantı kapatılana kadar iletileri okuyup yazabileceğini görebilirsiniz.

### <a name="chatter-client"></a>Chatter istemcisi

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
>[Önceki](wcf-bindings.md)
>[İleri](metadata.md)
