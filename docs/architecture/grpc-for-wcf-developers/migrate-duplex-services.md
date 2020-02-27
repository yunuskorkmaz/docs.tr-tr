---
title: WCF geliştiricileri için WCF çift yönlü hizmetlerini gRPC-gRPC 'ye geçirme
description: Çeşitli WCF çift yönlü hizmetleri gRPC akış hizmetlerine geçirmeyi öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: 5737f02044ab9e4064f632164db764541a9c4d31
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628546"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="59b54-103">WCF çift yönlü hizmetlerini gRPC'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="59b54-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="59b54-104">Artık temel kavramlara sahip olduğunuza göre, bu bölümde daha karmaşık *akış* GRPC hizmetlerine bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="59b54-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="59b54-105">Windows Communication Foundation (WCF) içinde çift yönlü hizmetler kullanmanın birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="59b54-106">Bazı hizmetler istemci tarafından başlatılır ve sonra sunucudan veri akışı yapılır.</span><span class="sxs-lookup"><span data-stu-id="59b54-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="59b54-107">Diğer tam çift yönlü hizmetler, WCF belgelerindeki klasik Hesaplayıcı örneği gibi daha devam eden iki yönlü iletişim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="59b54-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="59b54-108">Bu bölümde, iki olası WCF stok şeridi uygulaması ele alınacaktır ve bunları gRPC 'ye geçirirsiniz: bir sunucu akış RPC ve çift yönlü bir akış RPC kullanan başka bir tane.</span><span class="sxs-lookup"><span data-stu-id="59b54-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="59b54-109">Sunucu akış RPC</span><span class="sxs-lookup"><span data-stu-id="59b54-109">Server streaming RPC</span></span>

<span data-ttu-id="59b54-110">[Örnek SIMPLESTOCKTICKER WCF çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, istemcinin bir hisse senedi sembolleri listesi ile bağlantıyı başlattığı bir çift yönlü hizmet vardır ve sunucu, kullanılabilir hale geldiğinde güncelleştirmeleri göndermek için *geri çağırma arabirimini* kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b54-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="59b54-111">İstemci, sunucudan yapılan çağrılara yanıt vermek için bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="59b54-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="59b54-112">WCF çözümü</span><span class="sxs-lookup"><span data-stu-id="59b54-112">The WCF solution</span></span>

<span data-ttu-id="59b54-113">WCF çözümü, .NET Framework 4 ' te kendi kendine barındırılan bir net. TCP sunucusu olarak uygulanır. *x* konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="59b54-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="59b54-114">Türünden</span><span class="sxs-lookup"><span data-stu-id="59b54-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="59b54-115">Hizmetin, verileri istemciye gerçek zamanlı olarak göndermek için `ISimpleStockTickerCallback` geri çağırma arabirimini kullandığından, dönüş türü olmayan tek bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="59b54-116">Geri çağırma arabirimi</span><span class="sxs-lookup"><span data-stu-id="59b54-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="59b54-117">Bu arabirimlerin uygulamalarını çözümde ve test verileri sağlamak için sık gönderilmiş dış bağımlılıklarla birlikte bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b54-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="59b54-118">gRPC akışı</span><span class="sxs-lookup"><span data-stu-id="59b54-118">gRPC streaming</span></span>

<span data-ttu-id="59b54-119">Gerçek zamanlı verileri işlemeye yönelik gRPC işlemi WCF işleminden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="59b54-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="59b54-120">İstemciden sunucuya çağrı, zaman uyumsuz olarak gelen iletiler için izlenebilecek kalıcı bir akış oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="59b54-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="59b54-121">Farklılık olsa da, akışlar bu verilerle ilgilenmenin daha sezgisel bir yolu olabilir ve LINQ, reaktif akışları, işlevsel programlama vb. ile daha kolay bir şekilde modern programlama ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="59b54-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="59b54-122">Hizmet tanımında iki ileti gerekir: bir istek ve akış için bir tane.</span><span class="sxs-lookup"><span data-stu-id="59b54-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="59b54-123">Hizmet, `return` bildiriminde `stream` anahtar sözcüğünü içeren `StockTickerUpdate` iletisinin bir akışını döndürür.</span><span class="sxs-lookup"><span data-stu-id="59b54-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="59b54-124">Fiyat değişikliğinin tam süresini göstermek için güncelleştirmeye bir `Timestamp` eklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="59b54-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="59b54-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="59b54-125">simple_stock_ticker.proto</span></span>

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

### <a name="implement-simplestockticker"></a><span data-ttu-id="59b54-126">SimpleStockTicker Uygula</span><span class="sxs-lookup"><span data-stu-id="59b54-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="59b54-127">`TraderSys.StockMarket` sınıf kitaplığından üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte `StockPriceSubscriber` kullanın.</span><span class="sxs-lookup"><span data-stu-id="59b54-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="59b54-128">En iyi uygulamaları daha iyi izlemek için, örnek oluşturmak üzere bir `Factory` türü ekleyin ve `IStockPriceSubscriberFactory` ASP.NET Core bağımlılık ekleme hizmetleri ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="59b54-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="59b54-129">Fabrika uygulama</span><span class="sxs-lookup"><span data-stu-id="59b54-129">The factory implementation</span></span>

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

#### <a name="register-the-factory"></a><span data-ttu-id="59b54-130">Fabrikası kaydetme</span><span class="sxs-lookup"><span data-stu-id="59b54-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="59b54-131">Bu sınıf artık gRPC `StockTickerService`uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59b54-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="59b54-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="59b54-132">StockTickerService.cs</span></span>

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
            // Handle any errors caused by broken connection, etc.
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

<span data-ttu-id="59b54-133">Gördüğünüz gibi, `.proto` dosyasındaki bildirim yöntemi bir `StockTickerUpdate` iletilerinin akışını döndürdüğünden, aslında bir `Task`döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="59b54-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="59b54-134">Akışı oluşturma işi oluşturulan kod ve gRPC çalışma zamanı kitaplıkları tarafından işlenir ve bu `IServerStreamWriter<StockTickerUpdate>` yanıt akışını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="59b54-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="59b54-135">Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b54-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="59b54-136">Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59b54-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="59b54-137">Hizmet, `ServerCallContext``CancellationToken` kullanarak istemcinin bağlantıyı kapattığını söyleyebilir.</span><span class="sxs-lookup"><span data-stu-id="59b54-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="59b54-138">Basit bir statik yöntem `AwaitCancellation`, belirteç iptal edildiğinde tamamlanan bir görev oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59b54-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="59b54-139">`Subscribe` yönteminde, bir `StockPriceSubscriber` alın ve yanıt akışına yazan bir olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="59b54-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="59b54-140">Daha sonra `subscriber`, kapalı akışa veri yazmaya çalışmasını engellemek için hemen elden alınmadan önce bağlantının kapatılmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="59b54-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="59b54-141">`WriteUpdateAsync` yönteminde bir ileti akışa yazıldığında oluşabilecek hataları işlemek için bir `try`/`catch` bloğu vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="59b54-142">Bu durum, her türlü milisaniyeye göre veya bir yerde bir hata nedeniyle kopmuş olan ağlar üzerinden kalıcı bağlantılarda önemli bir konudur.</span><span class="sxs-lookup"><span data-stu-id="59b54-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="59b54-143">İstemci uygulamasından StockTickerService kullanma</span><span class="sxs-lookup"><span data-stu-id="59b54-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="59b54-144">`.proto` dosyasından bir paylaşılabilir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="59b54-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="59b54-145">Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET Core 3,0 konsol uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="59b54-146">Örnek Program.cs</span><span class="sxs-lookup"><span data-stu-id="59b54-146">Example Program.cs</span></span>

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

<span data-ttu-id="59b54-147">Bu durumda, oluşturulan istemcideki `Subscribe` yöntemi zaman uyumsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="59b54-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="59b54-148">Akış oluşturulur ve hemen kullanılabilir çünkü `MoveNext` yöntemi zaman uyumsuzdur ve ilk çağrılışında bağlantı etkin olana kadar tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="59b54-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="59b54-149">Akış zaman uyumsuz bir `DisplayAsync` yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="59b54-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="59b54-150">Uygulama daha sonra kullanıcının bir tuşa basmasını bekler ve sonra `DisplayAsync` yöntemini iptal eder ve çıkmadan önce görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="59b54-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="59b54-151">Bu kod, `Main` yöntemi C# çıktığında akışı ve kanalı atmak için yeni 8 `using` bildirimi sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b54-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="59b54-152">Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.</span><span class="sxs-lookup"><span data-stu-id="59b54-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="59b54-153">Akışı tüketme</span><span class="sxs-lookup"><span data-stu-id="59b54-153">Consume the stream</span></span>

<span data-ttu-id="59b54-154">WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="59b54-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="59b54-155">gRPC akışları farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="59b54-155">gRPC streams work differently.</span></span> <span data-ttu-id="59b54-156">İstemci, bir `IEnumerable`döndüren yerel bir yöntemden döndürüldüğünden olduğu gibi döndürülen akışın üzerinde dolaşır ve iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="59b54-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="59b54-157">`IAsyncStreamReader<T>` türü `IEnumerator<T>`çok benzer.</span><span class="sxs-lookup"><span data-stu-id="59b54-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="59b54-158">Daha fazla veri ve en son değeri döndüren bir `Current` özelliği olan sürece true döndüren bir `MoveNext` yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="59b54-159">Tek fark, `MoveNext` yönteminin yalnızca bir `bool`yerine `Task<bool>` döndürdüğünden oluşur.</span><span class="sxs-lookup"><span data-stu-id="59b54-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="59b54-160">`ReadAllAsync` uzantısı yöntemi, akışı yeni `await foreach` sözdizimiyle kullanılabilecek standart C# bir 8 `IAsyncEnumerable` kaydırır.</span><span class="sxs-lookup"><span data-stu-id="59b54-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

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
> <span data-ttu-id="59b54-161">Reaktif programlama düzenlerini kullanan geliştiriciler için, bu bölümün sonundaki [istemci kitaplıklarında](client-libraries.md#iobservable) bulunan bölüm, bir `IObservable<T>``IAsyncStreamReader<T>` bir genişletme yönteminin ve sınıfların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59b54-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="59b54-162">Burada, ağ arızası nedeniyle özel durumları yakalamadığınızdan emin olun ve kod döngüyü bölmek için bir <xref:System.Threading.CancellationToken> kullandığından, kaçınılmaz <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="59b54-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="59b54-163">`RpcException` türü, gRPC çalışma zamanı hataları hakkında, `StatusCode`dahil olmak üzere çok yararlı bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="59b54-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="59b54-164">Daha fazla bilgi için, bkz. [Bölüm 4 ' te *hata işleme* ](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="59b54-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="59b54-165">Çift yönlü akış</span><span class="sxs-lookup"><span data-stu-id="59b54-165">Bidirectional streaming</span></span>

<span data-ttu-id="59b54-166">WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b54-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="59b54-167">Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır.</span><span class="sxs-lookup"><span data-stu-id="59b54-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="59b54-168">Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="59b54-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="59b54-169">Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.</span><span class="sxs-lookup"><span data-stu-id="59b54-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="59b54-170">`IFullStockTickerService` arabirimi üç yöntem sağlar:</span><span class="sxs-lookup"><span data-stu-id="59b54-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="59b54-171">`Subscribe` bağlantıyı başlatır.</span><span class="sxs-lookup"><span data-stu-id="59b54-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="59b54-172">`AddSymbol` izlemek için bir hisse senedi simgesi ekler.</span><span class="sxs-lookup"><span data-stu-id="59b54-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="59b54-173">`RemoveSymbol` izlenen listeden bir sembol kaldırır.</span><span class="sxs-lookup"><span data-stu-id="59b54-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

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

<span data-ttu-id="59b54-174">Geri çağırma arabirimi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="59b54-174">The callback interface remains the same.</span></span>

<span data-ttu-id="59b54-175">Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="59b54-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="59b54-176">Ekleme ve kaldırma işlemlerini uygulamak için birden çok yöntem kullanılması mümkün değildir ancak [Bölüm 3](protobuf-any-oneof.md)' te kapsanan `Any` türünü veya `oneof` anahtar sözcüğünü kullanarak tek bir akışta birden fazla ileti türü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b54-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="59b54-177">Kabul edilebilir olan belirli bir tür kümesinin olduğu durumlarda `oneof` daha iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="59b54-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="59b54-178">Bir `AddSymbolRequest` ya da `RemoveSymbolRequest`tutabilecek bir `ActionMessage` kullanın:</span><span class="sxs-lookup"><span data-stu-id="59b54-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

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

<span data-ttu-id="59b54-179">`ActionMessage` iletilerinin akışını alan bir çift yönlü akış hizmeti bildirin:</span><span class="sxs-lookup"><span data-stu-id="59b54-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="59b54-180">Bu hizmetin uygulanması, önceki örnekteki yönteme benzerdir, çünkü `Subscribe` yönteminin ilk parametresi, `Add` ve `Remove` isteklerini işlemek için kullanılabilen bir `IAsyncStreamReader<ActionMessage>`.</span><span class="sxs-lookup"><span data-stu-id="59b54-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

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
        // Handle any errors caused by broken connection, etc.
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

<span data-ttu-id="59b54-181">GRPC tarafından oluşturulan `ActionMessage` sınıfı, `Add` ve `Remove` özelliklerinden yalnızca birinin ayarlandığına güvence sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b54-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="59b54-182">Hangisinin `null` hangi türde bir ileti kullanıldığını bulmak için geçerli bir yoldur, ancak daha iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="59b54-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="59b54-183">Kod oluşturma Ayrıca, aşağıdaki gibi görünen `ActionMessage` sınıfında bir `enum ActionOneOfCase` oluşturmuştur:</span><span class="sxs-lookup"><span data-stu-id="59b54-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="59b54-184">`ActionMessage` nesnesindeki `ActionCase` özellik, hangi alanın ayarlandığını anlamak için bir `switch` ifadesiyle birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="59b54-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

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
> <span data-ttu-id="59b54-185">`switch` deyimin, bilinmeyen bir `ActionOneOfCase` değeriyle karşılaştığında uyarı kaydeden bir `default` durumu vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="59b54-186">Bu, bir istemcinin daha fazla eylem ekleyen `.proto` dosyasının daha yeni bir sürümünü kullandığını göstermek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b54-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="59b54-187">Bunun nedeni, `switch` kullanmanın bilinen alanlar üzerinde `null` test ediden daha iyi olmasının bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="59b54-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="59b54-188">İstemci uygulamasından FullStockTickerService kullanma</span><span class="sxs-lookup"><span data-stu-id="59b54-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="59b54-189">Bu daha karmaşık istemcinin kullanımını gösteren basit bir .NET Core 3,0 WPF uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="59b54-189">There's a simple .NET Core 3.0 WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="59b54-190">Tam uygulamayı [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)' da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b54-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="59b54-191">İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, bağımlılık ekleme işleminden `FullStockTicker.FullStockTickerClient` türünün bir örneğini alır:</span><span class="sxs-lookup"><span data-stu-id="59b54-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

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

<span data-ttu-id="59b54-192">`client.Subscribe()` yöntemi tarafından döndürülen nesne artık gRPC kitaplık türü `AsyncDuplexStreamingCall<TRequest, TResponse>`bir örneğidir. Bu, sunucuya istek göndermek için bir `RequestStream` ve yanıtları işlemeye yönelik bir `ResponseStream` sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b54-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="59b54-193">İstek akışı, bazı WPF `ICommand` yöntemlerinden sembolleri eklemek ve kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59b54-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="59b54-194">Her işlem için `ActionMessage` nesnesi üzerinde ilgili alanı ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="59b54-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

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
> <span data-ttu-id="59b54-195">Bir ileti üzerinde `oneof` alan değerinin ayarlanması, önceden ayarlanmış olan tüm alanları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="59b54-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="59b54-196">Yanıt akışı `async` bir yöntemde işlenir.</span><span class="sxs-lookup"><span data-stu-id="59b54-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="59b54-197">Geri döndürdüğü `Task` pencere kapatıldığında atılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="59b54-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

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

### <a name="client-cleanup"></a><span data-ttu-id="59b54-198">İstemci Temizleme</span><span class="sxs-lookup"><span data-stu-id="59b54-198">Client cleanup</span></span>

<span data-ttu-id="59b54-199">Pencere kapatıldığında ve `MainWindowViewModel` atıldığı zaman (`MainWindow``Closed` olayından), `AsyncDuplexStreamingCall` nesnesini düzgün bir şekilde elden çıkardığınızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="59b54-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="59b54-200">Özellikle, sunucu üzerindeki akışı düzgün bir şekilde kapatmak için `RequestStream` `CompleteAsync` yöntemi çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59b54-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="59b54-201">Bu örnekte örnek görünüm modelinden `DisposeAsync` yöntemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="59b54-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public async ValueTask DisposeAsync()
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

<span data-ttu-id="59b54-202">İstek akışlarını kapatmak, sunucunun kendi kaynaklarını zamanında elden atmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b54-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="59b54-203">Bu, hizmetlerin verimliliğini ve ölçeklenebilirliğini geliştirir ve özel durumları engeller.</span><span class="sxs-lookup"><span data-stu-id="59b54-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="59b54-204">[Önceki](migrate-request-reply.md)
>[İleri](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="59b54-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
