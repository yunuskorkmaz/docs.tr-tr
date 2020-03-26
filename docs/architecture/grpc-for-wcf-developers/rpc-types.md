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
# <a name="types-of-rpc"></a><span data-ttu-id="3c921-103">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="3c921-103">Types of RPC</span></span>

<span data-ttu-id="3c921-104">Bir Windows Communication Foundation (WCF) geliştiricisi olarak, büyük olasılıkla aşağıdaki uzaktan yordam çağrısı (RPC) türleri ile başa çıkmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3c921-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="3c921-105">İstek/yanıtla</span><span class="sxs-lookup"><span data-stu-id="3c921-105">Request/reply</span></span>
- <span data-ttu-id="3c921-106">Çift yönlü:</span><span class="sxs-lookup"><span data-stu-id="3c921-106">Duplex:</span></span>
  - <span data-ttu-id="3c921-107">Oturumlu tek yönlü çift yönlü</span><span class="sxs-lookup"><span data-stu-id="3c921-107">One-way duplex with session</span></span>
  - <span data-ttu-id="3c921-108">Oturumile tam çift yönlü</span><span class="sxs-lookup"><span data-stu-id="3c921-108">Full duplex with session</span></span>
- <span data-ttu-id="3c921-109">Tek yönlü</span><span class="sxs-lookup"><span data-stu-id="3c921-109">One-way</span></span>

<span data-ttu-id="3c921-110">Bu RPC türlerini oldukça doğal olarak mevcut gRPC kavramlarıyla haritalamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3c921-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="3c921-111">Bu bölümde sırayla bu alanların her biri bakacağız.</span><span class="sxs-lookup"><span data-stu-id="3c921-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="3c921-112">[Bölüm 5](migrate-wcf-to-grpc.md) daha derinlemesine benzer örnekler inceleyecektir.</span><span class="sxs-lookup"><span data-stu-id="3c921-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="3c921-113">WCF</span><span class="sxs-lookup"><span data-stu-id="3c921-113">WCF</span></span> | <span data-ttu-id="3c921-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="3c921-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="3c921-115">Düzenli istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="3c921-115">Regular request/reply</span></span> | <span data-ttu-id="3c921-116">Tekli</span><span class="sxs-lookup"><span data-stu-id="3c921-116">Unary</span></span> |
| <span data-ttu-id="3c921-117">İstemci geri arama arabirimi kullanarak oturumlu çift yönlü hizmet</span><span class="sxs-lookup"><span data-stu-id="3c921-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="3c921-118">Sunucu akışı</span><span class="sxs-lookup"><span data-stu-id="3c921-118">Server streaming</span></span> |
| <span data-ttu-id="3c921-119">Oturumlu tam çift yönlü hizmet</span><span class="sxs-lookup"><span data-stu-id="3c921-119">Full duplex service with session</span></span> | <span data-ttu-id="3c921-120">Çift yönlü akış</span><span class="sxs-lookup"><span data-stu-id="3c921-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="3c921-121">Tek yönlü işlemler</span><span class="sxs-lookup"><span data-stu-id="3c921-121">One-way operations</span></span> | <span data-ttu-id="3c921-122">İstemci akışı</span><span class="sxs-lookup"><span data-stu-id="3c921-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="3c921-123">İstek/yanıtla</span><span class="sxs-lookup"><span data-stu-id="3c921-123">Request/reply</span></span>

<span data-ttu-id="3c921-124">Küçük miktarda veri alan ve döndüren basit istek/yanıt yöntemleri için en basit gRPC deseni olan unary RPC'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c921-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="3c921-125">Gördüğünüz gibi, bir gRPC unary RPC hizmet yöntemi uygulamak bir WCF işlemi uygulamaya benzer.</span><span class="sxs-lookup"><span data-stu-id="3c921-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="3c921-126">Fark, gRPC ile bir arabirim uygulamak yerine bir taban sınıf yöntemigeçersiz kılmak.</span><span class="sxs-lookup"><span data-stu-id="3c921-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="3c921-127">Sunucuda, istemci hizmeti çağırmak için <xref:System.Threading.Tasks.Task%601>hem eşitleme hem de engelleme yöntemleri sağlasa da, gRPC temel yöntemleri her zaman geri döner.</span><span class="sxs-lookup"><span data-stu-id="3c921-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="3c921-128">WCF dubleks, istemciye tek yönlü</span><span class="sxs-lookup"><span data-stu-id="3c921-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="3c921-129">WCF uygulamaları (belirli bağlamalarla) istemci ve sunucu arasında kalıcı bir bağlantı oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="3c921-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="3c921-130">Sunucu, <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özellikte belirtilen bir *geri arama arabirimi* kullanarak bağlantı kapanana kadar istemciye eşzamanlı olarak veri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="3c921-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="3c921-131">gRPC hizmetleri ileti akışları ile benzer işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c921-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="3c921-132">Akışlar uygulama açısından WCF çift yönlü hizmetlerine *tam olarak* eş vermez, ancak aynı sonuçları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="3c921-133">gRPC akışı</span><span class="sxs-lookup"><span data-stu-id="3c921-133">gRPC streaming</span></span>

<span data-ttu-id="3c921-134">gRPC istemciden sunucuya ve sunucudan istemciye kalıcı akışların oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="3c921-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="3c921-135">Her iki akış türü de aynı anda etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c921-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="3c921-136">Bu yeteneğe çift yönlü akış denir.</span><span class="sxs-lookup"><span data-stu-id="3c921-136">This ability is called bidirectional streaming.</span></span>

<span data-ttu-id="3c921-137">Akışları zaman içinde rasgele, eşzamanlı mesajlaşma için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="3c921-138">Veya bunları, tek bir istek veya yanıt oluşturamayacak ve gönderilemeyecek kadar büyük büyük veri kümelerini geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="3c921-139">Aşağıdaki örnekte bir sunucu akışı RPC gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c921-139">The following example shows a server-streaming RPC.</span></span>

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

<span data-ttu-id="3c921-140">Bu sunucu akışı, aşağıdaki kodda gösterildiği gibi istemci uygulamasından tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="3c921-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

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
> <span data-ttu-id="3c921-141">Sunucu akışı RPC'leri abonelik tarzı hizmetler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c921-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="3c921-142">Ayrıca, tüm veri kümesini bellekte oluşturmak verimsiz veya imkansız olduğunda büyük veri kümeleri göndermek için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c921-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="3c921-143">Ancak, yanıt akışı tek bir `repeated` iletideki alanları göndermek kadar hızlı değildir.</span><span class="sxs-lookup"><span data-stu-id="3c921-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="3c921-144">Kural olarak, akış küçük veri kümeleri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c921-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="3c921-145">WCF'den Farklar</span><span class="sxs-lookup"><span data-stu-id="3c921-145">Differences from WCF</span></span>

<span data-ttu-id="3c921-146">WCF çift yönlü hizmeti, birden çok yöntemi olan bir istemci geri arama arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c921-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="3c921-147">Bir gRPC sunucu akış hizmeti yalnızca tek bir akış üzerinden ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="3c921-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="3c921-148">Birden çok yönteme ihtiyacınız varsa, farklı iletiler göndermek için [herhangi bir alana veya alandan birine](protobuf-any-oneof.md) sahip bir ileti türü kullanın ve bunları işlemek için istemciye kod yazın.</span><span class="sxs-lookup"><span data-stu-id="3c921-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="3c921-149">WCF'de, oturumlu [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) sınıfı bağlantı kapanana kadar canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="3c921-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="3c921-150">Oturum içinde birden çok yöntem çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c921-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="3c921-151">gRPC'de, `Task` uygulama yönteminin döndürülmesi bağlantı kapatılana kadar bitmez.</span><span class="sxs-lookup"><span data-stu-id="3c921-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="3c921-152">WCF tek yönlü işlemler ve gRPC istemci akışı</span><span class="sxs-lookup"><span data-stu-id="3c921-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="3c921-153">WCF, aktarıma özgü `[OperationContract(IsOneWay = true)]`bir bildirimi döndüren tek yönlü işlemler (işaretli) sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c921-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgment.</span></span> <span data-ttu-id="3c921-154">gRPC hizmet yöntemleri boş olsa bile her zaman yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="3c921-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="3c921-155">İstemci her zaman bu yanıtı beklemelidir.</span><span class="sxs-lookup"><span data-stu-id="3c921-155">The client should always await that response.</span></span> <span data-ttu-id="3c921-156">gRPC'de "ateş ve unut" mesajlaşma stili için bir istemci akış hizmeti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="3c921-157">thing_log.proto</span><span class="sxs-lookup"><span data-stu-id="3c921-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="3c921-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="3c921-158">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="3c921-159">ThingLog istemci örneği</span><span class="sxs-lookup"><span data-stu-id="3c921-159">ThingLog client example</span></span>

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

<span data-ttu-id="3c921-160">Önceki örnekte gösterildiği gibi, yangın ve unut iletisi için istemci akışı RPC'lerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="3c921-161">Bunları sunucuya çok büyük veri kümeleri göndermek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="3c921-162">Performans la ilgili aynı uyarı geçerlidir: `repeated` daha küçük veri kümeleri için, normal iletilerde alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c921-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="3c921-163">WCF tam çift yönlü hizmetler</span><span class="sxs-lookup"><span data-stu-id="3c921-163">WCF full-duplex services</span></span>

<span data-ttu-id="3c921-164">WCF çift yönlü bağlama, hem hizmet arabiriminde hem de istemci geri çağırma arabiriminde birden çok tek yönlü işlemi destekler.</span><span class="sxs-lookup"><span data-stu-id="3c921-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="3c921-165">Bu destek, istemci ve sunucu arasında devam eden konuşmalara izin verir.</span><span class="sxs-lookup"><span data-stu-id="3c921-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="3c921-166">gRPC, her iki parametrenin `stream` değiştirici ile işaretlendiği çift yönlü akış RPC'leri ile benzer bir şeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="3c921-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="3c921-167">chat.proto</span><span class="sxs-lookup"><span data-stu-id="3c921-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="3c921-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="3c921-168">ChatterService.cs</span></span>

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

<span data-ttu-id="3c921-169">Önceki örnekte, uygulama yönteminin hem istek akışı (`IAsyncStreamReader<MessageRequest>`) hem de`IServerStreamWriter<MessageResponse>`yanıt akışı ( ) aldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c921-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="3c921-170">Yöntem, bağlantı kapanana kadar iletileri okuyabilir ve yazabilir.</span><span class="sxs-lookup"><span data-stu-id="3c921-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="3c921-171">Geveze istemci</span><span class="sxs-lookup"><span data-stu-id="3c921-171">Chatter client</span></span>

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
><span data-ttu-id="3c921-172">[Önceki](wcf-bindings.md)
>[Sonraki](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="3c921-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
