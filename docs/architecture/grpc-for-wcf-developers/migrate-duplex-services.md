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
# <a name="migrate-wcf-duplex-services-to-grpc"></a>WCF çift yönlü hizmetlerini gRPC'ye geçirme

Artık temel kavramlara sahip olduğunuza göre, bu bölümde daha karmaşık *akış* GRPC hizmetlerine bakacaksınız.

Windows Communication Foundation (WCF) içinde çift yönlü hizmetler kullanmanın birden çok yolu vardır. Bazı hizmetler istemci tarafından başlatılır ve sonra sunucudan veri akışı yapılır. Diğer tam çift yönlü hizmetler, WCF belgelerindeki klasik Hesaplayıcı örneği gibi daha devam eden iki yönlü iletişim içerebilir. Bu bölümde, iki olası WCF stok şeridi uygulaması ele alınacaktır ve bunları gRPC 'ye geçirirsiniz: bir sunucu akış RPC ve çift yönlü bir akış RPC kullanan başka bir tane.

## <a name="server-streaming-rpc"></a>Sunucu akış RPC

[Örnek SIMPLESTOCKTICKER WCF çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, istemcinin bir hisse senedi sembolleri listesi ile bağlantıyı başlattığı bir çift yönlü hizmet vardır ve sunucu, kullanılabilir hale geldiğinde güncelleştirmeleri göndermek için *geri çağırma arabirimini* kullanır. İstemci, sunucudan yapılan çağrılara yanıt vermek için bu arabirimi uygular.

### <a name="the-wcf-solution"></a>WCF çözümü

WCF çözümü, .NET Framework 4 ' te kendi kendine barındırılan bir net. TCP sunucusu olarak uygulanır. *x* konsol uygulaması.

#### <a name="servicecontract"></a>Türünden

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

Hizmetin, verileri istemciye gerçek zamanlı olarak göndermek için `ISimpleStockTickerCallback` geri çağırma arabirimini kullandığından, dönüş türü olmayan tek bir yöntemi vardır.

#### <a name="the-callback-interface"></a>Geri çağırma arabirimi

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

Bu arabirimlerin uygulamalarını çözümde ve test verileri sağlamak için sık gönderilmiş dış bağımlılıklarla birlikte bulabilirsiniz.

### <a name="grpc-streaming"></a>gRPC akışı

Gerçek zamanlı verileri işlemeye yönelik gRPC işlemi WCF işleminden farklıdır. İstemciden sunucuya çağrı, zaman uyumsuz olarak gelen iletiler için izlenebilecek kalıcı bir akış oluşturabilir. Farklılık olsa da, akışlar bu verilerle ilgilenmenin daha sezgisel bir yolu olabilir ve LINQ, reaktif akışları, işlevsel programlama vb. ile daha kolay bir şekilde modern programlama ile ilgilidir.

Hizmet tanımında iki ileti gerekir: bir istek ve akış için bir tane. Hizmet, `return` bildiriminde `stream` anahtar sözcüğünü içeren `StockTickerUpdate` iletisinin bir akışını döndürür. Fiyat değişikliğinin tam süresini göstermek için güncelleştirmeye bir `Timestamp` eklemenizi öneririz.

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
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a>SimpleStockTicker Uygula

`TraderSys.StockMarket` sınıf kitaplığından üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte `StockPriceSubscriber` kullanın. En iyi uygulamaları daha iyi izlemek için, örnek oluşturmak üzere bir `Factory` türü ekleyin ve `IStockPriceSubscriberFactory` ASP.NET Core bağımlılık ekleme hizmetleri ile kaydedin.

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

#### <a name="register-the-factory"></a>Fabrikası kaydetme

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

Bu sınıf artık gRPC `StockTickerService`uygulamak için kullanılabilir.

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

Gördüğünüz gibi, `.proto` dosyasındaki bildirim yöntemi bir `StockTickerUpdate` iletilerinin akışını döndürdüğünden, aslında bir `Task`döndürüyor. Akışı oluşturma işi oluşturulan kod ve gRPC çalışma zamanı kitaplıkları tarafından işlenir ve bu `IServerStreamWriter<StockTickerUpdate>` yanıt akışını kullanıma sunar.

Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır. Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.

Hizmet, `ServerCallContext``CancellationToken` kullanarak istemcinin bağlantıyı kapattığını söyleyebilir. Basit bir statik yöntem `AwaitCancellation`, belirteç iptal edildiğinde tamamlanan bir görev oluşturmak için kullanılır.

`Subscribe` yönteminde, bir `StockPriceSubscriber` alın ve yanıt akışına yazan bir olay işleyicisi ekleyin. Daha sonra `subscriber`, kapalı akışa veri yazmaya çalışmasını engellemek için hemen elden alınmadan önce bağlantının kapatılmasını bekleyin.

`WriteUpdateAsync` yönteminde bir ileti akışa yazıldığında oluşabilecek hataları işlemek için bir `try`/`catch` bloğu vardır. Bu durum, her türlü milisaniyeye göre veya bir yerde bir hata nedeniyle kopmuş olan ağlar üzerinden kalıcı bağlantılarda önemli bir konudur.

### <a name="use-stocktickerservice-from-a-client-application"></a>İstemci uygulamasından StockTickerService kullanma

`.proto` dosyasından bir paylaşılabilir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin. Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET Core 3,0 konsol uygulaması vardır.

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

Akış zaman uyumsuz bir `DisplayAsync` yöntemine geçirilir. Uygulama daha sonra kullanıcının bir tuşa basmasını bekler ve sonra `DisplayAsync` yöntemini iptal eder ve çıkmadan önce görevin tamamlanmasını bekler.

> [!NOTE]
> Bu kod, `Main` yöntemi C# çıktığında akışı ve kanalı atmak için yeni 8 `using` bildirimi sözdizimini kullanır. Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.

#### <a name="consume-the-stream"></a>Akışı tüketme

WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullanır. gRPC akışları farklı şekilde çalışır. İstemci, bir `IEnumerable`döndüren yerel bir yöntemden döndürüldüğünden olduğu gibi döndürülen akışın üzerinde dolaşır ve iletileri işler.

`IAsyncStreamReader<T>` türü `IEnumerator<T>`çok benzer. Daha fazla veri ve en son değeri döndüren bir `Current` özelliği olan sürece true döndüren bir `MoveNext` yöntemi vardır. Tek fark, `MoveNext` yönteminin yalnızca bir `bool`yerine `Task<bool>` döndürdüğünden oluşur. `ReadAllAsync` uzantısı yöntemi, akışı yeni `await foreach` sözdizimiyle kullanılabilecek standart C# bir 8 `IAsyncEnumerable` kaydırır.

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
> Reaktif programlama düzenlerini kullanan geliştiriciler için, bu bölümün sonundaki [istemci kitaplıklarında](client-libraries.md#iobservable) bulunan bölüm, bir `IObservable<T>``IAsyncStreamReader<T>` bir genişletme yönteminin ve sınıfların nasıl ekleneceğini gösterir.

Burada, ağ arızası nedeniyle özel durumları yakalamadığınızdan emin olun ve kod döngüyü bölmek için bir <xref:System.Threading.CancellationToken> kullandığından, kaçınılmaz <xref:System.OperationCanceledException>. `RpcException` türü, gRPC çalışma zamanı hataları hakkında, `StatusCode`dahil olmak üzere çok yararlı bilgiler içerir. Daha fazla bilgi için, bkz. [Bölüm 4 ' te *hata işleme* ](error-handling.md).

## <a name="bidirectional-streaming"></a>Çift yönlü akış

WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar. Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır. Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir. Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.

`IFullStockTickerService` arabirimi üç yöntem sağlar:

- `Subscribe` bağlantıyı başlatır.
- `AddSymbol` izlemek için bir hisse senedi simgesi ekler.
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

Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir. Ekleme ve kaldırma işlemlerini uygulamak için birden çok yöntem kullanılması mümkün değildir ancak [Bölüm 3](protobuf-any-oneof.md)' te kapsanan `Any` türünü veya `oneof` anahtar sözcüğünü kullanarak tek bir akışta birden fazla ileti türü geçirebilirsiniz.

Kabul edilebilir olan belirli bir tür kümesinin olduğu durumlarda `oneof` daha iyi bir yoldur. Bir `AddSymbolRequest` ya da `RemoveSymbolRequest`tutabilecek bir `ActionMessage` kullanın:

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

`ActionMessage` iletilerinin akışını alan bir çift yönlü akış hizmeti bildirin:

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Bu hizmetin uygulanması, önceki örnekteki yönteme benzerdir, çünkü `Subscribe` yönteminin ilk parametresi, `Add` ve `Remove` isteklerini işlemek için kullanılabilen bir `IAsyncStreamReader<ActionMessage>`.

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

GRPC tarafından oluşturulan `ActionMessage` sınıfı, `Add` ve `Remove` özelliklerinden yalnızca birinin ayarlandığına güvence sağlar. Hangisinin `null` hangi türde bir ileti kullanıldığını bulmak için geçerli bir yoldur, ancak daha iyi bir yoldur. Kod oluşturma Ayrıca, aşağıdaki gibi görünen `ActionMessage` sınıfında bir `enum ActionOneOfCase` oluşturmuştur:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

`ActionMessage` nesnesindeki `ActionCase` özellik, hangi alanın ayarlandığını anlamak için bir `switch` ifadesiyle birlikte kullanılabilir:

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
> `switch` deyimin, bilinmeyen bir `ActionOneOfCase` değeriyle karşılaştığında uyarı kaydeden bir `default` durumu vardır. Bu, bir istemcinin daha fazla eylem ekleyen `.proto` dosyasının daha yeni bir sürümünü kullandığını göstermek için yararlı olabilir. Bunun nedeni, `switch` kullanmanın bilinen alanlar üzerinde `null` test ediden daha iyi olmasının bir nedenidir.

### <a name="use-fullstocktickerservice-from-a-client-application"></a>İstemci uygulamasından FullStockTickerService kullanma

Bu daha karmaşık istemcinin kullanımını gösteren basit bir .NET Core 3,0 WPF uygulaması vardır. Tam uygulamayı [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)' da bulabilirsiniz.

İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, bağımlılık ekleme işleminden `FullStockTicker.FullStockTickerClient` türünün bir örneğini alır:

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

`client.Subscribe()` yöntemi tarafından döndürülen nesne artık gRPC kitaplık türü `AsyncDuplexStreamingCall<TRequest, TResponse>`bir örneğidir. Bu, sunucuya istek göndermek için bir `RequestStream` ve yanıtları işlemeye yönelik bir `ResponseStream` sağlar.

İstek akışı, bazı WPF `ICommand` yöntemlerinden sembolleri eklemek ve kaldırmak için kullanılır. Her işlem için `ActionMessage` nesnesi üzerinde ilgili alanı ayarlayın:

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
> Bir ileti üzerinde `oneof` alan değerinin ayarlanması, önceden ayarlanmış olan tüm alanları otomatik olarak temizler.

Yanıt akışı `async` bir yöntemde işlenir. Geri döndürdüğü `Task` pencere kapatıldığında atılmaktadır:

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

### <a name="client-cleanup"></a>İstemci Temizleme

Pencere kapatıldığında ve `MainWindowViewModel` atıldığı zaman (`MainWindow``Closed` olayından), `AsyncDuplexStreamingCall` nesnesini düzgün bir şekilde elden çıkardığınızı öneririz. Özellikle, sunucu üzerindeki akışı düzgün bir şekilde kapatmak için `RequestStream` `CompleteAsync` yöntemi çağrılmalıdır. Bu örnekte örnek görünüm modelinden `DisposeAsync` yöntemi gösterilmektedir:

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

İstek akışlarını kapatmak, sunucunun kendi kaynaklarını zamanında elden atmalarını sağlar. Bu, hizmetlerin verimliliğini ve ölçeklenebilirliğini geliştirir ve özel durumları engeller.

>[!div class="step-by-step"]
>[Önceki](migrate-request-reply.md)
>[İleri](streaming-versus-repeated.md)
