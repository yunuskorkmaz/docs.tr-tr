---
title: WCF geliştiricileri için RPC - gRPC türleri
description: WCF tarafından desteklenen uzaktan yordam çağrısı türlerinin ve bunların gRPC'deki eşdeğerlerinin gözden geçirilmesi
ms.date: 09/02/2019
ms.openlocfilehash: 40c0779dc015904e9dabbb448075e3c5aa5dc49a
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111094"
---
# <a name="types-of-rpc"></a>RPC türleri

Bir Windows Communication Foundation (WCF) geliştiricisi olarak, büyük olasılıkla aşağıdaki uzaktan yordam çağrısı (RPC) türleri ile başa çıkmak için kullanılır:

- İstek/yanıtla
- Çift yönlü:
  - Oturumlu tek yönlü çift yönlü
  - Oturumile tam çift yönlü
- Tek yönlü

Bu RPC türlerini oldukça doğal olarak mevcut gRPC kavramlarıyla haritalamak mümkündür. Bu bölümde sırayla bu alanların her biri bakacağız. [Bölüm 5](migrate-wcf-to-grpc.md) daha derinlemesine benzer örnekler inceleyecektir.

| WCF | gRPC |
| --- | ---- |
| Düzenli istek/yanıt | Tekli |
| İstemci geri arama arabirimi kullanarak oturumlu çift yönlü hizmet | Sunucu akışı |
| Oturumlu tam çift yönlü hizmet | Çift yönlü akış |
| Tek yönlü işlemler | İstemci akışı |

## <a name="requestreply"></a>İstek/yanıtla

Küçük miktarda veri alan ve döndüren basit istek/yanıt yöntemleri için en basit gRPC deseni olan unary RPC'yi kullanın.

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

Gördüğünüz gibi, bir gRPC unary RPC hizmet yöntemi uygulamak bir WCF işlemi uygulamaya benzer. Fark, gRPC ile bir arabirim uygulamak yerine bir taban sınıf yöntemigeçersiz kılmak. Sunucuda, istemci hizmeti çağırmak için <xref:System.Threading.Tasks.Task%601>hem eşitleme hem de engelleme yöntemleri sağlasa da, gRPC temel yöntemleri her zaman geri döner.

## <a name="wcf-duplex-one-way-to-client"></a>WCF dubleks, istemciye tek yönlü

WCF uygulamaları (belirli bağlamalarla) istemci ve sunucu arasında kalıcı bir bağlantı oluşturabilir. Sunucu, <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özellikte belirtilen bir *geri arama arabirimi* kullanarak bağlantı kapanana kadar istemciye eşzamanlı olarak veri gönderebilir.

gRPC hizmetleri ileti akışları ile benzer işlevsellik sağlar. Akışlar uygulama açısından WCF çift yönlü hizmetlerine *tam olarak* eş vermez, ancak aynı sonuçları elde edebilirsiniz.

### <a name="grpc-streaming"></a>gRPC akışı

gRPC istemciden sunucuya ve sunucudan istemciye kalıcı akışların oluşturulmasını destekler. Her iki akış türü de aynı anda etkin olabilir. Bu yeteneğe çift yönlü akış denir.

Akışları zaman içinde rasgele, eşzamanlı mesajlaşma için kullanabilirsiniz. Veya bunları, tek bir istek veya yanıt oluşturamayacak ve gönderilemeyecek kadar büyük büyük veri kümelerini geçirmek için kullanabilirsiniz.

Aşağıdaki örnekte bir sunucu akışı RPC gösterir.

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

Bu sunucu akışı, aşağıdaki kodda gösterildiği gibi istemci uygulamasından tüketilebilir:

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
> Sunucu akışı RPC'leri abonelik tarzı hizmetler için yararlıdır. Ayrıca, tüm veri kümesini bellekte oluşturmak verimsiz veya imkansız olduğunda büyük veri kümeleri göndermek için de yararlıdır. Ancak, yanıt akışı tek bir `repeated` iletideki alanları göndermek kadar hızlı değildir. Kural olarak, akış küçük veri kümeleri için kullanılmamalıdır.

### <a name="differences-from-wcf"></a>WCF'den Farklar

WCF çift yönlü hizmeti, birden çok yöntemi olan bir istemci geri arama arabirimi kullanır. Bir gRPC sunucu akış hizmeti yalnızca tek bir akış üzerinden ileti gönderebilir. Birden çok yönteme ihtiyacınız varsa, farklı iletiler göndermek için [herhangi bir alana veya alandan birine](protobuf-any-oneof.md) sahip bir ileti türü kullanın ve bunları işlemek için istemciye kod yazın.

WCF'de, oturumlu [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) sınıfı bağlantı kapanana kadar canlı tutulur. Oturum içinde birden çok yöntem çağrılabilir. gRPC'de, `Task` uygulama yönteminin döndürülmesi bağlantı kapatılana kadar bitmez.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF tek yönlü işlemler ve gRPC istemci akışı

WCF, aktarıma özgü `[OperationContract(IsOneWay = true)]`bir bildirimi döndüren tek yönlü işlemler (işaretli) sağlar. gRPC hizmet yöntemleri boş olsa bile her zaman yanıt verir. İstemci her zaman bu yanıtı beklemelidir. gRPC'de "ateş ve unut" mesajlaşma stili için bir istemci akış hizmeti oluşturabilirsiniz.

### <a name="thing_logproto"></a>thing_log.proto

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

Önceki örnekte gösterildiği gibi, yangın ve unut iletisi için istemci akışı RPC'lerini kullanabilirsiniz. Bunları sunucuya çok büyük veri kümeleri göndermek için de kullanabilirsiniz. Performans la ilgili aynı uyarı geçerlidir: `repeated` daha küçük veri kümeleri için, normal iletilerde alanları kullanın.

## <a name="wcf-full-duplex-services"></a>WCF tam çift yönlü hizmetler

WCF çift yönlü bağlama, hem hizmet arabiriminde hem de istemci geri çağırma arabiriminde birden çok tek yönlü işlemi destekler. Bu destek, istemci ve sunucu arasında devam eden konuşmalara izin verir. gRPC, her iki parametrenin `stream` değiştirici ile işaretlendiği çift yönlü akış RPC'leri ile benzer bir şeyi destekler.

### <a name="chatproto"></a>chat.proto

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

Önceki örnekte, uygulama yönteminin hem istek akışı (`IAsyncStreamReader<MessageRequest>`) hem de`IServerStreamWriter<MessageResponse>`yanıt akışı ( ) aldığını görebilirsiniz. Yöntem, bağlantı kapanana kadar iletileri okuyabilir ve yazabilir.

### <a name="chatter-client"></a>Geveze istemci

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
>[Sonraki](metadata.md)
