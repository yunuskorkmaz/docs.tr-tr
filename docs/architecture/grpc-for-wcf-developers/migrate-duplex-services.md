---
title: WCF geliştiricileri için WCF çift yönlü hizmetlerini gRPC-gRPC 'ye geçirme
description: Çeşitli WCF çift yönlü hizmetini gRPC akış Hizmetleri 'ne geçirmeyi öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 525dc3006c45f773242ab08b112dba72087a2e3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834514"
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

Hizmetin, verileri istemciye gerçek zamanlı olarak göndermek için `ISimpleStockTickerCallback` geri çağırma arabirimini kullanacağı için, dönüş türü olmayan tek bir yöntemi vardır.

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

Hizmet tanımında iki ileti gerekir: istek için bir tane ve akış için bir tane. Hizmet, `return` bildiriminde `stream` anahtar sözcüğünü kullanarak `StockTickerUpdate` iletisinin bir akışını döndürür. Fiyatın değiştiği zamanı tam olarak göstermek için güncelleştirmeye `Timestamp` eklemeniz önerilir.

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

@No__t-1 Sınıf kitaplığındaki üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte `StockPriceSubscriber` ' yı yeniden kullanın. En iyi uygulamaları daha iyi izlemek için, örnek oluşturmak için bir `Factory` türü ekleyin ve `IStockPriceSubscriberFactory` ' i ASP.NET Core bağımlılık ekleme hizmetleri ile kaydedin.

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

Gördüğünüz gibi, `.proto` dosyasındaki bildirim, "döndürülen" bir `StockTickerUpdate` ileti akışını "döndüren", aslında bir Vanilla `Task` döndürüyor. Akışı oluşturma işi oluşturulan kod ve gRPC çalışma zamanı kitaplıkları tarafından işlenir ve bu, `IServerStreamWriter<StockTickerUpdate>` yanıt akışı kullanıma sunar.

Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır. Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.

Hizmet, `ServerCallContext` ' den `CancellationToken` kullanarak istemcinin bağlantıyı kapattığını söyleyebilir. @No__t-0 olan basit bir statik yöntem, belirteç iptal edildiğinde tamamlanmış bir görevi oluşturmak için kullanılır.

@No__t-0 yönteminde, bir `StockPriceSubscriber` alın ve yanıt akışına yazan bir olay işleyicisi ekleyin. Sonra, `subscriber` ' ı hemen elden bırakmadan önce, kapalı akışa veri yazmaya çalışmasını engellemek için bağlantının kapatılmasını bekleyin.

@No__t-0 yönteminde, akışa ileti yazılırken oluşabilecek hataları işlemek için bir `try` @ no__t-2 @ no__t-3 bloğu vardır. Bu, ağ üzerinden yapılan kalıcı bağlantılarda önemli bir konudur. Bu, kasıtlı olarak veya bir yerde bir hata nedeniyle herhangi bir milisaniyeye ayrılabilir.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Bir istemci uygulamasından StockTickerService kullanma

@No__t-0 dosyasından paylaşılabilir bir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin. Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET Core 3,0 konsol uygulaması vardır.

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

Bu durumda, oluşturulan istemcideki `Subscribe` yöntemi zaman uyumsuz değildir. Akış oluşturulur ve hemen kullanılabilir çünkü `MoveNext` yöntemi zaman uyumsuzdur ve ilk çağrılışında bağlantı etkin olana kadar tamamlanmaz.

Akış zaman uyumsuz bir `DisplayAsync` yöntemine geçirilir; uygulama daha sonra kullanıcının bir tuşa basmasını bekler, sonra `DisplayAsync` metodunu iptal eder ve çıkmadan önce görevin tamamlanmasını bekler.

> [!NOTE]
> Bu kod, `Main` C# yöntemi çıktığında akışı ve kanalı atmak için yeni 8 "using bildirimi" sözdizimini kullanıyor. Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.

#### <a name="consume-the-stream"></a>Akışı tüketme

WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullandı. gRPC akışları farklı şekilde çalışır. İstemci, döndürülen akışın üzerinde yinelenir ve bir `IEnumerable` döndüren yerel bir yöntemden döndürüldüğünden olduğu gibi iletileri işler.

@No__t-0 türü bir `IEnumerator<T>` gibi çalışır: daha fazla veri ve en son değeri döndüren bir `Current` özelliği olan sürece true döndürecek bir `MoveNext` yöntemi vardır. Tek fark, `MoveNext` yönteminin yalnızca bir `bool` yerine bir `Task<bool>` döndürdüğünden oluşur. @No__t-0 genişletme yöntemi, akışı yeni `await foreach` sözdizimiyle C# kullanılabilecek standart bir 8 `IAsyncEnumerable` ' de sarmalar.

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
> Bu bölümün sonundaki [istemci kitaplıklarında](client-libraries.md#iobservable) bulunan bölümü, reaktif programlama düzenlerini kullanan geliştiriciler için `IAsyncStreamReader<T>` ' i bir `IObservable<T>` ' ye kaydırmak üzere bir genişletme yöntemi ve sınıfları ekleme bölümüne bakar.

Ayrıca, ağ hatası olasılığı nedeniyle özel durumların yanı sıra, kodun döngüyü bölmek için bir <xref:System.Threading.CancellationToken> kullandığından kaçınılmaz <xref:System.OperationCanceledException> olduğundan emin olun. @No__t-0 türü, `StatusCode` dahil olmak üzere gRPC çalışma zamanı hataları hakkında çok sayıda yararlı bilgi içerir. Daha fazla bilgi için, bkz. [Bölüm 4 ' te *hata işleme* ](error-handling.md).

## <a name="bidirectional-streaming"></a>Çift yönlü akış

WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar. Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır. Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir. Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.

@No__t-0 arabirimi üç yöntem sağlar:

- `Subscribe` bağlantıyı başlatır.
- `AddSymbol`, izlemek için bir hisse senedi simgesi ekler.
- `RemoveSymbol` izlenen listeden bir sembol kaldırır.

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

Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir. Ekleme ve kaldırma işlemi uygulamak için birden çok yöntem kullanılması mümkün değildir, ancak [Bölüm 3](protobuf-any-oneof.md)' te kapsanan `Any` tür veya `oneof` anahtar sözcüğü kullanılarak tek bir akışa birden fazla ileti türü geçirilebilir.

Kabul edilebilir bir tür kümesi olduğunda, `oneof` ' ı daha iyi bir yoldur. Bir `AddSymbolRequest` veya `RemoveSymbolRequest` tutabilecek `ActionMessage` kullanın.

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

@No__t-0 iletilerinin akışını alan, iki yönlü bir akış hizmeti bildirin.

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Bu hizmetin uygulanması, `Subscribe` yönteminin ilk parametresi dışında, `Add` ve `Remove` isteklerini işlemek için kullanılabilen bir `IAsyncStreamReader<ActionMessage>` olduğunda, önceki örneğe benzer.

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

GRPC 'nin oluşturduğu `ActionMessage` sınıfı, `Add` ve `Remove` özelliklerinden yalnızca birinin ayarlanamadığına ve `null` ' ün ne tür bir ileti kullanıldığını bulmanın geçerli bir yoludur, ancak daha iyi bir yoldur. Kod oluşturma Ayrıca, aşağıdaki gibi görünen `ActionMessage` sınıfında `enum ActionOneOfCase` olarak oluşturulur:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

@No__t-1 nesnesindeki `ActionCase` özelliği, hangi alanın ayarlandığını belirleyen bir `switch` ifadesiyle birlikte kullanılabilir.

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
> @No__t-0 ifadesinde, bilinmeyen bir @no__t 2 değeriyle karşılaşılırsa uyarı kaydeden bir `default` durumu vardır. Bu, bir istemcinin daha fazla eylem ekleyen `.proto` dosyasının daha yeni bir sürümünü kullandığını gösteren yararlı olabilir. Bunun nedeni, `switch` kullanmanın bilinen alanlar üzerinde `null` ' i sınamadan daha iyi bir nedenidir.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Bir istemci uygulamasından FullStockTickerService kullanma

Bu daha karmaşık istemcinin kullanımını göstermek için basit bir .NET Core 3,0 WPF uygulaması vardır. Tam uygulama [GitHub 'da](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)bulunabilir.

İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, bağımlılık ekleme işleminden `FullStockTicker.FullStockTickerClient` türünün bir örneğini alır.

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

@No__t-0 yöntemi tarafından döndürülen nesne artık gRPC kitaplığı türünün bir örneğidir `AsyncDuplexStreamingCall<TRequest, TResponse>`, bu da sunucuya istek göndermek için bir `RequestStream` ve yanıtları işlemek için bir `ResponseStream` sağlar.

İstek akışı, sembolleri eklemek ve kaldırmak için bazı WPF `ICommand` yöntemlerinden kullanılır. Her işlem için `ActionMessage` nesnesi üzerinde ilgili alanı ayarlayın:

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
> @No__t-0 alanının değeri bir ileti üzerinde ayarlandığında, daha önce ayarlanmış olan tüm alanları otomatik olarak temizler.

Yanıt akışı `async` yönteminde işlenir ve döndürdüğü `Task`, pencere kapatıldığında atılmaktadır.

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

Pencere kapatıldığında ve `MainWindowViewModel` bırakıldığında (`MainWindow` ' nin `Closed` olayından), `AsyncDuplexStreamingCall` nesnesini düzgün bir şekilde elden çıkardığınızdan önerilir. Özellikle, sunucuda akışı düzgün bir şekilde kapatmak için, `RequestStream` üzerindeki `CompleteAsync` yöntemi çağrılmalıdır. Aşağıdaki örnek, örnek görünüm modelinden `DisposeAsync` yöntemini gösterir:

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
