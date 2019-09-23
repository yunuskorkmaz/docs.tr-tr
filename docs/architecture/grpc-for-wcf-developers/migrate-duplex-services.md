---
title: WCF geliştiricileri için WCF çift yönlü hizmetlerini gRPC-gRPC 'ye geçirme
description: Çeşitli WCF çift yönlü hizmetini gRPC akış Hizmetleri 'ne geçirmeyi öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 06ac784a31df43fd270f7ef0475bcdc282efad8f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184339"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>WCF çift yönlü hizmetlerini gRPC 'ye geçirme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Artık temel kavramlar hazır olduğuna göre, bu bölüm daha karmaşık *akış* GRPC hizmetlerine bakacaktır.

Windows Communication Foundation (WCF) içinde çift yönlü hizmetler kullanmanın birden çok yolu vardır. Bazı hizmetler istemci tarafından başlatılır ve sonra sunucudan veri akışı yapılır. Diğer tam çift yönlü hizmetler, WCF belgelerinden klasik "Hesaplayıcı" örneği gibi devam eden iki yönlü iletişim içerebilir. Bu bölümde, iki olası WCF "hisse senedi bandı" uygulaması ele alınır ve bu uygulamalar gRPC 'ye geçirilir: bir sunucu akış RPC ve diğeri çift yönlü bir akış RPC kullanarak.

## <a name="server-streaming-rpc"></a>Sunucu akış RPC

[Örnek SIMPLESTOCKTICKER WCF çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, istemcinin bir hisse senedi sembolleri listesi ile bağlantıyı başlattığı bir çift yönlü hizmet vardır ve sunucu, güncelleştirmeleri bu şekilde göndermek için *geri çağırma arabirimini* kullanır kullanılabilir hale gelir. İstemci, sunucudan yapılan çağrılara yanıt vermek için bu arabirimi uygular.

### <a name="the-wcf-solution"></a>WCF çözümü

WCF çözümü, .NET Framework 4. x konsol uygulamasında şirket içinde barındırılan bir NetTCP sunucusu olarak uygulanır.

#### <a name="the-servicecontract"></a>ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

Hizmetin, verileri istemciye gerçek zamanlı olarak göndermek için geri çağırma arabirimini `ISimpleStockTickerCallback` kullanacağı için, dönüş türü olmayan tek bir yöntemi vardır.

#### <a name="the-callback-interface"></a>Geri çağırma arabirimi

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

Bu arabirimlerin uygulamaları, test verileri sağlamak için sık yapılan dış bağımlılıklarla birlikte çözümde bulunabilir.

### <a name="grpc-streaming"></a>gRPC akışı

Gerçek zamanlı verileri işlemenin gRPC yolu farklıdır. İstemciden sunucuya çağrı, zaman uyumsuz olarak gelen iletiler için izlenebilecek kalıcı bir akış oluşturabilir. Farklılık olsa da, akışlar bu verilerle ilgilenmenin daha sezgisel bir yolu olabilir ve LINQ, reaktif akışlar, işlevsel programlama vb. üzerinde vurgu ile modern programlama ile daha ilgili olabilir.

Hizmet tanımında iki ileti gerekir: istek için bir tane ve akış için bir tane. Hizmet, `StockTickerUpdate` `return` bildiriminde `stream` anahtar sözcüğünü kullanarak iletinin bir akışını döndürür. Fiyat değiştirme süresini tam olarak göstermek için `Timestamp` güncelleştirmeye bir eklemeniz önerilir.

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker. proto

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
  int32 priceCents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a>SimpleStockTicker uygulama

`TraderSys.StockMarket` Sınıf kitaplığındaki üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte `StockPriceSubscriber` öğesini yeniden kullanın. En iyi uygulamaları daha iyi izlemek için, `Factory` örnek oluşturmak üzere bir tür ekleyin ve ASP.NET Core bağımlılık `IStockPriceSubscriberFactory` ekleme hizmetleri ile kaydedin.

#### <a name="the-factory-implementation"></a>Fabrika uygulama

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

#### <a name="registering-the-factory"></a>Fabrikası kaydetme

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

Şimdi, bu sınıf gRPC StockTicker hizmetini uygulamak için kullanılabilir.

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

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

Gördüğünüz gibi, `.proto` dosyadaki bildirim "döndürülen" yöntemini bir `StockTickerUpdate` ileti akışı olarak diyor olsa da, aslında Vanilla `Task`döndürüyor. Akışı oluşturma işi, üretilen kod ve `IServerStreamWriter<StockTickerUpdate>` yanıt akışını sağlayan GRPC çalışma zamanı kitaplıkları tarafından işlenir.

Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır. Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.

Hizmet, `CancellationToken` `ServerCallContext`kaynağından ' i kullanarak bağlantıyı ne zaman kapattığını söyleyebilir. Basit bir statik yöntem `AwaitCancellation`, belirteç iptal edildiğinde tamamlanmış bir görev oluşturmak için kullanılır.

Yönteminde, bir `StockPriceSubscriber` alın ve yanıt akışına yazan bir olay işleyicisi ekleyin. `Subscribe` Daha sonra, `subscriber` kapalı akışa veri yazmaya çalışmasını engellemek için hemen elden ayrılmadan önce bağlantının kapatılmasını bekleyin.

Yöntemi, akışa ileti `try` yazılırken oluşabilecek hataları işlemek için bir / `catch` bloğa sahiptir. `WriteUpdateAsync` Bu, ağ üzerinden yapılan kalıcı bağlantılarda önemli bir konudur. Bu, kasıtlı olarak veya bir yerde bir hata nedeniyle herhangi bir milisaniyeye ayrılabilir.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Bir istemci uygulamasından StockTickerService kullanma

`.proto` Dosyadan paylaşılabilir bir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin. Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET Core 3,0 konsol uygulaması vardır.

#### <a name="example-programcs"></a>Örnek Program.cs

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

Bu durumda, `Subscribe` oluşturulan istemcideki yöntemi zaman uyumsuz değildir. Akış oluşturulur ve hemen kullanılabilir çünkü `MoveNext` yöntemi zaman uyumsuz olduğundan ve ilk kez çağrıldığında bağlantı etkin olana kadar tamamlanmaz.

Akış zaman uyumsuz `DisplayAsync` bir metoda geçirilir; uygulama daha sonra kullanıcının bir tuşa basmasını bekler, sonra `DisplayAsync` yöntemi iptal eder ve çıkmadan önce görevin tamamlanmasını bekler.

> [!NOTE]
> Bu kod, "bildirimi kullanma C# " söz dizimini kullanarak akışı atma, `Main` yöntemi çıkış olduğunda kanalı. Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.

#### <a name="consume-the-stream"></a>Akışı tüketme

WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullandı. gRPC akışları farklı şekilde çalışır. İstemci döndürülen akışın üzerinde yinelenir ve bir `IEnumerable`yerel yöntemden döndürüldüğünden olduğu gibi iletileri işler.

Türü bir `IEnumerator<T>`çok gibi çalışır: daha fazla veri ve `MoveNext` en son değeri döndüren bir `Current` özellik olan sürece true döndürecek bir yöntem vardır. `IAsyncStreamReader<T>` Tek fark, `MoveNext` yöntemin yalnızca bir `bool`yerine bir `Task<bool>` döndürmektedir. Genişletme yöntemi, akışı yeni C# `IAsyncEnumerable` `await foreach` sözdizimiyle kullanılabilecek standart bir 8 ' de sarmalar. `ReadAllAsync`

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
> Bu bölümün sonundaki [istemci kitaplıkları](client-libraries.md#iobservable) bölümünde, bir genişletme yöntemi ve sınıflarının `IAsyncStreamReader<T>` nasıl ekleneceğini, reaktif programlama düzenlerini kullanan geliştiriciler için bir `IObservable<T>` şekilde nasıl ekleyeceğiniz gösterilmektedir.

Ayrıca, ağ arızası nedeniyle özel durumları yakalamak ve kodun döngüyü bölmek için bir <xref:System.OperationCanceledException> <xref:System.Threading.CancellationToken> kullandığından, kaçınılmaz şekilde oluşturulması gerektiği konusunda dikkatli olun. Türü, GRPC çalışma zamanı hataları hakkında, `StatusCode`dahil olmak üzere çok yararlı bilgiler içerir. `RpcException` Daha fazla bilgi için bkz. [Bölüm 4 ' te *hata işleme*](error-handling.md)

## <a name="bidirectional-streaming"></a>Çift yönlü akış

WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar. Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır. Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir. Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.

`IFullStockTickerService` Arabirim üç yöntem sağlar:

- `Subscribe`bağlantıyı başlatır.
- `AddSymbol`izlemek için bir hisse senedi simgesi ekler.
- `RemoveSymbol`izlenen listeden bir sembol kaldırır.

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

Geri çağırma arabirimi aynı kalır.

Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir. Ekleme ve kaldırma işlemini uygulamak için birden çok yöntem kullanılması mümkün değildir, ancak `Any` [Bölüm 3](protobuf-any-oneof.md)' te kapsanan tür veya `oneof` anahtar sözcüğü kullanılarak tek bir akışta birden fazla ileti türü geçirilebilir.

Kabul edilebilir `oneof` olan belirli türde bir durum için daha iyi bir yoldur. Ya da'`ActionMessage` i tutabilecek bir kullanın. `RemoveSymbolRequest` `AddSymbolRequest`

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

`ActionMessage` İleti akışını alan bir çift yönlü akış hizmeti bildirin.

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Bu hizmetin uygulanması, önceki örneğe benzerdir `Subscribe` , yöntemin `IAsyncStreamReader<ActionMessage>`ilk parametresi, `Add` ve `Remove` isteklerini işlemek için kullanılabilecek.

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

GRPC 'nin oluşturduğu `Add` `Remove` `null` sınıf, ve özelliklerinden yalnızca birinin ayarlanamadığına ve hangi bir tür ileti kullanıldığını bulmanın geçerli bir yolu olduğunu garanti eder, ancak daha iyi bir yoldur `ActionMessage` . Kod oluşturma, aşağıdaki gibi görünen `enum ActionOneOfCase` `ActionMessage` sınıfında de oluşturulur:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

Nesne üzerindeki özelliği `ActionCase` , hangi alanın ayarlandığını belirleyen bir `switch` ifadesiyle birlikte kullanılabilir. `ActionMessage`

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
> `default` Bilinmeyen `switch` birdeğerlekarşılaşılırsa,bildiriminde`ActionOneOfCase` bir uyarıyı günlüğe kaydeden bir durum vardır. Bu, bir istemcinin daha fazla eylem ekleyen `.proto` dosyanın daha yeni bir sürümünü kullandığını gösteren yararlı olabilir. Bunun nedeni, bilinen alanlar üzerinde için `switch` `null` test kullanmaktan daha iyi bir nedendir.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Bir istemci uygulamasından FullStockTickerService kullanma

Bu daha karmaşık istemcinin kullanımını göstermek için basit bir .NET Core 3,0 WPF uygulaması vardır. Tam uygulama [GitHub 'da](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)bulunabilir.

İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, bağımlılık ekleme işleminden `FullStockTicker.FullStockTickerClient` türün bir örneğini alır.

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

`client.Subscribe()` Yöntemi tarafından döndürülen nesne artık GRPC kitaplık türünün `AsyncDuplexStreamingCall<TRequest, TResponse>`bir örneğidir. Bu, sunucuya istek `ResponseStream` göndermek `RequestStream` için ve yanıtlarını işlemek için bir sağlar.

İstek akışı, bazı WPF `ICommand` yöntemlerinden sembolleri eklemek ve kaldırmak için kullanılır. Her işlem için, bir `ActionMessage` nesne üzerinde ilgili alanı ayarlayın:

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
> Bir ileti `oneof` üzerinde bir alanın değerini ayarlamak, daha önce ayarlanmış olan tüm alanları otomatik olarak temizler.

Yanıt akışı bir `async` yöntemde işlenir `Task` ve pencere kapatıldığında bu geri dönüş atılmaktadır.

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

### <a name="client-clean-up"></a>İstemci Temizleme

Pencere `MainWindowViewModel` kapalıyken ve, bırakıldığında ( `Closed` olayından `MainWindow`), `AsyncDuplexStreamingCall` nesneyi düzgün bir şekilde elden çıkardığınızdan önerilir. Özellikle `CompleteAsync` ,`RequestStream` üzerindeki yönteminin, akışı düzgün bir şekilde kapatmak için çağrılması gerekir. Aşağıdaki örnek, örnek görünüm `DisposeAsync` modelinden yöntemi gösterir:

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

İstek akışlarını kapatmak, sunucunun kendi kaynaklarını zamanında elden atmalarını sağlar. Bu, hizmetlerin verimliliğini ve ölçeklenebilirliğini geliştirir ve özel durumları engeller.

>[!div class="step-by-step"]
>[Önceki](migrate-request-reply.md)
>[İleri](streaming-versus-repeated.md)
