---
title: WCF geliştiricileri için WCF çift yönlü hizmetlerini gRPC-gRPC 'ye geçirme
description: Çeşitli WCF çift yönlü hizmetleri gRPC akış hizmetlerine geçirmeyi öğrenin.
ms.date: 12/15/2020
ms.openlocfilehash: 4741e5ad5c12fa358853381d4f2c286add14f8f5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938032"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="132fb-103">WCF çift yönlü hizmetlerini gRPC'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="132fb-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="132fb-104">Artık temel kavramlara sahip olduğunuza göre, bu bölümde daha karmaşık *akış* GRPC hizmetlerine bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="132fb-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="132fb-105">Windows Communication Foundation (WCF) içinde çift yönlü hizmetler kullanmanın birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="132fb-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="132fb-106">Bazı hizmetler istemci tarafından başlatılır ve sonra sunucudan veri akışı yapılır.</span><span class="sxs-lookup"><span data-stu-id="132fb-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="132fb-107">Diğer tam çift yönlü hizmetler, WCF belgelerindeki klasik Hesaplayıcı örneği gibi daha devam eden iki yönlü iletişim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="132fb-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="132fb-108">Bu bölümde, iki olası WCF stok şeridi uygulaması ele alınacaktır ve bunları gRPC 'ye geçirirsiniz: bir sunucu akış RPC ve çift yönlü bir akış RPC kullanan başka bir tane.</span><span class="sxs-lookup"><span data-stu-id="132fb-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="132fb-109">Sunucu akış RPC</span><span class="sxs-lookup"><span data-stu-id="132fb-109">Server streaming RPC</span></span>

<span data-ttu-id="132fb-110">[Örnek SIMPLESTOCKTICKER WCF çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, istemcinin bir hisse senedi sembolleri listesi ile bağlantıyı başlattığı bir çift yönlü hizmet vardır ve sunucu, kullanılabilir hale geldiğinde güncelleştirmeleri göndermek için *geri çağırma arabirimini* kullanır.</span><span class="sxs-lookup"><span data-stu-id="132fb-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="132fb-111">İstemci, sunucudan yapılan çağrılara yanıt vermek için bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="132fb-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="132fb-112">WCF çözümü</span><span class="sxs-lookup"><span data-stu-id="132fb-112">The WCF solution</span></span>

<span data-ttu-id="132fb-113">WCF çözümü, .NET Framework 4 ' te kendi kendine barındırılan bir net. TCP sunucusu olarak uygulanır. *x* konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="132fb-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="132fb-114">Türünden</span><span class="sxs-lookup"><span data-stu-id="132fb-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="132fb-115">Hizmetin, `ISimpleStockTickerCallback` verileri istemciye gerçek zamanlı olarak göndermek için geri çağırma arabirimini kullandığından, dönüş türü olmayan tek bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="132fb-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="132fb-116">Geri çağırma arabirimi</span><span class="sxs-lookup"><span data-stu-id="132fb-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="132fb-117">Bu arabirimlerin uygulamalarını çözümde ve test verileri sağlamak için sık gönderilmiş dış bağımlılıklarla birlikte bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="132fb-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="132fb-118">gRPC akışı</span><span class="sxs-lookup"><span data-stu-id="132fb-118">gRPC streaming</span></span>

<span data-ttu-id="132fb-119">Gerçek zamanlı verileri işlemeye yönelik gRPC işlemi WCF işleminden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="132fb-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="132fb-120">İstemciden sunucuya çağrı, zaman uyumsuz olarak gelen iletiler için izlenebilecek kalıcı bir akış oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="132fb-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="132fb-121">Farklılık olsa da, akışlar bu verilerle ilgilenmenin daha sezgisel bir yolu olabilir ve LINQ, reaktif akışları, işlevsel programlama vb. ile daha kolay bir şekilde modern programlama ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="132fb-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="132fb-122">Hizmet tanımında iki ileti gerekir: bir istek ve akış için bir tane.</span><span class="sxs-lookup"><span data-stu-id="132fb-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="132fb-123">Hizmet, `StockTickerUpdate` `stream` bildiriminde anahtar kelimesiyle iletinin bir akışını döndürür `return` .</span><span class="sxs-lookup"><span data-stu-id="132fb-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="132fb-124">`Timestamp`Fiyat değişikliğinin tam süresini göstermek için güncelleştirmeye bir eklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="132fb-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="132fb-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="132fb-125">simple_stock_ticker.proto</span></span>

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

### <a name="implement-simplestockticker"></a><span data-ttu-id="132fb-126">SimpleStockTicker Uygula</span><span class="sxs-lookup"><span data-stu-id="132fb-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="132fb-127">`StockPriceSubscriber` `TraderSys.StockMarket` Sınıf kitaplığındaki üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte öğesini yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fb-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="132fb-128">En iyi uygulamaları daha iyi izlemek için, `Factory` örnek oluşturmak üzere bir tür ekleyin ve `IStockPriceSubscriberFactory` ASP.NET Core bağımlılık ekleme hizmetleri ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="132fb-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="132fb-129">Fabrika uygulama</span><span class="sxs-lookup"><span data-stu-id="132fb-129">The factory implementation</span></span>

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

#### <a name="register-the-factory"></a><span data-ttu-id="132fb-130">Fabrikası kaydetme</span><span class="sxs-lookup"><span data-stu-id="132fb-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="132fb-131">Bu sınıf artık gRPC 'yi uygulamak için kullanılabilir `StockTickerService` .</span><span class="sxs-lookup"><span data-stu-id="132fb-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="132fb-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="132fb-132">StockTickerService.cs</span></span>

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

<span data-ttu-id="132fb-133">Gördüğünüz gibi, `.proto` dosyadaki bildirim yöntemi bir ileti akışı döndürse de, `StockTickerUpdate` aslında bir döndürür `Task` .</span><span class="sxs-lookup"><span data-stu-id="132fb-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="132fb-134">Akışı oluşturma işi, üretilen kod ve yanıt akışını sağlayan gRPC çalışma zamanı kitaplıkları tarafından işlenir `IServerStreamWriter<StockTickerUpdate>` .</span><span class="sxs-lookup"><span data-stu-id="132fb-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="132fb-135">Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="132fb-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="132fb-136">Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="132fb-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="132fb-137">Hizmet, kaynağından ' i kullanarak bağlantıyı ne zaman kapattığını söyleyebilir `CancellationToken` `ServerCallContext` .</span><span class="sxs-lookup"><span data-stu-id="132fb-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="132fb-138">Basit bir statik yöntem, `AwaitCancellation` belirteç iptal edildiğinde tamamlanmış bir görev oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="132fb-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="132fb-139">Yönteminde, `Subscribe` bir alın `StockPriceSubscriber` ve yanıt akışına yazan bir olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="132fb-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="132fb-140">Ardından, `subscriber` verilerin kapalı akışa veri yazmaya çalışmasını engellemek için hemen elden alınmadan önce bağlantının kapatılmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="132fb-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="132fb-141">`WriteUpdateAsync`Yöntemi, `try` / `catch` akışa bir ileti yazıldığında oluşabilecek hataları işlemek için bir bloğa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="132fb-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="132fb-142">Bu durum, her türlü milisaniyeye göre veya bir yerde bir hata nedeniyle kopmuş olan ağlar üzerinden kalıcı bağlantılarda önemli bir konudur.</span><span class="sxs-lookup"><span data-stu-id="132fb-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="132fb-143">İstemci uygulamasından StockTickerService kullanma</span><span class="sxs-lookup"><span data-stu-id="132fb-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="132fb-144">Dosyadan paylaşılabilir bir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin `.proto` .</span><span class="sxs-lookup"><span data-stu-id="132fb-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="132fb-145">Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET konsol uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="132fb-145">In the sample, there's a .NET console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="132fb-146">Örnek Program.cs</span><span class="sxs-lookup"><span data-stu-id="132fb-146">Example Program.cs</span></span>

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

<span data-ttu-id="132fb-147">Bu durumda, `Subscribe` oluşturulan istemcideki yöntemi zaman uyumsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="132fb-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="132fb-148">Akış oluşturulur ve hemen kullanılabilir çünkü `MoveNext` yöntemi zaman uyumsuz olduğundan ve ilk kez çağrıldığında bağlantı etkin olana kadar tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="132fb-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="132fb-149">Akış zaman uyumsuz bir `DisplayAsync` metoda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="132fb-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="132fb-150">Uygulama daha sonra kullanıcının bir tuşa basmasını bekler ve sonra yöntemi iptal eder `DisplayAsync` ve çıkmadan önce görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="132fb-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="132fb-151">Bu kod, `using` yöntemin çıkış sırasında akışa ve kanala atılırken yeni C# 8 bildirim söz dizimini kullanır `Main` .</span><span class="sxs-lookup"><span data-stu-id="132fb-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="132fb-152">Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.</span><span class="sxs-lookup"><span data-stu-id="132fb-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="132fb-153">Akışı tüketme</span><span class="sxs-lookup"><span data-stu-id="132fb-153">Consume the stream</span></span>

<span data-ttu-id="132fb-154">WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="132fb-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="132fb-155">gRPC akışları farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="132fb-155">gRPC streams work differently.</span></span> <span data-ttu-id="132fb-156">İstemci döndürülen akışın üzerinde yinelenir ve bir yerel yöntemden döndürüldüğünden olduğu gibi iletileri işler `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="132fb-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="132fb-157">`IAsyncStreamReader<T>`Türü bir çok benzer `IEnumerator<T>` .</span><span class="sxs-lookup"><span data-stu-id="132fb-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="132fb-158">`MoveNext`Daha fazla veri ve `Current` en son değeri döndüren bir özellik olan sürece true döndüren bir yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="132fb-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="132fb-159">Tek fark, `MoveNext` yöntemin `Task<bool>` yalnızca bir yerine bir döndürmektedir `bool` .</span><span class="sxs-lookup"><span data-stu-id="132fb-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="132fb-160">`ReadAllAsync`Genişletme yöntemi, akışı `IAsyncEnumerable` Yeni sözdizimi ile kullanılabilen standart bir C# 8 ' de sarmalar `await foreach` .</span><span class="sxs-lookup"><span data-stu-id="132fb-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

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
> <span data-ttu-id="132fb-161">Reaktif programlama düzenlerini kullanan geliştiriciler için, bu bölümün sonundaki [istemci kitaplıklarında](client-libraries.md#iobservable) bulunan bölüm, bir uzantı yönteminin ve bir sınıf içinde sarılacağı sınıfların nasıl ekleneceğini gösterir `IAsyncStreamReader<T>` `IObservable<T>` .</span><span class="sxs-lookup"><span data-stu-id="132fb-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="132fb-162">Yine de, ağ arızası nedeniyle özel durumları yakalamadığınızdan emin olun ve <xref:System.OperationCanceledException> kod döngüyü bölmek için bir kullandığından, bu durum, kaçınılmaz bir şekilde oluşturulur <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="132fb-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="132fb-163">`RpcException`Türü, gRPC çalışma zamanı hataları hakkında, dahil olmak üzere çok yararlı bilgiler içerir `StatusCode` .</span><span class="sxs-lookup"><span data-stu-id="132fb-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="132fb-164">Daha fazla bilgi için, bkz. [Bölüm 4 ' te *hata işleme*](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="132fb-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="132fb-165">Çift yönlü akış</span><span class="sxs-lookup"><span data-stu-id="132fb-165">Bidirectional streaming</span></span>

<span data-ttu-id="132fb-166">WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar.</span><span class="sxs-lookup"><span data-stu-id="132fb-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="132fb-167">Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır.</span><span class="sxs-lookup"><span data-stu-id="132fb-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="132fb-168">Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="132fb-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="132fb-169">Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.</span><span class="sxs-lookup"><span data-stu-id="132fb-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="132fb-170">`IFullStockTickerService`Arabirim üç yöntem sağlar:</span><span class="sxs-lookup"><span data-stu-id="132fb-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="132fb-171">`Subscribe` bağlantıyı başlatır.</span><span class="sxs-lookup"><span data-stu-id="132fb-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="132fb-172">`AddSymbol` izlemek için bir hisse senedi simgesi ekler.</span><span class="sxs-lookup"><span data-stu-id="132fb-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="132fb-173">`RemoveSymbol` izlenen listeden bir sembol kaldırır.</span><span class="sxs-lookup"><span data-stu-id="132fb-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

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

<span data-ttu-id="132fb-174">Geri çağırma arabirimi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="132fb-174">The callback interface remains the same.</span></span>

<span data-ttu-id="132fb-175">Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="132fb-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="132fb-176">Ekleme ve kaldırma işlemlerini uygulamak için birden çok yöntem kullanılması mümkün değildir ancak `Any` `oneof` [Bölüm 3](protobuf-any-oneof.md)' te kapsanan tür veya anahtar sözcüğünü kullanarak tek bir akışta birden fazla ileti türü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="132fb-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="132fb-177">Kabul edilebilir olan belirli bir tür kümesinin olması durumunda, `oneof` daha iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="132fb-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="132fb-178">`ActionMessage`Ya da ' i tutabilecek bir kullanın `AddSymbolRequest` `RemoveSymbolRequest` :</span><span class="sxs-lookup"><span data-stu-id="132fb-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

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

<span data-ttu-id="132fb-179">İleti akışını alan bir çift yönlü akış hizmeti bildirin `ActionMessage` :</span><span class="sxs-lookup"><span data-stu-id="132fb-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="132fb-180">Bu hizmetin uygulanması, yöntemin ilk parametresi dışında, `Subscribe` `IAsyncStreamReader<ActionMessage>` ve isteklerini işlemek için kullanılabilecek bir önceki örnekle benzerdir `Add` `Remove` :</span><span class="sxs-lookup"><span data-stu-id="132fb-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

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

<span data-ttu-id="132fb-181">`ActionMessage`GRPC tarafından oluşturulan sınıf, ve özelliklerinden yalnızca birinin ayarlanabilir olmasını garanti `Add` eder `Remove` .</span><span class="sxs-lookup"><span data-stu-id="132fb-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="132fb-182">Hangi `null` tür bir ileti kullanıldığını belirlemenin geçerli bir yolu olduğunu bulmak, ancak daha iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="132fb-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="132fb-183">Kod oluşturma, aşağıdaki `enum ActionOneOfCase` `ActionMessage` gibi görünen sınıfında de oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="132fb-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="132fb-184">`ActionCase`Nesne üzerindeki özelliği, `ActionMessage` `switch` hangi alanın ayarlandığını belirleyen bir ifadesiyle birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="132fb-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

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
> <span data-ttu-id="132fb-185">`switch`Bildiriminde, bilinmeyen bir `default` değer ile karşılaştığında uyarı kaydeden bir durum vardır `ActionOneOfCase` .</span><span class="sxs-lookup"><span data-stu-id="132fb-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="132fb-186">Bu, bir istemcinin `.proto` daha fazla eylem ekleyen dosyanın daha yeni bir sürümünü kullandığını göstermek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="132fb-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="132fb-187">Bunun nedeni, `switch` bilinen alanlar üzerinde için test kullanmaktan daha iyi bir nedendir `null` .</span><span class="sxs-lookup"><span data-stu-id="132fb-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="132fb-188">İstemci uygulamasından FullStockTickerService kullanma</span><span class="sxs-lookup"><span data-stu-id="132fb-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="132fb-189">Bu daha karmaşık istemcinin kullanımını gösteren basit bir .NET WPF uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="132fb-189">There's a simple .NET WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="132fb-190">Tam uygulamayı [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)' da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="132fb-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="132fb-191">İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, `FullStockTicker.FullStockTickerClient` bağımlılık ekleme işleminden türün bir örneğini alır:</span><span class="sxs-lookup"><span data-stu-id="132fb-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

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

<span data-ttu-id="132fb-192">Yöntemi tarafından döndürülen nesne `client.Subscribe()` artık gRPC kitaplık türünün bir örneğidir `AsyncDuplexStreamingCall<TRequest, TResponse>` . Bu, `RequestStream` sunucuya istek göndermek için ve yanıtlarını işlemek için bir sağlar `ResponseStream` .</span><span class="sxs-lookup"><span data-stu-id="132fb-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="132fb-193">İstek akışı, bazı WPF `ICommand` yöntemlerinden sembolleri eklemek ve kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="132fb-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="132fb-194">Her işlem için, bir nesne üzerinde ilgili alanı ayarlayın `ActionMessage` :</span><span class="sxs-lookup"><span data-stu-id="132fb-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

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
> <span data-ttu-id="132fb-195">Bir `oneof` ileti üzerinde bir alanın değerini ayarlamak, önceden ayarlanmış olan tüm alanları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="132fb-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="132fb-196">Yanıt akışı bir `async` yöntemde işlenir.</span><span class="sxs-lookup"><span data-stu-id="132fb-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="132fb-197">`Task`Bu geri dönüş, pencere kapatıldığında atılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="132fb-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

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

### <a name="client-cleanup"></a><span data-ttu-id="132fb-198">İstemci Temizleme</span><span class="sxs-lookup"><span data-stu-id="132fb-198">Client cleanup</span></span>

<span data-ttu-id="132fb-199">Pencere kapalıyken ve, bırakıldığında `MainWindowViewModel` ( `Closed` olayından `MainWindow` ), nesneyi doğru şekilde atmayı öneririz `AsyncDuplexStreamingCall` .</span><span class="sxs-lookup"><span data-stu-id="132fb-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="132fb-200">Özellikle, `CompleteAsync` üzerindeki yönteminin, `RequestStream` akışı düzgün bir şekilde kapatmak için çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="132fb-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="132fb-201">Bu örnek, `DisposeAsync` örnek görünüm modelinden yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="132fb-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

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

<span data-ttu-id="132fb-202">İstek akışlarını kapatmak, sunucunun kendi kaynaklarını zamanında elden atmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="132fb-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="132fb-203">Bu, hizmetlerin verimliliğini ve ölçeklenebilirliğini geliştirir ve özel durumları engeller.</span><span class="sxs-lookup"><span data-stu-id="132fb-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="132fb-204">[Önceki](migrate-request-reply.md) 
> [Sonraki](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="132fb-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
