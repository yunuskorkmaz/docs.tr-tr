---
title: WCF geliştiricileri için RPC-gRPC türleri
description: WCF tarafından desteklenen uzak yordam çağrısı türlerinin ve gRPC 'de eşdeğerleri gözden geçirme
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4fed4ca7fa4ae6a0f861185719917ff0ed5929fd
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184164"
---
# <a name="types-of-rpc"></a><span data-ttu-id="b6c6f-103">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="b6c6f-103">Types of RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b6c6f-104">Windows Communication Foundation (WCF) geliştiricisi olarak, büyük olasılıkla şu türde uzak yordam çağrısı (RPC) ile ilgilenirken kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b6c6f-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of Remote Procedure Call (RPC):</span></span>

- <span data-ttu-id="b6c6f-105">İstek/yanıt</span><span class="sxs-lookup"><span data-stu-id="b6c6f-105">Request/Reply</span></span>
- <span data-ttu-id="b6c6f-106">Duplex</span><span class="sxs-lookup"><span data-stu-id="b6c6f-106">Duplex:</span></span>
  - <span data-ttu-id="b6c6f-107">Oturumla tek yönlü çift yönlü</span><span class="sxs-lookup"><span data-stu-id="b6c6f-107">One-way duplex with session</span></span>
  - <span data-ttu-id="b6c6f-108">Oturumla tam çift yönlü</span><span class="sxs-lookup"><span data-stu-id="b6c6f-108">Full duplex with session</span></span>
- <span data-ttu-id="b6c6f-109">Tek yönlü</span><span class="sxs-lookup"><span data-stu-id="b6c6f-109">One-way</span></span>

<span data-ttu-id="b6c6f-110">Bu RPC türlerini, doğal olarak mevcut gRPC kavramlarıyla eşleştirmek mümkündür ve bu bölümde, bu alanların her birine sırayla bakacağız.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts and this chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="b6c6f-111">Benzer örnekler, [Bölüm 5](migrate-wcf-to-grpc.md)' te çok daha ayrıntılı bir şekilde araştıralınacaktır.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-111">Similar examples will be explored in much greater depth in [Chapter 5](migrate-wcf-to-grpc.md).</span></span>

| <span data-ttu-id="b6c6f-112">WCF</span><span class="sxs-lookup"><span data-stu-id="b6c6f-112">WCF</span></span> | <span data-ttu-id="b6c6f-113">gRPC</span><span class="sxs-lookup"><span data-stu-id="b6c6f-113">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="b6c6f-114">Normal istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="b6c6f-114">Regular request/reply</span></span> | <span data-ttu-id="b6c6f-115">Li</span><span class="sxs-lookup"><span data-stu-id="b6c6f-115">Unary</span></span> |
| <span data-ttu-id="b6c6f-116">İstemci geri çağırma arabirimi kullanarak oturum ile çift yönlü hizmet</span><span class="sxs-lookup"><span data-stu-id="b6c6f-116">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="b6c6f-117">Sunucu akışı</span><span class="sxs-lookup"><span data-stu-id="b6c6f-117">Server streaming</span></span> |
| <span data-ttu-id="b6c6f-118">Oturumla tam çift yönlü hizmet</span><span class="sxs-lookup"><span data-stu-id="b6c6f-118">Full duplex service with session</span></span> | <span data-ttu-id="b6c6f-119">Çift yönlü akış</span><span class="sxs-lookup"><span data-stu-id="b6c6f-119">Bidirectional streaming</span></span> |
| <span data-ttu-id="b6c6f-120">Tek yönlü işlemler</span><span class="sxs-lookup"><span data-stu-id="b6c6f-120">One-way operations</span></span> | <span data-ttu-id="b6c6f-121">İstemci akışı</span><span class="sxs-lookup"><span data-stu-id="b6c6f-121">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="b6c6f-122">İstek/yanıt</span><span class="sxs-lookup"><span data-stu-id="b6c6f-122">Request/reply</span></span>

<span data-ttu-id="b6c6f-123">Küçük miktarlarda veri alıp döndüren basit istek/yanıt yöntemleri için, birli RPC olan en basit gRPC modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-123">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="b6c6f-124">Görebileceğiniz gibi, bir gRPC birli RPC hizmeti yöntemi uygulamak, gRPC ile bir arabirim uygulamak yerine bir temel sınıf yöntemini geçersiz kıldığınız durumlar hariç, bir WCF işlemi uygulamaya çok benzer.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-124">As you can see, implementing a gRPC unary RPC service method is very similar to implementing a WCF operation, except that with gRPC you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="b6c6f-125">Sunucuda, GRPC temel yöntemleri her zaman bir <xref:System.Threading.Tasks.Task%601>döndürür; ancak istemci hizmeti çağırmak için hem zaman uyumsuz hem de engelleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-125">Note that on the server, gRPC base methods always return a <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="b6c6f-126">WCF çift yönlü, tek yönlü istemciye</span><span class="sxs-lookup"><span data-stu-id="b6c6f-126">WCF duplex, one-way to client</span></span>

<span data-ttu-id="b6c6f-127">WCF uygulamaları (belirli bağlamalarla birlikte), istemci ve sunucu arasında kalıcı bir bağlantı oluşturabilir ve bağlantı kapatılana kadar sunucu zaman uyumsuz olarak istemciye veri gönderebilir, burada belirtilen <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> bir *geri çağırma arabirimi* özelliði.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-127">WCF applications (with certain bindings) can create a persistent connection between client and server, and the server can asynchronously send data to the client until the connection is closed, using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="b6c6f-128">gRPC Hizmetleri, ileti akışlarıyla benzer işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-128">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="b6c6f-129">Akışlar, uygulama açısından *tam olarak* WCF çift yönlü hizmetlerine eşlenmiyor, ancak aynı sonuçlar elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-129">Streams don't map *exactly* to WCF duplex services in terms of implementation, but the same results can be achieved.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="b6c6f-130">gRPC akışı</span><span class="sxs-lookup"><span data-stu-id="b6c6f-130">gRPC streaming</span></span>

<span data-ttu-id="b6c6f-131">gRPC, istemciden sunucuya ve sunucudan istemciye kalıcı akış oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-131">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="b6c6f-132">Her iki akış türü de aynı anda etkin olabilir; Bu, çift yönlü akış olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-132">Both types of stream may be active concurrently; this is called bidirectional streaming.</span></span> <span data-ttu-id="b6c6f-133">Akışlar, zaman içinde rastgele, zaman uyumsuz mesajlaşma veya tek bir istek ya da yanıt oluşturmak ve göndermek için çok büyük veri kümelerinin geçirilmesi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-133">Streams can be used for arbitrary, asynchronous messaging over time, or for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="b6c6f-134">Aşağıdaki örnekte, bir sunucu akış RPC gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-134">The following example shows a server streaming RPC.</span></span>

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

<span data-ttu-id="b6c6f-135">Bu sunucu akışı, aşağıdaki kodda gösterildiği gibi bir istemci uygulamasından tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="b6c6f-135">This server stream could be consumed from a client application as shown in the following code:</span></span>

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
> <span data-ttu-id="b6c6f-136">Sunucu akış RPC 'leri, abonelik stili hizmetler için yararlıdır ve veri kümesinin tamamını bellekte oluşturmak verimsiz veya imkansız olduğunda çok büyük veri kümeleri göndermek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-136">Server streaming RPCs are useful for subscription-style services, and also for sending very large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="b6c6f-137">Ancak, akış yanıtları, alanları tek bir ileti `repeated` içine göndermek kadar hızlı değildir, bu nedenle küçük veri kümeleri için bir kural akışı kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-137">However, streaming responses isn't as fast as sending `repeated` fields in a single message, so as a rule streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-to-wcf"></a><span data-ttu-id="b6c6f-138">WCF farkları</span><span class="sxs-lookup"><span data-stu-id="b6c6f-138">Differences to WCF</span></span>

<span data-ttu-id="b6c6f-139">WCF çift yönlü hizmeti, birden çok metodu olan bir istemci geri çağırma arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-139">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="b6c6f-140">GRPC sunucu akışı hizmeti yalnızca tek bir akış üzerinden ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-140">A gRPC server streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="b6c6f-141">Birden çok yöntem gerekiyorsa, farklı iletiler göndermek için [herhangi bir alan veya bir alan](protobuf-any-oneof.md) içeren bir ileti türü kullanın ve bunları işlemek için istemciye kod yazın.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-141">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="b6c6f-142">WCF 'de, oturum içeren [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) sınıfı, bağlantı kapatılana ve oturum içinde birden çok yöntem çağrılana kadar etkin tutulur.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-142">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed, and multiple methods may be called within the session.</span></span> <span data-ttu-id="b6c6f-143">GRPC 'de, `Task` uygulama yöntemi tarafından döndürülen bağlantı kapatılana kadar tamamlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-143">In gRPC, the `Task` returned by the implementation method shouldn't complete until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="b6c6f-144">WCF tek yönlü işlemler ve gRPC istemci akışı</span><span class="sxs-lookup"><span data-stu-id="b6c6f-144">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="b6c6f-145">WCF, aktarıma özgü bir onay döndüren tek yönlü `[OperationContract(IsOneWay = true)]`işlemler (ile işaretlenir) sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-145">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="b6c6f-146">gRPC hizmeti yöntemleri, boş olsa bile her zaman bir yanıt döndürür ve istemci her zaman bu yanıtı bekler.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-146">gRPC service methods always return a response, even if it's empty, and the client should always await that response.</span></span> <span data-ttu-id="b6c6f-147">GRPC 'de "yangın-unut" stil mesajlaşması için bir istemci akış hizmeti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-147">For "fire-and-forget" style messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="b6c6f-148">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="b6c6f-148">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="b6c6f-149">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="b6c6f-149">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="b6c6f-150">ThingLog istemci örneği</span><span class="sxs-lookup"><span data-stu-id="b6c6f-150">ThingLog client example</span></span>

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

<span data-ttu-id="b6c6f-151">Ayrıca, istemci akış RPC 'leri, önceki örnekte gösterildiği gibi yangın ve unutma iletileri için, aynı zamanda sunucuya çok büyük veri kümeleri göndermek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-151">Again, client streaming RPCs can be used for fire-and-forget messaging as shown in the previous example, but also for sending very large datasets to the server.</span></span> <span data-ttu-id="b6c6f-152">Performans için geçerli uyarı: daha küçük veri kümeleri için normal iletilerdeki `repeated` alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-152">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="b6c6f-153">WCF tam çift yönlü hizmetler</span><span class="sxs-lookup"><span data-stu-id="b6c6f-153">WCF full duplex services</span></span>

<span data-ttu-id="b6c6f-154">WCF çift yönlü bağlama, istemci ve sunucu arasında devam eden konuşmaları sağlayan hem hizmet arabiriminde hem de istemci geri çağırma arabiriminde birden çok tek yönlü işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-154">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface, allowing ongoing conversations between client and server.</span></span> <span data-ttu-id="b6c6f-155">GRPC, iki parametrenin de `stream` değiştiriciyle işaretlendiği çift yönlü akış RPC 'ler ile benzer bir şeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-155">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="b6c6f-156">sohbet. proto</span><span class="sxs-lookup"><span data-stu-id="b6c6f-156">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="b6c6f-157">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="b6c6f-157">ChatterService.cs</span></span>

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

<span data-ttu-id="b6c6f-158">Önceki örnekte, uygulama yönteminin hem istek akışını (`IAsyncStreamReader<MessageRequest>`) hem de yanıt akışını (`IServerStreamWriter<MessageResponse>`) aldığını ve bağlantı kapatılana kadar iletileri okuyup yazabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6c6f-158">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`), and can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="b6c6f-159">Chatter istemcisi</span><span class="sxs-lookup"><span data-stu-id="b6c6f-159">Chatter client</span></span>

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
><span data-ttu-id="b6c6f-160">[Önceki](wcf-bindings.md)
>[İleri](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="b6c6f-160">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
