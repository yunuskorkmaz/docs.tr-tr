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

Hizmetin, `ISimpleStockTickerCallback` verileri istemciye gerçek zamanlı olarak göndermek için geri çağırma arabirimini kullandığından, dönüş türü olmayan tek bir yöntemi vardır.

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

Hizmet tanımında iki ileti gerekir: bir istek ve akış için bir tane. Hizmet, `StockTickerUpdate` `stream` bildiriminde anahtar kelimesiyle iletinin bir akışını döndürür `return` . `Timestamp`Fiyat değişikliğinin tam süresini göstermek için güncelleştirmeye bir eklemeniz önerilir.

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

`StockPriceSubscriber` `TraderSys.StockMarket` Sınıf kitaplığındaki üç sınıfı hedef çözümde yeni bir .NET Standard sınıf kitaplığına kopyalayarak, WCF projesinden sahte öğesini yeniden kullanın. En iyi uygulamaları daha iyi izlemek için, `Factory` örnek oluşturmak üzere bir tür ekleyin ve `IStockPriceSubscriberFactory` ASP.NET Core bağımlılık ekleme hizmetleri ile kaydedin.

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

Bu sınıf artık gRPC 'yi uygulamak için kullanılabilir `StockTickerService` .

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

Gördüğünüz gibi, `.proto` dosyadaki bildirim yöntemi bir ileti akışı döndürse de, `StockTickerUpdate` aslında bir döndürür `Task` . Akışı oluşturma işi, üretilen kod ve yanıt akışını sağlayan gRPC çalışma zamanı kitaplıkları tarafından işlenir `IServerStreamWriter<StockTickerUpdate>` .

Bağlantı açıkken, hizmet sınıfı örneğinin etkin tutulduğu bir WCF çift yönlü hizmeti 'nin aksine, gRPC hizmeti, hizmeti canlı tutmak için döndürülen görevi kullanır. Bağlantı kapatılana kadar görevin tamamlanmamış olması gerekir.

Hizmet, kaynağından ' i kullanarak bağlantıyı ne zaman kapattığını söyleyebilir `CancellationToken` `ServerCallContext` . Basit bir statik yöntem, `AwaitCancellation` belirteç iptal edildiğinde tamamlanmış bir görev oluşturmak için kullanılır.

Yönteminde, `Subscribe` bir alın `StockPriceSubscriber` ve yanıt akışına yazan bir olay işleyicisi ekleyin. Ardından, `subscriber` verilerin kapalı akışa veri yazmaya çalışmasını engellemek için hemen elden alınmadan önce bağlantının kapatılmasını bekleyin.

`WriteUpdateAsync`Yöntemi, `try` / `catch` akışa bir ileti yazıldığında oluşabilecek hataları işlemek için bir bloğa sahiptir. Bu durum, her türlü milisaniyeye göre veya bir yerde bir hata nedeniyle kopmuş olan ağlar üzerinden kalıcı bağlantılarda önemli bir konudur.

### <a name="use-stocktickerservice-from-a-client-application"></a>İstemci uygulamasından StockTickerService kullanma

Dosyadan paylaşılabilir bir istemci sınıfı kitaplığı oluşturmak için önceki bölümdeki adımları izleyin `.proto` . Örnekte, istemcisinin nasıl kullanılacağını gösteren bir .NET konsol uygulaması vardır.

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

Akış zaman uyumsuz bir `DisplayAsync` metoda geçirilir. Uygulama daha sonra kullanıcının bir tuşa basmasını bekler ve sonra yöntemi iptal eder `DisplayAsync` ve çıkmadan önce görevin tamamlanmasını bekler.

> [!NOTE]
> Bu kod, `using` yöntemin çıkış sırasında akışa ve kanala atılırken yeni C# 8 bildirim söz dizimini kullanır `Main` . Küçük bir değişiklik, ancak girintili ve boş satırları azaltan bir çok iyi.

#### <a name="consume-the-stream"></a>Akışı tüketme

WCF, sunucunun doğrudan istemcide Yöntem çağırmasını sağlamak için geri çağırma arabirimlerini kullanır. gRPC akışları farklı şekilde çalışır. İstemci döndürülen akışın üzerinde yinelenir ve bir yerel yöntemden döndürüldüğünden olduğu gibi iletileri işler `IEnumerable` .

`IAsyncStreamReader<T>`Türü bir çok benzer `IEnumerator<T>` . `MoveNext`Daha fazla veri ve `Current` en son değeri döndüren bir özellik olan sürece true döndüren bir yöntem vardır. Tek fark, `MoveNext` yöntemin `Task<bool>` yalnızca bir yerine bir döndürmektedir `bool` . `ReadAllAsync`Genişletme yöntemi, akışı `IAsyncEnumerable` Yeni sözdizimi ile kullanılabilen standart bir C# 8 ' de sarmalar `await foreach` .

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
> Reaktif programlama düzenlerini kullanan geliştiriciler için, bu bölümün sonundaki [istemci kitaplıklarında](client-libraries.md#iobservable) bulunan bölüm, bir uzantı yönteminin ve bir sınıf içinde sarılacağı sınıfların nasıl ekleneceğini gösterir `IAsyncStreamReader<T>` `IObservable<T>` .

Yine de, ağ arızası nedeniyle özel durumları yakalamadığınızdan emin olun ve <xref:System.OperationCanceledException> kod döngüyü bölmek için bir kullandığından, bu durum, kaçınılmaz bir şekilde oluşturulur <xref:System.Threading.CancellationToken> . `RpcException`Türü, gRPC çalışma zamanı hataları hakkında, dahil olmak üzere çok yararlı bilgiler içerir `StatusCode` . Daha fazla bilgi için, bkz. [Bölüm 4 ' te *hata işleme*](error-handling.md).

## <a name="bidirectional-streaming"></a>Çift yönlü akış

WCF tam çift yönlü hizmeti, her iki yönde de zaman uyumsuz ve gerçek zamanlı mesajlaşma sağlar. Sunucu akışı örneğinde, istemci bir istek başlatır ve ardından bir güncelleştirme akışı alır. Bu hizmetin daha iyi bir sürümü, yeni bir aboneliği durdurup oluşturmak zorunda kalmadan, istemcinin listeden hisse senedi eklemesine ve kaldırmasına izin verir. Bu işlev [FullStockTicker örnek çözümünde](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)uygulandı.

`IFullStockTickerService`Arabirim üç yöntem sağlar:

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

Şu anda bir istemciden sunucuya ve diğeri sunucudan istemciye olan iki veri akışı olduğundan, bu düzenin gRPC 'de uygulanması daha basit bir işlemdir. Ekleme ve kaldırma işlemlerini uygulamak için birden çok yöntem kullanılması mümkün değildir ancak `Any` `oneof` [Bölüm 3](protobuf-any-oneof.md)' te kapsanan tür veya anahtar sözcüğünü kullanarak tek bir akışta birden fazla ileti türü geçirebilirsiniz.

Kabul edilebilir olan belirli bir tür kümesinin olması durumunda, `oneof` daha iyi bir yoldur. `ActionMessage`Ya da ' i tutabilecek bir kullanın `AddSymbolRequest` `RemoveSymbolRequest` :

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

İleti akışını alan bir çift yönlü akış hizmeti bildirin `ActionMessage` :

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Bu hizmetin uygulanması, yöntemin ilk parametresi dışında, `Subscribe` `IAsyncStreamReader<ActionMessage>` ve isteklerini işlemek için kullanılabilecek bir önceki örnekle benzerdir `Add` `Remove` :

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

`ActionMessage`GRPC tarafından oluşturulan sınıf, ve özelliklerinden yalnızca birinin ayarlanabilir olmasını garanti `Add` eder `Remove` . Hangi `null` tür bir ileti kullanıldığını belirlemenin geçerli bir yolu olduğunu bulmak, ancak daha iyi bir yoldur. Kod oluşturma, aşağıdaki `enum ActionOneOfCase` `ActionMessage` gibi görünen sınıfında de oluşturulur:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

`ActionCase`Nesne üzerindeki özelliği, `ActionMessage` `switch` hangi alanın ayarlandığını belirleyen bir ifadesiyle birlikte kullanılabilir:

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
> `switch`Bildiriminde, bilinmeyen bir `default` değer ile karşılaştığında uyarı kaydeden bir durum vardır `ActionOneOfCase` . Bu, bir istemcinin `.proto` daha fazla eylem ekleyen dosyanın daha yeni bir sürümünü kullandığını göstermek için yararlı olabilir. Bunun nedeni, `switch` bilinen alanlar üzerinde için test kullanmaktan daha iyi bir nedendir `null` .

### <a name="use-fullstocktickerservice-from-a-client-application"></a>İstemci uygulamasından FullStockTickerService kullanma

Bu daha karmaşık istemcinin kullanımını gösteren basit bir .NET WPF uygulaması vardır. Tam uygulamayı [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)' da bulabilirsiniz.

İstemci `MainWindowViewModel` sınıfında kullanılır ve bu, `FullStockTicker.FullStockTickerClient` bağımlılık ekleme işleminden türün bir örneğini alır:

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

Yöntemi tarafından döndürülen nesne `client.Subscribe()` artık gRPC kitaplık türünün bir örneğidir `AsyncDuplexStreamingCall<TRequest, TResponse>` . Bu, `RequestStream` sunucuya istek göndermek için ve yanıtlarını işlemek için bir sağlar `ResponseStream` .

İstek akışı, bazı WPF `ICommand` yöntemlerinden sembolleri eklemek ve kaldırmak için kullanılır. Her işlem için, bir nesne üzerinde ilgili alanı ayarlayın `ActionMessage` :

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
> Bir `oneof` ileti üzerinde bir alanın değerini ayarlamak, önceden ayarlanmış olan tüm alanları otomatik olarak temizler.

Yanıt akışı bir `async` yöntemde işlenir. `Task`Bu geri dönüş, pencere kapatıldığında atılmaktadır:

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

Pencere kapalıyken ve, bırakıldığında `MainWindowViewModel` ( `Closed` olayından `MainWindow` ), nesneyi doğru şekilde atmayı öneririz `AsyncDuplexStreamingCall` . Özellikle, `CompleteAsync` üzerindeki yönteminin, `RequestStream` akışı düzgün bir şekilde kapatmak için çağrılması gerekir. Bu örnek, `DisposeAsync` örnek görünüm modelinden yöntemi gösterir:

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
> [Sonraki](streaming-versus-repeated.md)
