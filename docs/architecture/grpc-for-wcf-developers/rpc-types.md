---
title: WCF geliştiricileri için RPC-gRPC türleri
description: WCF tarafından desteklenen uzak yordam çağrısı türlerinin ve gRPC 'de eşdeğerleri gözden geçirme
ms.date: 09/02/2019
ms.openlocfilehash: 58f097bac61395e6810155e8ae9a6bbf2219ec5e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503436"
---
# <a name="types-of-rpc"></a><span data-ttu-id="403f8-103">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="403f8-103">Types of RPC</span></span>

<span data-ttu-id="403f8-104">Windows Communication Foundation (WCF) geliştiricisi olarak, büyük olasılıkla şu türde uzak yordam çağrısı (RPC) ile ilgilenirken kullanılır:</span><span class="sxs-lookup"><span data-stu-id="403f8-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="403f8-105">İstek/yanıt</span><span class="sxs-lookup"><span data-stu-id="403f8-105">Request/reply</span></span>
- <span data-ttu-id="403f8-106">Duplex</span><span class="sxs-lookup"><span data-stu-id="403f8-106">Duplex:</span></span>
  - <span data-ttu-id="403f8-107">Oturumla tek yönlü çift yönlü</span><span class="sxs-lookup"><span data-stu-id="403f8-107">One-way duplex with session</span></span>
  - <span data-ttu-id="403f8-108">Oturumla tam çift yönlü</span><span class="sxs-lookup"><span data-stu-id="403f8-108">Full duplex with session</span></span>
- <span data-ttu-id="403f8-109">Tek yönlü</span><span class="sxs-lookup"><span data-stu-id="403f8-109">One-way</span></span>

<span data-ttu-id="403f8-110">Bu RPC türlerini, doğal olarak mevcut gRPC kavramlarıyla eşleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="403f8-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="403f8-111">Bu bölüm, bu alanların her birine sırayla bakar.</span><span class="sxs-lookup"><span data-stu-id="403f8-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="403f8-112">[5. Bölüm](migrate-wcf-to-grpc.md) , benzer örnekleri daha ayrıntılı bir şekilde keşfedebilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="403f8-113">WCF</span><span class="sxs-lookup"><span data-stu-id="403f8-113">WCF</span></span> | <span data-ttu-id="403f8-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="403f8-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="403f8-115">Normal istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="403f8-115">Regular request/reply</span></span> | <span data-ttu-id="403f8-116">Li</span><span class="sxs-lookup"><span data-stu-id="403f8-116">Unary</span></span> |
| <span data-ttu-id="403f8-117">İstemci geri çağırma arabirimi kullanarak oturum ile çift yönlü hizmet</span><span class="sxs-lookup"><span data-stu-id="403f8-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="403f8-118">Sunucu akışı</span><span class="sxs-lookup"><span data-stu-id="403f8-118">Server streaming</span></span> |
| <span data-ttu-id="403f8-119">Oturumla tam çift yönlü hizmet</span><span class="sxs-lookup"><span data-stu-id="403f8-119">Full duplex service with session</span></span> | <span data-ttu-id="403f8-120">Çift yönlü akış</span><span class="sxs-lookup"><span data-stu-id="403f8-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="403f8-121">Tek yönlü işlemler</span><span class="sxs-lookup"><span data-stu-id="403f8-121">One-way operations</span></span> | <span data-ttu-id="403f8-122">İstemci akışı</span><span class="sxs-lookup"><span data-stu-id="403f8-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="403f8-123">İstek/yanıt</span><span class="sxs-lookup"><span data-stu-id="403f8-123">Request/reply</span></span>

<span data-ttu-id="403f8-124">Küçük miktarlarda veri alıp döndüren basit istek/yanıt yöntemleri için, birli RPC olan en basit gRPC modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="403f8-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="403f8-125">Gördüğünüz gibi, bir gRPC birli RPC hizmeti yöntemi uygulamak, WCF işlemi uygulamaya benzer.</span><span class="sxs-lookup"><span data-stu-id="403f8-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="403f8-126">Aradaki fark, gRPC ile bir arabirim uygulamak yerine bir temel sınıf yöntemini geçersiz kılmanızdır.</span><span class="sxs-lookup"><span data-stu-id="403f8-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="403f8-127">Sunucuda, gRPC temel yöntemleri her zaman <xref:System.Threading.Tasks.Task%601>döndürür, ancak istemci hizmeti çağırmak için hem zaman uyumsuz hem de engelleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="403f8-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="403f8-128">WCF çift yönlü, istemciye bir yol</span><span class="sxs-lookup"><span data-stu-id="403f8-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="403f8-129">WCF uygulamaları (belirli bağlamalarla birlikte), istemci ve sunucu arasında kalıcı bir bağlantı oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="403f8-130">Sunucu, <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliğinde belirtilen bir *geri çağırma arabirimi* kullanılarak, bağlantı kapatılana kadar istemciye zaman uyumsuz olarak veri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="403f8-131">gRPC Hizmetleri, ileti akışlarıyla benzer işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="403f8-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="403f8-132">Akışlar, uygulama açısından *tam olarak* WCF çift yönlü hizmetlerine eşlenmiyor, ancak aynı sonuçları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="403f8-133">gRPC akışı</span><span class="sxs-lookup"><span data-stu-id="403f8-133">gRPC streaming</span></span>

<span data-ttu-id="403f8-134">gRPC, istemciden sunucuya ve sunucudan istemciye kalıcı akış oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="403f8-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="403f8-135">Her iki akış türü de aynı anda etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="403f8-136">Bu özellik çift yönlü akış olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="403f8-136">This ability is called bidirectional streaming.</span></span> 

<span data-ttu-id="403f8-137">Akışları zaman içinde rastgele, zaman uyumsuz mesajlaşma için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="403f8-138">Ya da bunları tek bir istekte veya yanıtta oluşturmak ve göndermek için çok büyük veri kümelerini geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="403f8-139">Aşağıdaki örnekte bir sunucu akış RPC gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="403f8-139">The following example shows a server-streaming RPC.</span></span>

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

<span data-ttu-id="403f8-140">Bu sunucu akışı, aşağıdaki kodda gösterildiği gibi bir istemci uygulamasından tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="403f8-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

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
> <span data-ttu-id="403f8-141">Sunucu akış RPC 'ler, abonelik stili hizmetler için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="403f8-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="403f8-142">Ayrıca, veri kümesinin tamamını bellekte oluşturmak verimsiz veya imkansız olduğunda büyük veri kümeleri göndermek için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="403f8-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="403f8-143">Ancak, akış yanıtları, tek bir iletide `repeated` alanları göndermek kadar hızlı değildir.</span><span class="sxs-lookup"><span data-stu-id="403f8-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="403f8-144">Bir kural olarak, küçük veri kümeleri için akış kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="403f8-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="403f8-145">WCF farkları</span><span class="sxs-lookup"><span data-stu-id="403f8-145">Differences from WCF</span></span>

<span data-ttu-id="403f8-146">WCF çift yönlü hizmeti, birden çok metodu olan bir istemci geri çağırma arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="403f8-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="403f8-147">GRPC sunucu akışı hizmeti yalnızca tek bir akış üzerinden ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="403f8-148">Birden çok yöntem gerekiyorsa, farklı iletiler göndermek için [herhangi bir alan veya bir alan](protobuf-any-oneof.md) içeren bir ileti türü kullanın ve bunları işlemek için istemciye kod yazın.</span><span class="sxs-lookup"><span data-stu-id="403f8-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="403f8-149">WCF 'de, oturum içeren [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) sınıfı bağlantı kapatılana kadar canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="403f8-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="403f8-150">Oturum içinde birden çok yöntem çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="403f8-151">GRPC 'de, uygulama yönteminin döndürdüğü `Task` bağlantı kapatılana kadar tamamlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="403f8-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="403f8-152">WCF tek yönlü işlemler ve gRPC istemci akışı</span><span class="sxs-lookup"><span data-stu-id="403f8-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="403f8-153">WCF, aktarıma özgü bir onay döndüren tek yönlü işlemler (`[OperationContract(IsOneWay = true)]`ile işaretlenir) sağlar.</span><span class="sxs-lookup"><span data-stu-id="403f8-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="403f8-154">gRPC hizmeti yöntemleri, boş olsa bile her zaman bir yanıt döndürür.</span><span class="sxs-lookup"><span data-stu-id="403f8-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="403f8-155">İstemci her zaman bu yanıtı bekler.</span><span class="sxs-lookup"><span data-stu-id="403f8-155">The client should always await that response.</span></span> <span data-ttu-id="403f8-156">GRPC 'de "yangın-unut" stili için bir istemci akış hizmeti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="403f8-157">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="403f8-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="403f8-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="403f8-158">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="403f8-159">ThingLog istemci örneği</span><span class="sxs-lookup"><span data-stu-id="403f8-159">ThingLog client example</span></span>

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

<span data-ttu-id="403f8-160">Önceki örnekte gösterildiği gibi, yangın ve unutma mesajlaşması için istemci akış RPC 'ler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="403f8-161">Ayrıca, sunucuya çok büyük veri kümeleri göndermek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="403f8-162">Performans için geçerli uyarı: daha küçük veri kümeleri için normal iletilerde `repeated` alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="403f8-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="403f8-163">WCF tam çift yönlü hizmetler</span><span class="sxs-lookup"><span data-stu-id="403f8-163">WCF full-duplex services</span></span>

<span data-ttu-id="403f8-164">WCF çift yönlü bağlama, hem hizmet arabiriminde hem de istemci geri çağırma arabiriminde birden çok tek yönlü işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="403f8-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="403f8-165">Bu destek, istemci ve sunucu arasında devam eden konuşmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="403f8-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="403f8-166">gRPC, iki parametrenin `stream` değiştiriciyle işaretlendiği çift yönlü akış RPC 'ler ile benzer bir şeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="403f8-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="403f8-167">sohbet. proto</span><span class="sxs-lookup"><span data-stu-id="403f8-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="403f8-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="403f8-168">ChatterService.cs</span></span>

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

<span data-ttu-id="403f8-169">Önceki örnekte, uygulama yönteminin hem istek akışını (`IAsyncStreamReader<MessageRequest>`) hem de yanıt akışını (`IServerStreamWriter<MessageResponse>`) aldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="403f8-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="403f8-170">Yöntemi, bağlantı kapatılana kadar iletileri okuyabilir ve yazabilir.</span><span class="sxs-lookup"><span data-stu-id="403f8-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="403f8-171">Chatter istemcisi</span><span class="sxs-lookup"><span data-stu-id="403f8-171">Chatter client</span></span>

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
><span data-ttu-id="403f8-172">[Önceki](wcf-bindings.md)
>[İleri](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="403f8-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
