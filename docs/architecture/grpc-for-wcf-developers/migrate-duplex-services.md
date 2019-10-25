---
title: WCF geliştiricileri için WCF çift yönlü hizmetlerini gRPC-gRPC 'ye geçirme
description: Çeşitli WCF çift yönlü hizmetini gRPC akış Hizmetleri 'ne geçirmeyi öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1702c9f7659f056af9009e81847f28c6e65b277c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846599"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="da141-103">WCF çift yönlü hizmetlerini gRPC'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="da141-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="da141-104">Artık temel kavramlar hazır olduğuna göre, bu bölüm daha karmaşık *akış* GRPC hizmetlerine bakacaktır.</span><span class="sxs-lookup"><span data-stu-id="da141-104">Now that the basic concepts are in place, this section will look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="da141-105">Windows Communication Foundation (WCF) içinde çift yönlü hizmetler kullanmanın birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="da141-106">Bazı hizmetler istemci tarafından başlatılır ve sonra sunucudan veri akışı yapılır.</span><span class="sxs-lookup"><span data-stu-id="da141-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="da141-107">Diğer tam çift yönlü hizmetler, WCF belgelerinden klasik "Hesaplayıcı" örneği gibi devam eden iki yönlü iletişim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="da141-107">Other full-duplex services might involve more ongoing two-way communication like the classic "Calculator" example from the WCF documentation.</span></span> <span data-ttu-id="da141-108">Bu bölümde, iki olası WCF "hisse senedi bandı" uygulaması ele alınır ve bu uygulamalar gRPC 'ye geçirilir: bir sunucu akış RPC ve diğeri çift yönlü bir akış RPC kullanarak.</span><span class="sxs-lookup"><span data-stu-id="da141-108">This chapter will take two possible WCF "Stock Ticker" implementations and migrate them to gRPC: one using a server streaming RPC, and the other one using a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="da141-109">Sunucu akış RPC</span><span class="sxs-lookup"><span data-stu-id="da141-109">Server streaming RPC</span></span>

<span data-ttu-id="da141-110">[Örnek SIMPLESTOCKTICKER WCF çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, istemcinin bir hisse senedi sembolleri listesi ile bağlantıyı başlattığı bir çift yönlü hizmet vardır ve sunucu, güncelleştirmeleri bu şekilde göndermek için *geri çağırma arabirimini* kullanır kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="da141-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, there's a duplex service where the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="da141-111">İstemci, sunucudan yapılan çağrılara yanıt vermek için bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="da141-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="da141-112">WCF çözümü</span><span class="sxs-lookup"><span data-stu-id="da141-112">The WCF solution</span></span>

<span data-ttu-id="da141-113">WCF çözümü, .NET Framework 4. x konsol uygulamasında şirket içinde barındırılan bir NetTCP sunucusu olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="da141-113">The WCF solution is implemented as a self-hosted NetTCP server in a .NET Framework 4.x console application.</span></span>

#### <a name="the-servicecontract"></a><span data-ttu-id="da141-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="da141-114">The ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="da141-115">Hizmetin, verileri istemciye gerçek zamanlı olarak göndermek için `ISimpleStockTickerCallback` geri çağırma arabirimini kullanacağı için, dönüş türü olmayan tek bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-115">The service has a single method with no return type, because it will be using the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="da141-116">Geri çağırma arabirimi</span><span class="sxs-lookup"><span data-stu-id="da141-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="da141-117">Bu arabirimlerin uygulamaları, test verileri sağlamak için sık yapılan dış bağımlılıklarla birlikte çözümde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-117">The implementations of these interfaces can be found in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="da141-118">gRPC akışı</span><span class="sxs-lookup"><span data-stu-id="da141-118">gRPC streaming</span></span>

<span data-ttu-id="da141-119">Gerçek zamanlı verileri işlemenin gRPC yolu farklıdır.</span><span class="sxs-lookup"><span data-stu-id="da141-119">The gRPC way of handling real-time data is different.</span></span> <span data-ttu-id="da141-120">İstemciden sunucuya çağrı, zaman uyumsuz olarak gelen iletiler için izlenebilecek kalıcı bir akış oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-120">A call from client to server can create a persistent stream, which can be monitored for messages arriving asynchronously.</span></span> <span data-ttu-id="da141-121">Farklılık olsa da, akışlar bu verilerle ilgilenmenin daha sezgisel bir yolu olabilir ve LINQ, reaktif akışlar, işlevsel programlama vb. üzerinde vurgu ile modern programlama ile daha ilgili olabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming with the emphasis on LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="da141-122">Hizmet tanımında iki ileti gerekir: istek için bir tane ve akış için bir tane.</span><span class="sxs-lookup"><span data-stu-id="da141-122">The service definition needs two messages: one for the request, and one for the stream.</span></span> <span data-ttu-id="da141-123">Hizmet, `return` bildiriminde `stream` anahtar sözcüğünü kullanarak `StockTickerUpdate` iletisinin bir akışını döndürür.</span><span class="sxs-lookup"><span data-stu-id="da141-123">The service returns a stream of the `StockTickerUpdate` message using the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="da141-124">Fiyatın değiştiği zamanı tam olarak göstermek için güncelleştirmeye `Timestamp` eklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="da141-124">It's recommended that you add a `Timestamp` to the update to show the exact time the price changed.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="da141-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="da141-125">simple_stock_ticker.proto</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a><span data-ttu-id="da141-126">SimpleStockTicker uygulama</span><span class="sxs-lookup"><span data-stu-id="da141-126">Implement the SimpleStockTicker</span></span>

<span data-ttu-id="da141-127">`TraderSys.StockMarket` sınıf kitaplığından üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte `StockPriceSubscriber` kullanın.</span><span class="sxs-lookup"><span data-stu-id="da141-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="da141-128">En iyi uygulamaları daha iyi izlemek için, örnek oluşturmak üzere bir `Factory` türü ekleyin ve `IStockPriceSubscriberFactory` ASP.NET Core bağımlılık ekleme hizmetleri ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="da141-128">To better follow best practices, add a `Factory` type to create instances of it and register the `IStockPriceSubscriberFactory` with ASP.NET Core's dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="da141-129">Fabrika uygulama</span><span class="sxs-lookup"><span data-stu-id="da141-129">The factory implementation</span></span>

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="registering-the-factory"></a><span data-ttu-id="da141-130">Fabrikası kaydetme</span><span class="sxs-lookup"><span data-stu-id="da141-130">Registering the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="da141-131">Şimdi, bu sınıf gRPC StockTicker hizmetini uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-131">Now, this class can be used to implement the gRPC StockTicker service.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="da141-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="da141-132">StockTickerService.cs</span></span>

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors due to broken connection etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

<span data-ttu-id="da141-133">Gördüğünüz gibi, `.proto` dosyasındaki bildirim "döndürülen" yöntemini bir `StockTickerUpdate` iletilerinin akışını söyetse de, aslında bir Vanilla `Task` döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="da141-133">As you can see, although the declaration in the `.proto` file says the method "returns" a stream of `StockTickerUpdate` messages, in fact it returns a vanilla `Task`.</span></span> <span data-ttu-id="da141-134">Akışı oluşturma işi oluşturulan kod ve gRPC çalışma zamanı kitaplıkları tarafından işlenir ve bu `IServerStreamWriter<StockTickerUpdate>` yanıt akışını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="da141-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="da141-135">Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="da141-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned Task to keep the service alive.</span></span> <span data-ttu-id="da141-136">Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="da141-136">The Task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="da141-137">Hizmet, `ServerCallContext` `CancellationToken` kullanarak istemcinin bağlantıyı kapattığını söyleyebilir.</span><span class="sxs-lookup"><span data-stu-id="da141-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="da141-138">Basit bir statik yöntem `AwaitCancellation`, belirteç iptal edildiğinde tamamlanan bir görev oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da141-138">A simple static method, `AwaitCancellation`, is used to create a Task that completes when the token is canceled.</span></span>

<span data-ttu-id="da141-139">`Subscribe` yönteminde, bir `StockPriceSubscriber` alın ve yanıt akışına yazan bir olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="da141-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="da141-140">Daha sonra, `subscriber`, kapatılan akışa veri yazmaya çalışmasını engellemek için hemen elden bırakmadan önce bağlantının kapatılmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="da141-140">Then wait for the connection to be closed, before immediately disposing the `subscriber` to prevent it trying to write data to the closed stream.</span></span>

<span data-ttu-id="da141-141">`WriteUpdateAsync` yönteminde, akışa ileti yazılırken oluşabilecek hataları işlemek için bir `try`/`catch` bloğu vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when writing a message to the stream.</span></span> <span data-ttu-id="da141-142">Bu, ağ üzerinden yapılan kalıcı bağlantılarda önemli bir konudur. Bu, kasıtlı olarak veya bir yerde bir hata nedeniyle herhangi bir milisaniyeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-142">This is an important consideration in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="using-the-stocktickerservice-from-a-client-application"></a><span data-ttu-id="da141-143">Bir istemci uygulamasından StockTickerService kullanma</span><span class="sxs-lookup"><span data-stu-id="da141-143">Using the StockTickerService from a client application</span></span>

<span data-ttu-id="da141-144">`.proto` dosyasından bir paylaşılabilir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="da141-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="da141-145">Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET Core 3,0 konsol uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="da141-146">Örnek Program.cs</span><span class="sxs-lookup"><span data-stu-id="da141-146">Example Program.cs</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

<span data-ttu-id="da141-147">Bu durumda, oluşturulan istemcideki `Subscribe` yöntemi zaman uyumsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="da141-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="da141-148">Akış oluşturulur ve hemen kullanılabilir çünkü `MoveNext` yöntemi zaman uyumsuzdur ve ilk çağrılışında bağlantı etkin olana kadar tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="da141-148">The stream is created and usable right away, because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="da141-149">Akış zaman uyumsuz bir `DisplayAsync` metoduna geçirilir; uygulama daha sonra kullanıcının bir tuşa basmasını bekler, sonra `DisplayAsync` yöntemini iptal eder ve çıkmadan önce görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="da141-149">The stream is passed to an async `DisplayAsync` method; the application then waits for the user to press a key, then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="da141-150">Bu kod, `Main` yöntemi çıktığında C# akışı ve kanalı atmak için yeni 8 "using bildirimi" sözdizimini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="da141-150">This code is using the new C# 8 "using declaration" syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="da141-151">Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.</span><span class="sxs-lookup"><span data-stu-id="da141-151">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="da141-152">Akışı tüketme</span><span class="sxs-lookup"><span data-stu-id="da141-152">Consume the stream</span></span>

<span data-ttu-id="da141-153">WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullandı.</span><span class="sxs-lookup"><span data-stu-id="da141-153">WCF used callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="da141-154">gRPC akışları farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="da141-154">gRPC streams work differently.</span></span> <span data-ttu-id="da141-155">İstemci, bir `IEnumerable` döndüren yerel bir yöntemden döndürüldüğünden olduğu gibi döndürülen akışın üzerinde dolaşır ve iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="da141-155">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="da141-156">`IAsyncStreamReader<T>` türü bir `IEnumerator<T>`gibi çalışır: daha fazla veri ve en son değeri döndüren bir `Current` özelliği olan sürece true döndürecek bir `MoveNext` yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-156">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`: there's a `MoveNext` method that will return true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="da141-157">Tek fark, `MoveNext` yönteminin yalnızca bir `bool` yerine `Task<bool>` döndürdüğünden oluşur.</span><span class="sxs-lookup"><span data-stu-id="da141-157">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="da141-158">`ReadAllAsync` uzantısı yöntemi, akışı yeni`await foreach`sözdizimiyle kullanılabilecek standart C# bir 8`IAsyncEnumerable`kaydırır.</span><span class="sxs-lookup"><span data-stu-id="da141-158">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> <span data-ttu-id="da141-159">Bu bölümün sonundaki [istemci kitaplıklarında](client-libraries.md#iobservable) bulunan bölüm, bir uzantı yöntemi ve sınıfların nasıl ekleneceğini, bir `IObservable<T>` `IAsyncStreamReader<T>`, reaktif programlama düzenlerini kullanan geliştiriciler için bir.</span><span class="sxs-lookup"><span data-stu-id="da141-159">The section on [client libraries](client-libraries.md#iobservable) at the end of this chapter looks at how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>` for developers using reactive programming patterns.</span></span>

<span data-ttu-id="da141-160">Ayrıca, ağ hatası olasılığı nedeniyle özel durumların yanı sıra, kod döngüyü bölmek için bir <xref:System.Threading.CancellationToken> kullandığından, kaçınılmaz <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="da141-160">Again, be careful to catch exceptions here because of the possibility of network failure, as well as the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="da141-161">`RpcException` türü, gRPC çalışma zamanı hataları hakkında, `StatusCode`dahil olmak üzere çok yararlı bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="da141-161">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="da141-162">Daha fazla bilgi için, bkz. [Bölüm 4 ' te *hata işleme* ](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="da141-162">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="da141-163">Çift yönlü akış</span><span class="sxs-lookup"><span data-stu-id="da141-163">Bidirectional streaming</span></span>

<span data-ttu-id="da141-164">WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar.</span><span class="sxs-lookup"><span data-stu-id="da141-164">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="da141-165">Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır.</span><span class="sxs-lookup"><span data-stu-id="da141-165">In the server streaming example, the client starts a request, then receives a stream of updates.</span></span> <span data-ttu-id="da141-166">Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="da141-166">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="da141-167">Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.</span><span class="sxs-lookup"><span data-stu-id="da141-167">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="da141-168">`IFullStockTickerService` arabirimi üç yöntem sağlar:</span><span class="sxs-lookup"><span data-stu-id="da141-168">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="da141-169">`Subscribe` bağlantıyı başlatır.</span><span class="sxs-lookup"><span data-stu-id="da141-169">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="da141-170">`AddSymbol` izlemek için bir hisse senedi simgesi ekler.</span><span class="sxs-lookup"><span data-stu-id="da141-170">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="da141-171">`RemoveSymbol` izlenen listeden bir sembol kaldırır.</span><span class="sxs-lookup"><span data-stu-id="da141-171">`RemoveSymbol` removes a symbol from the watched list.</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

<span data-ttu-id="da141-172">Geri çağırma arabirimi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="da141-172">The callback interface remains the same.</span></span>

<span data-ttu-id="da141-173">Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="da141-173">Implementing this pattern in gRPC is less straightforward, because there are now two streams of data with messages being passed: one from client to server, and another from server to client.</span></span> <span data-ttu-id="da141-174">Ekleme ve kaldırma işlemini uygulamak için birden çok yöntem kullanılması mümkün değildir, ancak [Bölüm 3](protobuf-any-oneof.md)' te kapsanan `Any` türü veya `oneof` anahtar sözcüğü kullanılarak tek bir akışta birden fazla ileti türü geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="da141-174">It isn't possible to use multiple methods to implement the Add and Remove operation, but more than one type of message can be passed on a single stream, using either the `Any` type or `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="da141-175">Kabul edilebilir olan belirli türde bir durum için `oneof` daha iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="da141-175">For a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="da141-176">Bir `AddSymbolRequest` ya da `RemoveSymbolRequest` tutabilecek bir `ActionMessage` kullanın.</span><span class="sxs-lookup"><span data-stu-id="da141-176">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`.</span></span>

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

<span data-ttu-id="da141-177">`ActionMessage` iletilerinin akışını alan, iki yönlü bir akış hizmeti bildirin.</span><span class="sxs-lookup"><span data-stu-id="da141-177">Declare a bi-directional streaming service that takes a stream of `ActionMessage` messages.</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="da141-178">Bu hizmetin uygulanması, `Subscribe` yönteminin ilk parametresi dışında, `Add` ve `Remove` isteklerini işlemek için kullanılabilen bir `IAsyncStreamReader<ActionMessage>`, önceki örneğe benzer.</span><span class="sxs-lookup"><span data-stu-id="da141-178">The implementation for this service is similar to the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests.</span></span>

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors due to broken connection etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

<span data-ttu-id="da141-179">GRPC 'nin oluşturduğu `ActionMessage` sınıfı, `Add` ve `Remove` özelliklerinden yalnızca birinin ayarlanamadığına ve hangi `null` bir tür ileti kullanıldığını bulmanın geçerli bir yolu olduğunu garanti etmektedir. , ancak daha iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="da141-179">The `ActionMessage` class that gRPC has generated for us guarantees that only one of the `Add` and `Remove` properties can be set, and finding which one isn't `null` is a valid way of finding which type of message is used, but there's a better way.</span></span> <span data-ttu-id="da141-180">Kod oluşturma Ayrıca, aşağıdaki gibi görünen `ActionMessage` sınıfında bir `enum ActionOneOfCase` oluşturmuştur:</span><span class="sxs-lookup"><span data-stu-id="da141-180">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="da141-181">`ActionMessage` nesnesindeki `ActionCase` özellik, hangi alanın ayarlandığını belirleyebilmek için bir `switch` ifadesiyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-181">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set.</span></span>

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="da141-182">`switch` deyimin, bilinmeyen bir `ActionOneOfCase` değeriyle karşılaşılırsa uyarı kaydeden bir `default` durumu vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-182">The `switch` statement has a `default` case that logs a warning if an unknown `ActionOneOfCase` value is encountered.</span></span> <span data-ttu-id="da141-183">Bu, bir istemcinin daha fazla eylem ekleyen `.proto` dosyasının daha yeni bir sürümünü kullandığını gösteren yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-183">This could be useful in indicating that a client is using a later version of the `.proto` file which has added more actions.</span></span> <span data-ttu-id="da141-184">Bunun nedeni, `switch` kullanmanın bilinen alanlar üzerinde `null` test ediden daha iyi olmasının bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="da141-184">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="da141-185">Bir istemci uygulamasından FullStockTickerService kullanma</span><span class="sxs-lookup"><span data-stu-id="da141-185">Use the FullStockTickerService from a client application</span></span>

<span data-ttu-id="da141-186">Bu daha karmaşık istemcinin kullanımını göstermek için basit bir .NET Core 3,0 WPF uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="da141-186">There's a simple .NET Core 3.0 WPF application to demonstrate use of this more complex client.</span></span> <span data-ttu-id="da141-187">Tam uygulama [GitHub 'da](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="da141-187">The full application can be found [on GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="da141-188">İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, bağımlılık ekleme işleminden `FullStockTicker.FullStockTickerClient` türünün bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="da141-188">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection.</span></span>

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

<span data-ttu-id="da141-189">`client.Subscribe()` yöntemi tarafından döndürülen nesne artık gRPC kitaplık türü `AsyncDuplexStreamingCall<TRequest, TResponse>`bir örneğidir. Bu, sunucuya istek göndermek için bir `RequestStream` ve yanıtları işlemeye yönelik bir `ResponseStream` sağlar.</span><span class="sxs-lookup"><span data-stu-id="da141-189">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server, and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="da141-190">İstek akışı, bazı WPF `ICommand` yöntemlerinden sembolleri eklemek ve kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da141-190">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="da141-191">Her işlem için `ActionMessage` nesnesi üzerinde ilgili alanı ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="da141-191">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> <span data-ttu-id="da141-192">Bir ileti üzerinde `oneof` alan değerinin ayarlanması, daha önce ayarlanmış olan tüm alanları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="da141-192">Setting a `oneof` field's value on a message automatically clears any fields that have been previously set.</span></span>

<span data-ttu-id="da141-193">Yanıt akışı `async` bir yöntemde işlenir ve döndürdüğü `Task` pencere kapatıldığında atılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="da141-193">The stream of responses is handled in an `async` method, and the `Task` it returns is held to be disposed when the window is closed.</span></span>

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-clean-up"></a><span data-ttu-id="da141-194">İstemci Temizleme</span><span class="sxs-lookup"><span data-stu-id="da141-194">Client clean-up</span></span>

<span data-ttu-id="da141-195">Pencere kapatıldığında ve `MainWindowViewModel` atıldığı zaman (`MainWindow` `Closed` olayından), `AsyncDuplexStreamingCall` nesnesini düzgün bir şekilde elden çıkardığınızdan önerilir.</span><span class="sxs-lookup"><span data-stu-id="da141-195">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), it's recommended that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="da141-196">Özellikle, sunucu üzerindeki akışı düzgün bir şekilde kapatmak için `RequestStream` `CompleteAsync` yöntemi çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da141-196">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="da141-197">Aşağıdaki örnek, örnek görünüm modelinden `DisposeAsync` yöntemini gösterir:</span><span class="sxs-lookup"><span data-stu-id="da141-197">The following example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

<span data-ttu-id="da141-198">İstek akışlarını kapatmak, sunucunun kendi kaynaklarını zamanında elden atmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="da141-198">Closing request streams enables the server to dispose of its own resources in a timely manner.</span></span> <span data-ttu-id="da141-199">Bu, hizmetlerin verimliliğini ve ölçeklenebilirliğini geliştirir ve özel durumları engeller.</span><span class="sxs-lookup"><span data-stu-id="da141-199">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="da141-200">[Önceki](migrate-request-reply.md)
>[İleri](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="da141-200">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
